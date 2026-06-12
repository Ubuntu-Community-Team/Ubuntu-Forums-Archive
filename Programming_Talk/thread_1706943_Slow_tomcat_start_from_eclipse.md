---
title: "Slow tomcat start from eclipse"
date: 2011-03-14
forum: Programming Talk
---

### Post by Paul Weaver on 2011-03-14
I'm running eclipse on a 64bit 10.10 laptop. All works fine with normal eclipse, and all works fine when I'm writing a servlet, however Catalina takes forever to start up (well, 20 seconds)

It smells like some timeout on something like DNS, but wireshark doesn't show anything obvious. 

```

14-Mar-2011 20:35:20 org.apache.catalina.core.AprLifecycleListener init
INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/amd64/server:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.24/jre/../lib/amd64:/usr/lib64/xulrunner-addons:/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib
14-Mar-2011 20:35:20 org.apache.tomcat.util.digester.SetPropertiesRule begin
WARNING: [SetPropertiesRule]{Server/Service/Engine/Host/Context} Setting property 'source' to 'org.eclipse.jst.jee.server:Testweb' did not find a matching property.
14-Mar-2011 20:35:41 org.apache.coyote.http11.Http11Protocol init
INFO: Initializing Coyote HTTP/1.1 on http-8080
14-Mar-2011 20:35:41 org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 21621 ms
14-Mar-2011 20:35:41 org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
14-Mar-2011 20:35:41 org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/6.0.24
14-Mar-2011 20:35:42 org.apache.coyote.http11.Http11Protocol start
INFO: Starting Coyote HTTP/1.1 on http-8080
14-Mar-2011 20:35:42 org.apache.catalina.startup.Catalina start
INFO: Server startup in 405 ms
```

Any ideas how to diagnose it? Servers config has the following settings:

Server name: Tomcat v6.0 Server at localhost
Hostname: 127.0.0.1
Runtime: Apache Tomcat 6.0

It's very frustrating. By comparison I have a jboss (3.2.3!) environment that starts up a tone of stuff, talking to various other systems, in under 20 seconds, so I don't think it's a general problem about being underspecced (i5 M520, ssd, 8GB ram)

---

### Post by Paul Weaver on 2011-04-26
The problem turned out to be ipv6 -- I have ip6tables dropping all incoming and outgoing IPv6, including that on the local loopback. This caused tomcat/eclipse great problems.

---

