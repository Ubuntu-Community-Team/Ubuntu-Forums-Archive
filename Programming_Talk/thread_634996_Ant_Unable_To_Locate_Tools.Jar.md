---
title: "Ant Unable To Locate Tools.Jar"
date: 2007-12-08
forum: Programming Talk
---

### Post by Chris55 on 2007-12-08
In an effort to install Sun's Glassfish J2EE App Svr I ran into the following problem when executing:

sudo -s
ENTER PASSWORD
java -Xmx256m -jar glassfish-installer-v2-b58g.jar
cd glassfish
chmod -R +x lib/ant/bin
lib/ant/bin/ant -f setup.xml     <= This blew-up

Here is the Terminal stack...

root@JavaDev:/usr/local/glassfish# lib/ant/bin/ant -f setup.xml
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-sun-1.6.0.03/lib/tools.jar
Buildfile: setup.xml

all:

get.java.home:

setup.init:

check-java:

get.java.home:

setup.init:

validate-java:
     [echo] Current Java Version 1.6.0_03

BUILD FAILED
/usr/local/glassfish/setup.xml:156: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:136: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:132: Please set java.home to a JDK installation

Total time: 7 seconds

I installed ant from the Ubuntu package archive...
root@JavaDev: apt-get install ant

I selected the latest version of Java (1.6.0.03)...
root@JavaDev: sudo update-alternatives --config java

I edited the Java environment variables...
root@JavaDev. gksu gedit /etc/environment

JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.03"
CLASSPATH=".:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/rt.jar"
PATH="/usr/lib/jvm/java-6-sun-1.6.0.03/jre/sbin:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

And Ant still can not find the tools.jar! I searched the entire file system and can not find tools.jar. Any suguests would be appreciated.

Thanks.

Chris

---

### Post by Chris55 on 2007-12-09
Problem fixed. I installed J2EE without the JDK. I installed the JDK and all is fine.

---

### Post by stednick on 2010-09-09
Thanks for posting your answer, 3 years later same issue solved the same way as you did.

---

### Post by mjrmua on 2010-11-05
I tried this, but couldn't figure out how to install J2EE.
any suggestions?

---

### Post by sureshatt on 2011-01-05
Hi,, above error occur when you have installed JRE but not JDK. you can check this by typing "javac" in the terminal (It will ask you to install a JDK.)

Solution :
apt-get install sun-java6-jdk

issue above command. it will install the JDK and problem solved. :guitar:

---

### Post by RF. on 2011-02-28
> **sureshatt said:**
> Hi,, above error occur when you have installed JRE but not JDK. you can check this by typing "javac" in the terminal (It will ask you to install a JDK.)

Solution :
apt-get install sun-java6-jdk

issue above command. it will install the JDK and problem solved. :guitar:
This definitely DID solve my problem, but I don't understand why:

1. I completely uninstalled the OpenJDK stuff 
2. I added the sun-java software repository to synaptics and installed the sun-java6-jdk via synaptics, incl. the documentation and some more stuff.
3. I worked with Eclipse for a while on some Java projects. Everything worked fine, including the usage of ant build.xml files in the shell.
4. after installing the IntelliJ IDE (and settings the required shell-variables) i always got the error:
```
intellij idea tools.jar is not in IDEA classpath. Please ensure JAVA_HOME points to JDK rather than JRE
```I don't understand why there was something missing in my JDK installation, because I definitly had the JDK installed (checked it more than twice...)
5. I found your post and simply tried it out --> and apt downloaded and installed the sun-java6-jdk without giving any error. 

What could have happened? :confused: A broken JDK installation?

PS: i forgot: the download for sun-java6-jdk which I started in the shell at step 5 just had around 20MB, which definitely is not the whole package.

---

### Post by sureshatt on 2011-03-23
Hi,,

[LIST]
[*]As the error says, it seems the problem is with the JAVA_HOME variable
[*]Did you try "**echo $JAVA_HOME**" command to see where JAVA_HOME variable has set to?
[*]JAVA_HOME must points to the JDK you've installed
[/LIST] 

**To set JAVA_HOME**

[LIST=1]
[*]To open the .bashrc file, issue the following command in new terminal: **gedit $HOME/.bashrc**
[*]Append the following lines to the opened .bashrc file, save it and close: **export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.22"** **export PATH=$PATH:$JAVA_HOME/bin**
[*]issue the following command in the terminal:   **source $HOME/.bashrc**
[/LIST]

please refer this [blog post for more info]("http://sureshatt.blogspot.com/2011/01/easiest-way-to-install-java-in-ubuntu.html")

---

