---
title: "Unable to execute a .jar file in Ubuntu"
date: 2015-04-26
forum: New to Ubuntu
---

### Post by alargorak on 2015-04-26
[ATTACH=CONFIG]261595[/ATTACH]

Hello, I am new to Ubuntu. I have installed oracle java 7 and 8 runtime. I am unable to get this jar file to respond at all, and i cannot double click it.
I have marked it in the properties to allow executing as a program.

java -version   gives me 
java version "1.8.0_40"
Java(TM) SE Runtime Environment (build 1.8.0_40-b26)
Java HotSpot(TM) Server VM (build 25.40-b25, mixed mode)


I am sure i am making some new user mistake, please help me determine what it is so that I can learn for the future :]

---

### Post by Mark Phelps on 2015-04-26
Have you tried doing "java -jar <filename>"?  I have jar files and that's how they get run.

---

### Post by alargorak on 2015-04-26
> **Mark Phelps said:**
> Have you tried doing "java -jar <filename>"?  I have jar files and that's how they get run.

Yes, I have. The image I enclosed is the result of "java -jar TechnicLauncher.jar".

---

### Post by Mark Phelps on 2015-04-26
I use the OpenJDK runtime v1.7.0_79 in Ubuntu 15.04 and jar files open just fine.

Don't use Oracle java, so can't offer any suggestions.

---

### Post by alargorak on 2015-04-26
Maybe this will help- 

To clarify, I can open other .jar files without a problem. I can double click Minecraft.jar, and it runs without fail. It's just this other .jar file that seems to be giving me the trouble, but it's the latest release from technicpack.net, so I am pretty sure the error is on my end somehow.

---

### Post by sandyd on 2015-04-26
Try
```

sudo apt-get install libxi6
```

---

### Post by alargorak on 2015-04-26
I just did that, it says libxi6 is already the newest version; it did however recommend i do "apt-get autoremove" which i did.

---

### Post by CantankRus on 2015-04-27
I downloaded the TechnicLauncher.jar file from [http://www.technicpack.net/download](http://www.technicpack.net/download)
It will open here via terminal with "java -jar TechnicLauncher.jar" or right click and open with "Oracle java runtime"

I noticed your pick in post #1 seemed to indicate it couldn't find a 32bit link ie unsatisfiedlinkerror /home/me/lib/**i386**/lib...

I am running Ubuntu 14.04 64bit with **java-8-oracle** set as default java. [**_[COLOR="#B22222"]INSTALL ORACLE JAVA 8 IN UBUNTU[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
What do these commands give you?
```
lsb_release -a
uname -a
sudo update-alternatives --config java
```

eg my output...
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] lsb_release -a**
LSB Version:	security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

**[COLOR="#008000"]glen@Trusty:~$[/COLOR] uname  -a**
Linux Trusty 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 [COLOR="#FF0000"]x86_64 x86_64 x86_64[/COLOR] GNU/Linux

**[COLOR="#008000"]glen@Trusty:~$[/COLOR] sudo update-alternatives --config java**
[sudo] password for glen: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-oracle/jre/bin/java          1079      auto mode
  1            /usr/lib/jvm/java-6-oracle/jre/bin/java          1079      manual mode
  2            /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java   1071      manual mode
*** 3            /usr/lib/jvm/java-8-oracle/jre/bin/java          1078      manual mode**

Press enter to keep the current choice[*], or type selection number:
```

All works here.
The java app sets a default directory, downloads some files then presents a login window.

---

### Post by alargorak on 2015-04-27
[ATTACH=CONFIG]261609[/ATTACH]

Here is the results of what you requested; it seems I didn't have LSB, which after checking the repository, is Linux Standard Base, so i installed just now.

After getting the same error message attempting to run the launcher from terminal, i had the earth-shattering idea to, instead of "java -jar TechnicLauncher.jar", to try "sudo java -jar TechnicLauncher.jar".

It worked.

The error message seemed to be either telling me the file wasn't there or I didn't have permissions, solved by using sudo. Wow. 

Thank you so much for the help!

---

### Post by CantankRus on 2015-04-27
Shouldn't need sudo and not sure if it's even wise to use with a java app that connects to the net and downloads.
I would be checking permissions of my files and folders.
I don't have **lsb** installed but do have **lsb_release** installed by default.

Main difference I can see is you have java-**7**-oracle set as default java where I have java-**8**-oracle.

---

