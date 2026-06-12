---
title: "ubuntu intel graphics driver installation"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by techtakular on 2012-07-08
Processor      : 4x Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
Memory      : 3096MB (1619MB used)
Operating System      : Ubuntu 10.04.4 LTS
Date/Time      : Sat 07 Jul 2012 04:38:16 PM EDT
-Display-
Resolution      : 1280x1024 pixels
OpenGL Renderer      : Software Rasterizer
X11 Vendor      : The X.Org Foundation
-Multimedia-
Audio Adapter      : HDA-Intel - HDA Intel

So I've playing a game in wine and its choppy, it was brought to my attention that I should try try (re-)installing the proper graphics and OpenGL drivers for your chipset. How do I do that

---

### Post by idoitprone on 2012-07-08
> **techtakular said:**
> Processor      : 4x Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
Memory      : 3096MB (1619MB used)
Operating System      : Ubuntu 10.04.4 LTS
Date/Time      : Sat 07 Jul 2012 04:38:16 PM EDT
-Display-
Resolution      : 1280x1024 pixels
OpenGL Renderer      : Software Rasterizer
X11 Vendor      : The X.Org Foundation
-Multimedia-
Audio Adapter      : HDA-Intel - HDA Intel

So I've playing a game in wine and its choppy, it was brought to my attention that I should try try (re-)installing the proper graphics and OpenGL drivers for your chipset. How do I do that


The intel drivers are bundled with the kernel. It will not help your situation

If your framerate is choppy then you probably have a multi-threaded app but wine is single threaded.

what app are you running?

---

### Post by techtakular on 2012-07-08
by app you mean program? Its *Kerbal Space Program.*

---

### Post by Mark Phelps on 2012-07-08
The link below is to the WineHQ page for that game:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13283]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13283")

Bronze means the app/game barely works -- making installing it a waste of time.  Silver means SOME functions work, but depending on what functions you need, that could be a waste of time, as well.

---

### Post by techtakular on 2012-07-08
ive been trying ** 0.13.2 **which is platinum hat shouldn't be a problem right? but it is[B]...
[/B]

---

### Post by techtakular on 2012-07-08
hello?

---

### Post by idoitprone on 2012-07-09
> **techtakular said:**
> hello?

```
wine --version
```

that program is tested with a specific version of wine.

You can test the newest version of the program to see if it works

---

### Post by techtakular on 2012-07-09
it says its wine-1.2.2

---

### Post by techtakular on 2012-07-09
so what now?

---

### Post by idoitprone on 2012-07-10
> **techtakular said:**
> so what now?

```
sudo  add-apt-repository   ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get upgrade


```

---

### Post by techtakular on 2012-07-10
I did the first bit but 

sudo apt-get update sudo apt-get upgrade
that upgrades my system? I can't do that. there is a reasaon im runing 10.04, because 12 won't run on my system upgrading ***** me over man.

---

### Post by QIII on 2012-07-10
No.  That will not upgrade your system to another version of Ubuntu.  It will update/upgrade what you have installed on your current system.

---

### Post by techtakular on 2012-07-10
ok, thanks. did all that then went to start the game and all it does now is crash.

---

### Post by idoitprone on 2012-07-10
> **techtakular said:**
> ok, thanks. did all that then went to start the game and all it does now is crash.

try a newer version of the game, or i guess you have to do the painful thing and compile the proper version of wine against your computer

---

### Post by techtakular on 2012-07-10
its wine 1.2.3 and its still crashing :/

---

