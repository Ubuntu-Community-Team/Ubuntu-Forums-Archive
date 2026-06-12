---
title: "eclipse 4.0 on AMD64bit ???"
date: 2008-03-04
forum: Programming Talk
---

### Post by hofmann_labor on 2008-03-04
hi there,

i am using Ubunutu 7.10 Gutsy on an AMD 64-bit. now i want to install Eclipse 4.0. One week ago  i install on this PC a 32-bit version of Ubuntu, Sun.Java JDK 6.0 and eclipse and it was running. Now i reinstalled  the PC and install a 64-bit version of Ubuntu. According to Eclispe its possible to run Eclipse on a 64-bit target.  

now i already install the java6 , JDK for 64bit-Systems. when i typ in "java -version" in the Terminal i get the message :"java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)"

So i think its correctly installed. 

But when i try to start the Eclipse - application an errormessage appears:   
JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/hofmann/Desktop/eclipse/eclipse
-name Eclipse
--launcher.library /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.3.R33x_v20080118/eclipse_1023.so
-startup /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-exitdata 1c800a
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar

---

### Post by irrdev on 2008-03-04
The Eclipse website recommends using JDK 5, although the IDE does work well with JDK 6 on 32bit platforms. However, from reading the error messages, it seems that Eclipse requires JDK 5 to work with all 64bit editions. For example, the line *-Dosgi.requiredJavaVersion=1.5* shows up twice on the list.

---

### Post by H264 on 2008-03-04
From my experience, Sun's Java runtime sucks on everything except solaris, 32bit linux, windows, and OSX. 64bit, PowerPC, and SPARC with linux or BSD would need to download IBM's Java... which seems to work quite well.

[http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

I've only used IBM's Java on PowerPC linux, but I would imagine it works just as well on 64bit X86.

---

### Post by hofmann_labor on 2008-03-04
hmm, i test ur suggestion. now i installed java 1.5 (or called java5) ->>> java version "1.5.0_14"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_14-b03)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_14-b03, mixed mode)


but the error is the same.... 

JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/hofmann/Desktop/eclipse/eclipse
-name Eclipse
--launcher.library /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.3.R33x_v20080118/eclipse_1023.so
-startup /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-exitdata 22800a
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/hofmann/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar 

but, thanks for ur comment

---

### Post by Tuna-Fish on 2008-03-04
try running 
```
/usr/bin/java -version

```

it is possible that 1.6 is installed somewhere else where it is before of /usr/bin in your path. Then eclipse would try to use the java at /usr/bin, while your java -version would use the wrong java from /usr/bin.

Assuming that 'java -version' returns 1.6, do:
```

sudo mv /usr/bin/java /usr/bin/javaOLD
sudo ln -s `which java` /usr/bin/java

```
Now you should have 1.6 as /usr/bin/java

---

### Post by hofmann_labor on 2008-03-04
i already try this , and i think the path is correct ... 

hofmann@hofmann-desktop:~$ /usr/bin/java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

 but, thanks

---

### Post by hofmann_labor on 2008-03-04
is it possible that eclipse looks in another path for the Java ??? .. because one line of the error-message is: -vm /usr/bin/java


but i already try to start the aplication with : 

$ sudo ./eclipse -vm /usr/lib/jvm/java-6-sun/jre/bin/java:confused:

---

### Post by Buddhika on 2008-04-05
I'm also using a AMD64bit Turion with Gutsy 64bit and facing this error. I was using eclipse 3.2 since I didn't need to update to 3.3 but now when I'm trying to do it, eclipse gives this error. 

I've also used JRockit JRE but error remains. Seems like this is an error of Ubuntu 64bit + eclipse rather than java platform. 

Btw, if you want to change the jvm used for eclipse, just give the path of that JVM to your classpath (export $PATH=$HOME/<path to your java bin>:$PATH) -> change the java VM (java -jrockit for example)..and run eclipse ./eclipse. But that didn't fix the error for me :(

---

### Post by gekkio on 2008-04-05
Make sure you're using the correct version of eclipse for your platform.
If you are using 64-bit Java, you **must** use the 64-bit version of eclipse.
Normally Java is cross-platform and it wouldn't matter, but eclipse uses some native stuff (SWT), so it does matter in this case.

---

### Post by hno3 on 2008-04-05
I too am facing the same problem I trie to use the following commands 

sudo mv /usr/bin/java /usr/bin/javaOLD
sudo ln -s `which java` /usr/bin/java

as suggested in the earlier posts but but now as I try t install it gives me the following error message:


A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/pratap/Desktop/eclipse/jre/bin/java
java in your current PATH

Also after typing in the command "/usr/bin/java -version" in the TERMINAL I get the message 

bash: /usr/bin/java: No such file or directory

earlier before entering the command suggested i used to get the foollowing message for

/usr/bin/java -version

java version "1.6.0_03"

---

### Post by ugiflezet on 2008-08-10
I had the same problem,

try: sudo update-alternatives --config java 
make sure you select the 64bit version and not the ia32 version

--D

---

