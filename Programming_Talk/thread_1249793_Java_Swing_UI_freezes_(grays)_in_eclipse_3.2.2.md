---
title: "Java Swing UI freezes (grays) in eclipse 3.2.2"
date: 2009-08-25
forum: Programming Talk
---

### Post by Winmalar on 2009-08-25
Hi,

        I am new to  Ubuntu.  I have been trying to run a sample 
Swing application using Eclipse IDE since this evening but my application UI always freezes.  I have no idea why my application window freezes.

**The same application works in windows environment**

Can any one give me the solution for this problem?



My eclipse version is 3.2.2 ,
Ubuntu version is 9.04
and JDK version is 1.6


sat:o

---

### Post by baizon on 2009-08-26
The best way is that you install the newest version of Eclipse from source.

---

### Post by kpkeerthi on 2009-08-26
Verify your Java version using **java -version** and try running the application from command line. Or download the latest eclipse (v3.5) from [www.eclipse.org](www.eclipse.org) and try with it. No need to compile eclipse from source. Download > Extract > Double-click the file **eclipse** in the folder.

---

### Post by moma on 2009-08-26
Hello,
Getting the latest Eclipse IDE from eclipse.org.
Read steps 1, 2 and 3 of this Android-guide.
[http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html](http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html)

---

### Post by Winmalar on 2009-08-26
> **moma said:**
> Hello,
Getting the latest Eclipse IDE from eclipse.org.
Read steps 1, 2 and 3 of this Android-guide.
[http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html](http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html)

Hi All, 

           Thanks for your help. I just followed Moma's link because the installation procedure was explained in a simple manner.  But still I have the same problem :confused:.  
I found a strange path when I was executing my application using Eclipse IDE. The path was **DBView[Java Application] /usr/lib/jvm/java-1.5.0-gcj-4.3-1.5.0.0/bin/java**

When I type java -version in the terminal, I am getting the following details

java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode, sharing)

But eclipse path seems to be different :(.  I was trying to change the default JRE in eclipse, but I do not know path of installed JRE 1.6.0

sat:P

---

### Post by Winmalar on 2009-08-26
Hi all,

              I solved the problem. I changed the default path in eclipse. Now my application works fine 

thanks for your help

sat:P

---

### Post by doas777 on 2009-08-26
not that this is helpful, but my swing apps (netbeans) run at about  50-60% the speed on linux that they do on windows. no idea why, but I am kinda glad that my client is planning on this being a windows app.

---

