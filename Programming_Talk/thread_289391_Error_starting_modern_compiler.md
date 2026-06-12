---
title: "Error starting modern compiler"
date: 2006-10-30
forum: Programming Talk
---

### Post by chapake on 2006-10-30
Hi there!

I recently moved from XP to Kubuntu. I like it so far, but one little thing is driving me crazy.
When I changed my OS, I was in a middle of a Java project, so I installed JDK and Eclipse too.
Just in case, I give my environment variables:
> chapake@Snoggox:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/jdk1.5.0_09/bin:/opt/jdk1.5.0_09/jre/bin
chapake@Snoggox:~$ echo $CLASSPATH
/opt/jdk1.5.0_09/lib:/opt/jdk1.5.0_09/jre/lib
chapake@Snoggox:~$ echo $JAVA_HOME
/opt/jdk1.5.0_09


But when I try to build my project in Eclipse using ant, I get an error looking like this:
> Buildfile: /home/chapake/tvt svn/auch/lab4/build.xml
build:
    [javac] Compiling 19 source files to /home/chapake/tvt svn/auch/lab4/build/classes

BUILD FAILED
/home/chapake/tvt svn/auch/lab4/build.xml:72: Error starting modern compiler

Total time: 1 second
Strange... At least to me. :-k 

I also noticed, that Eclipse is using> /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
instead of the location I specified.

Has anyone had a similar problem? Or is just smart enough to answer, because I'm kinda new to this Linux-thing.

Thanks in advance!
Chapake

---

### Post by amo-ej1 on 2006-10-31
Yeah, I experienced somethings similar, i used update-alternatives to specify the jdk/jre that should be used (man update-alternatives) but somehow eclipse is probing itself for jdk/jre's that have been installed. And the gcj/eclipse combo turned into some unexpected behaviour. 

So the quick fix for me was to throw gcj off ;-), the nice solution is the following: (See man eclipse) eclipse has a startup flag -vm

so
```

eclipse -vm /here/is/my/bin/java

```

forces eclipse to use a certain java.

---

### Post by chapake on 2006-10-31
Hi again and thanks for the answer!

But still I get 100 errors from Eclipse, and half of them are
> Syntax error, parameterized types are only available if source level is 5.
It's starting to freak me out... ](*,) 

I forced Eclipse to use JDK installed by me, but still no use. I also edited Eclipse settings on available JRE's.

When I list the available JVM's, it doesn't show /opt/jdk as one.
> chapake@Snoggox:~$ update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj

I have also tried to use update-alternatives, to specify the default JRE, but even there I can't see JDK installed by me.

So I'm a bit :-? . Can anyone help me out?

---

### Post by amo-ej1 on 2006-10-31
did you do a manual install or did you install the jdk from apt ?

```

e@lap:~$ apt-cache search sun | grep jdk
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0

```

it would be easier to simply use the jdk from the apt repository, that will do more configuration for you.

---

### Post by chapake on 2006-11-01
Well, at first I installed the JDK using apt-get and tried to configure it with update-alternatives. But no use. Eclipse still used the gcj. Changed the Eclipse settings to use Sun's Java, but Eclipse still preferred gcj.
So I tried to install the JDK manually, downloaded it from the Sun site etc. Now, if I try to execute Eclipse with
```
eclipse -vm /here/is/my/bin/java
```
it says something about not finding a virtual machine from that location.

---

### Post by amo-ej1 on 2006-11-01
have you tried apt-get remove gcj ? ;-) that'll stop eclipse from finding ;)

---

### Post by chapake on 2006-11-02
Thanks, I'll try it as soon as I get home.

---

