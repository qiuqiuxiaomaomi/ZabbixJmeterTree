# ZabbixJmeterTree
后台监控、性能测试


###安装部署
图文讲解zabbix安装全过程（5
http://www.ttlsa.com/zabbix/install-zabbix-on-linux-5-ttlsa/

![](https://i.imgur.com/tbbkyBk.png)

<pre>
Zabbix安装

      PHP
      Mysql
      Zabbix Server
      Zabbix Client

      Zabbix支持的通讯方式：
          1）agent
          2) ssh/telnet
          3) snmp(大部分网络设备支持这种，比如路由器，交换机等)
          5）ipmi(通过标准的ipmi硬件接口，监控被监控对象的物理特征，比如电压，温度，
                 风扇状态，电源状态等)
          6）jmx（监控JVM虚拟机时是一种非常不错的选择）


          一般情况下，将zabbix agent部署到被监控主机上，由agent采集数据，报告给负责监控
      的中心主机，中心主机也就是master/agent模型中的master，负责监控的中心主机被称作
      zabbix server， zabbix server将从agent端接收到的信息存储于zabbix的数据库中，
      我们把zabbix的数据库端称为zabbix data base，如果管理员需要查看各种监控信息，则
      需要zabbix的GUI,zabbix的GUI是一种web ui,我们称之为zabbix web，zabbix web是
      php编写的，所以，如果想要使用zabbix web展示相关监控信息，需要依赖LAMP环境，不管是
      zabbix server， zabbix web都需要连接到zabbix data base获取相关数据。

          当监控规模变得庞大时，我们可能有成千上万台设备需要监控，这时我们是否需要部署多套
      zabbix系统进行监控呢？如果部署多套zabbix监控系统，那么监控压力就会被分摊，但是，这
      些监控的对象将会被尽量平均的分配到不同的监控系统中，这个时候，我们就无法通过统一的
      监控入口，去监控这些对象了，虽然分摊了监控压力，但是也增加了监控工作的复杂度，那么
      我们到底该不该建立多套zabbix监控系统从而分摊巨大的监控压力呢？其实，zabbix天生就有
      处理这种问题的能力，因为zabbix支持分布式监控，我们可以把成千上万台的被监控对象分成
      不同的区域，每个区域中设置一台代理主机，区域内的每个被监控对象的信息被agent采集，提交
      给代理主机，在这个区域内，代理主机的作用就好比zabbix server，我们称这些代理主机为
      zabbix proxy， zabbix proxy再将收集到的信息统一提交给真正的zabbix server处理，
      这样，zabbix proxy分摊了zabbix server的压力，同时，我们还能够通过统一的监控入口，
      监控所有的对象。

      zabbix的工作模式：
            1）agent端将采集完的数据主动发送给server端，主动模式，对于agent来说是主动的。
            2）等待server端过来拉取数据，被动模式
</pre>