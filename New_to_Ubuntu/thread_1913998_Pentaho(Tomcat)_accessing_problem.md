---
title: "Pentaho(Tomcat) accessing problem"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by marsyas on 2012-01-23
I've installed pentaho on ubuntu.After installation there werent any problem but after restarting pc i cant access the pentaho console.

I try to start pentaho by using start-pentaho.sh

Here is the error :

[[IMG]http://img9.imageshack.us/img9/8148/tomcat.th.png[/img]](http://imageshack.us/photo/my-images/9/tomcat.png/)

---

### Post by lechien73 on 2012-01-23
Hi and welcome to the forums,

You could check the contents of pentaho.log and catalina.out in your tomcat directory. These should give you some idea as to why it's failing.

Common reasons include a problem communicating with the database server, or the chosen port (8081 in your case) being already in use. The default port for pentaho is 8080, so you may need to change the listening port in other configuration files as well.

---

### Post by marsyas on 2012-01-23
After installation there was no problem with port(8081) but after restarting pc it started to give error.(BI Server (Tomcat) startup port: 8081--From Installation Summary.txt)

I cant understand the log files.Will i share?

---

### Post by lechien73 on 2012-01-23
Yes, by all means attach them here. I have to go to a meeting in a few minutes, but I'll take a look when I get back if no one else has commented on them in the meantime :)

---

### Post by marsyas on 2012-01-23
Pentaho.log
```
2012-01-23 22:32:17,208 ERROR [org.hibernate.util.JDBCExceptionReporter] Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
2012-01-23 22:32:17,835 ERROR [org.hibernate.util.JDBCExceptionReporter] Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
2012-01-23 22:32:17,837 ERROR [org.hibernate.tool.hbm2ddl.SchemaUpdate] could not get database metadata
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1116)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:344)
	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2333)
	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2370)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2154)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:792)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:381)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:169)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriverManager(DriverManagerDataSource.java:174)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriver(DriverManagerDataSource.java:165)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnectionFromDriver(AbstractDriverBasedDataSource.java:149)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnection(AbstractDriverBasedDataSource.java:119)
	at org.springframework.orm.hibernate3.LocalDataSourceConnectionProvider.getConnection(LocalDataSourceConnectionProvider.java:82)
	at org.hibernate.tool.hbm2ddl.SuppliedConnectionProviderConnectionHelper.prepare(SuppliedConnectionProviderConnectionHelper.java:27)
	at org.hibernate.tool.hbm2ddl.SchemaUpdate.execute(SchemaUpdate.java:127)
	at org.hibernate.impl.SessionFactoryImpl.<init>(SessionFactoryImpl.java:314)
	at org.hibernate.cfg.Configuration.buildSessionFactory(Configuration.java:1300)
	at org.springframework.orm.hibernate3.LocalSessionFactoryBean.newSessionFactory(LocalSessionFactoryBean.java:814)
	at org.springframework.orm.hibernate3.LocalSessionFactoryBean.buildSessionFactory(LocalSessionFactoryBean.java:732)
	at org.springframework.orm.hibernate3.AbstractSessionFactoryBean.afterPropertiesSet(AbstractSessionFactoryBean.java:211)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1369)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveManagedList(BeanDefinitionValueResolver.java:287)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:126)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:168)
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:884)
	at org.springframework.security.intercept.web.FIDSToFilterChainMapConverter.<init>(FIDSToFilterChainMapConverter.java:54)
	at org.springframework.security.util.FilterChainProxy.afterPropertiesSet(FilterChainProxy.java:119)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1369)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:429)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:728)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:380)
	at org.springframework.web.context.ContextLoader.createWebApplicationContext(ContextLoader.java:255)
	at org.springframework.web.context.ContextLoader.initWebApplicationContext(ContextLoader.java:199)
	at org.springframework.web.context.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:45)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:4135)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4630)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
Caused by: java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at java.net.Socket.<init>(Socket.java:392)
	at java.net.Socket.<init>(Socket.java:235)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:257)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:294)
	... 148 more
2012-01-23 22:32:17,844 ERROR [org.hibernate.tool.hbm2ddl.SchemaUpdate] could not complete schema update
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1116)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:344)
	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2333)
	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2370)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2154)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:792)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:381)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:169)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriverManager(DriverManagerDataSource.java:174)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriver(DriverManagerDataSource.java:165)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnectionFromDriver(AbstractDriverBasedDataSource.java:149)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnection(AbstractDriverBasedDataSource.java:119)
	at org.springframework.orm.hibernate3.LocalDataSourceConnectionProvider.getConnection(LocalDataSourceConnectionProvider.java:82)
	at org.hibernate.tool.hbm2ddl.SuppliedConnectionProviderConnectionHelper.prepare(SuppliedConnectionProviderConnectionHelper.java:27)
	at org.hibernate.tool.hbm2ddl.SchemaUpdate.execute(SchemaUpdate.java:127)
	at org.hibernate.impl.SessionFactoryImpl.<init>(SessionFactoryImpl.java:314)
	at org.hibernate.cfg.Configuration.buildSessionFactory(Configuration.java:1300)
	at org.springframework.orm.hibernate3.LocalSessionFactoryBean.newSessionFactory(LocalSessionFactoryBean.java:814)
	at org.springframework.orm.hibernate3.LocalSessionFactoryBean.buildSessionFactory(LocalSessionFactoryBean.java:732)
	at org.springframework.orm.hibernate3.AbstractSessionFactoryBean.afterPropertiesSet(AbstractSessionFactoryBean.java:211)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1369)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveManagedList(BeanDefinitionValueResolver.java:287)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:126)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:168)
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:884)
	at org.springframework.security.intercept.web.FIDSToFilterChainMapConverter.<init>(FIDSToFilterChainMapConverter.java:54)
	at org.springframework.security.util.FilterChainProxy.afterPropertiesSet(FilterChainProxy.java:119)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1369)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:429)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:728)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:380)
	at org.springframework.web.context.ContextLoader.createWebApplicationContext(ContextLoader.java:255)
	at org.springframework.web.context.ContextLoader.initWebApplicationContext(ContextLoader.java:199)
	at org.springframework.web.context.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:45)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:4135)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4630)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
Caused by: java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at java.net.Socket.<init>(Socket.java:392)
	at java.net.Socket.<init>(Socket.java:235)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:257)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:294)
	... 148 more
2012-01-23 22:32:18,128 ERROR [org.hibernate.util.JDBCExceptionReporter] Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
2012-01-23 22:32:18,130 ERROR [org.hibernate.util.JDBCExceptionReporter] Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
2012-01-23 22:32:18,137 ERROR [org.springframework.web.context.ContextLoader] Context initialization failed
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'filterChainProxy' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Invocation of init method failed; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'authenticationProcessingFilter' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Cannot resolve reference to bean 'authenticationManager' while setting bean property 'authenticationManager'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'authenticationManager' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Cannot resolve reference to bean 'daoAuthenticationProvider' while setting bean property 'providers' with key [0]; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'daoAuthenticationProvider' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userDetailsService' while setting bean property 'userDetailsService'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userDetailsService' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userRoleDao' while setting bean property 'userRoleDao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1338)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:429)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:728)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:380)
	at org.springframework.web.context.ContextLoader.createWebApplicationContext(ContextLoader.java:255)
	at org.springframework.web.context.ContextLoader.initWebApplicationContext(ContextLoader.java:199)
	at org.springframework.web.context.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:45)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:4135)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4630)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'authenticationProcessingFilter' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Cannot resolve reference to bean 'authenticationManager' while setting bean property 'authenticationManager'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'authenticationManager' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Cannot resolve reference to bean 'daoAuthenticationProvider' while setting bean property 'providers' with key [0]; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'daoAuthenticationProvider' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userDetailsService' while setting bean property 'userDetailsService'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userDetailsService' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userRoleDao' while setting bean property 'userRoleDao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:275)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:168)
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:884)
	at org.springframework.security.intercept.web.FIDSToFilterChainMapConverter.<init>(FIDSToFilterChainMapConverter.java:54)
	at org.springframework.security.util.FilterChainProxy.afterPropertiesSet(FilterChainProxy.java:119)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1369)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	... 39 more
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'authenticationManager' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security.xml]: Cannot resolve reference to bean 'daoAuthenticationProvider' while setting bean property 'providers' with key [0]; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'daoAuthenticationProvider' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userDetailsService' while setting bean property 'userDetailsService'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userDetailsService' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userRoleDao' while setting bean property 'userRoleDao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:275)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveManagedList(BeanDefinitionValueResolver.java:287)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:126)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	... 56 more
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'daoAuthenticationProvider' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userDetailsService' while setting bean property 'userDetailsService'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userDetailsService' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userRoleDao' while setting bean property 'userRoleDao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:275)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	... 71 more
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userDetailsService' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Cannot resolve reference to bean 'userRoleDao' while setting bean property 'userRoleDao'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:275)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveValueIfNecessary(BeanDefinitionValueResolver.java:104)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.applyPropertyValues(AbstractAutowireCapableBeanFactory.java:1245)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.populateBean(AbstractAutowireCapableBeanFactory.java:1010)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:472)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	... 84 more
Caused by: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'userRoleDao' defined in file [/home/pc/pentaho/server/biserver-ee/pentaho-solutions/system/applicationContext-spring-security-hibernate.xml]: Invocation of init method failed; nested exception is org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1338)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:473)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory$1.run(AbstractAutowireCapableBeanFactory.java:409)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:380)
	at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:264)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:261)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:185)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:164)
	at org.springframework.beans.factory.support.BeanDefinitionValueResolver.resolveReference(BeanDefinitionValueResolver.java:269)
	... 97 more
Caused by: org.springframework.transaction.CannotCreateTransactionException: Could not open Hibernate Session for transaction; nested exception is org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.springframework.orm.hibernate3.HibernateTransactionManager.doBegin(HibernateTransactionManager.java:599)
	at org.springframework.transaction.support.AbstractPlatformTransactionManager.getTransaction(AbstractPlatformTransactionManager.java:374)
	at org.springframework.transaction.support.TransactionTemplate.execute(TransactionTemplate.java:125)
	at org.pentaho.platform.engine.security.userroledao.hibernate.UserRoleDaoTransactionDecorator.getUsers(UserRoleDaoTransactionDecorator.java:117)
	at org.pentaho.platform.engine.security.userroledao.hibernate.sample.SampleUsersAndRolesInitHandler.handleInit(SampleUsersAndRolesInitHandler.java:58)
	at org.pentaho.platform.engine.security.userroledao.hibernate.HibernateUserRoleDao.init(HibernateUserRoleDao.java:77)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeCustomInitMethod(AbstractAutowireCapableBeanFactory.java:1414)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1375)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1335)
	... 107 more
Caused by: org.hibernate.exception.JDBCConnectionException: Cannot open connection
	at org.hibernate.exception.SQLStateConverter.convert(SQLStateConverter.java:74)
	at org.hibernate.exception.JDBCExceptionHelper.convert(JDBCExceptionHelper.java:43)
	at org.hibernate.exception.JDBCExceptionHelper.convert(JDBCExceptionHelper.java:29)
	at org.hibernate.jdbc.ConnectionManager.openConnection(ConnectionManager.java:426)
	at org.hibernate.jdbc.ConnectionManager.getConnection(ConnectionManager.java:144)
	at org.hibernate.jdbc.JDBCContext.connection(JDBCContext.java:119)
	at org.hibernate.transaction.JDBCTransaction.begin(JDBCTransaction.java:57)
	at org.hibernate.impl.SessionImpl.beginTransaction(SessionImpl.java:1326)
	at org.springframework.orm.hibernate3.HibernateTransactionManager.doBegin(HibernateTransactionManager.java:558)
	... 119 more
Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1116)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:344)
	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2333)
	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2370)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2154)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:792)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:381)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(DriverManager.java:620)
	at java.sql.DriverManager.getConnection(DriverManager.java:169)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriverManager(DriverManagerDataSource.java:174)
	at org.springframework.jdbc.datasource.DriverManagerDataSource.getConnectionFromDriver(DriverManagerDataSource.java:165)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnectionFromDriver(AbstractDriverBasedDataSource.java:149)
	at org.springframework.jdbc.datasource.AbstractDriverBasedDataSource.getConnection(AbstractDriverBasedDataSource.java:119)
	at org.springframework.orm.hibernate3.LocalDataSourceConnectionProvider.getConnection(LocalDataSourceConnectionProvider.java:82)
	at org.hibernate.jdbc.ConnectionManager.openConnection(ConnectionManager.java:423)
	... 124 more
Caused by: java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:327)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:193)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:180)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at java.net.Socket.<init>(Socket.java:392)
	at java.net.Socket.<init>(Socket.java:235)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:257)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:294)
	... 144 more
2012-01-23 22:32:18,191 ERROR [org.pentaho.platform.util.logging.Logger] Error: Pentaho
2012-01-23 22:32:18,191 ERROR [org.pentaho.platform.util.logging.Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.scheduler.QuartzSystemListener
java.lang.NullPointerException
	at org.pentaho.platform.scheduler.QuartzSystemListener.shutdown(QuartzSystemListener.java:183)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
2012-01-23 22:32:18,192 ERROR [org.pentaho.platform.util.logging.Logger] Error end:
2012-01-23 22:32:18,192 ERROR [org.pentaho.platform.util.logging.Logger] Error: Pentaho
2012-01-23 22:32:18,192 ERROR [org.pentaho.platform.util.logging.Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.engine.services.connection.datasource.dbcp.PooledDatasourceSystemListener
java.lang.NullPointerException
	at org.pentaho.platform.engine.core.system.PentahoSystem.getCacheManager(PentahoSystem.java:973)
	at org.pentaho.platform.engine.services.connection.datasource.dbcp.PooledDatasourceSystemListener.shutdown(PooledDatasourceSystemListener.java:80)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
2012-01-23 22:32:18,193 ERROR [org.pentaho.platform.util.logging.Logger] Error end:
2012-01-23 22:32:18,195 ERROR [org.pentaho.platform.util.logging.Logger] Error: Pentaho
2012-01-23 22:32:18,195 ERROR [org.pentaho.platform.util.logging.Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.plugin.services.pluginmgr.PluginAdapter
java.lang.NullPointerException
	at org.pentaho.platform.engine.core.system.PentahoSystem.get(PentahoSystem.java:551)
	at org.pentaho.platform.engine.core.system.PentahoSystem.get(PentahoSystem.java:533)
	at org.pentaho.platform.plugin.services.pluginmgr.PluginAdapter.shutdown(PluginAdapter.java:47)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
2012-01-23 22:32:18,196 ERROR [org.pentaho.platform.util.logging.Logger] Error end:
```

catalina.out
```
22:32:18,191 ERROR [Logger] Error: Pentaho
22:32:18,191 ERROR [Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.scheduler.QuartzSystemListener
java.lang.NullPointerException
	at org.pentaho.platform.scheduler.QuartzSystemListener.shutdown(QuartzSystemListener.java:183)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
22:32:18,192 ERROR [Logger] Error end:
22:32:18,192 ERROR [Logger] Error: Pentaho
22:32:18,192 ERROR [Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.engine.services.connection.datasource.dbcp.PooledDatasourceSystemListener
java.lang.NullPointerException
	at org.pentaho.platform.engine.core.system.PentahoSystem.getCacheManager(PentahoSystem.java:973)
	at org.pentaho.platform.engine.services.connection.datasource.dbcp.PooledDatasourceSystemListener.shutdown(PooledDatasourceSystemListener.java:80)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
22:32:18,193 ERROR [Logger] Error end:
22:32:18,195 ERROR [Logger] Error: Pentaho
22:32:18,195 ERROR [Logger] misc-org.pentaho.platform.engine.core.system.PentahoSystem: PentahoSystem.ERROR_0015 - Error while trying to execute shutdown sequence for org.pentaho.platform.plugin.services.pluginmgr.PluginAdapter
java.lang.NullPointerException
	at org.pentaho.platform.engine.core.system.PentahoSystem.get(PentahoSystem.java:551)
	at org.pentaho.platform.engine.core.system.PentahoSystem.get(PentahoSystem.java:533)
	at org.pentaho.platform.plugin.services.pluginmgr.PluginAdapter.shutdown(PluginAdapter.java:47)
	at org.pentaho.platform.engine.core.system.PentahoSystem.shutdown(PentahoSystem.java:793)
	at org.pentaho.platform.web.http.context.SolutionContextListener.contextDestroyed(SolutionContextListener.java:215)
	at org.apache.catalina.core.StandardContext.listenerStop(StandardContext.java:4174)
	at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4778)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4675)
	at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:791)
	at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:771)
	at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:546)
	at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:637)
	at org.apache.catalina.startup.HostConfig.deployDescriptors(HostConfig.java:563)
	at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:498)
	at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1277)
	at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:321)
	at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:119)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:785)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:445)
	at org.apache.catalina.core.StandardService.start(StandardService.java:519)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:581)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:289)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:414)
22:32:18,196 ERROR [Logger] Error end:
[Server@1c1c92b]: Initiating shutdown sequence...
[Server@1c1c92b]: Shutdown sequence completed in 1 ms.
[Server@1c1c92b]: 2012-01-23 22:32:18.198 SHUTDOWN : System.exit() was not called
Jan 23, 2012 10:32:18 PM org.apache.catalina.loader.WebappClassLoader clearReferencesJdbc
SEVERE: The web application [/pentaho] registered the JBDC driver [mondrian.olap4j.MondrianOlap4jDriver] but failed to unregister it when the web application was stopped. To prevent a memory leak, the JDBC Driver has been forcibly unregistered.
Jan 23, 2012 10:32:18 PM org.apache.catalina.loader.WebappClassLoader clearReferencesThreads
SEVERE: The web application [/pentaho] appears to have started a thread named [HSQLDB Timer @15e538e] but has failed to stop it. This is very likely to create a memory leak.
Jan 23, 2012 10:32:18 PM org.apache.catalina.loader.WebappClassLoader clearReferencesThreads
SEVERE: The web application [/pentaho] appears to have started a thread named [Timer-0] but has failed to stop it. This is very likely to create a memory leak.
Jan 23, 2012 10:32:19 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory ROOT
Jan 23, 2012 10:32:19 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory sw-style
Jan 23, 2012 10:32:19 PM org.apache.catalina.startup.HostConfig deployDirectory
INFO: Deploying web application directory pentaho-style
Jan 23, 2012 10:32:19 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8081
Jan 23, 2012 10:32:19 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8024
Jan 23, 2012 10:32:19 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/28  config=null
Jan 23, 2012 10:32:19 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 13201 ms
```

---

### Post by lechien73 on 2012-01-23
Hmmm...could you try editing pentaho's web.xml file and commenting out the following snippet:

```
<listener>
<listener-class>org.pentaho.platform.web.http.context.HsqldbStartupListener</listener-class>
</listener>
```

Then try restarting pentaho again?

---

### Post by marsyas on 2012-01-23
i edited web.xml under /home/pc/pentaho/server/biserver-ee/tomcat/webapps/pentaho/WEB-INF but the result is same.

---

### Post by lechien73 on 2012-01-23
Ok, then I'm afraid I've reached the limit of my knowledge.

I'm not trying to pass the buck, but I don't think this is an Ubuntu issue, and I know that the same issue has been covered many times over at [http://forums.pentaho.com/](http://forums.pentaho.com/)

Maybe you could post the same question over there. I'm sure that you would get a quicker response. Leave the comment open here and greater minds than mine might be able to help as well :D

---

### Post by marsyas on 2012-01-23
Thank you so much :)

---

### Post by marsyas on 2012-01-26
```
pc@pc:~/pentaho3/server/biserver-ee$ ./start-pentaho.sh
/home/pc/pentaho3/server/biserver-ee
/home/pc/pentaho3/server/biserver-ee
DEBUG: Found JAVA two folders up
DEBUG: Found Pentaho License two folders up
DEBUG: _PENTAHO_JAVA_HOME=/home/pc/pentaho3/server/biserver-ee/../../java
DEBUG: _PENTAHO_JAVA=/home/pc/pentaho3/server/biserver-ee/../../java/bin/java
DEBUG: PENTAHO_INSTALLED_LICENSE_PATH=/home/pc/pentaho3/server/biserver-ee/../../.installedLicenses.xml
Using CATALINA_BASE:   /home/pc/pentaho3/server/biserver-ee/tomcat
Using CATALINA_HOME:   /home/pc/pentaho3/server/biserver-ee/tomcat
Using CATALINA_TMPDIR: /home/pc/pentaho3/server/biserver-ee/tomcat/temp
Using JRE_HOME:        /home/pc/pentaho3/server/biserver-ee/../../java
Using CLASSPATH:       /home/pc/pentaho3/server/biserver-ee/tomcat/bin/bootstrap.jar

```

---

