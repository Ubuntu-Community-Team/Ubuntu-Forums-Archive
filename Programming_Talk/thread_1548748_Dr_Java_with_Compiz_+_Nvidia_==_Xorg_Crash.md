---
title: "Dr Java with Compiz + Nvidia == Xorg Crash"
date: 2010-08-08
forum: Programming Talk
---

### Post by Quake on 2010-08-08
I've been trying to figure out how to make Dr.Java work with Compiz and Nvidia but to no avail.  I even tried this trick but it doesn't work [http://ubuntuforums.org/showthread.php?t=455896](http://ubuntuforums.org/showthread.php?t=455896)

I know it's a known bug: [http://drjava.org/compiz/](http://drjava.org/compiz/), but weirdly, it works fine on my laptop which has an Ati video card. 

Does anyone else use Dr.Java?

Btw, I posted it here because I doubt non-programmers use the program.

---

### Post by Queue29 on 2010-08-08
> **Quake said:**
> I've been trying to figure out how to make Dr.Java work with Compiz and Nvidia but to no avail.  I even tried this trick but it doesn't work [http://ubuntuforums.org/showthread.php?t=455896](http://ubuntuforums.org/showthread.php?t=455896)

I know it's a known bug: [http://drjava.org/compiz/](http://drjava.org/compiz/), but weirdly, it works fine on my laptop which has an Ati video card. 

Does anyone else use Dr.Java?

Btw, I posted it here because I doubt non-programmers use the program.

I gave it an honest go for one of my programming assignments just a few weeks ago (I don't use compiz). While it does actually have some nice features, the font rendering is **horrid**, and not worth chasing a ghost of a solution for this bug.

---

### Post by Quake on 2010-08-08
> **Queue29 said:**
>  While it does actually have some nice features, the font rendering is **horrid**, and not worth chasing a ghost of a solution for this bug.

For me, the fonts aren't that bad on my system, I've installed the java fonts.

---

### Post by mgricken on 2010-08-09
From what I've heard, the Java/Compiz problem has been fixed in Ubuntu 10.04 with compiz 0.8.4.

We haven't been able to test this sufficiently, though, and therefore we haven't removed the Compiz warning from DrJava yet.

Does your computer actually crash when you try to use it?

---

### Post by Quake on 2010-08-09
Thank you for replying.

Yes, it crashes Xorg. Xorg takes 100% off the CPU and the only way to restart the computer (or Xorg) is by SSH, the CTRL+ALT+Fx keys does not work.

By what I've seen, each time Dr.Java highlights a text, the screen flickers. When it's maximized, the problem is minimized, but after continual use, it crashes Xorg.

I hope I have been clear enough, if you need more information, does not hesitate to tell me what to do in order to gather information.

---

### Post by mgricken on 2010-08-09
> **Quake said:**
> Yes, it crashes Xorg. Xorg takes 100% off the CPU and the only way to restart the computer (or Xorg) is by SSH, the CTRL+ALT+Fx keys does not work.

Could you please let me know what version of Ubuntu you are using?
Additionally, please let me know the Java and compiz version on your machine.

You can get the Java version using

java -version

and the compiz version using

compiz --version

We've had positive reports on Ubuntu 10.04 with Sun's Java 1.6.0_20 and compiz 0.8.4. I'm sorry that, should this still crash for you, there is nothing we can do. It is definitely a Java bug (see also [https://bugzilla.redhat.com/show_bug.cgi?id=608977](https://bugzilla.redhat.com/show_bug.cgi?id=608977) ).

Thanks for your help!

---

### Post by Quake on 2010-08-09
I wonder if my configuration is wrong somewhere because my ATI machine is fine.

Compiz version: 0.8.4
java version: 1.6.0_18

---

### Post by mgricken on 2010-08-09
> **Quake said:**
> java version: 1.6.0_18

Please try upgrading to Java 1.6.0_20. From what I've heard, this has only been fixed very recently.

---

### Post by Quake on 2010-08-09
Thank you! Upgrading to Java 1.6.0_20 did the trick!

Edit: Only when maximized... The screen still flickers when it's windowed.

---

### Post by cynthia386 on 2010-10-31
> **mgricken said:**
> From what I've heard, the Java/Compiz problem has been fixed in Ubuntu 10.04 with compiz 0.8.4.

We haven't been able to test this sufficiently, though, and therefore we haven't removed the Compiz warning from DrJava yet.

Does your computer actually crash when you try to use it?
I still have problems with Java apps crashing with compiz, and I am on 10.10.

---

### Post by lwhitmore on 2010-11-08
I'm still getting problems.  I have to power off my machine, because everything freezes.  

I'm going to try to find a PPA with a newer version of Compiz and see if that sorts the problem out.

---

### Post by efhilton on 2011-06-23
I hate to say it, but I have the latest and the grandest Ubuntu (11.04).  All windows decorations die randomly during random operations on 100% of our Linux workstations.  The only common thing between all of us is that we use Java extensively (ArgoUML, NetBeans, and home grown Java apps).  Disabling compiz fixes the problem, though now we miss out on the eye candy....

Java version: 1.6.0.24.
Ubuntu: 11.04
Architecture: Thinkpad laptops (different models, T61, T60, etc.), HP 4600 desktop, and HP Z200 workstation among others.

By the way, though not as often, we still get the occasional blank java dialog.... reopening the dialog fixes the problem most of the time.

---

