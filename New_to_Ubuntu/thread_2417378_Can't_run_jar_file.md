---
title: "Can't run jar file"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by lamlengend98 on 2019-04-23
I have a jar file from a project. So, i run "java -jar xxx.jar" and it happened although it's normal if i run in intellij 


```
2019-04-23 11:49:36.756  INFO 30642 --- [           main] org.hibernate.Version                    : HHH000412: Hibernate Core {5.0.12.Final}
2019-04-23 11:49:36.758  INFO 30642 --- [           main] org.hibernate.cfg.Environment            : HHH000206: hibernate.properties not found
2019-04-23 11:49:36.759  INFO 30642 --- [           main] org.hibernate.cfg.Environment            : HHH000021: Bytecode provider name : javassist
2019-04-23 11:49:36.813  INFO 30642 --- [           main] o.hibernate.annotations.common.Version   : HCANN000001: Hibernate Commons Annotations {5.0.1.Final}
2019-04-23 11:49:37.237  INFO 30642 --- [           main] org.hibernate.dialect.Dialect            : HHH000400: Using dialect: org.hibernate.dialect.MySQL5Dialect
2019-04-23 11:49:38.252  INFO 30642 --- [           main] j.LocalContainerEntityManagerFactoryBean : Initialized JPA EntityManagerFactory for persistence unit 'default'
2019-04-23 11:49:40.105  WARN 30642 --- [           main] ationConfigEmbeddedWebApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'processService': Bean with name 'processService' has been injected into other beans [mailReceiveRuleService] in its raw version as part of a circular reference, but has eventually been wrapped. This means that said other beans do not use the final version of the bean. This is often the result of over-eager type matching - consider using 'getBeanNamesOfType' with the 'allowEagerInit' flag turned off, for example.
2019-04-23 11:49:40.124  INFO 30642 --- [           main] j.LocalContainerEntityManagerFactoryBean : Closing JPA EntityManagerFactory for persistence unit 'default'
2019-04-23 11:49:40.141  INFO 30642 --- [           main] o.apache.catalina.core.StandardService   : Stopping service [Tomcat]
2019-04-23 11:49:40.168  INFO 30642 --- [           main] utoConfigurationReportLoggingInitializer : 


Error starting ApplicationContext. To display the auto-configuration report re-run your application with 'debug' enabled.
2019-04-23 11:49:40.178 ERROR 30642 --- [           main] o.s.boot.SpringApplication               : Application startup failed


org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'processService': Bean with name 'processService' has been injected into other beans [mailReceiveRuleService] in its raw version as part of a circular reference, but has eventually been wrapped. This means that said other beans do not use the final version of the bean. This is often the result of over-eager type matching - consider using 'getBeanNamesOfType' with the 'allowEagerInit' flag turned off, for example.
    at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:585) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:483) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.AbstractBeanFactory$1.getObject(AbstractBeanFactory.java:306) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:230) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:302) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:197) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:761) ~[spring-beans-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:867) ~[spring-context-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:543) ~[spring-context-4.3.13.RELEASE.jar!/:4.3.13.RELEASE]
    at org.springframework.boot.context.embedded.EmbeddedWebApplicationContext.refresh(EmbeddedWebApplicationContext.java:122) ~[spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:693) [spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:360) [spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:303) [spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1118) [spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1107) [spring-boot-1.5.9.RELEASE.jar!/:1.5.9.RELEASE]
    at io.owslab.mailreceiver.MailReceiverApplication.main(MailReceiverApplication.java:44) [classes!/:0.0.1-SNAPSHOT]
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_201]
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_201]
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_201]
    at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_201]
    at org.springframework.boot.loader.MainMethodRunner.run(MainMethodRunner.java:48) [MailReceiver-0.0.1-SNAPSHOT.jar:0.0.1-SNAPSHOT]
    at org.springframework.boot.loader.Launcher.launch(Launcher.java:87) [MailReceiver-0.0.1-SNAPSHOT.jar:0.0.1-SNAPSHOT]
    at org.springframework.boot.loader.Launcher.launch(Launcher.java:50) [MailReceiver-0.0.1-SNAPSHOT.jar:0.0.1-SNAPSHOT]
    at org.springframework.boot.loader.JarLauncher.main(JarLauncher.java:51) [MailReceiver-0.0.1-SNAPSHOT.jar:0.0.1-SNAPSHOT]
```

---

### Post by wildmanne39 on 2019-04-23
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

