---
title: "eclipse tomcat catalina error"
date: 2012-05-20
forum: Programming Talk
---

### Post by KRISHNASHK on 2012-05-20
hi , i have installed eclipse ,jdk and tomcat6. when  i run my project on server i get the following error

May 20, 2012 2:45:22 PM org.apache.tomcat.util.digester.SetPropertiesRule begin
WARNING: [SetPropertiesRule]{Server/Service/Engine/Host/Context} Setting property 'source' to 'org.eclipse.jst.jee.server:BusinessIntelligence' did not find a matching property.
May 20, 2012 2:45:22 PM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
May 20, 2012 2:45:22 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 525 ms
May 20, 2012 2:45:22 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
May 20, 2012 2:45:22 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.28
May 20, 2012 2:45:22 PM org.apache.catalina.loader.WebappClassLoader validateJarFile
INFO: validateJarFile(/home/krishna/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps/BusinessIntelligence/WEB-INF/lib/servlet-api.jar) - jar not loaded. See Servlet Spec 2.3, section 9.7.2. Offending class: javax/servlet/Servlet.class
May 20, 2012 2:45:23 PM org.apache.struts.action.ActionServlet initChain
INFO: Loading chain catalog from jar:file:/home/krishna/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/wtpwebapps/BusinessIntelligence/WEB-INF/lib/struts-core-1.3.10.jar!/org/apache/struts/chain/chain-config.xml
May 20, 2012 2:45:23 PM org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
May 20, 2012 2:45:23 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1048 ms
May 20, 2012 2:59:24 PM org.apache.catalina.loader.WebappClassLoader modified
SEVERE:     Resource '/WEB-INF/lib/antlr-2.7.2.jar' is missing
May 20, 2012 2:59:24 PM org.apache.catalina.core.StandardContext reload
INFO: Reloading this Context has started
May 20, 2012 2:59:24 PM org.apache.catalina.session.StandardManager doUnload
SEVERE: IOException while saving persisted sessions: java.io.FileNotFoundException: /home/krishna/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/BusinessIntelligence/SESSIONS.ser (No such file or directory)
java.io.FileNotFoundException: /home/krishna/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/BusinessIntelligence/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:495)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:469)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:673)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4774)
    at org.apache.catalina.core.StandardContext.reload(StandardContext.java:3385)
    at org.apache.catalina.loader.WebappLoader.backgroundProcess(WebappLoader.java:426)
    at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBase.java:1309)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1601)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1610)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1610)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.run(ContainerBase.java:1590)
    at java.lang.Thread.run(Thread.java:636)
May 20, 2012 2:59:24 PM org.apache.catalina.session.StandardManager stop
SEVERE: Exception unloading sessions to persistent storage
java.io.FileNotFoundException: /home/krishna/workspace/.metadata/.plugins/org.eclipse.wst.server.core/tmp0/work/Catalina/localhost/BusinessIntelligence/SESSIONS.ser (No such file or directory)
    at java.io.FileOutputStream.open(Native Method)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
    at java.io.FileOutputStream.<init>(FileOutputStream.java:99)
    at org.apache.catalina.session.StandardManager.doUnload(StandardManager.java:495)
    at org.apache.catalina.session.StandardManager.unload(StandardManager.java:469)
    at org.apache.catalina.session.StandardManager.stop(StandardManager.java:673)
    at org.apache.catalina.core.StandardContext.stop(StandardContext.java:4774)
    at org.apache.catalina.core.StandardContext.reload(StandardContext.java:3385)
    at org.apache.catalina.loader.WebappLoader.backgroundProcess(WebappLoader.java:426)
    at org.apache.catalina.core.ContainerBase.backgroundProcess(ContainerBase.java:1309)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1601)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1610)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.processChildren(ContainerBase.java:1610)
    at org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.run(ContainerBase.java:1590)
    at java.lang.Thread.run(Thread.java:636)

plz help? should i fix the catalina environment variable,

---

