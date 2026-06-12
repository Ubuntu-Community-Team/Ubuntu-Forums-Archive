---
title: "Why is Java so much faster in this case on Linux?"
date: 2009-03-02
forum: Programming Talk
---

### Post by cl333r on 2009-03-02
Hi folks,
I got windows XP and Ubuntu on same machine, and running the same Java applet test yields only about 55 fps on windows XP and about 195 fps on Ubuntu (the test is btw [http://bubblemark.com/java_optimized.html](http://bubblemark.com/java_optimized.html)) with Java 6 update 12 in both cases, also tested with Ubuntu 8.10' Java 6 update 10 - same 195 fps. That is almost 400% faster for Linux.

The question: Java for windows enjoys graphics acceleration and Linux doesn't, so how come the speed results are so unexpected?

I've seen the source code, it has to do with lots of math using "double" types, could it be that Java on Linux somehow handles double mathematics so well (or windows handles so bad) ?

---

### Post by jyaan on 2009-03-02
You're mistaken about the graphics acceleration. Linux definitely has it with projects such as JOGL out there. :P

---

### Post by CptPicard on 2009-03-02
Is your Linux (OS / Java VM) 64bit and Windows not?

---

### Post by cl333r on 2009-03-02
I was almost sure someone is gonna say that.
1) I mean the default sun's jre.
2) There's no JOGL code in the test applet I'm talking about.

I'm not mistaken, you misunderstood or you're misinformed:
> New Direct3D Accelerated Rendering Pipeline for Microsoft Windows Platforms, Enabled by Default 
[http://java.sun.com/javase/6/webnotes/6u10.html](http://java.sun.com/javase/6/webnotes/6u10.html)

---

### Post by cl333r on 2009-03-02
> **CptPicard said:**
> Is your Linux (OS / Java VM) 64bit and Windows not?

Both windows and Linux versions are 32 bit on 32 bit chip: Intel Pentium D 3.4 Ghz.
Nvidia's binary drivers installed on windows and Ubuntu.
Geforce 7600GT 256MB, 2GB ram.

---

### Post by jyaan on 2009-03-02
Well, my point stands that Linux has graphics acceleration. It just doesn't use D3D, but OpenGL instead. No idea what's in the applet because it lagged my browser. :S

It's also possible that they developed the program on Linux and did barely any Windows testing. :P Just kidding of course.

---

### Post by Reiger on 2009-03-02
Well it might be that Linux is willing to dedicate more CPU to Java than XP is, or that some browsers are inherently better at working with the Java plugin on Linux than others are on Windows.

---

### Post by slavik on 2009-03-02
linux is simply better ... Next :)

---

### Post by Ferrat on 2009-03-02
I'm getting 190-200FPS as well (with 16 balls, 100FPS+ with 32balls, 50+ with 64 balls and 25FPS+ with 128 balls so on) on a 32bit system, Java is using ~25% of the cpus power and holing steady at that.

---

### Post by Bulletbeast on 2009-03-02
I'm also getting ~50 with 64 balls, but only ~90 fps with 16 balls, Athlon64 3800+, Geforce 7600GS 256, 1GB RAM, running Intrepid 64... help?

---

### Post by Gordon Bennett on 2009-03-02
Ok I ran some tests, and I get the same FPS with 1 ball that I do with 16 (190FPS), with 128 balls I get 115FPS.

This leads me to believe the Java app is timer-restricted; Windows could be throttling the app's draw timer.  Also note that variants of Linux with X11/Cairo/Compositing enabled, graphics are heavily accelerated.

While running graphics tests, if your CPU timer is below 100% (e.g. 25%) it is very likely the draw ops are being deferred to an accelerated subsystem - the greater the gap, the more that is being accelerated in proportion to CPU use.

---

### Post by Reiger on 2009-03-02
I see Java+Linux (Firefox) actually performing worse than Windows Vista 64bit here, consistently by a factor of 2. It may be that the ATI Linux drivers are simply much more limited compared to their Windows counterparts...

---

### Post by johnycage on 2009-03-02
Windows XP released way back in 2001 & SP 2 in ~2004 with only some changes with firewall/security settings.
Ubuntu on the other hand is more technologically aware of the other (such as java) softwares and developements.

You can compare windows contemporary OS with current Ubuntu, say **Ubuntu 9.04 Alpha/beta Vs Windows 7**. ;)

PS: I am not agaist/pro or biased...

---

### Post by Can+~ on 2009-03-02
> **Reiger said:**
> I see Java+Linux (Firefox) actually performing worse than Windows Vista 64bit here, consistently by a factor of 2. It may be that the ATI Linux drivers are simply much more limited compared to their Windows counterparts...

Actually, it's a limitation on Firefox, specially with javascript.

[http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty](http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty)

---

### Post by Npl on 2009-03-02
I`d try running it directly, ie not as Applet in a Browser. Its likely the Browser and/or Java-Plugin restricts or disables Hardware-Accelerated drawing. The spec for netscape-plugins is from 1996 after all, and Applets gotta run through that ancient pipe.

---

### Post by Reiger on 2009-03-02
> **Can+~ said:**
> Actually, it's a limitation on Firefox, specially with javascript.

[http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty](http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty)

Well I would try testing in Opera (if only because that's what I used for the Windows testing), only there isn't a proper 64bit plugin for sun-java6 in the repositories? (aptitude can't find the sun-java6-plugin, though on a 32bit system the equivalent is present). Don't think I'm complaining, though: the 32bit plugin with Opera on my 32bit system (a laptop) => system hang. Iced-tea/Open JDK/JRE plugins simply won't load the applet on a 64bit system. Oh well, guess that leaves Konqueror for the occasional Java based page.

---

