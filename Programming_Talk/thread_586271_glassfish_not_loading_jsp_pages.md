---
title: "glassfish not loading jsp pages"
date: 2007-10-22
forum: Programming Talk
---

### Post by dguido on 2007-10-22
I installed glassfish (apt-get install glassfish) and went to localhost:8080 and 4848 and they both load fine. However, when I download the hello.war test app ([https://glassfish.dev.java.net/downloads/quickstart/index.html](https://glassfish.dev.java.net/downloads/quickstart/index.html)) into the domain1 autodeploy directory and try to browse to it, I got an HTTP 500 error like this:

```
type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException: java.lang.NoClassDefFoundError: org/apache/tools/ant/BuildListener

root cause

java.lang.NoClassDefFoundError: org/apache/tools/ant/BuildListener

note The full stack traces of the exception and its root causes are available in the Sun Java System Application Server Platform Edition 9.0_01 logs.
```

The logs look like this:

```
[#|2007-10-22T02:02:33.824-0500|SEVERE|sun-appserver-pe9.0|javax.enterprise.system.container.web|_ThreadID=13;_ThreadName=httpWorkerThread-8080-1;_RequestID=0d44dfaa-9fe9-4d7d-8481-3f94d635b0dc;|StandardWrapperValve[jsp]: Servlet.service() for servlet jsp threw exception
java.lang.NoClassDefFoundError: org/apache/tools/ant/BuildListener
        at org.apache.jasper.JspCompilationContext.createCompiler(JspCompilationContext.java:210)
        at org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:527)
        at org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:324)
        at org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:412)
        at org.apache.jasper.servlet.JspServlet.service(JspServlet.java:318)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:820)
        at org.apache.catalina.core.ApplicationFilterChain.servletService(ApplicationFilterChain.java:397)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:278)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:566)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:536)
        at org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:240)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:179)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:566)
        at com.sun.enterprise.web.WebPipeline.invoke(WebPipeline.java:73)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:182)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:566)
        at com.sun.enterprise.web.VirtualServerPipeline.invoke(VirtualServerPipeline.java:120)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:939)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:137)
        at org.apache.catalina.core.StandardPipeline.doInvoke(StandardPipeline.java:566)
        at org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:536)
        at org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:939)
        at org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:239)
        at com.sun.enterprise.web.connector.grizzly.ProcessorTask.invokeAdapter(ProcessorTask.java:667)
        at com.sun.enterprise.web.connector.grizzly.ProcessorTask.processNonBlocked(ProcessorTask.java:574)
        at com.sun.enterprise.web.connector.grizzly.ProcessorTask.process(ProcessorTask.java:844)
        at com.sun.enterprise.web.connector.grizzly.ReadTask.executeProcessorTask(ReadTask.java:287)
        at com.sun.enterprise.web.connector.grizzly.ReadTask.doTask(ReadTask.java:212)
        at com.sun.enterprise.web.connector.grizzly.TaskBase.run(TaskBase.java:252)
        at com.sun.enterprise.web.connector.grizzly.WorkerThread.run(WorkerThread.java:75)
|#]
```

Also, when I put a test.jsp page in the docroot, I get the same HTTP 500 error. I tried apt-get'ing ant but that wasn't the problem. Does anyone know what is going on?

---

### Post by dguido on 2007-10-22
I was just checking if I had the command-line tools mentioned at the bottom of Sun's quickstart document (linked to above) and I seem to be missing a bunch. Granted, Ubuntu is using Glassfish v1 and it looks like this guide is for v2, but I still think this could be a problem.

Could this be an environment variable problem? I see all the tools in /usr/share/sunappserver/bin but they're not in my PATH.

---

### Post by lavajumper on 2007-12-05
I'm having the same problem. One small step I found was to run :```

update-alternatives --config java
```
and select a sun-java option. Ant won't work without them.
I'm new to the java/sunappserver world so I can't offer more than that, and it only fixed the ant problem, the server is still not serving up pages.

---

### Post by Peter LaValle on 2008-01-08
Err ... I have the same problem too. I have tried the alternatives thing and I have tried installing Ant from apt-get ... but GlassFish didn't seem to care ...

I also tried the example app from netbeans on my Ubuntu server (the host in question) again; no joy.

---

### Post by ecimon on 2008-01-09
Hi,

This exception :
```

java.lang.NoClassDefFoundError: org/apache/tools/ant/BuildListener

```
says that you're missing BuildListener class in your CLASSPATH. You need to add ant.jar (and possibly other depending on it jars) to the server CLASSPATH. On Glassfish, you can do this from the admin panel (goto [http://localhost:4848](http://localhost:4848)). 

If you have installed ant package already, then ant.jar should be in /usr/share/ant/lib.

Good luck

---

