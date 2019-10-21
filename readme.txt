1、添加系统日志功能。20190422
   新建数据库表：
     /*
     Navicat MySQL Data Transfer
     Source Server         : sino-ets
     Source Server Version : 50718
     Target Server Type    : MYSQL
     Target Server Version : 50718
     File Encoding         : 65001
     Date: 2019-04-22 18:47:00
     */

     SET FOREIGN_KEY_CHECKS=0;

     -- ----------------------------
     -- Table structure for ap_sys_log
     -- ----------------------------
     DROP TABLE IF EXISTS `ap_sys_log`;
     CREATE TABLE `ap_sys_log` (
       `id` decimal(18,0) NOT NULL COMMENT '日志id',
       `type` char(1) DEFAULT '1' COMMENT '日志类型',
       `title` varchar(255) DEFAULT '' COMMENT '日志标题',
       `remote_addr` varchar(255) DEFAULT NULL COMMENT '操作IP地址',
       `user_agent` varchar(1000) DEFAULT NULL COMMENT '用户代理',
       `request_uri` varchar(255) DEFAULT NULL COMMENT '请求URI',
       `method` varchar(10) DEFAULT NULL COMMENT '操作方式',
       `params` text COMMENT '操作提交的数据',
       `time` mediumtext COMMENT '执行时间',
       `del_flag` char(1) DEFAULT '0' COMMENT '删除标记',
       `exception` text COMMENT '异常信息',
       `adt_id` decimal(18,0) DEFAULT NULL COMMENT '创建人ID',
       `adt_co_id` decimal(18,0) DEFAULT NULL COMMENT '创建人企业ID',
       `adt_time` datetime DEFAULT NULL COMMENT '创建时间',
       `adt_name` varchar(50) DEFAULT NULL,
       `ac_name` varchar(50) DEFAULT NULL COMMENT '组织名称',
       PRIMARY KEY (`id`)
     ) ENGINE=InnoDB DEFAULT CHARSET=utf8 ROW_FORMAT=DYNAMIC COMMENT='日志表';

   （1） 开启日志功能需要在spring-context文件中添加面向切面支持。
     <!-- 启动对@AspectJ注解的支持  -->
    <aop:aspectj-autoproxy proxy-target-class="true" />
   （2）在spring-mvc文件中添加：<aop:aspectj-autoproxy/>


