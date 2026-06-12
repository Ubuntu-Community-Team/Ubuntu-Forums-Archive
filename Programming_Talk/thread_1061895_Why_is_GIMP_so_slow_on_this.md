---
title: "Why is GIMP so slow on this?"
date: 2009-02-06
forum: Programming Talk
---

### Post by cl333r on 2009-02-06
Hi folks,
I noticed that when I'm drawing lines in GIMP it starts using right away above 60% of both my CPU cores. That's horrible. Anybody else got such experience?
On the flip side there's a Java applet on the web I googled for to test whether all apps behave the same, but it uses almost no CPU at all:
[http://www.stowlake.com/files/draw.html](http://www.stowlake.com/files/draw.html)
Even Flash (see attached file) is performing a lot better without any optimizations.
Is this by design or something wrong with GIMP? (If by design, it's certainly a bad one).

PS: Rather than slow I'd rather say "CPU intensive"

2GB ram, Intel D 3.4Ghz, GeForce 7600GT 256MB, with standard Ubuntu nvidia binary drivers.

---

### Post by khelben1979 on 2009-02-06
I think you need better nVidia drivers. If the drivers are bad, the cpu cores needs to work very hard.

---

### Post by cl333r on 2009-02-06
I got the standard ones that come with Ubuntu, as I stated in the 1st post.
I watch movies and the CPU isn't loaded at all, so I think my drivers are fine, and afaik Gimp doesn't use GPU acceleration (unlike latest version of photoshop). And also why then is the "slow" flash working faster than gimp, including Java.

---

### Post by khelben1979 on 2009-02-06
Okay, then I don't know.

[Gimper.net]("http://gimper.net/") is a forum which I found today which might be of interest to you?

---

### Post by Reiger on 2009-02-06
That's odd never noticed such a thing myself. I checked, and in both cases (both the Java Applet and GIMP) I could hear the GFX card spring into action. GIMP is only marginally slower than the Java applet is; but GIMP has to pull more weight too...

---

### Post by Martje_001 on 2009-02-06
Did you deactivate compiz?

---

### Post by cl333r on 2009-02-06
Compiz is deactivated cause the nvidia driver is glitchy while rendering the window title, this bug seems to be solved in the driver 180.27 which is shipped with Jaunty alpha 4.

---

