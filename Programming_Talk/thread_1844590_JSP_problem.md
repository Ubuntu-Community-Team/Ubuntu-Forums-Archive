---
title: "JSP problem"
date: 2011-09-15
forum: Programming Talk
---

### Post by kunal00731 on 2011-09-15
Hi guys ,
facing a critical problem . Kindly advice.
I am suing spring 2.5.6 and tomcat 6.0.14.
when i deploy my project , i get some errors like :


```
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.AprLifecycleListener init
INFO: The Apache Tomcat Native library which allows optimal performance in produ
ction environments was not found on the java.library.path: C:\Program Files\jdk1
.6.0\bin;.;C:\Windows\Sun\Java\bin;C:\Windows\system32;C:\Windows;C:\Windows\sys
tem32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\
v1.0\;D:\SOFTWARES\apache-ant-1.8.2-bin\apache-ant-1.8.2\bin
Sep 15, 2011 9:25:06 AM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
Sep 15, 2011 9:25:06 AM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 692 ms
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.14
Sep 15, 2011 9:25:07 AM org.apache.catalina.loader.WebappClassLoader validateJar
File
INFO: validateJarFile(C:\Users\253876\apache-tomcat-6.0.14\webapps\springapp\WEB
-INF\lib\servlet-api.jar) - jar not loaded. See Servlet Spec 2.3, section 9.7.2.
 Offending class: javax/servlet/Servlet.class
Sep 15, 2011 9:25:08 AM org.springframework.web.servlet.FrameworkServlet initSer
vletBean
INFO: FrameworkServlet 'action': initialization started
Sep 15, 2011 9:25:08 AM org.springframework.context.support.AbstractApplicationC
ontext prepareRefresh
INFO: Refreshing org.springframework.web.context.support.XmlWebApplicationContex
t@c2ee15: display name [WebApplicationContext for namespace 'action-servlet']; s
tartup date [Thu Sep 15 09:25:08 ACT 2011]; root of context hierarchy
Sep 15, 2011 9:25:08 AM org.springframework.beans.factory.xml.XmlBeanDefinitionR
eader loadBeanDefinitions
INFO: Loading XML bean definitions from ServletContext resource [/WEB-INF/action
-servlet.xml]
Sep 15, 2011 9:25:08 AM org.springframework.web.servlet.FrameworkServlet initSer
vletBean
SEVERE: Context initialization failed
org.springframework.beans.factory.BeanDefinitionStoreException: IOException pars
ing XML document from ServletContext resource [/WEB-INF/action-servlet.xml]; nes
ted exception is java.io.FileNotFoundException: Could not open ServletContext re
source [/WEB-INF/action-servlet.xml]
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:349)
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:310)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:143)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:178)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:149)
        at org.springframework.web.context.support.XmlWebApplicationContext.load
BeanDefinitions(XmlWebApplicationContext.java:124)
        at org.springframework.web.context.support.XmlWebApplicationContext.load
BeanDefinitions(XmlWebApplicationContext.java:92)
        at org.springframework.context.support.AbstractRefreshableApplicationCon
text.refreshBeanFactory(AbstractRefreshableApplicationContext.java:123)
        at org.springframework.context.support.AbstractApplicationContext.obtain
FreshBeanFactory(AbstractApplicationContext.java:422)
        at org.springframework.context.support.AbstractApplicationContext.refres
h(AbstractApplicationContext.java:352)
        at org.springframework.web.servlet.FrameworkServlet.createWebApplication
Context(FrameworkServlet.java:402)
        at org.springframework.web.servlet.FrameworkServlet.initWebApplicationCo
ntext(FrameworkServlet.java:316)
        at org.springframework.web.servlet.FrameworkServlet.initServletBean(Fram
eworkServlet.java:282)
        at org.springframework.web.servlet.HttpServletBean.init(HttpServletBean.
java:126)
        at javax.servlet.GenericServlet.init(GenericServlet.java:212)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.
java:1161)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:98
1)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex
t.java:4045)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4
351)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase
.java:791)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:77
1)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:525)

        at org.apache.catalina.startup.HostConfig.deployDirectory(HostConfig.jav
a:920)
        at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.j
ava:883)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:492
)
        at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1138)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:311)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:117)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)

        at org.apache.catalina.core.StandardHost.start(StandardHost.java:719)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)

        at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443
)
        at org.apache.catalina.core.StandardService.start(StandardService.java:5
16)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:710
)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:566)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)
Caused by: java.io.FileNotFoundException: Could not open ServletContext resource
 [/WEB-INF/action-servlet.xml]
        at org.springframework.web.context.support.ServletContextResource.getInp
utStream(ServletContextResource.java:116)
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:336)
        ... 40 more

```


Kindly advice on this.

---

### Post by kunal00731 on 2011-09-17
Hi solved it.

---

### Post by Smart Viking on 2011-09-17
Can you share the solution? There might be future visitors redirected here by the search engines, they would probably like the solution.

---

### Post by psrdotcom on 2011-09-17
Yes, Please share your solution.

---

### Post by lisati on 2011-09-17
> **kunal00731 said:**
> Hi guys ,
facing a critical problem . Kindly advice.
I am suing spring 2.5.6 and tomcat 6.0.14.
when i deploy my project , i get some errors like :


