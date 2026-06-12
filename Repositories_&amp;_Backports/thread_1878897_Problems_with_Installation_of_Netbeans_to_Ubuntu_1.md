---
title: "Problems with Installation of Netbeans to Ubuntu 11.10."
date: 2011-11-10
forum: Repositories &amp; Backports
---

### Post by Randy Schilling on 2011-11-10
I followed the instructions at

[http://www.oracle.com/technetwork/java/javase/downloads/install-jdk6-22nb691-177131.html](http://www.oracle.com/technetwork/java/javase/downloads/install-jdk6-22nb691-177131.html)

to install: JavaTM SE Development Kit 6 Update 29 and NetBeansTM IDE 7.0.1 Software Bundle.

My systems response to the command 

       ./jdk-6u29-nb-7_0_1-linux-ml.sh 

was this:

Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
Extracting installation data...
Running the installer wizard...

and there was no sign of an installer.  Please tell me know what's wrong.

Thanks so much  - Randy

---

### Post by jorok_tupur on 2011-11-13
How about using NetBeans installer that's not bundled with JDK.

[LIST=1]
[*]First install OpenJDK (OpenJDK 6 and/or 7 works fine with NetBeans 7.0.1)
```
sudo apt-get install openjdk-6-jdk openjdk-7-jdk
```
The code above will install both OpenJDK 6 and 7. If you do not want OpenJDK 7 then ommit the openjdk-7-jdk.
[*]Download NetBeans installer.
[*]Verify the md5sum of the NetBeans installer (to make sure your installer is not corrupted).
```
md5sum -b netbeans-7.0.1-ml-linux.sh
```
Compare the md5sum with the one listed on NetBeans download page. Last I checked, its:```
3559ec7d1ce1d4bcafd7eea98cc9c648
```
If your calculated md5sum is different with the one listed in NetBeans download page, that means your download is corrupted, and you have to download the installer again.
[*]Then install NetBeans.
```

chmod +x netbeans-7.0.1-ml-linux.sh
sh ./netbeans-7.0.1-ml-linux.sh

```
[/LIST]

But as to your original question: >  there was no sign of an installer. Please tell me know what's wrong. I have no idea.

---

