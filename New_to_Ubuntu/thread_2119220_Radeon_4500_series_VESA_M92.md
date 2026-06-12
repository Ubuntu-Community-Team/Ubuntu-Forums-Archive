---
title: "Radeon 4500 series VESA: M92"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by nickmrad on 2013-02-23
I got a HP laptop with ATI Radeon 4500 HD mobility series. I installed ubuntu 12.04, but noticed that the OS recognized my graphics as VESA: M92. Is this normal becuase i read somewhere that VESA: M92 doesn't give out the full performance of the graphics card. If so can I install a new driver that performs better?

---

### Post by Mark Phelps on 2013-02-23
If you're using System Info to get those results -- that basically does not work properly.

Ubuntu installed Radeon drivers for your PC automatically.  If it hadn't, you'd be seeing black blank screen.

Unless you're planning on doing intensive 3D gaming, or you're overclocking your GPU and need to do temperature management, you don't need the restricted AMD drivers.

---

### Post by nickmrad on 2013-02-23
the problem is that i'm experiencing visual lags, that is if i move lets say the terminal around it does mini jumps and doesn't move smoothly, same thing happens when i minimize a window. Moreover i enabled the visual effects in compiz but they are not working.
I got windows 8 also installed on the laptop and all of the visual effects work perfectly so the problem isn't with the graphics card.
will the restricted drivers solve my problem?

---

### Post by Pilot6 on 2013-02-23
To see driver correctly install mesa-utils.
You can install it from Software Center or in terminal

sudo apt-get install mesa-utils

Also you can install a proprietary driver from AMD, but with your card you need a fglrx-legacy.

If you give me some information, I can guide how to do it.

Open terminal and run these commands. Then post the result here.

uname -a
dpkg --list | grep xserver-xorg

---

### Post by Yellow Pasque on 2013-02-23
> **nickmrad said:**
> the OS recognized my graphics as VESA: M92. Is this normal

It's normal (albeit confusing since a lot of users automatically assume they're using the generic VESA driver).

---

### Post by QIII on 2013-02-23
The fglrx driver in the Precise repo (except 12.04.2) will probably work, so installing fglrx and fglrx-amdcccle from the standard Precise repo (except 12.04.02) will  probably work.

For 12.04.2 and beyond you will have to use the default open source Radeon driver because of the upgrade to X Server 1.13.

---

### Post by nickmrad on 2013-02-23
ok so i typed in the commands:

nicolas@nicolas-HP-Pavilion-dv6-Notebook-PC:~$ uname -a
Linux nicolas-HP-Pavilion-dv6-Notebook-PC 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

nicolas@nicolas-HP-Pavilion-dv6-Notebook-PC:~$ dpkg --list | grep xserver-xorg
ii  xserver-xorg                           1:7.6+12ubuntu1                         X.Org X server
ii  xserver-xorg-core                      2:1.11.4-0ubuntu10                      Xorg X server - core server
ii  xserver-xorg-input-all                 1:7.6+12ubuntu1                         X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev               1:2.7.0-0ubuntu1                        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse               1:1.7.1-1build3                         X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics           1.5.99.902-0ubuntu5                     Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse             1:12.8.0-1                              X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom               1:0.14.0-0ubuntu2                       X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                 1:7.6+12ubuntu1                         X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                 1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus              1:1.3.2-4build1                         X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev               1:0.4.2-4ubuntu2                        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode               2.11.13-2build1                         X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel               2:2.17.0-1ubuntu4                       X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64              6.9.0-1build2                           X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                 1:1.4.13.dfsg-4build2                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic            1:1.2.5-2build2                         X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau             1:0.0.16+git20111201+b5534a1-1build2    X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome          1:0.2.904+svn1050-1                     X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                 0.0.16-2                                X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                6.8.1-5build2                           X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon              1:6.14.99~git20111219.aacbd629-0ubuntu2 X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                  1:0.6.3-4build2                         X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage              1:2.3.3-1ubuntu1                        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion       1:1.7.5-1build2                         X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                 1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb              1:0.9.4-2build2                         X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                1:1.4.3-4build2                         X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident             1:1.3.4-2build2                         X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                1:2.3.0-7build2                         X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware              1:12.0.1-1ubuntu1                       X.Org X server -- VMware display driver

i installed a driver form amd website and enabled a driver in the additional driver section ( called fglrx). yet the problem persists.

---

### Post by Pilot6 on 2013-02-23
That is not completely true.  It is possible to use fglrx-legacy with 12.04.2. But you need to install xserver-xorg instead of xserver-xorg-lts-quantal. And use patched driver for 3.5 kernel or use 3.2.

---

### Post by Pilot6 on 2013-02-23
Show me next command please

lspci -k | grep VGA -A2

---

### Post by Yellow Pasque on 2013-02-23
> **nickmrad said:**
> i installed a driver form amd website and enabled a driver in the additional driver section ( called fglrx)

