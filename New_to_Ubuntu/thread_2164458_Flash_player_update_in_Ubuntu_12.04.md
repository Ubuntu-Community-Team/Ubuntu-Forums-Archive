---
title: "Flash player update in Ubuntu 12.04"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by flyfishingphil on 2013-07-31
OK, lost again!

Have Firefox with latest updates and have just installed Chromium to see if that would gt around the problem. Having problems with requirements for latest version of Flash Player.

Several questions:

1. Is the latest version of Adobe Flash Player workable in Ubuntu 12.04 with latest updates?

2. If so, is there an easy step-by-step reference on the installation that anybody could follow? (Hate those that assume you already know how to do everything and forget to mention critical steps to the process.)

3. Also installed Chromium, because several other posts said it gets around the FP problems and is up to date, but found I get nowhere (on Pogo) with anything that requires Java or Flash player. Suggestions?

Thanks for the help for one that tends to forget lots of tech stuff.

ffp

---

### Post by SweetAurora on 2013-07-31
Adobe no longer updates Flash on linux anymore. Version 11.2 was the last. If you **MUST **have the latest Flash Player, you have to install Google Chrome. Chrome comes with an up to date copy of Flash for Linux by means of Google's intervention. Google keeps flash alive in the form of Pepper Flash which is an only Chrome compatible plugin.

---

### Post by flyfishingphil on 2013-07-31
> **flyfishingphil said:**
> OK, lost again!

Have Firefox with latest updates and have just installed Chromium to see if that would gt around the problem. Having problems with requirements for latest version of Flash Player.

Several questions:

1. Is the latest version of Adobe Flash Player workable in Ubuntu 12.04 with latest updates?

2. If so, is there an easy step-by-step reference on the installation that anybody could follow? (Hate those that assume you already know how to do everything and forget to mention critical steps to the process.)

3. Also installed Chromium, because several other posts said it gets around the FP problems and is up to date, but found I get nowhere (on Pogo) with anything that requires Java or Flash player. Suggestions?

Thanks for the help for one that tends to forget lots of tech stuff.

ffp

That was my understanding but tried Chrome the other day and got nowhere. Also had problems getting into my business side Open Exchange email because of the big ad panel that runs on Chrome. Read several places where Chromium is the better version for Ubuntu but it seems to have the same problems on Java and Flash Player as Firefox. It does allow me to check my business email, provides my complete Yahoo homepage with the bookmark tags, but doesn't seem to offer a solution.

Maybe what I need to do is break down and use the Win$ Vista I have as a second drive and do the 'net flash and java stuff from there. Hate using that because of all of the inherent problems with Win$.

Thanks for the suggestion though.

ffp

---

### Post by deadflowr on 2013-07-31
I think there is a misunderstanding here.
Flash on Ubuntu is fully up to date.

Google-Chrome, however, runs a newer version of flash built into it.

The flash available for linux is older, but it is still fully maintained and supported by Adobe.

---

### Post by ajgreeny on 2013-07-31
What hardware do you have, and in particular is it sse2 enabled?

Run command ```
cat /proc/cpuinfo | grep sse2
``` If you get no output your cpu is not sse2 enabled and you will have to run the older flash version 11.1.

Go to [Flash 11.1.102-63]("http://ubuntuforums.org/showthread.php?t=1953796") to get all the info about downloading and installing that version.  This is a problem that has been mentioned many times on many forums, but most linux users are totally unaware of the problem, as was I when I had a sempron 2400+ cpu, one of those with this sse2 problem.

