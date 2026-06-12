---
title: "Update to Ibex broke jdbc"
date: 2008-11-17
forum: Programming Talk
---

### Post by Dooley on 2008-11-17
Hi all,

Some java servlets that I was using with Gutsy have stopped working with the Interpid Ibex update. Basically I cannot seem to access my mysql databases anymore.

This is my /etc/environment at the moment
CLASSPATH=.:/usr/lib/jvm/java-6-sun/bin:/usr/share/tomcat5.5/common/lib/servlet-api.jar:/usr/share/tomcat5.5-webapps/ROOT/WEB-INF/classes/syshandlers:/usr/share/java/mysql.jar

I have also tried adding mysql.jar and mysql-connector.jar to eclipse manually, this worked for a non-root user but not for a root user, no luck at all.

Hope someone can help.
Cheers,
Dooley

---

### Post by Dooley on 2008-11-18
Can anyone help?

---

### Post by jespdj on 2008-11-18
Do you get any error messages? If so, then what are the error messages?

---

### Post by Dooley on 2008-11-18
Error messages, they would help. Looks to me like a standard class not found issue.

java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1363)
	at org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1209)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:169)
	at websysadmin.DBAccess.listAllTables(DBAccess.java:17)
	at org.apache.jsp.index_jsp._jspService(index_jsp.java:211)
	at org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:98)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:331)
	at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:329)
	at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:265)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:269)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:188)
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:213)
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:172)
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:127)
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:117)
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:108)
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:174)
	at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:874)
	at org.apache.coyote.http11.Http11BaseProtocol$Http11ConnectionHandler.processConnection(Http11BaseProtocol.java:665)
	at org.apache.tomcat.util.net.PoolTcpEndpoint.processSocket(PoolTcpEndpoint.java:528)
	at org.apache.tomcat.util.net.LeaderFollowerWorkerThread.runIt(LeaderFollowerWorkerThread.java:81)
	at org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:689)
	at java.lang.Thread.run(Thread.java:619)

---

### Post by Dooley on 2008-11-18
Actually it would probably be easier and better if I just used a non-root user running eclipse. However I use eclipse to start/stop tomcat.
 I don't actually need a root user to run tomcat, Im using port 8180.
So does anyone know how to set a non-root user startup tomcat.

Heres my error when I try.
18-Nov-2008 15:40:46 org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.io.FileNotFoundException: /usr/share/tomcat5.5/conf/server.xml (Permission denied)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:106)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:382)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:344)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:435)

---

### Post by jdmpike on 2008-11-24
I am having similar issues with JDBC in Tomcat 6 under Intrepid 64-bit.

I have installed tomcat6 and tomcat6-common, there is a symbolic link to commons-dbcp.jar that *should* contain BasicDataSourceFactory. Any help on this would be wonderful (stack trace below). I would guess that in less than 24 hours, I will just uninstall the packages and download the binary from Apache if there is no idea how to fix this.

```
SEVERE: Exception processing Global JNDI Resources
javax.naming.NamingException: Could not create resource factory instance [Root exception is java.lang.ClassNotFoundException: org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory]
        at org.apache.naming.factory.ResourceFactory.getObjectInstance(ResourceFactory.java:118)
        at javax.naming.spi.NamingManager.getObjectInstance(NamingManager.java:304)
        at org.apache.naming.NamingContext.lookup(NamingContext.java:793)
        at org.apache.naming.NamingContext.lookup(NamingContext.java:140)
        at org.apache.naming.NamingContextBindingsEnumeration.nextElementInternal(NamingContextBindingsEnumeration.java:113)
        at org.apache.naming.NamingContextBindingsEnumeration.next(NamingContextBindingsEnumeration.java:71)
        at org.apache.catalina.mbeans.GlobalResourcesLifecycleListener.createMBeans(GlobalResourcesLifecycleListener.java:137)
        at org.apache.catalina.mbeans.GlobalResourcesLifecycleListener.createMBeans(GlobalResourcesLifecycleListener.java:144)
        at org.apache.catalina.mbeans.GlobalResourcesLifecycleListener.createMBeans(GlobalResourcesLifecycleListener.java:109)
        at org.apache.catalina.mbeans.GlobalResourcesLifecycleListener.lifecycleEvent(GlobalResourcesLifecycleListener.java:81)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(LifecycleSupport.java:117)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:703)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:578)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177)
Caused by: java.lang.ClassNotFoundException: org.apache.tomcat.dbcp.dbcp.BasicDataSourceFactory
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at org.apache.naming.factory.ResourceFactory.getObjectInstance(ResourceFactory.java:114)
        ... 22 more

```

---

### Post by jespdj on 2008-11-24
> **Dooley said:**
> java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
This means that you don't have the MySQL driver in your classpath. Make sure it's in your classpath.

> **Dooley said:**
> Actually it would probably be easier and better if I just used a non-root user running eclipse. However I use eclipse to start/stop tomcat.
Running Eclipse as root is a bad idea. Make sure that you (as a normal user) have access to /usr/share/tomcat5.5/conf/server.xml.

**jdmpike** - that's a different problem than Dooley's. Please start your own topic in the forum instead of hijacking Dooley's topic.

---

