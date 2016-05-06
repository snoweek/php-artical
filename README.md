# artical
artical是一个基于php和mysql的文章发布系统

##数据库artical表信息
如果数据连接信息，例如数据库名或密码发生变化，可以到functions中的connect_mysql.php中修改。
* user
```
CREATE TABLE `user` (
  `user_id` mediumint(8) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(30) DEFAULT NULL,
  `password` varchar(40) DEFAULT NULL,
  `email` varchar(60) DEFAULT NULL,
  `register_date` datetime DEFAULT NULL,
  PRIMARY KEY (`user_id`),
  UNIQUE KEY `name` (`name`),
  UNIQUE KEY `email` (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
表user包含四列，user_id记录用户注册的顺序，同时用作主键;name记录用户的名称;password记录用户的密码;email记录用户的邮箱,register_date记录用户注册的时间。

* work

```
CREATE TABLE `work` (
  `work_id` mediumint(8) unsigned NOT NULL AUTO_INCREMENT,
  `name` text,
  `user_id` mediumint(8) DEFAULT NULL,
  `create_time` datetime DEFAULT NULL,
  PRIMARY KEY (`work_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
表work包含三列，work_id用于记录文集的个数;name用于记录文集的名称;
user_id是指此文集所属的用户。两个表之间以user_id来连接。

* artical
```

CREATE TABLE `artical` (
  `artical_id` mediumint(8) unsigned NOT NULL AUTO_INCREMENT,
  `title` text,
  `content` text,
  `user_id` mediumint(8) DEFAULT NULL,
  `work_id` mediumint(8) DEFAULT NULL,
  `write_time` datetime DEFAULT NULL,
  PRIMARY KEY (`artical_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
表artical包含六列，artical_id用于记录文章的个数;title用于记录文章的标题,content用于记录文章的内容;
user_id是指此文章所属的用户，work_id是指此文章所属的文集。

##License
Apache 
