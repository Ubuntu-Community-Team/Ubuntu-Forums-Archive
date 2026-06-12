---
title: "Java Applet Install Trouble"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by MaxxABillion on 2012-04-06
I need to run skillport applet for school and i'm getting the error "By not accepting to trust the skillsoft player applet, the course will not be launched."  Now, this seems to be a Java applet.  After researching, I went to the Java website and downloaded the Linux (self-extracting file).  This is where I'm stuck,  the instructions on Java's website doesn't really makes sense to me.  If anyone can help, I will greatly appreciate it

---

### Post by kazztan0325 on 2012-04-07
Hi MaxxABillion,

I would like to ask you...

Have you asked "UH HOME > UNIVERSITY INFORMATION TECHNOLOGY > SERVICES > IT TRAINING > SKILLPORT ELEARNING" about the problem?
[http://uh.edu/infotech/php/template.php?training_id=32]("http://uh.edu/infotech/php/template.php?training_id=32")

---

### Post by MaxxABillion on 2012-04-07
> **kazztan0325 said:**
> Hi MaxxABillion,

I would like to ask you...

Have you asked &quot;UH HOME > UNIVERSITY INFORMATION TECHNOLOGY > SERVICES > IT TRAINING > SKILLPORT ELEARNING&quot; about the problem?
[http://uh.edu/infotech/php/template.php?training_id=32](http://uh.edu/infotech/php/template.php?training_id=32)

 I checked the site and it basically says to ensure to allow skillport in popup blocker, which I did from the beginnning.  What makes me beleive its the java applet, is that, on my Mac OS, I have no issues running this website in firefox at all.  I checked the add-ons and I see that I have a java applet installed.  Which is why I beleive its a java applet problem.    After reseraching, I saw that a few people ran in to the same problem, but the commands that they are using are not working for me.  So any help you can provide will be greatly appreciated.

---

### Post by Welly Wu on 2012-04-07
Thomas,

This might help you to install Java: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java).

---

### Post by kazztan0325 on 2012-04-07
> **MaxxABillion said:**
> After reseraching, I saw that a few people ran in to the same problem, but the commands that they are using are not working for me.

Which version of Ubuntu and Firefox are you using?

Are "*the commands*" which you mentioned what have been discussed on following thread?

**"[ubuntu] Skillsoft not working"**
[http://ubuntuforums.org/showthread.php?t=1669014]("http://ubuntuforums.org/showthread.php?t=1669014")

---

### Post by MaxxABillion on 2012-04-07
> **kazztan0325 said:**
> Which version of Ubuntu and Firefox are you using?

Are &quot;*the commands*&quot; which you mentioned what have been discussed on following thread?

**&quot;[ubuntu] Skillsoft not working&quot;**
[http://ubuntuforums.org/showthread.php?t=1669014](http://ubuntuforums.org/showthread.php?t=1669014)

 Yes thats the particular post, and the commands do not work for me.

---

### Post by Welly Wu on 2012-04-07
Thomas, you need to determine which specific version of Java skillport requires in Mozilla Firefox.

You should install SUN Java JRE and JDK and remove OpenJDK and the IcedTea plugin.

Here is how to do it in step-by-step method:

To remove OpenJDK and the IcedTea plugin:
1. sudo apt-get remove openjdk-6-jre && sudo apt-get remove icedtea6-plugin. Type in your administrator password.

2. exit Mozilla Firefox. Then, launch Mozilla Firefox and type in about:plugins in the address bar. See which version of Java is installed in Mozilla Firefox and make a note. Exit Mozilla Firefox.

Install SUN Java JRE and JDK:
3. JDK or JRE
Downloads the Java binary installers from Oracle, builds the .deb packages locally on your computer and then installs them. Packages are compatible with the “official” Ubuntu ones and will upgrade Java 6 that was previously installed from packages.

You can find the script and full usage instructions on github.

[https://github.com/flexiondotorg/oab-java6](https://github.com/flexiondotorg/oab-java6)
Manual method
Do-it-yourself method, but very easy to apply (basically: you copy/paste some terminal commands).

oracle java 6 jre

 $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)
 $ chmod u+x jre-6u31-linux-i586.bin
 $ ./jre-6u31-linux-i586.bin
 $ mv jre1.6.0_31 /usr/lib/jvm/
 $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_31/bin/java" 1
 $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.6.0_31/lib/i386/libnpjp2.so" 1
or

oracle java 6 jdk

 $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-i586.bin)
 $ chmod u+x jdk-6u31-linux-i586.bin
 $ ./jdk-6u31-linux-i586.bin
 $ mv jdk1.6.0_31 /usr/lib/jvm/
 $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0_31/bin/java" 1
 $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jdk1.6.0_31/jre/lib/i386/libnpjp2.so" 1
IMPORTANT choose the java you installed as default

 $ sudo update-alternatives --config java
 $ sudo update-alternatives --config mozilla-javaplugin.so
Broken

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Find out which specific version of Java that is installed and you are using:

4. java-update-alternatives --list

Choose SUN Java JRE and JDK:

5. sudo update-alternatives --config java

Check Mozilla Firefox:

6. Launch Mozilla Firefox and type in about:plugins in the address bar. See which version of Java is installed.

7. Visit the skillsoft website and see if it works now.

Post a reply if you are still having problems or contact me directly on Facebook.

---

### Post by Welly Wu on 2012-04-07
[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

---

### Post by Welly Wu on 2012-04-07
[http://ubuntuforums.org/showthread.php?t=1905492](http://ubuntuforums.org/showthread.php?t=1905492)

---

### Post by MaxxABillion on 2012-04-07
After inputing the about:plugins...i see that I have no java at all.  This maybe the issue.  can anyone help me.  I am an newbie and just want to run skillport on firefox in the ubuntu os

---

### Post by Curtis6767 on 2012-04-07
When you did about:plugins in Firefox address bar, did you see IcedTea?

This might help: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I followed a discussion about installing Java on another thread, which is where I got the link.

Most important is to determine if your install is 32bit or 64bit because method is different for each.

64bit instructions is on the right.

32bit instructions is down the page so you'll have to scroll to it.

---

