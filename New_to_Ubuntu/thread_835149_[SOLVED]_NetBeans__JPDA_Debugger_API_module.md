---
title: "[SOLVED] NetBeans / JPDA Debugger API module"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-06-20
Hi, I have a problem with NetBeans 6 on Hardy Heron.

after install i get the message: 

Warning - could not install module JPDA Debugger API
JPDA Debugger API - This module requires JDKHOME/lib/tools.jar to be accessible.
This file was not found. Usually this means you are trying to run the IDE with the JRE instead of the full JDK.
If so, please use the --jdkhome command line option to specify a JDK installation.

I found a possible solution: [http://ubuntuforums.org/showthread.php?t=688392](http://ubuntuforums.org/showthread.php?t=688392) BUT: It seems like this solution only fixes or better, surpresses the error message. 

I`m curious,...as i have newer versions of Ubuntu and NetBeans, can`t I somehow load the missing JDKHOME/lib/tools.jar? And if yes, how? 

Any ideas or newer solutions to that problem?
any help is highly appreciated! 
Regards - Jab

NetBeans Log:

[COLOR="Gray"]>Log Session: Friday, June 20, 2008 12:50:37 PM CEST
>System Info: 
  Product Version         = NetBeans IDE 6.0.1 (Build 080320)
  Operating System        = Linux version 2.6.24-16-generic running on amd64
  Java; VM; Vendor        = 1.6.0_06; Java HotSpot(TM) 64-Bit Server VM 10.0-b22; Sun Microsystems Inc.
  Java Home               = /usr/lib/jvm/java-6-sun-1.6.0.06/jre
  System Locale; Encoding = en_US (nb); UTF-8
  Home Directory          = /home/myusername
  Current Directory       = /home/myusername
  User Directory          = /home/myusername/.netbeans/6.0
  Installation            = /usr/share/netbeans/6.0.1/nb6.0
                            /usr/share/netbeans/6.0.1/ide8
                            /usr/share/netbeans/6.0.1/java1
                            /usr/share/netbeans/6.0.1/apisupport1
                            /usr/share/netbeans/6.0.1/harness
                            /usr/share/netbeans/6.0.1/platform7
  Boot & Ext. Classpath   = /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jsse.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/jce.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/charsets.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/classes:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunpkcs11.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/localedata.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/dnsns.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/ext/sunjce_provider.jar
  Application Classpath   = /usr/share/netbeans/6.0.1/platform7/lib/boot.jar:/usr/share/netbeans/6.0.1/platform7/lib/org-openide-modules.jar:/usr/share/netbeans/6.0.1/platform7/lib/org-openide-util.jar
  Startup Classpath       = /usr/share/netbeans/6.0.1/platform7/core/core.jar:/usr/share/netbeans/6.0.1/platform7/core/org-openide-filesystems.jar:/usr/share/netbeans/6.0.1/nb6.0/core/org-netbeans-upgrader.jar:/usr/share/netbeans/6.0.1/nb6.0/core/locale/core_nb.jar
-------------------------------------------------------------------------------
WARNING [org.netbeans.core.startup.ModuleList]
org.netbeans.InvalidException: StandardModule:org.netbeans.api.debugger.jpda jarFile: /usr/share/netbeans/6.0.1/java1/modules/org-netbeans-api-debugger-jpda.jar: Dependency failed on package com.sun.jdi[VirtualMachineManager]
[catch] at org.netbeans.ModuleManager.enable(Unknown Source)
	at org.netbeans.core.startup.ModuleList.installNew(Unknown Source)
	at org.netbeans.core.startup.ModuleList.trigger(Unknown Source)
	at org.netbeans.core.startup.ModuleSystem.restore(Unknown Source)
	at org.netbeans.core.startup.Main.getModuleSystem(Unknown Source)
	at org.netbeans.core.startup.Main.start(Unknown Source)
	at org.netbeans.core.startup.TopThreadGroup.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:619)
Warning - could not install module JPDA Debugger API
	JPDA Debugger API - This module requires JDKHOME/lib/tools.jar to be accessible.
This file was not found. Usually this means you are trying to run the IDE with the JRE instead of the full JDK.
If so, please use the --jdkhome command line option to specify a JDK installation.[/COLOR]

---

### Post by salutis on 2008-06-25
This worked for me:
```
sudo aptitude install sun-java6-jdk
```

---

### Post by Jabz.biz on 2008-06-25
That helped. Thanks a billion. :guitar:

---

### Post by george kaplan on 2008-07-16
Great post, salutis. I was pulling the hairs out of my nose trying to figure out what I'd done wrong and your tip fixed everything right up! Thanks!

---

### Post by enternet1988 on 2008-08-20
Yeah I second that motion,
Thanks Guys

---

### Post by indian_gamer2003 on 2008-09-01
Wow worked for me too, thanks a million. Now i can get back to finishing my college project ;)

---

### Post by hezuo on 2008-09-26
Thanks a lot man!!

---

### Post by tmera on 2008-10-18
yoo can also use **apt-get** instead of **aptitude**.  aptitude will install all of the suggested packages by default.  Also run **apt-get autoremove** to get rid of unused packages that will no longer be needed after you install the new java package.

---

### Post by ponchomx on 2008-11-08
> **salutis said:**
> This worked for me:
```
sudo aptitude install sun-java6-jdk
```

Thanks :D

---

### Post by mahboop on 2009-01-15
> **salutis said:**
> This worked for me:
```
sudo aptitude install sun-java6-jdk
```

[COLOR="Green"][B]This solved the problem :-)
Thanks Dear!

-
Good Luck![/B][/COLOR]

---

