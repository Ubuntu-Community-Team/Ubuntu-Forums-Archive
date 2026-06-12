---
title: "set environment variables $JAVA_HOME"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by 007casper on 2012-08-05
java -version> 
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.3) (6b24-1.11.3-1ubuntu0.10.04.1)
OpenJDK Client VM (build 20.0-b12, mixed mode, sharing)



ls -l /usr/lib/jvm
> 
lrwxrwxrwx 1 root root   14 2012-08-05 02:48 java-1.6.0-openjdk -> java-6-openjdk
drwxr-xr-x 7 root root 4096 2012-08-05 02:48 java-6-openjdk

cd /home/user
root@puter:/home/user# vi .bashrc

at the end of the line inserted
#Java
export JAVA_HOME=/usr/lib/jvm/java-1.6.0_24

echo $JAVA_HOME
*none*

???

---

### Post by spjackson on 2012-08-05
If you make a change to ~/.bashrc, that change does not affect the shell that you are running, i.e. your terminal session. So either:

[LIST]
[*]start a new terminal window and type your echo command in there.
[*]or logout and login again.
[*]or in your current window do
[/LIST]
```

source ~/.bashrc
echo $JAVA_HOME

```

---

### Post by 007casper on 2012-08-05
> root@puter:/home/user# source ~/.bashrc
root@puter:/home/user# echo $JAVA_HOME

root@puter:/home/user#

I am wondering what I am doing wrong.

I wonder if "java-1.6.0_24" is the wrong line in .bashrc

should it be something else?

I tried

#Java
export JAVA_HOME=/usr/lib/jvm/java-1.6.0_24 

I also tried 
#Java
export JAVA_HOME=/usr/lib/jvm/java-1.6.0

???

---

### Post by 007casper on 2012-08-05
bump

---

### Post by spjackson on 2012-08-06
The problem you said that you had was
```

echo $JAVA_HOME
none

```
Is that still your problem? If so, did you try the suggestions? If you have a different problem, what are you trying to achieve and in what way is it not working?

As for choosing between /usr/lib/jvm/java-1.6.0_24 and /usr/lib/jvm/java-1.6.0, which directory exists? If both do, then which do you want to use?

---

### Post by drmrgd on 2012-08-06
I have a feeling it has something to do with the path you're entering.  I think you need to point to the actual java binary a little deeper in that directory.  So, for example:

```
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-openjdk-i386/bin/java
```

would be how I do it for the java-1.6 on my system.  I think you're not getting anything because the path you're using is not correct.  Of course, don't forget to source your .bashrc afterward as you did.

I'm not sure what you're trying to achieve.  But, one other suggestion would be to use alternatives instead of setting system variables.  That will allow you to switch between the default Java very quickly without having to edit files.  On my system I have several installed (really have to clean this up!).  But, I can switch between the default one quickly by running:

```
$ sudo update-alternatives --config java
There are 4 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
* 1            /opt/java/32/jre1.6.0_31/bin/java               1         manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode
  4            /usr/local/java/jre1.7.0_03/bin/java            1         manual mode

Press enter to keep the current choice[*], or type selection number: 

```


Then I get a nice little menu to choose and set the default.  That may help you if all you want to do is to change the default Java used on your system.

Hope that helps!

---

### Post by 007casper on 2012-08-06
I got rid of the openjdk.  I loaded IBM Java.  I guess that loads Oracle Java 7.

As drmrgd suggested...
> 
sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-7-oracle/jre/bin/java
Nothing to configure.

cd /home/user/
vi .bashrc

added 
#java
export JAVA_HOME=/usr/lib/jvm/java-7-oracle/jre/bin/java

echo $JAVA_HOME
/usr/lib/jvm/java-7-oracle/jre/bin/java

It seems like... it may work.  Thank you.

---

### Post by 1clue on 2012-08-06
I abandoned the ubuntu-specific java and went with an official download from oracle.

I unzip my JVM to */opt/jdk6/jdk6.x.yy_whatever*.
I *ln -s jdk6.x.yy_whatever current*
Finally I set JAVA_HOME=/opt/jdk6/current.

I do the same thing with a java 7 directory on boxes that use it.  If I need to have both on the same system, I put the link to somewhere else that isn't implying a major revision.

If I need to switch Java, I simply change the link.  The environment is already set to the proper place so I don't need to change anything.

I've been doing this for over 5 years now with no big problems.

---

