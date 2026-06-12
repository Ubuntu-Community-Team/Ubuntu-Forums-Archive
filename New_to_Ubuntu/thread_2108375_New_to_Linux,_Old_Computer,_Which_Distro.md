---
title: "New to Linux, Old Computer, Which Distro"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Beauenheim on 2013-01-24
I've been using only Windows and have attempted to use Ubuntu a few times, but it wasn't as nice as my familiar Windows 7 box last year, although very snappy and fast.
But when it comes to Linux, I just don't know. 

My main rig's video card broke, so I'm stuck with a an old laptop.

I have a Galaxy Nexus, and I also plan to start the slow process of learning how to build my own custom ROM for my phone. I figured Linux would help me with the speed of the old laptop, and get my started on my Android development.

I have

**Sony Vaio**
PCG-V505E
January 2004 
Pentium M 1.5 GHz, 
ATI Mobility 
Radeon 9200 32 MB
1GB of RAM (Upgraded myself)
137 IDE HDD
Wireless g/b
(Super thoroughly cleaned and thermal paste reapplied)

It's going to be plugged into an external 1680x1050 monitor.

So.. which distro do I use?

I installed Lubuntu with the Wubi installer, but I found it just a little faster than my n-lite super stripped version of XP. 
But what are your suggestions for those specs? What do you use?
I know that this topic has probably been posted quite a lot, but I want your current info. Any suggestions?

---

### Post by ibjsb4 on 2013-01-24
Xubuntu would be a good choice for that processor.

[http://xubuntu.org/screenshots/](http://xubuntu.org/screenshots/)

---

### Post by Sylos on 2013-01-24
As always I will be giving shout for Lubuntu. Its my choice for older hardware (unless its really old - then I go DSL).

If you have problems with the Lubuntu installer (I did with the last Lubuntu I tried) then its likely the Ubiquity slideshow. It can be removed from a live session then the install will go fine. Not sure if they have fixed this on the ISO yet.

Cheers

---

### Post by Nr90 on 2013-01-24
Lubuntu and Xubuntu will both work well with that hardware.

Debian with LXDE/XFCE might be slightly lighter. However you might find it slightly harder to set up.

Either Ubuntu or Debian with a lightweight WM like awesome WM will be even lighter, but again harder to set up.

As a newcommer to the linux world I'd recommend going with Lubuntu. I ran it for a while on my 512 mb ram / 1.4 ghz old laptop and it worked pretty well.
Currently running Debian with awesome.

PS: I wouldn't use the wubi installer. Just install from CD/USB.

---

### Post by Beauenheim on 2013-01-24
Lubuntu with the Wubi installer was quick but still choppy and could've been faster, should I use a livecd?

Maybe it just needed drivers and stuff, I didn't run it long enough to find out however, as I wanted to learn from the Ubuntu community before I set all my time into it.

---

### Post by Nr90 on 2013-01-24
wubi slows down drive access and has other limitations:
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)#Limitations](http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)#Limitations)

I would just install lubuntu natively to get a real feel for the performance. (for example run the installer from the live cd/usb)

---

### Post by Beauenheim on 2013-01-24
Alright.

So I'll try both Xubuntu and Lubuntu via live cd, and see how they differ with performance.

About UI's, which one would be easier to use?

---

### Post by mrjava on 2013-01-24
For something with that hardware, I recommend using Lubuntu 12.04 LTS.

---

### Post by Cheesemill on 2013-01-24
My go to distro for low-spec machines is always [#!]("http://crunchbang.org/") (CrunchBang).

I find it much quicker than Xubuntu or Lubuntu.

> So I'll try both Xubuntu and Lubuntu via live cd, and see how they differ with performance.
Running any OS from a Live CD wont give you a proper indication of its speed. You really need to do a full installation of your short-listed distos before you can make an informed choice. This shouldn't really take that long, you should be able to install any distro in under 20 minutes even on old hardware.

---

### Post by Beauenheim on 2013-01-24
I'll install them both and post back my results

---

### Post by verymadpip on 2013-01-25
> **mrjava said:**
> For something with that hardware, I recommend using Lubuntu 12.04 LTS.

If I recall correctly Lubuntu 12.04 [I]is not LTS.

[/I]Lubuntu 12.04 18 months support
Xubuntu 12.04 LTS 3 year support
Ubuntu 12.04 LTS 5 year support

---

### Post by Hylas de Niall on 2013-01-25
> **Cheesemill said:**
> My go to distro for low-spec machines is always [#!]("http://crunchbang.org/") (CrunchBang).

I find it much quicker than Xubuntu or Lubuntu.


Running any OS from a Live CD wont give you a proper indication of its speed. You really need to do a full installation of your short-listed distos before you can make an informed choice. This shouldn't really take that long, you should be able to install any distro in under 20 minutes even on old hardware.

+1 toall of that. #! Will play very nicely, but lubuntu will be a more familiar desktop for someone coming straight from windows.

---

### Post by snowpine on 2013-01-25
Lubuntu and Xubuntu are simply Ubuntu with different desktop environments or "skins." You can install them both and switch between them depending on your mood that day:

```
sudo apt-get install xubuntu-desktop lubuntu-desktop
```

I would expect some choppiness on such old hardware (not a realistic platform for multimedia, for example), but you should be able to perform basic tasks such as surf these forums, edit text documents, listen to music, learn Linux commands, etc. [Here are some fun project suggestions for old harware]("http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/").

---

### Post by Sarcastic Cows on 2013-01-25
Yeah, looks like Lubuntu and Xubuntu are being mentioned as well as Crunch Bang

Maybe take a look at Fedora LXDE and Mint?  guess it's all down to preference really.

---

