---
title: "Turning a java program to a daemon"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by kaliyugantagonist on 2012-05-17
Hello everyone,

I am working on Ubuntu 10.4 and I want to turn a java program as a daemon on the OS.

I zeroed-in on two approaches as below :


[LIST=1]
[*]***jsvc*** by Apache Commons Daemon
[*]**daemon** provided by Linux
[/LIST]
I am focusing on ***jvsc*** first.

I created a shell file viz. *simpletopsub.sh* that calls the java program :

```
java -cp .:jars/activemq-all-5.5.1.jar:jars/log4j-1.2.14.jar:jars/slf4j-log4j12-1.5.11.jar com.classes.jms.pubsub.SimpleTopicSubscriber SimpleTopic
```I am trying to execute the following command after having a quick look at the 'man daemon' :

```
daemon --name="TopSub" --output=log.txt sh simpletopsub.sh
```Nothing is happening - I'm sure that I have messed with the daemon's understanding and syntax.

Please guide about the same.

Thanks and regards !

---

### Post by idoitprone on 2012-05-17
> **kaliyugantagonist said:**
> Hello everyone,

I am working on Ubuntu 10.4 and I want to turn a java program as a daemon on the OS.

I zeroed-in on two approaches as below :


[LIST=1]
[*]***jsvc*** by Apache Commons Daemon
[*]**daemon** provided by Linux
[/LIST]
I am focusing on ***jvsc*** first.

I created a shell file viz. *simpletopsub.sh* that calls the java program :

```
java -cp .:jars/activemq-all-5.5.1.jar:jars/log4j-1.2.14.jar:jars/slf4j-log4j12-1.5.11.jar com.classes.jms.pubsub.SimpleTopicSubscriber SimpleTopic
```I am trying to execute the following command after having a quick look at the 'man daemon' :

```
daemon --name="TopSub" --output=log.txt sh simpletopsub.sh
```Nothing is happening - I'm sure that I have messed with the daemon's understanding and syntax.

Please guide about the same.

Thanks and regards !

Ubuntu uses upstart

Here some docs
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)
```

script
java -cp .:jars/activemq-all-5.5.1.jar:jars/log4j-1.2.14.jar:jars/slf4j-log4j12-1.5.11.jar com.classes.jms.pubsub.SimpleTopicSubscriber SimpleTopic
end script


```[http://upstart.ubuntu.com/cookbook/#precepts-for-creating-a-job-configuration-file](http://upstart.ubuntu.com/cookbook/#precepts-for-creating-a-job-configuration-file)

I do not know how to control much with upstart. So i cannot help you but i can tell you that you can run the script at runlevel 2-5 since according to wikipedia. Ubuntu and debian does not make a distinction

[http://en.wikipedia.org/wiki/Runlevel#Debian_Linux](http://en.wikipedia.org/wiki/Runlevel#Debian_Linux)
Here is proof for ubuntu upstart [http://upstart.ubuntu.com/cookbook/#runlevels](http://upstart.ubuntu.com/cookbook/#runlevels)

---