You did both? Sigh...

---

### Post by nickmrad on 2013-02-23
nicolas@nicolas-HP-Pavilion-dv6-Notebook-PC:~$ lspci -k | grep VGA -A2
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series]
    Subsystem: Hewlett-Packard Company Device 3628
    Kernel driver in use: fglrx_pci

---

### Post by QIII on 2013-02-23
> **Pilot6 said:**
> That is not completely true.  It is possible to use fglrx-legacy with 12.04.2. But you need to install xserver-xorg instead of xserver-xorg-lts-quantal. And use patched driver for 3.5 kernel or use 3.2.

A bit of a tall order for someone just trying to figure out how to install the driver, eh?  ;)

Let me step in for a moment so we can start fresh...

Let's get you back to the default open source Radeon driver.  Trying to install both could make moving on difficult.

Just to be sure we have cleared out the attempted install from the AMD website:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```This may fail.  Don't worry about it if it does.

Remove what was installed from the repo:

```
sudo apt-get purge fglrx fglrx-amdcccle
``````
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2
```Then:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri  xserver-xorg-core
``````
sudo dpkg-reconfigure  xserver-xorg
```Reboot.  You should now be on the default open source  Radeon driver.

---

### Post by Pilot6 on 2013-02-23
I could give already patched debs.

The driver looks to be installed.

Then one more command
dpkg --list | grep fglrx*

---

### Post by nickmrad on 2013-02-23
> **Temüjin said:**
> You did both? Sigh...

lol first i installed the driver from amd. then i checked the additional drivers and it notified me about the fglrx so i installed it too.
this is my first week with linux so excuse if i did something stupid :P
should i remove one of them?

---

### Post by nickmrad on 2013-02-23
> **Pilot6 said:**
> I could give already patched debs.

The driver looks to be installed.

Then one more command
dpkg --list | grep fglrx*

nicolas@nicolas-HP-Pavilion-dv6-Notebook-PC:~$ dpkg --list | grep fglrx*
ii  fglrx                                  2:8.960-0ubuntu1.1                      Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                         2:8.960-0ubuntu1.1                      Catalyst Control Center for the AMD graphics accelerators

---

### Post by Pilot6 on 2013-02-23
I am confused by model of the chip HD 4500/5100 Series.

For 4xxx you need legacy, for 5xxx you need normal driver.

---

### Post by nickmrad on 2013-02-23
ok so i'm gonna try QIII solution and check out the result :)

---

### Post by Pilot6 on 2013-02-23
I think the problem is that you need legacy.

So remove the driver

sudo apt-get purge fglrx*

