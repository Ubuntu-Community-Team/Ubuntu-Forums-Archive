---
title: "Ubuntu + NetBeans + JDK Error"
date: 2013-01-14
forum: Packaging and Compiling Programs
---

### Post by coolbud012 on 2013-01-14
Hey Guys I installed netbeans and when starting a java project its giving me error of JDK.

Can someone help me with the same?

Thanks

---

### Post by slickymaster on 2013-01-14
First make sure you really have JDK installed on your system, by typing the following in a terminal:
```
dpkg --list | grep -i jdk
```

If you already have it, what should be expected since you installed Netbeans, then probably you haven't set it in the Java Platform Manager in Netbeans. In order to do it just open Netbeans and navigate to **Tools -> Java Platforms -> Add Platform...** button and specify the path to your JDK folder.

---

### Post by coolbud012 on 2013-01-14
ii  icedtea-6-jre-cacao:i386                  6b24-1.11.5-0ubuntu1~12.10.1               i386         Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre-jamvm:i386                  6b24-1.11.5-0ubuntu1~12.10.1               i386         Alternative JVM for OpenJDK, using JamVM
ii  icedtea-7-jre-jamvm:i386                  7u9-2.3.3-0ubuntu1~12.10.1                 i386         Alternative JVM for OpenJDK, using JamVM
ii  openjdk-6-jre:i386                        6b24-1.11.5-0ubuntu1~12.10.1               i386         OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless:i386               6b24-1.11.5-0ubuntu1~12.10.1               i386         OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                         6b24-1.11.5-0ubuntu1~12.10.1               all          OpenJDK Java runtime (architecture independent libraries)
ii  openjdk-7-jre:i386                        7u9-2.3.3-0ubuntu1~12.10.1                 i386         OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:i386               7u9-2.3.3-0ubuntu1~12.10.1                 i386         OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                         7u9-2.3.3-0ubuntu1~12.10.1                 all          OpenJDK Java runtime (architecture independent libraries)

---

### Post by slickymaster on 2013-01-14
Now that you have a confirmation for JDK, you just have to point the Java Platform in Netbeans to your openJDK location like I posted previously.

If you don't know its location (**/usr/lib/jvm/** usually)  just type at a terminal window:
```
whereis java
```

---

### Post by coolbud012 on 2013-01-14
java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz



Also do I have to uninstall openJDK?

---

### Post by slickymaster on 2013-01-14
> **coolbud012 said:**
> java: /usr/bin/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz
By the looks of it your JDK location is at **/usr/lib/jvm/** that's the location you have to add to Java Platforms in your Netbeans.

> **coolbud012 said:**
> Also do I have to uninstall openJDK?No, if you uninstall it you won't be able to develop in Java since it's the JDK that contains the collection of the Java programming tools.

---

### Post by coolbud012 on 2013-01-14
How to set it in netbeans I'm not getting any option to set it in NB 7.2.1

---

### Post by slickymaster on 2013-01-14
Open Netbeans and navigate to **Tools -> Java Platforms**, click the **Add Platform...** button and specify the path to your JDK folder.

Another way is to edit the **netbeans.conf** file and change _'netbeans_jdkhome='_ value according to your JDK location. Something like this:
```
netbeans_jdkhome="path/to/your/JDK/location"
```

---

### Post by coolbud012 on 2013-01-14
There is no option for Java Platforms in tools, there is just Tools --> Options/ Plugins .

And how to edit the file?

---

### Post by coolbud012 on 2013-01-14
> **slickymaster said:**
> 
Another way is to edit the **netbeans.conf** file and change _'netbeans_jdkhome='_ value according to your JDK location. Something like this:
```
netbeans_jdkhome="path/to/your/JDK/location"
```

This is my current path in my config file :

```
netbeans_jdkhome="/usr/lib/jvm/java-6-openjdk-i386"
```

its of openjdk, so what exactly I have to do?

when I am changing it to :

```
netbeans_jdkhome="/usr/lib/jvm/"
```

Netbeans not opening then.

---

### Post by coolbud012 on 2013-01-14
I uninstalled netbeans and reinstalled it again and it asked me for JDK path. Done :)

I really appreciate your help...Thanks a lotz

---

### Post by slickymaster on 2013-01-14
> **coolbud012 said:**
> This is my current path in my config file :

```
netbeans_jdkhome="/usr/lib/jvm/java-6-openjdk-i386"
```

That was the correct path. When you change it, deleting the JDK, you made a complete mess because your Netbeans completly lost the reference to it, leaving it just with the reference to the folder where it was.

---

### Post by slickymaster on 2013-01-14
> **coolbud012 said:**
> There is no option for Java Platforms in tools, there is just Tools --> Options/ Plugins .

That is completely bizarre. It seems to me that your problem was from the start a corrupt installation of the Netbeans itself. 

> **coolbud012 said:**
> I uninstalled netbeans and reinstalled it again and it asked me for JDK path. Done :)

I really appreciate your help...Thanks a lotz

I'm really glad you were able to solve your problem. Now, perhaps you can _mark the thread as solved_.

Happy coding.

---

### Post by coolbud012 on 2013-01-15
I have already marked this as solved...

---

### Post by coolbud012 on 2013-01-15
> **slickymaster said:**
> That was the correct path. When you change it, deleting the JDK, you made a complete mess because your Netbeans completly lost the reference to it, leaving it just with the reference to the folder where it was.

> **slickymaster said:**
> That is completely bizarre. It seems to me that your problem was from the start a corrupt installation of the Netbeans itself. 



Nopes netbeans still not having that option...rest now when I told netbeans where my jdk is at the time of installation , now in config file the path is :

```
netbeans_jdkhome="/home/shivamd/Dev/Java/JDK/jdk1.7.0_10"
```

---

