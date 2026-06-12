---
title: "CATALINA_HOME - Ubuntu - Eclipse"
date: 2006-11-29
forum: Programming Talk
---

### Post by JimTDI on 2006-11-29
I've installed Tomcat5 on Ubuntu 6.06LTS - runs just fine!

Now I've installed an Eclipse plugin for Tomcat - and I get this error from within Eclipse when trying to "talk" to Tomcat.

[COLOR="Blue"]Bootstrap: Class loader creation threw exception
java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory
	at org.apache.tomcat.util.compat.JdkCompat.<clinit>(JdkCompat.java:55)
	at org.apache.catalina.startup.ClassLoaderFactory.<clinit>(ClassLoaderFactory.java:63)
	at org.apache.catalina.startup.Bootstrap.initClassLoaders(Bootstrap.java:103)
	at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:196)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:402)[/COLOR]

I suspect I need to set the CATALINA_HOME environment variable so Eclipse can pick it up, but I'm not sure which directory to specify CATALINA_HOME to point to.  Tomcat was simply installed thru Synaptic.  Can someone help me out as to what I should set it to?   Thank you!!

---

### Post by firebadger on 2006-11-30
Not sure where, but try...
>locate catalina.sh

That file should be here...  CATALINA_HOME/bin/catalina.sh

---

### Post by JimTDI on 2006-11-30
> **firebadger said:**
> Not sure where, but try...
>locate catalina.sh

That file should be here...  CATALINA_HOME/bin/catalina.sh

Thanks - that did the trick!

---

### Post by welshboy on 2006-12-08
Dumn question, 

I'm using Edgy, and I've installed Tomcat from Synaptic, now I'm not entirely sure where the CATALINA_HOME directory is.

I've seen the /var/lib/tomcat5.5/ folder which is where the web apps stuff goes etc, but I can't find the bin directory.  I used locate to find it, but it didn't display anything on screen as to where the file is.  

Any help would be cool

---

### Post by firebadger on 2006-12-09
Try running updatedb before running the locate command.  That should populate the database that locate uses.  It should be running automatically though.

If it still doesn't work, post the exact command you are running.

---

### Post by AllBuntu on 2007-03-06
To find what to set $CATALINA_HOME to we need to find a path that /bin/catalina.sh can be appended to:

```
$ find / -name catalina.sh 2> /dev/null
/usr/share/tomcat5.5/bin/catalina.sh

```

which means that $CATALINA_HOME is /usr/share/tomcat5.5
this is default on Edgy 6.10
note that Edgy links all write-folders over to /var

You can also go figure on JAVA_HOME in the same way, something that can take /bin/java:

```
$ find / -name java -type f 2> /dev/null
/var/lib/dpkg/alternatives/java
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java
/usr/local/j2sdk1.4.2_13/jre/bin/java
/usr/local/j2sdk1.4.2_13/bin/java
/usr/local/j2re1.4.2_13/bin/java

```

which could make us choose
[LIST=1]
[*]JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.00
  or
[*]JAVA_HOME=/usr/local/j2sdk1.4.2_13
 or
[*]JAVA_HOME=/usr/local/j2re1.4.2_13
  or
Edgy typically has a symbolic link intended to not change so often:
[*]JAVA_HOME=/usr/lib/jvm/java-6-sun
[/LIST]
root could put the selected line into the file /etc/environment

otherwise, a non-privileged user could put it into his ~/.bashrc file

Regards,

Harald Rudell

---

### Post by FirstByté on 2009-09-11
Thanks this came very handy.

To bad, there have been a lot of tutorials out there that fail to cater for newbies like me.

Spent SEVERAL hours trying to spot where

**"$CATALINA_HOME/webapps/ROOT/"** was on my Ubuntu Jaunty :)

**```
~$locate catalina.sh
```** gave the clue

```

/usr/share/tomcat5.5/bin/catalina.sh
/usr/share/tomcat6/bin/catalina.sh

```

THANKS GUYS:popcorn:

---

### Post by bbiandov on 2010-04-23
/usr/share/tomcat6 on my Ubuntu 9.04 all stock install using apt-get for Apache Tomcat 6 and java

---

### Post by Iowan on 2010-04-23
This thread is due a long rest. Feel free to start a new one :)

---

