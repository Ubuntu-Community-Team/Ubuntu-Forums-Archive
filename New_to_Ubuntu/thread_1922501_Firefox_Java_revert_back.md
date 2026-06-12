---
title: "Firefox Java revert back?"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by Deskjockey on 2012-02-08
I'm a noobie and have been struggling with Ubuntu 11.1 for a couple months. Saturday Firefox updated and now I can't load the Merrill Lynch trading platform site. The site uses Java. It gets to "applet initialize" and crashes Firefox. 

My strong suspicion is that the ML site is not updated enough to deal with the change Saturday. For example they do not support 64-bit Internet Explorer at all. However I suspect the last version of Firefox was 64-bit but it worked with a hang or crash a couple times a day. 

Now if the last version of Firefox was 32-bit and the new one is 64-bit then that answers my question. 

If I'm guessing in the correct direction would it make sense to put the older version of Java, maybe even a 32 bit version on Firefox 10 or just go back to Firefox 9.01 or whatever the last one was that we had. 

I suppose I can't use the Ubuntu Software Center to revert back except to remove the current version. So where do I go for the prior version of Java or Firefox? And I assume I have to write some short code to get what I need or load some other popular Software Center that I remember reading a month or two ago that everybody likes. I would appreciate being pointed to some idiot proof step by step directions if I'm on the right path.

---

### Post by sammiev on 2012-02-08
Can you go to your system info screen and copy/paste that info please. Then we can help you. Your post lacks a little info between the 32 and 64 bit. :)

---

### Post by Gremlinzzz on 2012-02-08
:popcorn:Java
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by graemev on 2012-02-09
For what it's worth I also see this firefox crash following recent firefox upgrade:

**IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.2))**

 File:  /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.soVersion:

---

### Post by Deskjockey on 2012-02-09
> **sammiev said:**
> Can you go to your system info screen and copy/paste that info please. Then we can help you. Your post lacks a little info between the 32 and 64 bit. :)

I'm not able to copy paste for some reason but I can retype it. 

Memory:  7.8 Gb

Processor:  AMD Phenom II X4 B45

Graphics:  Geforce 210/PCI/SSE2   (experience standard) 

OS:  64 bit

Disk:  30.2 GB    (that holds Ubuntu and my files are on the balance of the 320gb disk)
[U]
Default Apps[/U]

Firefox

TBird

gedit

Movie Player

Image Viewer

Here is the crash report

  	 	 	 	 	 	   Add-ons: [email]globalmenu@ubuntu.com:2.0.2,langpack-en-GB@firefox.mozilla.org:10.0,langpack-en-ZA@firefox.mozilla.org:10.0,ubufox@ubuntu.com[/email]:1.0.2,{972ce4c6-7e08-4474-a285-3208198ce6fd}:10.0 
 BuildID: 20120129141257 
 CrashTime: 1328821059 
 EMCheckCompatibility: true 
 FramePoisonBase: 7ffffffff0dea000 
 FramePoisonSize: 4096 
 InstallTime: 1328409028 
 Notes: OpenGL: NVIDIA Corporation -- GeForce 210/PCI/SSE2 -- 3.3.0 NVIDIA 280.13 -- texture_from_pixmap 
  
 ProductName: Firefox 
 SecondsSinceLastCrash: 69141 
 StartupTime: 1328814501 
 Theme: classic/1.0 
 Throttleable: 1 
 URL: [https://marketq.fs.ml.com/Launch](https://marketq.fs.ml.com/Launch) 
 Vendor: Mozilla 
 Version: 10.0 
  

Here is an error log

A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f72978005ba, pid=3049, tid=140129751623424
#
# JRE version: 6.0_23-b23
# Java VM: OpenJDK 64-Bit Server VM (20.0-b11 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.11pre
# Distribution: Ubuntu 11.10, package 6b23~pre11-0ubuntu1.11.10
# Problematic frame:
# V  [libjvm.so+0x4175ba]  frame::sender_for_compiled_frame(RegisterMap*) const+0x7a

---

### Post by sammiev on 2012-02-09
Now if your 11.10 version is a 64 bit version use the post that Gremlinzzz supplied and follow the instructions for 64 bit. I use the same java and instructions that Gremlinzzz uses. :)

