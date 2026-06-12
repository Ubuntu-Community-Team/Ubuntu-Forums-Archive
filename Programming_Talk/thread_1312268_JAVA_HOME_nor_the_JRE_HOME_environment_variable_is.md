---
title: "JAVA_HOME nor the JRE_HOME environment variable is defined"
date: 2009-11-03
forum: Programming Talk
---

### Post by samlabs821 on 2009-11-03
Hi there... who can help with problem... so let me show you what i have:
this is ~/.bashrc file:
[FONT="Courier New"][SIZE="4"]export JAVA_HOME=/usr/lib/jdk1.6.0_16
export CLASSPATH=/home/samlabs821/tomcat/lib/jsp-api.jar:/home/samlabs821/tomcat/lib/servlet-api.jar[/SIZE][/FONT]

and this is my ~/.bash_profile:
[FONT="Courier New"][SIZE="4"]JRE_HOME=/usr/lib/jdk1.6.0_16/jre/bin
JAVA_HOME=/usr/lib/jdk1.6.0_16[/SIZE][/FONT]

And i have this folders:

/usr/lib/jvm           \\this is Suns JVM
/usr/lib/jdk1.6._16    \\this is Suns JDK

---------------

echo $JAVA_HOME is working but javac is not working...
java command is working..


what must i do plizzz helppp :(

---

### Post by jespdj on 2009-11-03
How did you install the JDK? Try this (instead of downloading and manually installing it):
```
sudo apt-get install sun-java6-jdk
```

Did you close and re-open a terminal after editing ~/.bashrc?

---

### Post by Ann.A on 2009-11-03
Do you have your PATH variable pointing to the jdk's /bin ?  Something like export PATH=${PATH}:${JAVA_HOME}/bin

---

### Post by GuillermoEllison on 2009-11-21
[samlabs821]("http://www.uluga.ubuntuforums.org/member.php?u=943857") maybe you have a wrong JRE_HOME, try rewriting it doing [FONT=Courier New][SIZE=4]export [/SIZE][/FONT][FONT=Courier New][SIZE=4]JRE_HOME=/usr/lib/jdk1.6.0_16/jre [/SIZE][/FONT]or just nulling it. 
[FONT=Courier New][SIZE=4]
[/SIZE][/FONT]Regards

---

