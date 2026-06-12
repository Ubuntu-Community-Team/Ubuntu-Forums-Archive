---
title: "Tomcat8 on ubuntu 14, first run, then did not start ..."
date: 2014-12-16
forum: New to Ubuntu
---

### Post by JWebDev on 2014-12-16
Hi, I'm trying to understand what's wrong, tried all that interenet says - do not understand the reason.


Copy the folder tomcat starts from her - the first launch passed, everything is OK. 

The first off, I could no longer start.
Changed the new clean version, load the machine - does not work.


That's what I try.
Why the server does not start?

```

root@ubuntu-14:~# netstat -a | grep 8005
root@ubuntu-14:~# netstat -a | grep 8009
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/startup.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Tomcat started.
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# netstat -a | grep 8009
tcp6       0      0 [::]:8009               [::]:*                  LISTEN
root@ubuntu-14:~# netstat -a | grep 8005
root@ubuntu-14:~# lsof -i :8080
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java    1167 root   49u  IPv6  10051      0t0  TCP *:http-alt (LISTEN)
root@ubuntu-14:~# lsof -i :8005
root@ubuntu-14:~# lsof -i :8009
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
java    1167 root   54u  IPv6  10055      0t0  TCP *:8009 (LISTEN)
root@ubuntu-14:~# kill -15 1167
root@ubuntu-14:~# lsof -i :8009
root@ubuntu-14:~# netstat -a | grep 8009
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/startup.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Tomcat started.
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# netstat -a | grep 8009
tcp6       0      0 [::]:8009               [::]:*                  LISTEN
root@ubuntu-14:~# netstat -a | grep 8005
root@ubuntu-14:~# ps -ef | grep tomcat
root      1208     1  2 20:12 pts/0    00:00:03 /usr/lib/jvm/java-8-oracle/bin/java -Djava.util.logging.config.file=/usr/local/apache-tomcat-8.0.15/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/local/apache-tomcat-8.0.15/endorsed -classpath /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/apache-tomcat-8.0.15 -Dcatalina.home=/usr/local/apache-tomcat-8.0.15 -Djava.io.tmpdir=/usr/local/apache-tomcat-8.0.15/temp org.apache.catalina.startup.Bootstrap start
root      1233  1138  0 20:14 pts/0    00:00:00 grep --color=auto tomcat
root@ubuntu-14:~# kill -15 1208
root@ubuntu-14:~# kill -15 1233
-bash: kill: (1233) - No such process
root@ubuntu-14:~# ps -ef | grep tomcat
root      1240  1138  0 20:14 pts/0    00:00:00 grep --color=auto tomcat
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/startup.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Tomcat started.
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# netstat -a | grep 8009
tcp6       0      0 [::]:8009               [::]:*                  LISTEN
root@ubuntu-14:~# ps -ef | grep tomcat
root      1249     1 15 20:15 pts/0    00:00:03 /usr/lib/jvm/java-8-oracle/bin/java -Djava.util.logging.config.file=/usr/local/apache-tomcat-8.0.15/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/local/apache-tomcat-8.0.15/endorsed -classpath /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar -Dcatalina.base=/usr/local/apache-tomcat-8.0.15 -Dcatalina.home=/usr/local/apache-tomcat-8.0.15 -Djava.io.tmpdir=/usr/local/apache-tomcat-8.0.15/temp org.apache.catalina.startup.Bootstrap start
root      1270  1138  0 20:15 pts/0    00:00:00 grep --color=auto tomcat
root@ubuntu-14:~# kill -9 1249
root@ubuntu-14:~# ps -ef | grep tomcat
root      1274  1138  0 20:15 pts/0    00:00:00 grep --color=auto tomcat
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/startup.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Tomcat started.
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# netstat -a | grep 8009
tcp6       0      0 [::]:8009               [::]:*                  LISTEN
root@ubuntu-14:~#



```


It is noteworthy that after the start of the lift only from on port 8009, the other ports do not work - that's what the log says.



```
 vim /usr/local/apache-tomcat-8.0.15/logs/catalina.out

```


```

root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/shutdown.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Dec 15, 2014 8:30:57 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Could not contact localhost:8005. Tomcat may not be running.
Dec 15, 2014 8:30:57 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop:
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:345)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at java.net.Socket.connect(Socket.java:538)
        at java.net.Socket.<init>(Socket.java:434)
        at java.net.Socket.<init>(Socket.java:211)
        at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:450)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:483)
        at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:400)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:487)



```

Try to stop the server

```

root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/shutdown.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Dec 15, 2014 8:30:57 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Could not contact localhost:8005. Tomcat may not be running.
Dec 15, 2014 8:30:57 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop:
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:345)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at java.net.Socket.connect(Socket.java:538)
        at java.net.Socket.<init>(Socket.java:434)
        at java.net.Socket.<init>(Socket.java:211)
        at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:450)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:483)
        at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:400)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:487)



```


Trying to start again, kill processes, the last command just kills putty session ... is necessary to login again after ...


```

root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/startup.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Tomcat started.
root@ubuntu-14:~# netstat -a | grep 8080
root@ubuntu-14:~# /usr/local/apache-tomcat-8.0.15/bin/shutdown.sh
Using CATALINA_BASE:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_HOME:   /usr/local/apache-tomcat-8.0.15
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-8.0.15/temp
Using JRE_HOME:        /usr/lib/jvm/java-8-oracle
Using CLASSPATH:       /usr/local/apache-tomcat-8.0.15/bin/bootstrap.jar:/usr/local/apache-tomcat-8.0.15/bin/tomcat-juli.jar
Dec 15, 2014 8:33:53 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Could not contact localhost:8005. Tomcat may not be running.
Dec 15, 2014 8:33:53 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop:
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:345)
        at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)
        at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)
        at java.net.Socket.connect(Socket.java:589)
        at java.net.Socket.connect(Socket.java:538)
        at java.net.Socket.<init>(Socket.java:434)
        at java.net.Socket.<init>(Socket.java:211)
        at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:450)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:483)
        at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:400)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:487)


root@ubuntu-14:~# ps -ef | grep 8005
root      1670  1607  0 20:34 pts/0    00:00:00 grep --color=auto 8005
root@ubuntu-14:~# ps -ef | grep 8009
root      1672  1607  0 20:34 pts/0    00:00:00 grep --color=auto 8009
root@ubuntu-14:~# ps -ef | grep 8080
root      1674  1607  0 20:34 pts/0    00:00:00 grep --color=auto 8080
root@ubuntu-14:~# kill -15 1607
root@ubuntu-14:~# ps -ef | grep 8080
root      1676  1607  0 20:34 pts/0    00:00:00 grep --color=auto 8080
root@ubuntu-14:~# kill -9 1607



```

thanks

---

