---
title: "JAVA_HOME and maven environment variables"
date: 2007-12-03
forum: Programming Talk
---

### Post by xkorakidis on 2007-12-03
Hi!
I have a problem here, regarding environment variables..
I downloaded maven and added 
```

# Maven settings
export MAVEN_HOME=/home/administrator/maven-2.0.5
export PATH=$MAVEN_HOME/bin:$PATH

```

in .profile and .bashrc
When I try to run maven  (e.g. mvn version)
I get an error message " We cannot execute /home/administrator/jre1.6.0_03" /bin/java"
I have added 
```
JAVA_HOME="/home/administrator/jre1.6.0_03"
``` in /etc/environment
I tried also adding /home/administrator/jdk/jdk1.5.0_13 but nothing changed.
any idea?
(ubuntu 7.10 : amd64)
Thanks in advance!

---

### Post by tenmillionmilesaway on 2007-12-04
I have my settings in /etc/environment and they are:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/share/maven-2.0.7/bin"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.03/"
```

cant see why your way doesn't work, unless you have one of your paths wrong.  And afaik you dont need to put them in both .bashrc and .profile, from top of .profile file:

```
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
```


hope this helps

---

### Post by jvictor on 2008-03-22
I hope you have solved this by now, if not add
```

export JAVA_HOME
export M2_HOME 

```

in your .bashrc as the last lines

---

### Post by elyboy on 2010-11-22
Hi!
I am having a problem with maven.

The Java Home displayed when running "mvn -version" is different when running "echo $JAVA_HOME"... Where is maven pulling its Java Home?

Please Help, because of this issue, my "mvn install" fails.

Thank you very much.

---

### Post by spjackson on 2010-11-22
> **elyboy said:**
> Hi!
I am having a problem with maven.

The Java Home displayed when running "mvn -version" is different when running "echo $JAVA_HOME"... Where is maven pulling its Java Home?

Please Help, because of this issue, my "mvn install" fails.

Thank you very much.
What have you set JAVA_HOME to? What does maven show? Did you export JAVA_HOME?

---

### Post by elyboy on 2010-11-22
> **elyboy said:**
> Hi!
I am having a problem with maven.

The Java Home displayed when running "mvn -version" is different when running "echo $JAVA_HOME"... Where is maven pulling its Java Home?

Please Help, because of this issue, my "mvn install" fails.

Thank you very much.

I've found the solution to my problem. I download openjdk from java.sun.com, then used its installation dir as JAVA_HOME.

---

