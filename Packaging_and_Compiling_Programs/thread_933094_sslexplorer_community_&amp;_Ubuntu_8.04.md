---
title: "sslexplorer community &amp; Ubuntu 8.04"
date: 2008-09-29
forum: Packaging and Compiling Programs
---

### Post by erict35 on 2008-09-29
Hi,
 
I'm trying to install the last RC17 community version on a fresh Ubuntu 8.04 fr.
 
I install the java5 and ant packages from Synaptic and compile sslexplorer with ant install & ant install-service.
 
All the compile and install process worked fine.
 
I modify the wrapper.conf file in order to add this line :
 
wrapper.java.additional.1=-Dfile.encoding=UTF-8
 
and 
 
file.encoding=UTF-8 in the system.properties file.
 
All is correct with the configuration phase on [http://ip:20080](http://ip:20080)
 
As I try to connect in ssl mode with [https://ip](https://ip) the sslexplorer service is not started (nothing in ps -ax or netstat).
 
So, I finally start it with "/etc/init.d/sslexplore console".
 
The first time it works and I can create a local network ressource as the foler /home/test/Public then upload a 30 megs file with the SSL Firefox 3.0 interface.
 
Now I retry and I have this error message in the console mode :
 
root@test-desktop:/home/test# /etc/init.d/sslexplorer console Running SSL-Explorer...
wrapper | --> Wrapper Started as Console wrapper | Launching a JVM...
jvm 1 | Wrapper (Version 3.1.2) [http://wrapper.tanukisoftware.org](http://wrapper.tanukisoftware.org)
jvm 1 | 
jvm 1 | org.mortbay.util.MultiException[java.lang.IllegalArgumentException: ]
jvm 1 | at org.mortbay.http.HttpServer.doStart(HttpServer.java:732)
jvm 1 | at org.mortbay.util.Container.start(Container.java:71)
jvm 1 | at com.sslexplorer.server.Main$5.run(Main.java:984)
jvm 1 | java.lang.IllegalArgumentException: 
jvm 1 | at com.sun.net.ssl.internal.ssl.ProtocolVersion.valueOf(ProtocolVersion.java:120)
jvm 1 | at com.sun.net.ssl.internal.ssl.ProtocolList.<init>(ProtocolList.java:36)
jvm 1 | at com.sun.net.ssl.internal.ssl.SSLServerSocketImpl.setEnabledProtocols(SSLServerSocketImpl.java:182)
jvm 1 | at com.sslexplorer.server.jetty.CustomJsseListener.newServerSocket(CustomJsseListener.java:161)
jvm 1 | at org.mortbay.util.ThreadedServer.open(ThreadedServer.java:476)
jvm 1 | at org.mortbay.util.ThreadedServer.start(ThreadedServer.java:502)
jvm 1 | at org.mortbay.http.SocketListener.start(SocketListener.java:202)
jvm 1 | at org.mortbay.http.HttpServer.doStart(HttpServer.java:762)
jvm 1 | at org.mortbay.util.Container.start(Container.java:71)
jvm 1 | at com.sslexplorer.server.Main$5.run(Main.java:984)
jvm 1 | java.lang.IllegalArgumentException: 
jvm 1 | at com.sun.net.ssl.internal.ssl.ProtocolVersion.valueOf(ProtocolVersion.java:120)
jvm 1 | at com.sun.net.ssl.internal.ssl.ProtocolList.<init>(ProtocolList.java:36)
jvm 1 | at com.sun.net.ssl.internal.ssl.SSLServerSocketImpl.setEnabledProtocols(SSLServerSocketImpl.java:182)
jvm 1 | at com.sslexplorer.server.jetty.CustomJsseListener.newServerSocket(CustomJsseListener.java:161)
jvm 1 | at org.mortbay.util.ThreadedServer.open(ThreadedServer.java:476)
jvm 1 | at org.mortbay.util.ThreadedServer.start(ThreadedServer.java:502)
jvm 1 | at org.mortbay.http.SocketListener.start(SocketListener.java:202)
jvm 1 | at org.mortbay.http.HttpServer.doStart(HttpServer.java:762)
jvm 1 | at org.mortbay.util.Container.start(Container.java:71)
jvm 1 | at com.sslexplorer.server.Main$5.run(Main.java:984)
wrapper | <-- Wrapper Stopped
 
Any helps appreciated.
 
Best Regards
Eric

---