```
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.AprLifecycleListener init
INFO: The Apache Tomcat Native library which allows optimal performance in produ
ction environments was not found on the java.library.path: C:\Program Files\jdk1
.6.0\bin;.;C:\Windows\Sun\Java\bin;C:\Windows\system32;C:\Windows;C:\Windows\sys
tem32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\
v1.0\;D:\SOFTWARES\apache-ant-1.8.2-bin\apache-ant-1.8.2\bin
Sep 15, 2011 9:25:06 AM org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
Sep 15, 2011 9:25:06 AM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 692 ms
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Sep 15, 2011 9:25:06 AM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.14
Sep 15, 2011 9:25:07 AM org.apache.catalina.loader.WebappClassLoader validateJar
File
INFO: validateJarFile(C:\Users\253876\apache-tomcat-6.0.14\webapps\springapp\WEB
-INF\lib\servlet-api.jar) - jar not loaded. See Servlet Spec 2.3, section 9.7.2.
 Offending class: javax/servlet/Servlet.class
Sep 15, 2011 9:25:08 AM org.springframework.web.servlet.FrameworkServlet initSer
vletBean
INFO: FrameworkServlet 'action': initialization started
Sep 15, 2011 9:25:08 AM org.springframework.context.support.AbstractApplicationC
ontext prepareRefresh
INFO: Refreshing org.springframework.web.context.support.XmlWebApplicationContex
t@c2ee15: display name [WebApplicationContext for namespace 'action-servlet']; s
tartup date [Thu Sep 15 09:25:08 ACT 2011]; root of context hierarchy
Sep 15, 2011 9:25:08 AM org.springframework.beans.factory.xml.XmlBeanDefinitionR
eader loadBeanDefinitions
INFO: Loading XML bean definitions from ServletContext resource [/WEB-INF/action
-servlet.xml]
Sep 15, 2011 9:25:08 AM org.springframework.web.servlet.FrameworkServlet initSer
vletBean
SEVERE: Context initialization failed
org.springframework.beans.factory.BeanDefinitionStoreException: IOException pars
ing XML document from ServletContext resource [/WEB-INF/action-servlet.xml]; nes
ted exception is java.io.FileNotFoundException: Could not open ServletContext re
source [/WEB-INF/action-servlet.xml]
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:349)
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:310)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:143)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:178)
        at org.springframework.beans.factory.support.AbstractBeanDefinitionReade
r.loadBeanDefinitions(AbstractBeanDefinitionReader.java:149)
        at org.springframework.web.context.support.XmlWebApplicationContext.load
BeanDefinitions(XmlWebApplicationContext.java:124)
        at org.springframework.web.context.support.XmlWebApplicationContext.load
BeanDefinitions(XmlWebApplicationContext.java:92)
        at org.springframework.context.support.AbstractRefreshableApplicationCon
text.refreshBeanFactory(AbstractRefreshableApplicationContext.java:123)
        at org.springframework.context.support.AbstractApplicationContext.obtain
FreshBeanFactory(AbstractApplicationContext.java:422)
        at org.springframework.context.support.AbstractApplicationContext.refres
h(AbstractApplicationContext.java:352)
        at org.springframework.web.servlet.FrameworkServlet.createWebApplication
Context(FrameworkServlet.java:402)
        at org.springframework.web.servlet.FrameworkServlet.initWebApplicationCo
ntext(FrameworkServlet.java:316)
        at org.springframework.web.servlet.FrameworkServlet.initServletBean(Fram
eworkServlet.java:282)
        at org.springframework.web.servlet.HttpServletBean.init(HttpServletBean.
java:126)
        at javax.servlet.GenericServlet.init(GenericServlet.java:212)
        at org.apache.catalina.core.StandardWrapper.loadServlet(StandardWrapper.
java:1161)
        at org.apache.catalina.core.StandardWrapper.load(StandardWrapper.java:98
1)
        at org.apache.catalina.core.StandardContext.loadOnStartup(StandardContex
t.java:4045)
        at org.apache.catalina.core.StandardContext.start(StandardContext.java:4
351)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase
.java:791)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:77
1)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:525)

        at org.apache.catalina.startup.HostConfig.deployDirectory(HostConfig.jav
a:920)
        at org.apache.catalina.startup.HostConfig.deployDirectories(HostConfig.j
ava:883)
        at org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:492
)
        at org.apache.catalina.startup.HostConfig.start(HostConfig.java:1138)
        at org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java
:311)
        at org.apache.catalina.util.LifecycleSupport.fireLifecycleEvent(Lifecycl
eSupport.java:117)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1053)

        at org.apache.catalina.core.StandardHost.start(StandardHost.java:719)
        at org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1045)

        at org.apache.catalina.core.StandardEngine.start(StandardEngine.java:443
)
        at org.apache.catalina.core.StandardService.start(StandardService.java:5
16)
        at org.apache.catalina.core.StandardServer.start(StandardServer.java:710
)
        at org.apache.catalina.startup.Catalina.start(Catalina.java:566)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.
java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces
sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)
Caused by: java.io.FileNotFoundException: Could not open ServletContext resource
 [/WEB-INF/action-servlet.xml]
        at org.springframework.web.context.support.ServletContextResource.getInp
utStream(ServletContextResource.java:116)
        at org.springframework.beans.factory.xml.XmlBeanDefinitionReader.loadBea
nDefinitions(XmlBeanDefinitionReader.java:336)
        ... 40 more

```


Kindly advice on this.

I will happily advi**s**e with some advi**c**e: Please use "code" tags and share your solution.

---

### Post by kunal00731 on 2011-09-20
sure i will, kindly give me some time, i am little busy with the deliverables, will  post it in few days.

---

### Post by moldaviax on 2011-10-19
This problem is discussed here

[http://forum.springsource.org/archive/index.php/t-41601.html](http://forum.springsource.org/archive/index.php/t-41601.html)

M.

---