---

### Post by Deskjockey on 2012-02-09
> **sammiev said:**
> Now if your 11.10 version is a 64 bit version use the post that Gremlinzzz supplied and follow the instructions for 64 bit. I use the same java and instructions that Gremlinzzz uses. :)


I have been looking at that and trying to make sense of it. What I don't understand is that everything changed with the last update of Firefox on Saturday yet the Java seems  the same JDK type rather than JRE.

---

### Post by Dry Lips on 2012-02-09
I recommend that you remove OpenJDK and the Icedtea plugin and install Oracle Java. 
Lots of stuff simply doesn't work with OpenJDK.

So, assuming you run 11.10:
```

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

(rember to remove OpenJDK & Icedtea... This can be done from the software centre.)

---

### Post by Deskjockey on 2012-02-09
Dry Lips,
 
That seems to be the answer but I may not be able to try it for a while, I can't log into to my computer now. I fortunately have a spare Vista computer for such a crisis as this. The problem is I have not done a backup on Ubuntu because I don't know how nor the 10 minutes to find out how because of too many crisis in the past six months. I have all my files on a separate partition but I assume my Firefox is probably on the Ubuntu Partition so I'm going to spend the next week or two trying to figure out the password problem when time permits so that I can save all my emails if possible. When that is done or I just bite the bullet and load a new Ubuntu I'll go ahead and put in Sun. 
 
When I first joined the forum I asked if it was a bad idea to let updates load and everybody said no problem. My history has always been the opposite, if it is working at all, even if poorly don't change anything.

---

### Post by Deskjockey on 2012-02-15
Dry Lips

I have recovered from my crash and re-installed 11.10 and have most files back. I looked at the link by Gremlinzzz from the Sun site and it suggested just delete Icedtea not OpenJDK, what are the pros and cons? 

I have almost zero command line skills. What directory do I do your command from / ?  How do I get there from /home? I can't change directories using cd/.  I suspect that I'm missing a module to effectively use the command line. The command line opens as;

 xxxx@xxxx-System-Product-Name:~$xxxx@xxxx-System-Product-Name:~$   

 ( "xxxx") my computer name

---

### Post by QIII on 2012-02-15
DeskJockey

I would steer clear of the PPA.  Use the suggested site from Gremlinzzz.  PPAs should be used sparingly.

OpenJDK is an open source impementation of Java.  It would be nice if the world recognized it as Java, but not everyone does.  Some applications and sites require Sun Java.

What you are using on a website is a browser plugin.  In the case of OpenJDK it is called IcedTea.  Often it simply does not work -- again because it it is not Sun's plugin.

The site referred to by Gremlinzzz says not to remove OpenJDK because doing so might damage your system by removing common dependencies (but I think that has been largely resolved in the most recent versions/repos).  This was a beef I had with that site for quite some time (because the instructions used to say to uninstall OpenJDK) until I had contact with one of the maintainers, who assured me that part had been removed.

Use the easy linux tips tutorial.  If you can cut and paste, you can do it without "command line skills".  Just remember that to paste in the teeminal you need to use CNTL + SHIFT + V.

I install Java by essentially the same process, changing a few things to my purposes and changing the location of the symbolic link to the browser plug in.

---

### Post by Deskjockey on 2012-02-15
QIII

YOU ARE THE MAN. The web page opened and is working. I will admit that I spent 30 minutes trying everything to find why the terminal couldn't find the file, yet I could manually go to it in the side bar. Out of frustration I checked the file against the instructions and realized they have the 31 version instead of 30 that I was copying and pasting. :P

Deskjockey

---

