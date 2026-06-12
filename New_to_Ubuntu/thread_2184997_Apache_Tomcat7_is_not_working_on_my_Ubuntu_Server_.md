---
title: "Apache Tomcat7 is not working on my Ubuntu Server 12.04"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by Coolai on 2013-10-31
We have been creating servlets and animations on our Enterprise Java class and wanted to upload some of my projects on my home made server so that my classmates could see it online.

I followed this guide - [here]("https://www.digitalocean.com/community/articles/how-to-install-apache-tomcat-on-ubuntu-12-04") - on how to install tomcat7 on Ubuntu but when I run the command:

    ```
$CATALINA_HOME/bin/startup.sh
```

It doesn't seem to load the tomcat webpage.

Output of the command:

    ```
root@coolai:~# $CATALINA_HOME/bin/startup.sh
Using CATALINA_BASE:   /usr/share/tomcat7
Using CATALINA_HOME:   /usr/share/tomcat7
Using CATALINA_TMPDIR: /usr/share/tomcat7/temp
Using JRE_HOME:        /usr/lib/jvm/default-java
Using CLASSPATH:       /usr/share/tomcat7/bin/bootstrap.jar:/usr/share/tomcat7/bin/tomcat-juli.jar
```

Is it on how I installed tomcat7? Or is the problem from the configuration of my JAVA?

Edit:

Here is the output of my catalina.out log file:

```
root@coolai:~# cd /var/local/tomcat/logs
-bash: cd: /var/local/tomcat/logs: No such file or directory
root@coolai:~# cd /var/lib/tomcat7
root@coolai:/var/lib/tomcat7# tail -f /var/log/tomcat7/catalina.out
10 31, 13 11:33:47 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1808 ms
10 31, 13 11:56:47 PM org.apache.coyote.AbstractProtocol pause
INFO: Pausing ProtocolHandler ["http-bio-8080"]
10 31, 13 11:56:47 PM org.apache.catalina.core.StandardService stopInternal
INFO: Stopping service Catalina
10 31, 13 11:56:47 PM org.apache.coyote.AbstractProtocol stop
INFO: Stopping ProtocolHandler ["http-bio-8080"]
10 31, 13 11:56:47 PM org.apache.coyote.AbstractProtocol destroy
INFO: Destroying ProtocolHandler ["http-bio-8080"]
```

---

### Post by sandyd on 2013-10-31
are you installing using apt-get or the gz file?

Webapps should be  placed in  /var/lib/tomcat6/webapps/ (the .war files or the folder)

Tomcat should restart/start (if installed via apt-get which is reccomended) by running 
```

service tomcat7 restart
```

---

### Post by Coolai on 2013-11-02
I installed tomcat7 using apt-get.

Yeah, but when I try to open the *mypublicip*:8080 it doesn't show the tomcat page and just display an error.

Maybe I should have installed using the gz?

---

