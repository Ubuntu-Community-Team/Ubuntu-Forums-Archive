---
title: "dual monitor setup"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by srm001 on 2011-12-07
Hello,

I am returning to Linux after a few year hiatus with windows.  I always prefered the KDE desktop and decided to give Kubuntu 11.10 a shot.  I am trying this out on an old dell dimension 2400 2.5Ghz, 1GB ram system before putting it on my modern desktop pc.  During the installation process I installed 3rd party packages and allowed downloading of updates.  Other than that I am working with a "clean" install.

I am having a problem setting up dual monitors (HP w1907 & Samsung P2570HD) with an older Nvidia card (GeForce6200).  My HP monitor is VGA and the Samsung is DVI.  During the installation process both monitors were active and mirroring each other, I assumed once the install was complete I could set them to extended desktop or whatever.  Once the install as complete however, my Samsung monitor became disabled.  

I have searched a few different posts/websites on how to fix this but none seem very clear to me, nor does there seem to be a universal solution for dual monitors and Kubuntu 11.10.  I have some CLI experience but, by no means consider myself a Linux guru.  I am looking for clearification or a newbie guide for this if possible.  I am trying not to randomly download packages searching for a solution to this as I am dealing with a smaller hard drive right now (20GB) and would prefer to solve this issue without adding unnesessary packages.  

If there are any links that I have missed or posts that I have over looked, please feel free to bring them to my attention.  Any tips, advice, and/or suggestions are greatly appreciated.

Thanks for reading.

---

### Post by srm001 on 2011-12-07
For a little bit of clearification for how far I've dug into this.  

I have read a few posts about editing xrandr but when I execute the xrandr -q command in the terminal I only receive the following:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0  
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   1024x768       58.0     59.0     60.0  
   960x600        61.0  
   960x540        62.0  
   896x672        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0     73.0     74.0  
   800x512        75.0  
   720x450        76.0  
   680x384        77.0     78.0  
   640x512        79.0     80.0  
   640x480        81.0     82.0     83.0     84.0  
   576x432        85.0     86.0     87.0     88.0  
   512x384        89.0     90.0     91.0  
   416x312        92.0  
   400x300        93.0     94.0     95.0     96.0  
   320x240        97.0     98.0     99.0
```

As you can see only the resolutions for my HP monitor show up.  My Samsung DVI monitor is no where to be seen.

When I look into my /etc/X11/xorg.conf file I only see the following:


```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

No options to edit there either :confused:

When I look under System-Settings-NVIDIA X Server Settings I see my Samsung monitor listed under GPU 0 (Geforce 6200), but have no options when I select it other than Aquire EDID.  If I select X Server Display Configuration I receive the following message: 

Unable to load X Server Display Configuration page:
Failed to query NoScanout for screen 0.

And if I try to use System Settings-Display and Monitor-Multiple Monitor, I receive the following message:

This module is only for configuring systems with a single desktop spread across multiple monitors.  You do not appear to have this configuration.

Just a little more info as to how far I have gotten on my own.

---

### Post by seawolf167 on 2011-12-07
A couple things to try:

[LIST=1]
[*]If you go to your display settings under system settings, can you simply enable the additional monitor then select how you want to display on it?
[*]You can get the driver suite for your device which will most likely help, the proprietary driver suite from the manufacturer can be found [here]("http://www.nvidia.com/object/linux-display-ia32-290.10-driver.html"), or you can also install them through the additional drivers section
[*]Finally, if 1, 2 don't work, to manually change your display settings using xrandr you can start looking at the wiki [here ]("http://wiki.debian.org/XStrikeForce/HowToRandR12")for more information
[/LIST]

---

### Post by srm001 on 2011-12-07
Thank you Seawolf.

I went through additional drivers and installed 

NVIDIA accelerated graphics driver (version current)(recommended).  
Instead of the default
NVIDIA accelerated graphics driver (version 173)

Everything is working fine now.  Thank you again for a quick and painless fix to this issue.

---

### Post by seawolf167 on 2011-12-07
> **srm001 said:**
> Thank you Seawolf.

I went through additional drivers and installed 

NVIDIA accelerated graphics driver (version current)(recommended).  
Instead of the default
NVIDIA accelerated graphics driver (version 173)

Everything is working fine now.  Thank you again for a quick and painless fix to this issue.

Awesome :) Glad all is working now

---