Then download the driver frome here.
[https://www.dropbox.com/sh/aw6oth9799n43hh/jawiIddfZm](https://www.dropbox.com/sh/aw6oth9799n43hh/jawiIddfZm)

You need only 2 files with i386 at the end. These are latest legacy drivers. It is easier that to build them yourself.

Create a folder in your home folder and call it AMD. Put there these 2 files.

Then in terminal run commands

cd AMD
sudo dpkg -i *.deb

Then reboot.

---

### Post by Pilot6 on 2013-02-23
QIII is the right solution to remove the driver and use opesource one. Then you can install propritary. It must solve the problem.

Note: Driver I suggest can be used for kernel 3.5 as well.

---

### Post by QIII on 2013-02-23
> **Pilot6 said:**
> I am confused by model of the chip HD 4500/5100 Series.

For 4xxx you need legacy, for 5xxx you need normal driver.

Quirk in how ATI describes the Mobility line.  It's actually an overclocked 4000 series.

Also, again, the 12.4 driver is the one available in the Precise repo.  There is no need to do anything fancy.  The legacy driver is just 12.6 anyway.

---

### Post by Pilot6 on 2013-02-23
I gave link to 13.1 fglrx-legacy.
It can be downloaded from AMD site. 
Debs can be built by running

sh AMDblablabla.run --buildpkg Ubuntu/precise

But this works only with kernel up to 3.4. But I applied a patch and built for kernels up to 3.6.

Normal fglrx won't work since it is 4000 series.

---

### Post by nickmrad on 2013-02-23
ok so tried QIII solution, the gui experience is much faster and smoother now, although the visual effects are not working still. In system settings i get graphics: unkown, experience standard.
the FGLRX driver is disabled and the amd catalyst is uninstalled.
So is that how it's supposed to be? I know visual effects are only eye-candy but they prove for me that my graphics card is functioning properly.

---

### Post by Pilot6 on 2013-02-23
Try my method. Proprietary driver is much faster and supports all effects.

To see graphics card in system settings run

sudo apt-get install mesa-utils

If you are scared to download and install driver form me, I can tell how to get them using AMD site. But it is a bit longer way.
The problem is that if you install driver strait using official installer, after kernel is updated, you will need to reinstall it again. The system won't load properly. To avoid this you need to build deb packages.

---

### Post by QIII on 2013-02-23
I would suggest this, and I'm not trying to be a pain, Pilot6.  There are many things that *can *be done, and there are easy ways to do things.  ;)

```
sudo apt-get install fglrx fglrx-amdcccle
``````
sudo amdconfig --initial
```Reboot.  That will have you at ATI's 12.4 driver.

Then we can use CCC to adjust performance.

And this

> The problem is that if you install driver strait using official   installer, after kernel is updated, you will need to reinstall it again.    is backwards.

If installed through apt, when the kernel is installed the driver will be recompiled back into the kernel automatically.

---

### Post by nickmrad on 2013-02-23
> **Pilot6 said:**
> Try my method. Proprietary driver is much faster and supports all effects.

so i just download the files in the link you provided previously and type in the command?

---

### Post by Pilot6 on 2013-02-23
You download 2 files with i386 at the end and put them in folder called AMD in your home folder. Then type 2 commands.

---

### Post by Pilot6 on 2013-02-23
> **QIII said:**
> I would suggest this, and I'm not trying to be a pain, Pilot6.  There are many things that *can *be done, and there are easy ways to do things.

And this

 is backwards.

If installed through apt, when the kernel is installed the driver will be recompiled back into the kernel automatically.

```
sudo apt-get install fglrx fglrx-amdcccle
``````
sudo amdconfig --initial
```Reboot.

Then we can use CCC to adjust performance.

fglrx from official repos may not work well. After topicstarter installs 13.1, then we can do same.
If you install using dpkg, dkms will work normally as wellas using apt.

---

### Post by QIII on 2013-02-23
OK, Pilot6, I'm out.

@nickmrad:  Choose your path.  You know where to find me.

Cheers, everyone!

---

### Post by Pilot6 on 2013-02-23
> **QIII said:**
> OK, Pilot6, I'm out.

@nickmrad:  Choose your path.  You know where to find me.

Cheers, everyone!

I just fixed same problem yesterday with stock fglrx.

---

### Post by nickmrad on 2013-02-23
i tried QIII way but i got the lag again :/ so i'm downloading the files now and going to try your way (Pilot6).

---

### Post by Pilot6 on 2013-02-23
Don't forget to remove these drivers again

sudo apt-get purge fglrx*

---

### Post by nickmrad on 2013-02-23
i removed the drivers, downloaded the 2 files and ran the commands but still no effects!
There must be something missing because minimizing and maximizing windows is now smooth and lag is gone.

---

### Post by Pilot6 on 2013-02-23
What effects you are talking about?

---

### Post by nickmrad on 2013-02-23
the compiz effects (wobbly and stuff like that). does that mean there's something wrong with compiz or is it again a graphcs card issue?

---

### Post by Pilot6 on 2013-02-23
These effects do not work with default desktop environment - unity.
Or you need to tweak a lot. 
The driver works well? That's good. But regarding effects on unity, I tried to set them up too, but failed. It is possible, but no real need to dig deep. 

If you try another DE, like gnome3, kde, etc, effects may work.

---

### Post by nickmrad on 2013-02-23
i got gnome 3 installed, and they still don't work. gnome compatibility is checked in compiz so is openGL and the effects.

---

### Post by Pilot6 on 2013-02-23
Do you really need effects? Compiz is developed by Canonical now for unity interface. Not by community as before for general purpose. I also would like to see effects for fun, and I know that I can get them working. But I am too lazy for that.

Your graphics card works now as it can. New xorg is much better, but AMD does not want to support it. So there is nothing to improve with this hardware.

You can somehow setup effects, but it is not for beginners section.

---

### Post by nickmrad on 2013-02-23
thanks alot for your help :) the important thing is that i got the graphics card working properly.

---

### Post by Pilot6 on 2013-02-23
You are welocme. Sorry for my Saturday night drunk language.

---

### Post by nickmrad on 2013-02-23
lol, don't worry about it. I spent 3 days googling for a solution till i posted a thread here :)

---

### Post by czechreck on 2013-04-14
> **Pilot6 said:**
> I think the problem is that you need legacy.

So remove the driver

sudo apt-get purge fglrx*

Then download the driver frome here.
[https://www.dropbox.com/sh/aw6oth9799n43hh/jawiIddfZm](https://www.dropbox.com/sh/aw6oth9799n43hh/jawiIddfZm)

You need only 2 files with i386 at the end. These are latest legacy drivers. It is easier that to build them yourself.

Create a folder in your home folder and call it AMD. Put there these 2 files.

Then in terminal run commands

cd AMD
sudo dpkg -i *.deb

Then reboot.

I was a bit suspicious using this fix and downloading the files, but it worked.
In learning Linux, I've installed/messed up stuff at the command line, and have been pulling my hear out to try and get my graphic card drivers working.

You nailed it mate, cheers.

---

