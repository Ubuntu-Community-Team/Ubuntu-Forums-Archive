---
title: "Is two Java's possible?"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by virgodave61 on 2012-08-01
I just spent two days trying to get Java working on my system with the help of the forum I finally achieved success. But to my dismay when I tried to install MpLab X, I received an error message that it requires (JRE) v6 (1.6.x), release notes say don't use 1.6.26, I had just installed Java(TM) SE Runtime Environment (build 1.7.0_05-b05). How depressing! Anyway is it possible two install two versions at the same time? If so does anybody have an idiot proof set of instructions on how to do it? Plus how to test it to see if it's working?
Thanks!

---

### Post by drmrgd on 2012-08-01
If you install the other version of Java, it will peacefully coexist with the version you have installed currently, and not overwrite it.  You can then select which version you'd like to use by default by changing its alternatives entry like this:

```
sudo update-alternatives --config java
```

For example on my work computer, I get this:

```
There are 4 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
* 1            /opt/java/32/jre1.6.0_31/bin/java               1         manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode
  4            /usr/local/java/jre1.7.0_03/bin/java            1         manual mode

Press enter to keep the current choice[*], or type selection number: 

```

I can then choose which version to run by default.  

If it's not specifically required, I'd recommend to just use OpenJDK, which - for me at least - is able to run just about everything I've thrown at it.  And it's a LOT easier to install.  Just run:

```
sudo apt-get install openjdk-6-jre
```

---

### Post by QIII on 2012-08-01
Both OpenJDK and Oracle Java prior to version 7 update 5 are vulnerable to a "fence jumping" or "sandbox jumping" or "escape" vulnerability that will allow web applets (and even some applications) to "escape" from the Java sandbox and execute in the user's context, delivering a malware payload or doing other malicious damage.

I am very surprised you have found something that still specifies Java 6, either OpenJDK or Oracle.  To be honest, I wouldn't use it if they haven't updated it yet.  Their website says not to use Java 7 "for now".  That's lazy talk for "we are to busy to deal with security for now".

Oracle Java 6 (and OpenJDK 6 with it) will reach End Of Life in November.  It is subject to security vulnerabilities beyond this one and is being killed.

At the very least, I would do four things:

1.  Install the latest version of OpenJDK 7 or Oracle Java 7 (Update 5).  (You seem to have done this already, which is good.)

2.  When you are done using that application, switch to OpenJDK or Oracle Java 7.

3.  Create an [apparmor]("https://help.ubuntu.com/community/AppArmor") profile for your application to mitigate against the risk of this vulnerability.

4. Don't use a browser while Java 6 is selected or you might risk the malware vulnerability through a malicious applet, even if your browser plugin is the most recent one.

---

### Post by virgodave61 on 2012-08-01
I did what you said and OMG it was awesome cool! Rebooted computer after just to make sure. Then did the config thing from terminal and installed MPLAB X with no problems! Thank you very much for your time! I hate very much bothering people, but have a hard time with the net, because many of the posts are old and not applicable anymore (ie. musical repositories).

Thanks again you made my day!

However thought it was strange I selected ver6, but when I go to the java test page it tells me I'm running ver7. But not important MPLAB X is flying and now I can play with my microcontrollers!:D

Thanks also QIII for your input I will make sure I do the:
 
sudo update-alternatives --config java

thing and set back to ver. 7 when I'm done with the application.
Appreciate the headsup!:P

---

### Post by QIII on 2012-08-01
> **virgodave61 said:**
> However thought it was strange I selected ver6, but when I go to the java test page it tells me I'm running ver7. But not important MPLAB X is flying and now I can play with my microcontrollers!:D

That's because you have the browser plugin for version 7 that runs web applets.  That should keep you from most of the danger of the fence-jumping exploit.  But, as I said, be extra careful.  It can happen with applications as well if you are "duped" into installing a malicious one.

---

### Post by drmrgd on 2012-08-02
> **QIII said:**
> Both OpenJDK and Oracle Java prior to version 7 update 5 are vulnerable to a "fence jumping" or "sandbox jumping" or "escape" vulnerability that will allow web applets (and even some applications) to "escape" from the Java sandbox and execute in the user's context, delivering a malware payload or doing other malicious damage.

I am very surprised you have found something that still specifies Java 6, either OpenJDK or Oracle.  To be honest, I wouldn't use it if they haven't updated it yet.  Their website says not to use Java 7 "for now".  That's lazy talk for "we are to busy to deal with security for now".

Oracle Java 6 (and OpenJDK 6 with it) will reach End Of Life in November.  It is subject to security vulnerabilities beyond this one and is being killed.

At the very least, I would do four things:

1.  Install the latest version of OpenJDK 7 or Oracle Java 7 (Update 5).  (You seem to have done this already, which is good.)

2.  When you are done using that application, switch to OpenJDK or Oracle Java 7.

3.  Create an [apparmor]("https://help.ubuntu.com/community/AppArmor") profile for your application to mitigate against the risk of this vulnerability.

4. Don't use a browser while Java 6 is selected or you might risk the malware vulnerability through a malicious applet, even if your browser plugin is the most recent one.

Very informative!  I hadn't seen that exploit and didn't realize older versions were a security risk.  I'll be updating all of my systems to newer versions right away.  Thanks for that!

---

