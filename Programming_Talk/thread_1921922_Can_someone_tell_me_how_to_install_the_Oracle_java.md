---
title: "Can someone tell me how to install the Oracle java sdk (Ubuntu/Eclipse)?"
date: 2012-02-07
forum: Programming Talk
---

### Post by apollothethird on 2012-02-07
Can someone help with how to install the Oracle JDK package to Ubuntu 11.10?  I tried the using alien on the rpm file and it doesn't complete.  The errors are linked below.

Issues with Installing Java
[http://ubuntuforums.org/showpost.php?p=11668356&postcount=9](http://ubuntuforums.org/showpost.php?p=11668356&postcount=9)

I downloaded and extracted the tarball, but it doesn't have an install script or any instructions of where the directories should be moved or copied.

I'm looking to use the JDK package in the Eclipse environment running under Ubuntu 11.10.

The packages that I have downloaded are from:
[http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html)

I chose the two for Linux X64 (jdk-7u1-linux-x64.rpm and jdk-7u1-linux-x64.tar.gz) as I'm running Ubuntu 11.10 x64.

Again, the rpm won't install (using Alien) and the Tarball doesn't have any install script or install instructions.


Thanks in advance for any suggestions or comments!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by t1497f35 on 2012-02-07
The .tar.gz version doesn't need to be installed, you just unzip it and the resulting folder _is_ the jdk, btw there's already update 2 available.
In the past (JDK6) you had unzip the tar.gz file then execute the resulting the .bin file which would create the folder with the JDK, starting with Oracle Java 7 the step with the .bin file has been removed and you get the folder with the JDK right after unzipping the .tar.gz file.

When you want to install a program (say NetBeans) which would use that version of JDK you should point it to that folder, if there's no such option in the installer of that program (i.e. NetBeans) - improvise.

---

### Post by apollothethird on 2012-02-07
> **t1497f35 said:**
> The .tar.gz version doesn't need to be installed, you just unzip it and the resulting folder _is_ the jdk, btw there's already update 2 available.
In the past (JDK6) you had unzip the tar.gz file then execute the resulting the .bin file which would create the folder with the JDK, starting with Oracle Java 7 the step with the .bin file has been removed and you get the folder with the JDK right after unzipping the .tar.gz file.

When you want to install a program (say NetBeans) which would use that version of JDK you should point it to that folder, if there's no such option in the installer of that program (i.e. NetBeans) - improvise.

Thanks.  I guess my real question is how to make the download (after extracted) Eclipse aware?  The "improvise" part is confusing to me.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by t1497f35 on 2012-02-08
I unzipped the JDK tar.gz file to /home/fox/apps/jdk1.7.0_02
then updated the eclipse.ini file from the Eclipse folder, after the line "256m" I added 2 lines:

-vm
/home/fox/apps/jdk1.7.0_02/bin

saved and now eclipse runs with this JDK by default.
Found out [from here]("http://wiki.eclipse.org/Eclipse.ini").

Of course you can add other VMs from window->preferences->Java->Installed JREs

---

### Post by fallenshadow on 2012-02-08
If you want to install Java 7 JDK and have it detected by IDEs then here you go! :)

[http://www.youtube.com/watch?v=JVUpgqa7DZg](http://www.youtube.com/watch?v=JVUpgqa7DZg)

---

### Post by apollothethird on 2012-02-08
> **t1497f35 said:**
> I unzipped the JDK tar.gz file to /home/fox/apps/jdk1.7.0_02
then updated the eclipse.ini file from the Eclipse folder, after the line "256m" I added 2 lines:

-vm
/home/fox/apps/jdk1.7.0_02/bin

saved and now eclipse runs with this JDK by default.
Found out from here.

Thanks, T1497f35.  I tried.  It doesn't work.  Eclipse won't start when I add the 2 lines.  I get the following fetal error:
```
ljames@ubunzeus:~$ eclipse 
Unrecognized option: -vm 
Could not create the Java virtual machine.
```I also get a popup with this message:

```

JVM terminated. Exit code=1 
/usr/bin/java 
-Dosgi.requiredJavaVersion=1.5 
-XX:MaxPermSize=256m 
-Xms40m 
-Xmx384m 
-vm /home/users/l/j/ljames/install/jdk1.7.0_02 
-jar /lib/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar 
-os linux 
-ws gtk 
-arch x86_64 
-showsplash 
-launcher /lib/eclipse/eclipse 
-name Eclipse 
--launcher.library /lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.v20110505/eclipse_1407.so 
-startup /lib/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar 
--launcher.overrideVmargs 
-exitdata abb000d 
-product org.eclipse.epp.package.cpp.product 
-vm /usr/bin/java 
-vmargs 
-Dosgi.requiredJavaVersion=1.5 
-XX:MaxPermSize=256m 
-Xms40m 
-Xmx384m 
-vm /home/users/l/j/ljames/install/jdk1.7.0_02 
-jar /lib/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar 

```It appears to have a problem with the “-vm” option.

> 
Of course you can add other VMs from window->preferences->Java->Installed JREs
When I remove the lines and try to do it from the preferences menu I don't see the option you want me to click on after clicking on “->Java”.  Maybe I'm missing a step, but the “Installed JREs” option doesn't appear.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2012-02-08
> **fallenshadow said:**
> If you want to install Java 7 JDK and have it detected by IDEs then here you go! :)

