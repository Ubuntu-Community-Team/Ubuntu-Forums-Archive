---
title: "[SOLVED] What driver for ATI Radeon 9250 Video Card?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by doninsa on 2008-07-05
What's the best driver for an ATI Radeon 9250 video card.  The card is seen by ubuntu as an ATI Radeon (fglrx).  I've used Applications - Other - Screen and Graphics to install several different drivers which all seem to work okay.  But when I right click on the desktop and select change desktop background - Visual Effects tab; neither Normal or Extra can be enabled.  I'm assuming this is a driver problem - right?  Any helpful suggestions would be greatly appreciated.

---

### Post by Canis familiaris on 2008-07-05
This may help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by wpshooter on 2008-07-05
> **doninsa said:**
> What's the best driver for an ATI Radeon 9250 video card.  The card is seen by ubuntu as an ATI Radeon (fglrx).  I've used Applications - Other - Screen and Graphics to install several different drivers which all seem to work okay.  But when I right click on the desktop and select change desktop background - Visual Effects tab; neither Normal or Extra can be enabled.  I'm assuming this is a driver problem - right?  Any helpful suggestions would be greatly appreciated.

If your experience with the ATI 9250 is like mine, then you are BEST to leave the 9250 as it was configured by the installation process of the O/S.  Otherwise, you are just asking for problems !!!

Good luck.

---

### Post by Rocket2DMn on 2008-07-05
> **doninsa said:**
> What's the best driver for an ATI Radeon 9250 video card.  The card is seen by ubuntu as an ATI Radeon (fglrx).  I've used Applications - Other - Screen and Graphics to install several different drivers which all seem to work okay.  But when I right click on the desktop and select change desktop background - Visual Effects tab; neither Normal or Extra can be enabled.  I'm assuming this is a driver problem - right?  Any helpful suggestions would be greatly appreciated.

The labeling of fglrx is wrong, your card is using the open source "ati" aka "radeon" drivers.  See this thread for enabling desktop effects - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by doninsa on 2008-07-05
> **wpshooter said:**
> If your experience with the ATI 9250 is like mine, then you are BEST to leave the 9250 as it was configured by the installation process of the O/S.  Otherwise, you are just asking for problems !!!

Good luck.

What driver are you now using? Are you able to use "normal" or "extra" visual effects.  If you wouldn't mind doing a test for me, do the following.  Under System - Preferences - Appearance, select the Visual Effects tab and try selecting "normal" or "extra."  If it works for you, I'd really like to know what driver you have installed.  If it doesn't work for you, all that happens is a window pops up saying it failed.  

From my point of view, I think checking into these things is part of the fun in personal computing.  Not saying I don't end up in trouble now and then, but I always seem to recover.  Regards, Don

---

### Post by doninsa on 2008-07-05
> **Rocket2DMn said:**
> The labeling of fglrx is wrong, your card is using the open source "ati" aka "radeon" drivers.  See this thread for enabling desktop effects - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Thanks for the help Rocket Man!  I read the thread and followed the instructions.  Here's what the output looked like.  Unfortunately I'm still not able to select normal or extra effects.  Can you make any sense out of the output?  Looks to me like it failed.  Thanks Don

don@don-desktop:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
don@don-desktop:~$ compiz --replace &
Checking for Xgl: [1] 6560
don@don-desktop:~$ not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:5c61 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
don@don-desktop:~$ 
don@don-desktop:~$

---

### Post by Rocket2DMn on 2008-07-05
At any point did you try to install the restricted fglrx drivers?  If so, please remove them.  Also try running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE
Remove the package xserver-xgl if you ever had that installed.

You may also want to have a look at this thread if the above doesn't work - [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by doninsa on 2008-07-05
> **Rocket2DMn said:**
> At any point did you try to install the restricted fglrx drivers?  If so, please remove them.  Also try running
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then restart X with CTRL+ALT+BACKSPACE
Remove the package xserver-xgl if you ever had that installed.

You may also want to have a look at this thread if the above doesn't work - [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Today, I did a complete reinstall of ubuntu 8.04 including a new partition and formatting of the hard drive.  The video card was again recognized as ATI Radeon (fglrx) and the driver installed was the same ati - ATI MACH 8, MACH 32, MACH 64, AND RAGE...  However, after the reinstall I was able to select extra visual effects.  

The first reinstall was from a recently downloaded copy of Ubuntu 8.04.  However after installing I couldn't get past the boot select menu.  Everything failed to start.  My second attempt was from an pre-release CD of Ubuntu 8.04.  This time everything worked perfectly.  As expected, there was a lengthy upgrade to the current version.

I'm still concerned about using the "restricted" driver.  What are the implications or consequences of using this driver.  It seems to be working for me right now.  Thanks,  Don

---

### Post by Rocket2DMn on 2008-07-05
Although it says fgrlx, you are not using the fglrx driver unless you told it to install from System->Administration->Hardware Drivers or installed from Synaptic or from ATI's website.  Since it shouldn't show the restricted driver in the Hardware Drivers and you haven't installed it otherwise, you are currently using the "ati" aka "radeon" open source driver, despite what that menu says.

Cards older than the Radeon 9500 do not support the fgrlx drivers, so you should NOT install them.

---

### Post by starcannon on 2008-07-05
The Unofficial ATi Wiki shows that card is now in legacy status:
[http://wiki.cchtml.com/index.php/Hardware#RADEON_Legacy](http://wiki.cchtml.com/index.php/Hardware#RADEON_Legacy)
and recommends the Open Source "radeon" driver.

Excellent detailed instructions on how to install are here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way)

GL and don't skip steps.

---

### Post by doninsa on 2008-07-05
> **Rocket2DMn said:**
> Although it says fgrlx, you are not using the fglrx driver unless you told it to install from System->Administration->Hardware Drivers or installed from Synaptic or from ATI's website.  Since it shouldn't show the restricted driver in the Hardware Drivers and you haven't installed it otherwise, you are currently using the "ati" aka "radeon" open source driver, despite what that menu says.

Cards older than the Radeon 9500 do not support the fgrlx drivers, so you should NOT install them.

The video card is identified as "ATI Radeon (fglrx)," but the driver is "ati - ATI MACH 8, MACH 32, MACH 64, and RAGE..." which I believe is the generic driver.  I think having (fglrx) in the card name has been a little confusing.  The card, according to the box it came in, is actually an ATI Radeon 9250 128 meg, 64 bit.  Thanks again for taking the time to worry about my problem.  Hope the fires out there in California don't get you.    
Best Regards,
Don in San Antonio.

---

### Post by doninsa on 2008-07-05
> **starcannon said:**
> The Unofficial ATi Wiki shows that card is now in legacy status:
[http://wiki.cchtml.com/index.php/Hardware#RADEON_Legacy](http://wiki.cchtml.com/index.php/Hardware#RADEON_Legacy)
and recommends the Open Source "radeon" driver.

Excellent detailed instructions on how to install are here:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way)

GL and don't skip steps.

I checked out the site and the closest I could come to a 9250 was the following. 
RV280       Radeon 9200PRO/9200/9200SE, M9+
After a complete reinstall today, the generic driver "ati - ATI MACH 8, MACH 32, MACH 64, and RAGE..." seems to be working okay.  I now have the "Visual Effects set to "extra" which is what I wanted.  Thanks for the information on ATI drivers.  Don

---

