###api文档


###对外接口

* 添加游戏接口

| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| game_id | Y | 游戏名称 |
| game_name | Y | 游戏名称 |
| version| Y | 版本 |

返回值

```javascript
	array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
  ),
)%
```

* 获取用户的信息
| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| unionid | Y | 用户标识 |
```javascript
	array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
    'open_id' => 'o6_bmjrPTlm6_2sgVt7hMZOPfL2M',
    'nickname' => 'Band',
    'sex' => 1,
    'language' => '"zh_CN',
    'province' => '广东',
    'country' => '中国',
    'headimgurl' => 'http://wx.qlogo.cn/mmopen/g3MonUZtNHkdmzicIlibx6iaFqAc56vxLSUfpb6n5WKSYVY0ChQKkiaJSgQ1dZuTOgvLLrhJbERQQ4eMsv84eavHiaiceqxibJxCfHe/0',
  ),
)
```


* 开始游戏申请唯一的记录id
| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| game_id | Y | 游戏id |
| open_id | Y | 用户唯一标识 |
| app_id | N | 标识 |

返回值

```javascript
array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
    'unique_id' => 289005532186377472,
  ),
)
```

* 记录用户在游戏中的轨迹

| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| uniqueid | Y | 用户此次的游戏的唯一标识 |
| start_time | N | 开始时间 |
| run_time| N | 游戏时长 |

返回值
```javascript
	array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
  ),
)
```

* 记录用户的运行的次数
| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| uniqueid | Y | 用户此次的游戏的唯一标识 |
| num | Y | 运行次数 |

* 记录用户的成绩

| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| uniqueid | Y | 游戏名称 |
| game_id | Y | 游戏名称 |
| score   | Y | 得分 |

返回值

```javascript
array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
  ),
)
```
* 获取排行列表
| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| app_id | Y | 服务号_id |
| game_id | Y | 游戏_id |
| num   | Y | 获取数量 |

```javascript
array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
    0 =>
    array (
      'open_id' => 'o6_bmjrPTlm6_2sgVt7hMZOPfL2M',
      'score' => 100,
      'nickname' => 'Band',
      'headimgurl' => 'http://wx.qlogo.cn/mmopen/g3MonUZtNHkdmzicIlibx6iaFqAc56vxLSUfpb6n5WKSYVY0ChQKkiaJSgQ1dZuTOgvLLrhJbERQQ4eMsv84eavHiaiceqxibJxCfHe/0',
    ),
    1 =>
    array (
      'open_id' => 'o6_bmjrPTlm6_2sgVt7hMZOPfL2M',
      'score' => 99,
      'nickname' => 'Band',
      'headimgurl' => 'http://wx.qlogo.cn/mmopen/g3MonUZtNHkdmzicIlibx6iaFqAc56vxLSUfpb6n5WKSYVY0ChQKkiaJSgQ1dZuTOgvLLrhJbERQQ4eMsv84eavHiaiceqxibJxCfHe/0',
    ),
  ),
)
```
* 获取用户在游戏中的名次
 获取排行列表
| 参数 | 是否必须 | 说明 | | 
|:---:|:---:|:---:|:---:|
| app_id | Y | 服务号_id |
| game_id | Y | 游戏_id |
| user_id   | Y | 用户id |

```返回值
array (
  'code' => 200,
  'msg' => 'ok',
  'datas' =>
  array (
    'open_id' => 'o6_bmjrPTlm6_2sgVt7hMZOPfL2M',
    'order' => 1,
    'score' => 99,
    'nickname' => 'Band',
    'headimgurl' => 'http://wx.qlogo.cn/mmopen/g3MonUZtNHkdmzicIlibx6iaFqAc56vxLSUfpb6n5WKSYVY0ChQKkiaJSgQ1dZuTOgvLLrhJbERQQ4eMsv84eavHiaiceqxibJxCfHe/0',
  ),
)
```

### 基础信息表


### 记录游戏的信息
*  game_id,game_name,vesion,add_time
### 玩家来源
user_id,from
### 记录玩家的信息
* user_id,user_name,pic,sex
### 用户与游戏的关联
* user_id,game_id,play_time,add_time
### 记录玩家在游戏中的成绩 (后期根据游戏id分表)
* user_id,game_id,user_score,add_time,update_time


### table
* 游戏表
```javascript
CREATE TABLE `game_info` (
  `game_id` int(11) NOT NULL AUTO_INCREMENT COMMENT '游戏id',
  `game_name` varchar(200) DEFAULT NULL COMMENT '游戏名称',
  `version` tinyint NOT NULL DEFAULT '0' COMMENT '版本信息',
  `add_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`game_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

* 用户信息表
```javascript
CREATE TABLE `user_info` (
  `openid` int(11) NOT NULL AUTO_INCREMENT COMMENT '游戏id',
  `nickname` varchar(200) DEFAULT NULL COMMENT '游戏名称',
  `sex` tinyint NOT NULL DEFAULT '0' COMMENT '版本信息',
  `language` varchar(200) DEFAULT NULL COMMENT '语言',
  `city` int(11) NOT NULL AUTO_INCREMENT COMMENT '城市',
  `province` varchar(200) DEFAULT NULL COMMENT '身份',
  `country` varchar(200) DEFAULT NULL COMMENT '国家',
  `headimgurl` varchar(200) DEFAULT NULL COMMENT '头像',
  `unionid` varchar(200) DEFAULT NULL COMMENT '用户唯一ID',
  `from` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`game_id`),
  KEY `category_id` (`game_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

```
* 用户与游戏的关联

```javascript
CREATE TABLE `user_game` (
  `user_id` int(11) NOT NULL AUTO_INCREMENT COMMENT '游戏id',
  `game_id` varchar(200) DEFAULT NULL COMMENT '用户id',
  `play_time` tinyint NOT NULL DEFAULT '0' COMMENT '版本信息',
  `score` tinyint NOT NULL DEFAULT '0' COMMENT '版本信息',
  `status` tinyint NOT NULL DEFAULT '0' COMMENT '是否运行结束',
   `add_time` timestamp NOT NULL DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `update_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
  PRIMARY KEY (`user_id`),
  KEY `category_id` (`game_id`,`game_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8; 
```

* 记录用户的unique_id
|:---:|:---:|:---:|:---:|

| open_id | Y | 用户唯一标识 |
| unqiue_id | N | 标识 |
| add_time | N | 标识 |