[http://www.youtube.com/watch?v=JVUpgqa7DZg](http://www.youtube.com/watch?v=JVUpgqa7DZg)

Thanks, Fallshadow.  I'll study the video.  If I can get it working from the provided steps I'll come back and post the working steps here.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by t1497f35 on 2012-02-08
It must work, I used the **current release** from their site (for Java developers version), here's the full contents of my eclipse.ini file:

-startup
plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.v20110505
-product
org.eclipse.epp.package.java.product
--launcher.defaultAction
openFile
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vm
/home/fox/apps/jdk1.7/bin
--launcher.defaultAction
openFile
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m


EDIT: you probably put your args after the last occurence of "256m" which is wrong, see above.

---

### Post by apollothethird on 2012-02-08
> **t1497f35 said:**
> It must work, I used the **current release** from their site (for Java developers version), here's the full contents of my eclipse.ini file:

-startup
plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.100.v20110505
-product
org.eclipse.epp.package.java.product
--launcher.defaultAction
openFile
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
-vm
/home/fox/apps/jdk1.7/bin
--launcher.defaultAction
openFile
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m


EDIT: you probably put your args after the last occurence of "256m" which is wrong, see above.

Thanks, T1497f35.  That was what was producing the error.  I fixed it and no longer get the error.  However, my attempt at a java hello world fails.  Eclipse gives these errors:

```

Description    Resource    Path    Location    Type
The project cannot be built until build path errors are resolved    Java First        Unknown    Java Problem
------------------------------
Description    Resource    Path    Location    Type
Unbound classpath container: 'JRE System Library [JavaSE-1.7]' in project 'Java First'    Java First        Build path    Build Path Problem

```

Is there something I can check to verify that Eclipse is recognizing the installation?  I don't see any evidence in the Help -> About Eclipse screen.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by t1497f35 on 2012-02-08
I use NetBeans for imo it's (much) better, unless you're a long-time eclipse user, so if you need less issues - use NetBeans.

But I tried Eclipse and it works for me too, here's what I did (btw don't forget to close the welcome page):
1) File->New->Java Project, see settings on the 1st screenshot.
2) On the left pane, right-click the "src" dir, choose New->Class, see settings on 2nd screenshot.
3) Edit the newly created source file to print "Hello world", then run it, see 3rd screenshot, it printed "hello world" at the bottom, thus it works.

---

### Post by t1497f35 on 2012-02-08
It also uses JDK7, see Eclipse->About Eclipse->Installation Details->Configuration, as on my screenshot.

Also:
System.out.println("Java version: " + System.getProperty("java.version"));

prints "Java version: 1.7.0_02"

---

### Post by apollothethird on 2012-02-09
> **t1497f35 said:**
> It also uses JDK7, see Eclipse->About Eclipse->Installation Details->Configuration, as on my screenshot.

Also:
System.out.println("Java version: " + System.getProperty("java.version"));

prints "Java version: 1.7.0_02"

Thanks, T1497435, for all the thread updates.  I'm finally able to compile a Java program in Eclipse without errors.  It appears that the problem was my workspace.    I used the switch workspace command to create a new one and did the Hello World program test again and was able to compile without errors.

At present I can't run the Java application in Eclipse.  No matter what I do I can't get the "Run As" enabled.  I've searched the Internet and tried to follow the solutions but they don't work.

I'm sure there's probably something simple in the environment that has to be done, but can't figure out what.

I realize you're not the biggest Eclipse fan and appreciate your recommendation for me to switch to Netbeans.  By the way, I started out with Netbeans and used it for a long time.  I switched to Eclipse over a year ago and found it to be more virsitile than Netbeans.

I was using those IDE's in Windows but dropped Windows a little more than a year ago.  I never installed Netbeans on my Linux machines.

Originally I was using the IDE's on Windows for Java Apps.  On my Linux machines I've been programming only in C++ and Perl.  This is the first time of attempting Java.  I'm trying to get Java working because I want to write Apps for my newly purchased Android tablet.

I thought it would be nothing to first write a few test Java Apps, to test the environment, then continue to install the Android tools.

So that's the background.

The Hello world Java Application works when I run it from the command line:

```

$ java HelloWorld

```When trying to run from Eclipse I get:

