---
title: "How do I switch from GCJ to Sun Java"
date: 2007-06-12
forum: Programming Talk
---

### Post by vadania on 2007-06-12
My Ubuntu is 7.04, Feisty Fawn. I use Eclipse 3.2 and/or Netbeans 5.5 to (learn java programming) program in java.
I was trying to create an applet in Eclipse, but I got the following error:

Exception in thread "main" java.lang.NoClassDefFoundError: sun.applet.AppletViewer
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: sun.applet.AppletViewer not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/bogdan/workspace/QuickRead/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)


How do I switch from gcj to sun-java?
I found something about *sudo gedit /etc/eclipse/java_home*: 

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/j2sdk1.5-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.4-sun


Although j2sdk is the first in the config file, eclipse still uses gcj.
Yes, I after changing the config, I closed eclipse and reopened it, but I still get this error.

---

### Post by neo.patrix on 2007-06-12
Hi vadania,

You need take following steps to apply Sun Java 5 or 6 system wide

1) First you need to install sun java 5 from repository

sudo apt-get install sun-java5-jdk sun-java5-jre etc.

2) Sun java will be intalled in directory  /usr/lib/jvm, there should be one directory for Sun java
 

java-1.5.0-sun-1.5.0.11, also a link java-1.5.0-sun. If the link is not present i would advice to create one with 'ln' command.

3) Add following lines to your /etc/profile, remember it is editable only by superuser

```
#configuration for java
JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun"
export JAVA_HOME

```

---

### Post by neo.patrix on 2007-06-12
Actually i forgot to tell you to relogin to make new profile applicable....

---

### Post by neo.patrix on 2007-06-12
It seems that i am getting into habit of forgetting

please when you edit /etc/profile/ , add following lines

```

#configuration for java
JAVA_HOME="/usr/lib/jvm/java-1.5.0-sun"
export JAVA_HOME

PATH=.:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
export PATH


```

---

### Post by skaggapa on 2007-06-12
there is an other way

just

sudo update-alternatives --config java

and select jvm. this way its also easy to switch between jvm's if u have to.

also do

sudo update-alternatives --config javac

and maybe it documentation is available.

sudo update-alternatives --config javadoc

//Anders

---

### Post by vadania on 2007-06-13
This will be available only for the current user, not for java daemons (Tomcat), right?
I do not use java daemons yet, but I am asking not to have any surprises.

I guess I would get most of the daemon functionality by running them in userspace?
For example, to use Tomcat I would need to start it manually

---

### Post by ndrew2505 on 2007-07-04
drew@drew-laptop:~$ sudo apt-get install sun-java5-jdk sun-java5-jre etc.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
drew@drew-laptop:~$

any1 know what this is? i cant install java or the 4 new updates im showin b/c it gives me this message. im on fiesty 7.04

---

### Post by robgr85 on 2007-07-05
use apt-get to install java-1.6.0-sun

or

[use sudo update-java-alternatives -l          to get list of available java version on Your system.]

[depending on sun-java's version installed on Your ubuntu, use update-java-alternatives -s VERSION to select one of them]:

sudo update-java-alternatives -s java-1.6.0-sun 

regards,
Robert

---

### Post by jespdj on 2007-07-05
> **ndrew2505 said:**
> drew@drew-laptop:~$ sudo apt-get install sun-java5-jdk sun-java5-jre etc.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
drew@drew-laptop:~$

any1 know what this is? i cant install java or the 4 new updates im showin b/c it gives me this message. im on fiesty 7.04

You were not supposed to type the "etc." behind that command.

Did you try doing what the message suggests: sudo dpkg --configure -a

---

### Post by ndrew2505 on 2007-07-05
nvm i got it. thanks anyway.

---

### Post by robgr85 on 2007-07-05
did You try to use update-java-alternatives as I advised?

could you paste the entire screen telling that repository is broken?

did You try to fix it by: (as a root)

apt-get update
apt-get -f install
apt-get upgrade

etc?

try to

update-java-alternatives -l

to check if you have already installed sun's java on Your system.

---

### Post by s5554 on 2007-07-10
It's surprising and confusing that updating alternatives is not enough to get rid of gnu.gcj -- that gnu.gcj can be avoided only by editing /etc/profile.
I come to this conclusion when run my java class under Eclipse.
Thanks for the advice!

Btw, I didn't quite understand what was said of dpkg in this thread.

---

