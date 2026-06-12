---
title: "Minecraft stopped working in Java - Oneiric 64-bit"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by etienne@Rofti on 2011-10-07
Dear all

I have been running Oneiric 64-bit since the beta 1, and I have had no problems with it, apart from the bugs. I have happily been playing Minecraft under the IcedTea open Java implementation. However, literally overnight it stopped working. Last night I was playing it, and today it no longer works. I tried updating/upgrading, thinking a bug fix or something might come through, but that did not help.

In the terminal, this is the error message I get:
```
Exception in thread "Minecraft main thread" java.lang.ExceptionInInitializerError
	at net.minecraft.client.Minecraft.a(SourceFile:183)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
```
I did not upgrade or change anything since last night, until it stopped working and I only THEN upgraded in the hopes that it might work.

Does anyone have any suggestions?

Thanks in advance!

---

### Post by etienne@Rofti on 2011-10-09
It seems that the entire internet has been stumped by this problem... Even Google doesn't seem to know the answer...
It doesn't even seem to work in Oracle's Java. Same error...

---

### Post by SpEcIeS on 2011-10-09
Unless there is a particular reason that IcedTea is being used, try using Sun Java (1.6.0_26-b03), which has been working very well for minecraft.

Edit:

Seems sun-java packages were pulled from "partner", so here is the PPA:

[https://launchpad.net/~duh/+archive/sun-java6](https://launchpad.net/~duh/+archive/sun-java6)

AMD64 && i386

YOUR_UBUNTU_VERSION_HERE = Lucid || Maverick || Natty || Oneiric

deb [http://ppa.launchpad.net/duh/sun-java6/ubuntu](http://ppa.launchpad.net/duh/sun-java6/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/duh/sun-java6/ubuntu](http://ppa.launchpad.net/duh/sun-java6/ubuntu) YOUR_UBUNTU_VERSION_HERE main 

sudo add-apt-repository ppa:duh/sun-java6
sudo apt-get update

---

### Post by hollowsyndicate on 2011-10-10
minecraft = sunjava not openjd

---

### Post by Gnurfos on 2011-10-10
Mine is working right now, but for similar problems, a suggested solution was to download some recent lwjgl libs and put them in the minecraft folder (replacing the ones provided by minecraft).

This did not solve my problem at that time, but it could be your solution.

---

### Post by SpEcIeS on 2011-10-10
If one would like the lastest Sun Java, Version 6 Update 27, then follow the below links:

**[https://www.java.com/en/download/linux_manual.jsp?locale=en]("https://www.java.com/en/download/linux_manual.jsp?locale=en")**

---

### Post by etienne@Rofti on 2011-10-11
Thank you all for your friendly remarks.

I will be following SpEcIeS's advice and will be installing the PPA for SunJava - although I downloaded the latest Java from Oracle's website. I guess Notch is still designing the entire game around SunJava 6. I guess it's his decision.

I will let you know how it went, since I am not at home right now...

---

### Post by jonny on 2011-10-11
> **SpEcIeS said:**
> Unless there is a particular reason that IcedTea is being used, try using Sun Java (1.6.0_26-b03), which has been working very well for minecraft.

Edit:

Seems sun-java packages were pulled from "partner", so here is the PPA:

[https://launchpad.net/~duh/+archive/sun-java6](https://launchpad.net/~duh/+archive/sun-java6)

AMD64 && i386

YOUR_UBUNTU_VERSION_HERE = Lucid || Maverick || Natty || Oneiric

deb [http://ppa.launchpad.net/duh/sun-java6/ubuntu](http://ppa.launchpad.net/duh/sun-java6/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/duh/sun-java6/ubuntu](http://ppa.launchpad.net/duh/sun-java6/ubuntu) YOUR_UBUNTU_VERSION_HERE main 

sudo add-apt-repository ppa:duh/sun-java6
sudo apt-get update
That PPA worked fine for me.  Minecraft is now working in the browser, but I haven't yet tried it as a standalone executable.  Just for the record, I installed all relevant java packages from the repository including, probably unnecessarily, the developers' toolkit, and rounded it off with this command:
```
sudo update-java-alternatives -s java-6-sun
```
I'd been looking for an Oracle/Sun Java PPA for Oneiric to get Eclipse-Pydev working and for some reason failed to find that one.  Thanks for pointing it out.

---

### Post by linuxman94 on 2011-10-11
Are you playing the classic version or the beta?

---

### Post by jonny on 2011-10-12
> **linuxman94 said:**
> Are you playing the classic version or the beta?Not me... my son ;)

I believe he's on the beta.

---