```

The selection cannot be launched, and there are no recent launches.

```Sources on the Internet says to right click the main class from the src navigation, select "Run As" and pick "Java Application".  However, "Run As" is blank.

Thanks again for all the input!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by t1497f35 on 2012-02-09
That is weird, when you created the project, did you specify in the settings to create a "public static void main()"? If you created the "static main" method by hand then Eclipse might not be aware that that is your "main" class. See second screenshot on my post with 3 screenshots.

Btw, here's my Hello world project which runs fine when clicking the green run button from the toolbar.

If you post yours and I can run it from my eclipse - then the problem is somewhere in your eclipse configuration.

---

### Post by stchman on 2012-02-09
As of August 24th 2011, Canonical no longer have permission to   redistribute new Java packages as Oracle has retired the &#8220;Operating   System Distributor License for Java&#8221;.
 
Luckily there are 3rd party PPAs that have Oracle Java.
 
I prefer Oracle Java to OpenJDK.
 
To install Oracle Java on your Ubuntu box open a terminal and type the following:

```

sudo apt-add-repository ppa:flexiondotorg/java
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin



```

---

### Post by apollothethird on 2012-02-09
First I would like to think everyone for their input and suggestions.  Now I'll describe where I'm at for the benefit of others.

I had problems with the ppa:flexiodotorg/java in that I couldn't remove the “sudo apt-get update” error about the valid key.  I saw the “launchpad/flexiondotorg” reference in the source directory.  So I did a google search to ensure I was getting the right spelling and the best repository for the lastest (which is java7 at this time).  The search “launchpad ppa oracle jdk” gave me: 

[https://launchpad.net/~webupd8team/+archive/java]("https://launchpad.net/%7Ewebupd8team/+archive/java")
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-jdk7-installer

```This performance went without smoothly.

The Help -> About Eclipse -> Configuration showed the same latest version installed just as all the other steps provided in this thread.  I can create and compile without problems, but still the option to run the Java Application in the Eclipse IDE still fails in the same manner.

So now I'm sure the problem has something to do with my initial Eclipse installation.  I originally downloaded Eclipse IDE for C/C++ Developers.  I thought adding support for Java development would be simple.  It was for perl and python developing.  However, it appears to be a problem with adding Java developing support to this environment.

What I'm going to do next is download the tarball “Eclipse ID for Java EE Developers” and try to add the perl and C/C++ to that.

By the way running different installations of Eclipse is very easy.  So sometime in the future I'll revisit trying to add Java support to the C/C++ Developers' package and bring the procedure back to this thread.  But in the meantime to get productive with my Java programming, I'm going to go this route.

Thanks again for all the support and input.  Again, the only problem I experienced with the C/C++ version was being able to run the Java Applications from the IDE.  There is a missing item in the step provide on the Oracle/Eclipse support page ( [http://docs.oracle.com/javame/config/cdc/cdc-opt-impl/ojmeec/1.0/install/html/z400000a1006487.html](http://docs.oracle.com/javame/config/cdc/cdc-opt-impl/ojmeec/1.0/install/html/z400000a1006487.html) ) which coinsides with missing steps that didn't work from T1497435.  The “Installed JRE's” item doesn't appear under the Java panel.

– L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2012-02-10
The issue I was having is resolved.  After extracting the new download (Eclipse IDE for Java EE Developers) it worked flawlessly.  It also had the Java samples and tutorial via the Welcome screen.

I had proceeded to install the CDT (C/C++ support) when it occurred to me that I hadn't done this step with the the other installation.

I went back to my original installation (which support installed for C/C++, Perl/Epic, Phyton, and a host of other things).  In the installation Software screen I check marked the Java items under the Programming Languages category.  After restarting Eclipse it worked perfectly.

All the configuration options and steps provided by T1497435 from his first message and own became available.

As with most issues the solution was simple.  But I'm sure the best of us have mental blocks at times.

Thanks to everyone for your support and suggestions.

In summary the quick solution is to unzip the latest tarball from Oracle (for systemwide support), move it to /opt/java, then add the set the JAVA_HOME variable and add the variable to your bashrc file.  Eclipse will then use that version (without the need of reconfiguring eclipse.ini).  Using this method will allow you to easily change from one version to another for various compatibility testing or programming.

The steps for doing that is:

```

(Download the jdk package... ie jdk-7u2-linux-x64.tar.gz)
$ tar xjvf jdk-7u2-linux-x64.tar.gz
(move the extracted director to /opt/java)
$ sudo mkdir /opt/jdk
$ sudo mv jdk1.7.0_02 /opt/jdk/
(Set the JAVA_HOME variable)
export JAVA_HOME=/opt/jdk/jdk1.7.0_02
(Set your path variable... for commandline support Eclipse will use the JAVA_HOME variable)
PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH

```That's all it is to it... now off to try to the task of installing Android Mobile support!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