See [http://www.linuxformat.com/forums/viewtopic.php?t=16132&highlight=](http://www.linuxformat.com/forums/viewtopic.php?t=16132&highlight=) for another forum thread about the same trouble, luckily with a solution.

---

### Post by flyfishingphil on 2013-07-31
Here is what shows in Terminal: (NOTE: System info at bottom of post)
 
cat /proc/cpuinfo | grep sse2
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm

Also note that the current version I have installed is the one from the software center. That is version flashplugin-installer 11.2.202.297ubuntu12.04.1

Add a little more fun to this one. Tried Chromium, from the software center, and found that I can receive business emails but cannot send while it is installed. Uninstalled it and everything works fine again. Guess Chrome/Chromium and I don't get along!

---

### Post by flyfishingphil on 2013-07-31
OK, did some search and found the latest "stable" version of Google Chrome and installed that. Didn't see the chance to limit the "reporting" done to Google on what I do but everything seems to be working fine unlike the one I tried the other day. Call this one solved and will start a new one if there are numerous problems.

Thanks for the assists.

OK, further research shows that anything requiring the latest Java version is not operable in Chrome. 

Did some research and found statements that the latest version of Java is not applicable to Chrome so anything requiring it sets up the notification of need to update. Testing showed I have the Java 7.25 but it is not operational regardless of settings. Chrome is NOT the "fix all" to get around the JAVA problems.

---

### Post by craig10x on 2013-07-31
Chrome fixes the flash problem but not java...are you using the open source java? If so, that could be your problem...i have a java program that does not function with open source jdk version that you get in the software center, so i had to install the licensed version, which of course, works just fine...

If that is what you need...here is the easiest way to get it (and the way i get mine) works like a charm!
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by flyfishingphil on 2013-07-31
Ran the java test and have version 7 update 25 and yes, it is enabled and all but not recognized as workable. Have been thru everything I can find to make sure it is active but they all have the same groundwork and all show it as the actual in use. Pretty much lost now unless there is someplace that has exact step-by-steps to follow from "turn computer on" to re-start and Java will be active.

---

### Post by craig10x on 2013-08-01
But which version do you have...the java that is in the software center (that is the open source jdk version) or did you install the actual licensed version from oracle?  (which you would get if you follow the instructions on the link i included in my last post)  They are BOTH at version 7 update 25...but the open source version does not always work for everything...which is why i suggested you get the licensed version...

For example...the real time quotes in my stock brokerage website work great with the licensed version but DID NOT function properly with the open source version....and i use a program called Hamsphere which is a Java file and it DOES NOT work with the open source java but works PERFECT with the licensed version...

In theory, they are supposed to be the same....but i have found that is certainly not the case at all...

You have to paste in each command individually and hit enter and let the terminal do it's thing...and there is a point where you have to say "ok" to the Oracle license agreement...otherwise it will not get installed...
And that deb package also adds a "ppa" to your software sources which will get you the latest versions as they become available, through your ubuntu updater...

---

### Post by flyfishingphil on 2013-08-01
Pretty sure it's the Oracle. I had been on that same page a couple of days ago and followed the instructions as written. Maybe I need to do a total uninstall and try a re-install just to make sure. Won't be able to do that right away though. Heading out on a week long fishing trip first thing in the morning. I'll get by with my cell until I get back.

thanks for the assists.

---

### Post by craig10x on 2013-08-01
You are very welcome...when you get back, install (if you don't already have it installed) synaptic package manager and search in there to see if you see oracle java showing as installed...that is always a good way to check...and if it is, have the package manager re-install it...

If it still doesn't work....use the terminal command in that article i linked to uninstall and try doing it again in the terminal...worth a shot, anyway ;)

---

### Post by flyfishingphil on 2013-08-10
craig10x...I'm back. Went thru the process again and still can't do anything requiring the Java. Thought this might add to the info regarding version, etc, so did the "about:plugins" and here is the entire info regarding java version, etc:

1. Shows everything as "abled".
2. Shows "Download Critical Security Update". I have no idea what that is and this shows after installing the latest. Suggestions?
3. Noticed that under "Version:", in the headline sector that nothing shows. Problem here that tells me something more must be done than the directions you posted?
4. Does the location (Location:	/opt/java/32/jre1.7.0_25/lib/i386/libnpjp2.so) have anything to do with it? If so, how/where do I need to relocate to?

Thanks again for assist.

Java(TM) (3 files) Download Critical Security Update
Java plug-in for NPAPI-based browsers.
Name:	Java Plug-in 1.7.0_25
Description:	Java plug-in for NPAPI-based browsers.
Version:	
Location:	/opt/java/32/jre1.7.0_25/lib/i386/libnpjp2.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	Java™ Plug-in	
application/x-java-applet	Java™ Plug-in Applet	
application/x-java-bean	Java™ Plug-in JavaBeans	
application/x-java-applet;version=1.1	Java™ Plug-in	
application/x-java-bean;version=1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.2	Java™ Plug-in	
application/x-java-bean;version=1.1.2	Java™ Plug-in	
application/x-java-applet;version=1.1.3	Java™ Plug-in	
application/x-java-bean;version=1.1.3	Java™ Plug-in	
application/x-java-applet;version=1.2	Java™ Plug-in	
application/x-java-bean;version=1.2	Java™ Plug-in	
application/x-java-applet;version=1.2.1	Java™ Plug-in	
application/x-java-bean;version=1.2.1	Java™ Plug-in	
application/x-java-applet;version=1.2.2	Java™ Plug-in	
application/x-java-bean;version=1.2.2	Java™ Plug-in	
application/x-java-applet;version=1.3	Java™ Plug-in	
application/x-java-bean;version=1.3	Java™ Plug-in	
application/x-java-applet;version=1.3.1	Java™ Plug-in	
application/x-java-bean;version=1.3.1	Java™ Plug-in	
application/x-java-applet;version=1.4	Java™ Plug-in	
application/x-java-bean;version=1.4	Java™ Plug-in	
application/x-java-applet;version=1.4.1	Java™ Plug-in	
application/x-java-bean;version=1.4.1	Java™ Plug-in	
application/x-java-applet;version=1.4.2	Java™ Plug-in	
application/x-java-bean;version=1.4.2	Java™ Plug-in	
application/x-java-applet;version=1.5	Java™ Plug-in	
application/x-java-bean;version=1.5	Java™ Plug-in	
application/x-java-applet;version=1.6	Java™ Plug-in	
application/x-java-bean;version=1.6	Java™ Plug-in	
application/x-java-applet;version=1.7	Java™ Plug-in	
application/x-java-bean;version=1.7	Java™ Plug-in	
application/x-java-applet;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-bean;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-applet;deploy=10.25.2	Java™ Plug-in	
application/x-java-applet;javafx=2.2.25	Java™ Plug-in	
application/x-java-vm-npruntime	Java™ Plug-in	
Name:	Java Plug-in 1.7.0_25
Description:	Java plug-in for NPAPI-based browsers.
Version:	
Location:	/usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	Java™ Plug-in	
application/x-java-applet	Java™ Plug-in Applet	
application/x-java-bean	Java™ Plug-in JavaBeans	
application/x-java-applet;version=1.1	Java™ Plug-in	
application/x-java-bean;version=1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.2	Java™ Plug-in	
application/x-java-bean;version=1.1.2	Java™ Plug-in	
application/x-java-applet;version=1.1.3	Java™ Plug-in	
application/x-java-bean;version=1.1.3	Java™ Plug-in	
application/x-java-applet;version=1.2	Java™ Plug-in	
application/x-java-bean;version=1.2	Java™ Plug-in	
application/x-java-applet;version=1.2.1	Java™ Plug-in	
application/x-java-bean;version=1.2.1	Java™ Plug-in	
application/x-java-applet;version=1.2.2	Java™ Plug-in	
application/x-java-bean;version=1.2.2	Java™ Plug-in	
application/x-java-applet;version=1.3	Java™ Plug-in	
application/x-java-bean;version=1.3	Java™ Plug-in	
application/x-java-applet;version=1.3.1	Java™ Plug-in	
application/x-java-bean;version=1.3.1	Java™ Plug-in	
application/x-java-applet;version=1.4	Java™ Plug-in	
application/x-java-bean;version=1.4	Java™ Plug-in	
application/x-java-applet;version=1.4.1	Java™ Plug-in	
application/x-java-bean;version=1.4.1	Java™ Plug-in	
application/x-java-applet;version=1.4.2	Java™ Plug-in	
application/x-java-bean;version=1.4.2	Java™ Plug-in	
application/x-java-applet;version=1.5	Java™ Plug-in	
application/x-java-bean;version=1.5	Java™ Plug-in	
application/x-java-applet;version=1.6	Java™ Plug-in	
application/x-java-bean;version=1.6	Java™ Plug-in	
application/x-java-applet;version=1.7	Java™ Plug-in	
application/x-java-bean;version=1.7	Java™ Plug-in	
application/x-java-applet;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-bean;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-applet;deploy=10.25.2	Java™ Plug-in	
application/x-java-applet;javafx=2.2.25	Java™ Plug-in	
application/x-java-vm-npruntime	Java™ Plug-in	
Name:	Java Plug-in 1.7.0_25
Description:	Java plug-in for NPAPI-based browsers.
Version:	
Location:	/usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	Java™ Plug-in	
application/x-java-applet	Java™ Plug-in Applet	
application/x-java-bean	Java™ Plug-in JavaBeans	
application/x-java-applet;version=1.1	Java™ Plug-in	
application/x-java-bean;version=1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.2	Java™ Plug-in	
application/x-java-bean;version=1.1.2	Java™ Plug-in	
application/x-java-applet;version=1.1.3	Java™ Plug-in	
application/x-java-bean;version=1.1.3	Java™ Plug-in	
application/x-java-applet;version=1.2	Java™ Plug-in	
application/x-java-bean;version=1.2	Java™ Plug-in	
application/x-java-applet;version=1.2.1	Java™ Plug-in	
application/x-java-bean;version=1.2.1	Java™ Plug-in	
application/x-java-applet;version=1.2.2	Java™ Plug-in	
application/x-java-bean;version=1.2.2	Java™ Plug-in	
application/x-java-applet;version=1.3	Java™ Plug-in	
application/x-java-bean;version=1.3	Java™ Plug-in	
application/x-java-applet;version=1.3.1	Java™ Plug-in	
application/x-java-bean;version=1.3.1	Java™ Plug-in	
application/x-java-applet;version=1.4	Java™ Plug-in	
application/x-java-bean;version=1.4	Java™ Plug-in	
application/x-java-applet;version=1.4.1	Java™ Plug-in	
application/x-java-bean;version=1.4.1	Java™ Plug-in	
application/x-java-applet;version=1.4.2	Java™ Plug-in	
application/x-java-bean;version=1.4.2	Java™ Plug-in	
application/x-java-applet;version=1.5	Java™ Plug-in	
application/x-java-bean;version=1.5	Java™ Plug-in	
application/x-java-applet;version=1.6	Java™ Plug-in	
application/x-java-bean;version=1.6	Java™ Plug-in	
application/x-java-applet;version=1.7	Java™ Plug-in	
application/x-java-bean;version=1.7	Java™ Plug-in	
application/x-java-applet;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-bean;jpi-version=1.7.0_25	Java™ Plug-in	
application/x-java-applet;deploy=10.25.2	Java™ Plug-in	
application/x-java-applet;javafx=2.2.25	Java™ Plug-in	
application/x-java-vm-npruntime	Java™ Plug-in	
Disable   Always allowed

---

