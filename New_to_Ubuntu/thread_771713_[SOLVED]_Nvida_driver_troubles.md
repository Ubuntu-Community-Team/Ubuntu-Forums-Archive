---
title: "[SOLVED] Nvida driver troubles"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Dark Horse on 2008-04-27
I having a real problem with video resolution 640x480 with the restricted drivers enabled 600x800 without them and that's the best i have been able to get so far I have tried envyNG withe same result.I have even downloaded the driver from the website with the same result. I am beginning to think it might be an issue with the mother board Or GPU they are:
XFX MCP73PV mother board
GeForce 7150 on board GPU 
2gb 800 mhz ram
Intell duol core 2.2 ghz processor 
I just up graded to this board this week just in time for the hardy release. I am having the same problem on a second computer.
wich is a:
 gigabyte motherboard
 GeForce on board GPU
 3.5 gb ram
 AMD 2 ghz processor
I really am stumped and i need som help.
Thanks Mark  [http://ubuntuforums.org/images/smilies/eusa_think.gif](http://ubuntuforums.org/images/smilies/eusa_think.gif)
:-k

---

### Post by alienexplorers on 2008-04-27
Use Envy and select manual driver install option.  Select the middle driver option and see if that works for you.

---

### Post by kgriff on 2008-04-27
I assume you´re installing Hardy on both of these machines?
On the second computer, what is the Gigabyte motherboard, and what is the onboard grahics chipset?
You don´t happen to have a KVM switch between these two machines, do you?

---

### Post by Dark Horse on 2008-04-28
The Gigabyte mother board is a GA-51GM-S2G the on board GPU is a GeForce
6100 It is about 1.5 years old No KVM switch There not even in the same building. The Gigabyte system Is  triple boot with XP,Ubuntu Studio 7.10,Ubuntu Studio 8.04. The XFX system is a dual boot with XP, Ubuntu Studio 8.4. I tried all three options in envy and only one would boot the other two options failed at the xorg server start with a no device found error. Mark  [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by wheels. on 2008-04-28
Are you sure the driver is in use?
Check your /etc/X11/xorg.conf 
and make sure your driver isn't vesa and that it is "nvidia"

---

### Post by Dark Horse on 2008-04-28
Using the vesa driver right now I had have had all three of the nvida drivers Installed at one time or the other 640x 480 was the best res i could get with the default vesa driver I am getting 800 x 600 which is better  but really isn't very usable for what I need to do.
 I have been doing some more digging and the drivers and xorg only see my monitor as a generic CRT maybe if I can find a way to config xorg to see it as a better monitor  that might solve my problem? maybe but how to do that??
  Mark:)

---

### Post by wheels. on 2008-04-28
You said you tried downloading from their website, do you want to try that one more time? make sure you get version 169.12 
then sudo /etc/init.d/gdm stop (from memory so I dont know if I am exact on that) that should take you down to a terminal, no x environment
make sure you have build-essential installed
sudo apt-get install build-essential
then cd to the location of the nvidia driver you just downloaded
run sudo sh NVIDIA*
when it asks if you want it to download a precompiled kernel interface select no, but say yes to everything else, you want the program to configure your xorg, so it loads the driver by default.
I know you said you did this, but its always worth another shot
(as to the accuracy of my instructions to install the nvidia driver, I cannot say, it is what has always worked for me, you may want to look up some more info on that, just to be sure)

good luck!

---

### Post by Dark Horse on 2008-04-28
I seem to be missing the screens and Graphics app. I have seen mentioned in several other threads Does anybody know what I need to do to get it back? That seems to be where things are going wrong. I have had the right driver installed several times but that reduces the res and I am not going to do that until I have reason to it will be an improvement.So the question I need to answer is how do I tell ubuntu to use a different monitor file?:)

---

### Post by wheels. on 2008-04-28
I don't have a screens and graphics app either in my menus all though I do not need it nor know what it is for, anyway try 
sudo apt-get install nvidia-settings
Make sure you have to nvidia driver enable and are in your low resolution, you can use nvidia-settings to adjust resolution used and screen type.

---

### Post by alienexplorers on 2008-04-28
When running nvidia-settings remember to run it in super user mode:
> gksudo nvidia-settings
If you don't run it like this you will be unable to save your modifications to your xorg.conf file.

