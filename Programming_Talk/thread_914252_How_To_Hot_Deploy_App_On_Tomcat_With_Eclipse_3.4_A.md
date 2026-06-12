---
title: "How To Hot Deploy App On Tomcat With Eclipse 3.4 And Maven2.0.8"
date: 2008-09-08
forum: Programming Talk
---

### Post by FreeSpeech1981 on 2008-09-08
Hi,

I'm trying to configure my Eclipse 3.4 environment with Maven2.0.8 and Tomcat 6.0.18 to be able to use the 'Servers' tab in Eclipse to deploy my application.

I don't know what to give you to help you help me. All I can say is that I can generate a .war file that I copy to the Tomcat webapps folder and everything's working just fine. So I guess that my pom.xml is ok.

When I try to deploy via the 'Servers' tab in Eclipse, I receive this error :

```

8-Sep-2008 4:07:41 PM org.apache.catalina.core.StandardContext listenerStart
SEVERE: Error configuring application listener of class org.springframework.web.context.ContextLoaderListener
java.lang.ClassNotFoundException: org.springframework.web.context.ContextLoaderListener
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1387)
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1233)
	at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:3786)
	at org.apache.catalina.core.StandardContext.start(StandardContext.java:4342)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardHost.start(StandardHost.java:719)
	at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)
	at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443)
	at org.apache.catalina.core.StandardService.start(StandardService.java:516)
	at org.apache.catalina.core.StandardServer.start(StandardServer.java:710)
	at org.apache.catalina.startup.Catalina.start(Catalina.java:578)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)

```

It looks like my librairies are not linked with the application !! As you can see, I use Spring and Hibernate by the way ! ;)

Thanks in advance for any help you can give !

FS

PS : If it can help you I have the WTP 3.0 and Maven Embedder 2.1.0 plugins installed for Eclipse

---

