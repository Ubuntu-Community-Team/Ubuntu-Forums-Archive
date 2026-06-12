---
title: "Ubuntu 14 LTS Freezes and has GPU Lock ups"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by Dana_S on 2014-06-26
I installed Ubuntu 14.01 LTS on my desktop - a Dell Dimension 4500 with 1 GB of memory that previous had Windows XP installed until I cleaned the drive.  I've been having so trouble with it that I'm thinking the computer is just too old for it. Ubuntu freezes a lot and now the GPU locks up.  I actually had tried to install Windows 7 before trying Ubuntu, and had issues with freezing and locking as well.  I'm at a loss and I am beyond tired and frustrated with this computer. I wonder if the best thing to do is wipe the drive clean again, but run Ubuntu only from the DVD. I wanted it on the drive for more space to store files, music, etc.  What can I try?

---

### Post by grahammechanical on 2014-06-26
You have a sufficent amount or RAM but I cannot comment on the CPU or the graphic adapter. How much memory does the graphic adapter have. Run this command

```
/usr/lib/nux/unity_support_test -p
```

This is what I see:

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

You will see something different for the top part. I am using an open source video driver. You may be using a proprietary driver. The important thing is the ability of the video adapter to run Unity. You might get a better user experience running Xubuntu or Lubuntu.

Regards.

---

### Post by Vladlenin5000 on 2014-06-26
Hi, welcome.

What are the specs of the said computer?

---

### Post by Dana_S on 2014-06-26
Dell Dimension 4500

BIOS - a04
Processor - Intel Pentium 4
Processor Speed - 2 GHz
System Bus Speed - 400 MHz

I know there is a Nvidia graphics card installed, but that's about it.

---

### Post by Vladlenin5000 on 2014-06-26
Avoiding the standard Ubuntu's Unity DE is in order for that machine. As suggested before Xubuntu or Lubuntu are preferable. However, I noticed you mentioned the same problem happening with Windows 7. That alone points to hardware issues. Also, you Dell Dimension 4500 is from the time when there was an industry wide "catastrophic" even concerning capacitors (AKA the swollen capacitors).

Diagnosing the individual components should be your priority. The Dell diags tools should be enough.

---

### Post by Dana_S on 2014-07-14
I ended up not installing Ubuntu (and uninstalling Pinguy) on this computer.  I don't think this computer is powerful enough.  I installed XP back on this computer, and will just make sure to have virus protection on it if I need to use the internet there.  Thanks for everyone's help.  I use Ubuntu from the USB stick on my Acer Aspire...I may try Pinguy as well.

---

### Post by Vladlenin5000 on 2014-07-14
You couldn't have done worse, honestly. XP is no longer supported and that means NO security updates. Those are far more important than an anti-virus.

---

### Post by JeQhdMD on 2014-07-14
I've had good results, with similar computer, upon installing Linux Lite which then uses the open source graphics driver.

---

### Post by Dana_S on 2014-07-14
I understand about the security updates.  It was long and frustrating just trying to get something installed without freezing and hanging.  At this point I don't know about trying any other versions of Ubuntu on it at this time.

---

### Post by Dana_S on 2014-07-14
JeQhdMD - I haven't heard of Linux Lite.  Interesting.  I've heard of the various Ubuntus, Pinguy, Mint, and a couple others...

---

### Post by Vladlenin5000 on 2014-07-14
Back to the beginning and quoting myself:
> Avoiding the standard Ubuntu's Unity DE is in order for that machine. As suggested before Xubuntu or Lubuntu are preferable.

Linux Lite, LXLE and hundreds of other spins are good too. The point being you need a light desktop environment.
Now, you moved from Pinguy (resources hungry) to the standard Ubuntu (even worse, its system requirements are much closer to Windows 7 than XP) which is exactly the opposite we've been suggesting.

---

### Post by Dana_S on 2014-07-14
I see what you are saying.  I went with Pinguy based on a friend's advice; she said the OS would use minimal resources.  Xubuntu and Lubuntu can run with persistance from a DVD/CD, correct?  I may start out that way until I can research more regarding having possibly two OSes on the system.  As for my Acer that I'm running either Ubuntu or Pinguy on, there isn't too much problem outside my needed a larger USB stick or another hard drive.

---

### Post by Vladlenin5000 on 2014-07-14
> **Dana_S said:**
> I see what you are saying.  I went with Pinguy based on a friend's advice; she said the OS would use minimal resources. 

Tell your friend she's wrong. PinguyOS is Ubuntu with Gnome and a few extra apps installed by default and lots of themes OOTB. Yes, Gnome shell is slightly less resource demanding than Unity but way higher than XFCE (Xubuntu) or LXDE (Lubuntu). The rest is eye candy.
 
>  Xubuntu and Lubuntu can run with persistance from a DVD/CD, correct?

Incorrect. NOTHING runs with persistence in a CD or DVD. They're read only, how would you get persistence if you can't write to the medium? A live USB can have persistence.
I suspect your interest in live sessions stems from, again, the incorrect assumption the system will somehow run better from a live media than from a standard installation in a HDD. You couldn't be more wrong.

---

### Post by Dana_S on 2014-07-14
Sorry, I meant USB, not DVD/CD.  I'm very new to anything Linux, so there are a lot of things I just do not know.  Also I am running from USB on my computer (not the one where I spents weeks trying to get something to install) because my hard drive died...

---

### Post by Vladlenin5000 on 2014-07-14
USB (usually) faster than CD/DVD
HDD much faster than USB
SSD much faster than anything else...

---

### Post by Dana_S on 2014-07-14
Ssd?

---

### Post by JeQhdMD on 2014-07-14
SSd = Solid State Drive . . . in 3-5 years may totally replace spinning hard drives.   Much faster and more reliable (no moving parts).   My chromebook with a 16gb ssd starts up in 5 seconds, shuts down in 2.

By the way, 90% + of your problems with Linux thus far is graphic driver related.    Linux Lite should default to the noveau driver (not sure if I spelled it correctly) .
Your machine should fly on Linux Lite - - and the update process is more a function of consistently good internet connections.

---

### Post by fcdecker-gmail on 2014-07-30
I had the same issue on my computer, a 2007-vintage HP workhorse with an Nvidia card. 

The culprit -- first, last, and always -- is the Nouveau driver. Apparently it works fine for some people, but it's always been a hot mess on my machine. I switched to the proprietary 304.117 driver, and it seems to work (this is just the past few days, mind you). With Nouveau in use, my GPU was crashing out about every 4-5 hours of use. 

I also installed a current version of LXLE, and it works like hot damn. Much, much faster than my prior working OS, which was Ubuntu 12.04 and 2D Unity. I opted for the 12.04 remix of LXLE, rather than the 14.04 version, which would probably also work well on your Dell. LXLE even offers a set of pre-configured desktops, called "paradigms," to emulate XP, OS X and other DEs including Unity. Worth a shot, if you're still following this thread.

---

