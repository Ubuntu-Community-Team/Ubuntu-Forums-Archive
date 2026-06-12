---
title: "Installed Radeon Driver and Locked out of Ubuntu"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by TheKojuEffect on 2012-01-05
Hello Everyone,
I am using Ubuntu x64 11.10 in my HP pavilion g6-1037tx notebook.
Everything was working fine with VGA mode as it didn't recognize my Radeon 6470 HD graphics card.
Then, I downloaded radeon driver 11.12 from their website and installed it. Everything was working fine until I turned off my notebook.
When I tried to boot up the next day, my laptop freezes in both normal mode and recovery mode. I tried booting up (previous versions) in my boot menu, but same problem.
What can I do to recover my Ubuntu without doing fresh installation.

---

### Post by wildmanne39 on 2012-01-05
Hi, welcome to the forum! you can have a look at this link it should help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by QIII on 2012-01-06
Before you shut down, did you issue this command in the terminal?

```
sudo aticonfig --initial
```

---

### Post by TheKojuEffect on 2012-01-06
I didn't do that

---

### Post by QIII on 2012-01-06
And you can't even get to a command line from rescue mode?

---

### Post by TheKojuEffect on 2012-01-06
No, I can't even go to recovery mode from boot menu.

---

### Post by pastalavista on 2012-01-06
I misread and misspoke.. sorry, I don't know how to delete this post

---

### Post by waynefoutz on 2012-01-06
If you can boot into the command line: 



```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases

sudo dpkg-reconfigure xserver-xorg
```

If not, reinstall.

That ATI card is a "switchable" graphics card, meaning it's not your primary graphics card. 

here's a link on how to get it working (it's not for the faint at heart):

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

My best advice is to stick with Windows on that particular machine, at least for now

---

### Post by wildmanne39 on 2012-01-07
Hi, if it is because of the video card driver you should be able to get back in by:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Be sure you have root access with networking.
Thanks

---

### Post by QIII on 2012-01-07
Unfortunately, guys, all the suggested commands in the world won't help him at all if he can't get a command line.

First thing we need to do is get him to a command line.

---

### Post by bcschmerker on 2012-01-07
Unfortunately, it looks as though a reinstall may be forced.  From my own experience with 10.04.4-LTS with backported Kernels from later releases (I currently use Kernel 3.0, package: linux-image-generic-pae-lts-backport-oneiric), to my understanding as of 6 January 2012, [Advance Micro Devices®](http://www.amd.com/) has yet to catch up with the [LinUX Kernel Project](http://www.kernel.org/) on drivers for the R700-and-later series GPU's on Kernels 3.0-up; a Windows driver installed in error (as AMD® does fully support the Radeon® HD 6000 Series in Microsoft® Windows® Se7en 7.0.80xx and Server 2008 Release 2 6.1.76xx) could very well be enough to lock up the system.

The Live CD, fortunately, should allow recovery of whatever is in the /home subdirectory of the borked-11.10-install partition on the hard drive prior to reformat and reinstall.

---

### Post by TheKojuEffect on 2012-01-07
Thanks for all your support but since I can't even get into recovery mode, I had to reinstall ubuntu with the option "Upgrade 11.10 to 11.10" which worked fine for me.

And Just to Say, my laptop is all fine for ubuntu if I forget about graphics card in my laptop.
HP pavilion g6-1037tx ATI Radeon 6470 HD graphics card

---

### Post by QIII on 2012-01-07
After doing some searching around, it seems others are able to use the proprietary driver with similar machines.

Does this machine have a dual graphics card arrangement?

---

### Post by TheKojuEffect on 2012-01-07
The additional driver provided by ubuntu does work to some extent, but not so good.
In windows 7, I could switch graphics from ati radeon to power saving gpu.
Is this dual graphics card management ?

---

### Post by bcschmerker on 2012-01-08
> **TheKojuEffect said:**
> The additional driver provided by ubuntu does work to some extent, but not so good.
In windows 7, I could switch graphics from ati radeon to power saving gpu.
Is this dual graphics card management ?As I previously stated, as of 8 January 2012, Advance Micro Devices® has yet to catch up with the LinUX Kernel Project on drivers for Kernels 3.0-up.  The Catalyst™ Control Center (package: fglrx-amdcccle), which is capable of managing multiple Radeon® HD™ series GPU's, works only up to Kernel 2.6.38, meaning that it *will not* function in Oneiric.

---

### Post by pastalavista on 2012-01-08
> **QIII said:**
> Unfortunately, guys, all the suggested commands in the world won't help him at all if he can't get a command line.

First thing we need to do is get him to a command line.
+1

 ... this is why my comment was irrelevant as well as everyone else's so far, except yours QIII

---

### Post by waynefoutz on 2012-01-09
> **bcschmerker said:**
> As I previously stated, as of 8 January 2012, Advance Micro Devices® has yet to catch up with the LinUX Kernel Project on drivers for Kernels 3.0-up.  The Catalyst™ Control Center (package: fglrx-amdcccle), which is capable of managing multiple Radeon® HD™ series GPU's, works only up to Kernel 2.6.38, meaning that it *will not* function in Oneiric.

His card is a hybrid graphics card, meaning it's not the laptop's primary graphics card. The Windows driver switches it on when it's needed. 

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

