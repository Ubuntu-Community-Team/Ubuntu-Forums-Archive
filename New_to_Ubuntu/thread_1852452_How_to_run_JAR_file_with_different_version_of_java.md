---
title: "How to run JAR file with different version of java"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by ngubk on 2011-09-30
I downloaded jdk and jre1.5.0_16 and compile my project(this one is quite old so it had some error with the newest version) in Eclipse fine. But my default JDK is still 1.6

```
ngu@MyUbuntu:~/workspace/ims-communicator$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.9) (6b20-1.9.9-0ubuntu1~10.10.2)
OpenJDK Server VM (build 19.0-b09, mixed mode)
```
so when i type
```
 
java -jar myproject.jar
```

it returns with error. How can i run with version 1.5 instead of 1.6

---

### Post by cavh on 2011-09-30
In a terminal, navigate to the directory containing the java 1.5 executable 

/usr/lib/jvm/<OpenJDK or Sun Java here>/jre/bin

and run your command from there.

Alternatively you can set 1.5 as your default Java installation by running 

```
sudo update-alternatives --config java
```

See also [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by ngubk on 2011-09-30
Thanks for your helpful reply. I've copied jdk1.5.0_16 into usr/lib/jvm
but when i type:
```
ngu@MyUbuntu:~$ sudo update-alternatives --config java
[sudo] password for ngu: 
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.

```
How can i set jdk 1.5 to default?

---

### Post by ngubk on 2011-09-30
Also when i run:
```
ngu@MyUbuntu:/usr/lib/jvm/jdk1.5.0_16/bin$ ./java -jar /home/ngu/workspace/ims-communicator/ims-communicator.jar
```
It returns this error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: javax/media/NoProcessorException
at net.java.sip.communicator.SipCommunicator.<init>(SipCommunicator.java:126)
	at net.java.sip.communicator.SipCommunicator.main(SipCommunicator.java:423)

```
I think it relates to JMF. Do you have any idea how to fix this? I have already done a lot of search but nothing seems helpfull.

---

### Post by ngubk on 2011-09-30
Do you know how to change CLASSPATH and LIBRARY_PATH and other necessary stuffs for JMF. I've downloaded JMF from SUN website

---

### Post by Azdour on 2011-09-30
Hi,

I'm guessing you did not install the Sun JDK 1.5 via Synaptic Package Manager or apt-get.. so Ubuntu will not know about it.

Here you will find instructions on how to add different Java version to Ubuntu so that you can switch to them via the alternative command:

[http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html](http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html)

Hope that helps.

---

### Post by ngubk on 2011-09-30
> **Azdour said:**
> Hi,

I'm guessing you did not install the Sun JDK 1.5 via Synaptic Package Manager or apt-get.. so Ubuntu will not know about it.

Here you will find instructions on how to add different Java version to Ubuntu so that you can switch to them via the alternative command:

[http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html](http://daily-hacking.blogspot.com/2010/04/add-java-runtime-to-ubuntu-using-update.html)

Hope that helps.

WOW! That works. Thanks a lot.

---

### Post by cavh on 2011-09-30
Azdour is correct, you cannot simply copy jdk1.5.0_16 into usr/lib/jvm, that's not the way to do it. Read the help.ubuntu.com link I gave in my initial post for the way to install Java correctly. Once you have it correctly installed, you can follow either of the two options I gave.

---