---

### Post by FredB on 2008-04-28
As xorg changed between gutsy and hardy, for nvidia the best thing to do is to install and use nvidia-settings to choose resolution.

---

### Post by SnakeHips on 2008-04-28
try this

make backup xorg.conf

```
cd /etc/X11
sudo cp xorg.conf xorg.test

```

from desktop menu

if resticted driver checked in /apps/system/hardware drivers then uncheck

terminal

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-settings nvidia-kernel-common xserver-xorg-video-nv jockey-common
```

```
sudo apt-get install build-essential xserver-xorg-dev
```

shutdown and restart

---

### Post by Urbanmoth on 2008-04-28
> **Dark Horse said:**
> I seem to be missing the screens and Graphics app. I have seen mentioned in several other threads Does anybody know what I need to do to get it back? That seems to be where things are going wrong. I have had the right driver installed several times but that reduces the res and I am not going to do that until I have reason to it will be an improvement.So the question I need to answer is how do I tell ubuntu to use a different monitor file?:)

To access the screens and graphics app just enable it in your main menu, under 'Other' but I do not think this will solve your problem since I have the same issue - 8.04 seems to 'forget' the xorg settings upon each boot. I have tried so many configurations to get it to work I've worn my hard drive out:sad: - I think it is a bug with some nvidia cards - intend to do more investigation tonight when I get home.....

---

### Post by Urbanmoth on 2008-04-28
OK, I've finally got a working desktop on Hardy 8.04, the only issue is that I can't get Compiz to work (more on that later)

I finally figured out that it is a dual monitor problem.

I have a Nvidia GeForce 7800GS, it has VGA and DVI outputs and I have a Samsung SyncMaster 225BW on the digital output and a Hyundai Q17 on the Analog output.
I ended up removing absolutely all traces of the nvidia driver from my system
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
```
Downloaded the latest beta driver from the nvidia site - ([http://www.nvidia.com/object/linux_display_ia32_173.08.html]("http://www.nvidia.com/object/linux_display_ia32_173.08.html")) and then installed it.
```
sudo /etc/init.d/gdm stop
```
This stopped the current xwindows session - Then Ctrl+Alt F1 and login to the terminal. Then navigate to where the driver was downloaded (in my case the Desktop and run it - so:
```

cd Desktop
sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
```
After letting the install script configure my xorg.conf file I managed to start the xserver with a display on the Q17.
```
sudo /etc/init.d/gdm start
```
From there I could install nvidia-settings and configure the other display
```
sudo apt-get install nvidia-settings
```
I had to make sure, however, that the Analog Q17 was the default display, any attempt to make the SyncMaster the default (as I had in 7.10) would result in the nvidia driver not being correctly loaded at boot.

So - I am finally back to a semblance of normality but I cannot get compiz to work:

```
compiz --replace
```

results in:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:00f5 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
```

Unless anyone has any instant ideas I think I'll live without the eye candy in return for a usable desktop. 

Anyway, hope this noob rambling is of some help to someone else....

---

### Post by Dark Horse on 2008-04-29
I had the nvida driver and the nvida settings app It is still in the menu just not active Because I shut the driver down so I could have a usable resolution on my Monitor when it is active My choices are 640x480 or 320x268? neither of which is usable. I don't believe my problem is with the driver itself. The problem is with the app that detects the monitor and the available resolutions. That is why the best res is 800x600 Xorg dosent think that the monitor can handle any more than that.I will enable the nvida driver and try the settings as sudo but I doubt it will matter.
I will report the results later.
Mark  :)

---

### Post by SnakeHips on 2008-04-29
are the restricted modules installed ?

```
ls -la /lib/linux-restricted-modules/
```

pete@desk:~$ ls -la /lib/linux-restricted-modules/
total 24
drwxr-xr-x  3 root root  4096 2008-04-24 18:11 .
drwxr-xr-x 14 root root 12288 2008-04-19 09:22 ..
drwxr-xr-x 13 root root  4096 2008-04-15 11:41 2.6.24-16-generic
-rw-r--r--  1 root root    58 2008-04-15 10:56 .nvidia_new_installed
pete@desk:~$ uname -a
Linux desk 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
pete@desk:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

apols if it's a bit noobish

---

### Post by Dark Horse on 2008-04-30
Here is the result of my restricted modules:
mark@ubuntustudio1:~$ ls -la /lib/linux-restricted-modules/
total 16
drwxr-xr-x  3 root root 4096 2008-04-30 00:47 .
drwxr-xr-x 14 root root 4096 2008-04-29 05:33 ..
drwxr-xr-x 13 root root 4096 2008-04-30 00:47 2.6.24-16-rt
-rw-r--r--  1 root root   58 2008-04-30 00:47 .nvidia_new_installed
mark@ubuntustudio1:~$ 
Simular but mine is the rt Kernal instead of the generic since it is Ubuntu Studio. I am running the nvida driver now but again only 640 x 480 running nvidia settings as root didn't change any thing as for as options. It still apears that the Auto detiction on Install is faulty at least for my monitor 
I have been chasing this rabbit around the same tree for atleast a week. I am getting dizzy and frustrated!! I don't know if the problem is the new MB Or HH Both got changed at the same time. I can go to XP and Get screen resloutions Up to 2048x1536@120 I don't usually use that high of a res but I checked and made a list of avaiable res just so I would be sure of what the Monitor is capable of Mostly I use one near the middle 1280x1024 or so.
   Mark](*,)

---

### Post by alienexplorers on 2008-04-30
Dark Horse,
I have a GeForce FX-5200 video card. According to Nvidia I should use the latest driver.  I have tried it and lost use of compiz.  I decided to unload that driver and load the one I was using in Gutsy 96.43.05..  After loading this driver I again reloaded compiz and now both compiz and my screen resolutions are working correctly.  I used sudo nvidia-settings to set the resolution and refresh rate.
I don't know why the driver Nvidia recommended caused all these problems on my system, but I am glad I now have my system running correctly.

---

### Post by SnakeHips on 2008-04-30
> **alienexplorers said:**
> Dark Horse,
I have a GeForce FX-5200 video card. According to Nvidia I should use the latest driver.  I have tried it and lost use of compiz.  I decided to unload that driver and load the one I was using in Gutsy 96.43.05..  After loading this driver I again reloaded compiz and now both compiz and my screen resolutions are working correctly.  I used sudo nvidia-settings to set the resolution and refresh rate.
I don't know why the driver Nvidia recommended caused all these problems on my system, but I am glad I now have my system running correctly.

I'm not sure the driver is to blame ,for many are working fine with 169.12 on Hardy. Where it appears to have fallen over is with the detection of *some* monitors hence resolution issue's.

Just curious ,did you sudo nvidia-settings with the restricted driver and save to xorg.conf? and did you use the recommend install via "hardware drivers" in the menu?

Glad to hear it's all woking for you anyway.

---

### Post by SnakeHips on 2008-04-30
> **Dark Horse said:**
> Here is the result of my restricted modules:
mark@ubuntustudio1:~$ ls -la /lib/linux-restricted-modules/
total 16
drwxr-xr-x  3 root root 4096 2008-04-30 00:47 .
drwxr-xr-x 14 root root 4096 2008-04-29 05:33 ..
drwxr-xr-x 13 root root 4096 2008-04-30 00:47 2.6.24-16-rt
-rw-r--r--  1 root root   58 2008-04-30 00:47 .nvidia_new_installed
mark@ubuntustudio1:~$ 
Simular but mine is the rt Kernal instead of the generic since it is Ubuntu Studio. I am running the nvida driver now but again only 640 x 480 running nvidia settings as root didn't change any thing as for as options. It still apears that the Auto detiction on Install is faulty at least for my monitor 
I have been chasing this rabbit around the same tree for atleast a week. I am getting dizzy and frustrated!! I don't know if the problem is the new MB Or HH Both got changed at the same time. I can go to XP and Get screen resloutions Up to 2048x1536@120 I don't usually use that high of a res but I checked and made a list of avaiable res just so I would be sure of what the Monitor is capable of Mostly I use one near the middle 1280x1024 or so.
   Mark](*,)

Whats the make/model of your monitor/screen ?

edit: just another thought - roll back to the xserver version used by gutsy.

---

### Post by knaveofdiamonds on 2008-04-30
After having done an upgrade this evening, I had problems with the nvidia drivers (geforce 6200). 

My issues were:

1. the right linux-resticted-drivers didn't get installed for me by default, took a while to work out I needed to manually install the *-386 version not the -generic version.

2. My xorg.conf got screwed up somewhere along the line and the resolution was set to 680x480 - I had to manually change this - running the nvidia-settings in 640x480 doesn't let you see all of the control panel!

R

---

### Post by Dark Horse on 2008-05-01
the Monitor is a Sun Microsystems 21 inch I bought it used about a year and a half ago it has never been a problem until now. I think that if  I can edit the xorg.config file I might solve the problem I don't need all of the res to work just 2 or 3 of the right ones would be enough for now.This is my xorg file asit is right now:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

the last section is missing a section for modes and various resoulitions I need to find out what should be there to make it work .
I have seen a couple of threads that seemed to say that hardy controled that from a different file but nobody seams to know where?
the other system is a 19 inch Dell P99 also bought used gutsy has had no problem with either monitor  but Hardy can't figure either one out.If it makes anyone feel better hardy did find the wifi card in the other system and set it up correctly during install and that has never happened before.
mmore later 
Mark

---

### Post by SnakeHips on 2008-05-01
I'm guessing you have already tried this ?
```
gksudo displayconfig-gtk
```

and just as a data point ,what does the following show
```
xrandr -q
```

here's mine
pete@desk:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 0mm x 0mm
   1360x768       50.0* 
   1280x768       51.0     52.0  
   1024x768       53.0  
snip...
```

xrandr cfg
``` might be worth a look ,but i have'nt used this utility myself. looks like --newmode would force some new values into the table?

more info here:
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

### Post by por100pre1 on 2008-05-01
> **Dark Horse said:**
> 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection



You lack resolution settings there. Have you tried setting up and saving the resolution using nvidia-settings as root?

```
gksu nvidia-settings
```

Here's my resolution saved in xorg.conf file *(be aware that I use a graphics card with a monitor and a TV set)*:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
**    Option         "metamodes" "CRT: 1024x768_60 +0+0, TV: 1024x768 +0+0"**
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by oneup on 2008-05-01
> **kgriff said:**
> I assume you´re installing Hardy on both of these machines?
On the second computer, what is the Gigabyte motherboard, and what is the onboard grahics chipset?
You don´t happen to have a KVM switch between these two machines, do you?

Hi kgriff you mention a KVM switch in your answer to this question,can you say what effect that has, as I run 2 machines with a KVM switch between them and I find I must sacrifice resolution with a widescreen monitor(in 7.10) to get a full screen,other than not usuing a KVM switch is there a fix for this please?

---

### Post by Dark Horse on 2008-05-02
SnakeHips That was the answer!!! gksudo displayconfig-gtk Up pops the screens and graphics app I have been looking for I changed the monitor from Generic to Sun N3 reboot and WALA I have more resoulitions than I know what do do with. Thank You Now I going to see if it works on the other system With the dell monitor. I will check back with the results in a little while.
Mark:lolflag:):P:-D

---

### Post by Dark Horse on 2008-05-02
Worked on the other Monitor!! thank you and every one else that had  suggestions to offer .  I thought it would be some thing simple I just needed to find it .now how do I mark this as solved? :lolflag:
    Mark:):)

---

### Post by Dark Horse on 2008-05-02
Looks like I spoke to soon It worked on the Gigabyte system with the dell monitor until I rebooted for something else the the system died at the point  where you should expect the logon screen. I am not sure if this is a new Prob or is related to the video Problem when I boot into Recovery mode and tell it to fix the xsever It reboots back to 800x600 I have been around that circle 3 or 4 times with variations on whether or not the nvida driver is enabled or not. I will worry about It tomorrow after I have slept on it a while.
Incase anyone is interested here is my xorg.config after my display was configured:

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:16:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Sun"
	Modelname	"Sun 21-inch N3"
	Horizsync	30.0-96.0
	Vertrefresh	48.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"800x600@56"	"800x600@72"	"640x480@85"	"800x600@75"	"640x480@75"	"800x600@85"	"640x480@72"	"800x600@60"	"640x480@60"	"832x624@75"	"1024x768@85"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1024x768@43"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1792x1344@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
EndSection

Big change from before.
Thanks again to everyone for all the help.
   Mark:)

---

### Post by DaveBG on 2008-05-02
Hi, unfortunatelly this is not working for me:

> sudo sh NVIDIA-Linux-x86-173.08-pkg1.run

as it gives me that cannot find command "NVIDIA-Linux-x86-173.08-pkg1.run" ?

Can you help me?

---

### Post by monkeymoo on 2008-05-02
> **DaveBG said:**
> Hi, unfortunatelly this is not working for me:



as it gives me that cannot find command "NVIDIA-Linux-x86-173.08-pkg1.run" ?

Can you help me?

You need to download that driver from the nvidia website [http://www.nvidia.co.uk/object/linux_uk.html](http://www.nvidia.co.uk/object/linux_uk.html) (if you haven't already), and then navigate into the folder it is in before you run that command. 
Make sure you download the right driver for your card and computer and then type the correct name of that file into the command line. 

You will want to stop the display manager first:
```
sudo /etc/init.d/gdm stop
```
And then Ctrl+Alt F1 to the command line. 

If you aren't sure about which driver to use then you might find it easier to use Envy as that will examine your system and download and install the correct driver. Full details and download is here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). If you have Hardy then it should be in the repositories anyway.

---

### Post by SnakeHips on 2008-05-02
> **Dark Horse said:**
> Looks like I spoke to soon It worked on the Gigabyte system with the dell monitor until I rebooted for something else the the system died at the point  where you should expect the logon screen. I am not sure if this is a new Prob or is related to the video Problem when I boot into Recovery mode and tell it to fix the xsever It reboots back to 800x600 I have been around that circle 3 or 4 times with variations on whether or not the nvida driver is enabled or not. I will worry about It tomorrow after I have slept on it a while.
Incase anyone is interested here is my xorg.config after my display was configured:

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:16:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Sun"
	Modelname	"Sun 21-inch N3"
	Horizsync	30.0-96.0
	Vertrefresh	48.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"800x600@56"	"800x600@72"	"640x480@85"	"800x600@75"	"640x480@75"	"800x600@85"	"640x480@72"	"800x600@60"	"640x480@60"	"832x624@75"	"1024x768@85"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1024x768@43"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x960@85"	"1280x1024@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1600x1200@75"	"1600x1200@70"	"1792x1344@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
EndSection

Big change from before.
Thanks again to everyone for all the help.
   Mark:)

This is the xorg.conf from the XFX MCP73PV mother board machine that works - right?

Please post the xorg.conf from the Gigabyte machine if it's still failing.

---

### Post by Dark Horse on 2008-05-03
Yes with the Sun monitor. I just posted it so anyone who was interested could see the differance one command made. The other works untill I have to re boot for some reason then its back to 800x600. I have any idea why yet gutsy on the other partition works perfectly so far.:)

---

### Post by Dark Horse on 2008-05-04
I Think I have it solved I completely Removed and reinstalled Hardy From a later ISO. Re setup the monitor Reinstalled the nvidia drivers. I have re booted several times and the only thing that's not quite right is the log on screen is huge how do I change the res on it with out changing every thing else? Except for that every thing seams to be working just like it should.I can work around that if I have to.I think I saw that problem in another thread I will look around and see if i can find it again.
     Mark:)

---

### Post by SnakeHips on 2008-05-05
> **Dark Horse said:**
> I Think I have it solved I completely Removed and reinstalled Hardy From a later ISO. Re setup the monitor Reinstalled the nvidia drivers. I have re booted several times and the only thing that's not quite right is the log on screen is huge how do I change the res on it with out changing every thing else? Except for that every thing seams to be working just like it should.I can work around that if I have to.I think I saw that problem in another thread I will look around and see if i can find it again.
     Mark:)

This is what my /boot/grub/menu.lst looks like ,just incase you didnt find elsewhere.........add the part in red to give you 1024x768 ,the table below is worth saving to the same file...

```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda2 ro [COLOR="Red"]vga=773[/COLOR]
initrd /kernel26.img

```


```
#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
```

---

### Post by Dark Horse on 2008-05-20
That has all my video problems solved Again Thanks To every one for their help with my video Problem. So how do I mark this thread solved? 
    Mark :)

---

