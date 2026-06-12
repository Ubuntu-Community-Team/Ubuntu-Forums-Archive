---
title: "HOWTO: 3D Acceleration in ATI Mobility Radeon M6 LY (and possibly others)"
date: 2006-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by javaJake on 2006-08-29
[SIZE="3"]**This HOWTO does not follow the latest rules and regulations for all HOWTOs. This will be fixed in the near future, but caution is recommended.**[/SIZE]

[SIZE="3"]**Read First!!!**[/SIZE]
This HOWTO is NOT the standard "how to get 3D Acceleration working" HOWTO. It is meant for video cards that have the same symptoms as the ATI Mobility M6 LY card - random blanking of screen, or freezing of screen display (usually with strange screen distortion), most often when opening a new window or list, or some other display thing.

Please refer to a standard 3D HOWTO if your card doesn't crash after Part I after 30 minutes of good multitasking!


**_[SIZE="3"]Cards that Work in this HOWTO[/SIZE]_**
**A card may or may not work with this HOWTO even if it isn't in the list. The list is just meant to show which cards you NEED to follow this HOWTO on.**

[LIST]
[*]Radeon M6 LY
[/LIST]

If you find any other cards that work with this tutorial, let me know.
When I say "work with this tutorial", I mean...

**a)** You had issues before trying other tutorials, and this one worked.
**b)** Your computer was crashing after Part I, and you had to do Part II as well.
**c)** All of the above. :D

**_[SIZE="3"]Important Stuff To Read[/SIZE]**_

[list]
[*]This HOWTO works with Dapper, Edgy, and Feisty, but Edgy and Feisty are a lot easier to configure. **Feisty is recommended.**
[*]Please understand that this **may, under rare circumstances, make your system unstable**! My system is just fine, but you have been warned!
[*]If you really really need help, and just can't get this to work, contact one of my IM accounts listed in my profile. I am usually on weekends, Eastern Time, usually, though I cannot guarantee that.
[*] We will be upgrading packages using versions from Edgy, if you use Dapper. This may make your system unstable, but my tests ran fine.
[*] You don't have to have the Radeon M6 LY... I don't think. That's the thing. I don't really know for sure. This HOWTO is completely based on my limited experience, so I am open to suggestions about different situations that may come up! To tell if you should follow this HOWTO, go through Part I, and your computer becomes extremely unstable, this is fo' you!
[*] I assume you know how to use the terminal! If you don't, please visit this tutorial: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[*] I assume you haven't made any radical changes to xorg.conf, and that you don't have more then one card. If this isn't true, then I assume that you are somewhat experienced in editing xorg.conf.
[*][COLOR="Silver"]This tutorial **probably won't solve ALL freezing issues**. It only reduces them, and enables 3D Acceleration! My computer usually lasts around 2 hours of good use before it crashes, whereas before it wouldn't last 30 minutes.[/COLOR] - Apparently, *my* hardware is dying, so this note does not apply to everyone.
[*]**If you've installed fglrx, you've just partly trashed X (the graphics system).** In other words, if you've installed fglrx, and are getting issues when running glxinfo, or other programs that use the 3D engine, or even just trying to log in, then you should reinstall Ubuntu! Some users reported being able to get things to work just by uninstalling fglrx, and changing the driver back to radeon, but fglrx will most likely mess with Beryl, and possibly everything else 3D. You have been warned!
[/list]

**_[SIZE="3"]Part 1 - Getting The Card to Crash[/SIZE]_**
Er... yea... well, not really. What I mean is that we are going to see if the drivers to output specific errors, and if they don't enable 3D accelleration because of those errors. That will tell you that this HOWTO is for you.

**_[SIZE="2"]All Users - Dapper and Edgy[/SIZE]_**

First, let's check to be sure that we have the 3D Acceleration drivers installed:

```

sudo apt-get install libgl1-mesa-dri xlibmesa-dri

```

Next, open the xorg.conf file. This file controls how the graphical display acts.

```

sudo gedit /etc/X11/xorg.conf

```

Find the part of the configuration of the log that says Section "Device". Notice that the entire configuration is seperated into sections. Each Section configures a different thing. We are looking for the Section that configures your video card.

Make a copy of the entire Section, then add "#" to the beginning of the lines of the first copy, like the example below. _Be sure to change the "Driver 'ati'" part to "Driver 'radeon'"._ See example below for help.

*Before*
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```

*After*
```

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection

```

OK, now add the following Options to the second copy of the Section "Device":

```

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"

```
*(Thanks 2hansen for this superb xorg.conf configuration with excellent comments, which turns out to be better then mine in every way!!!)*

Here's what it looks like in my example Section:

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

```

Now look for the Section "Module", and insert these modules *if they don't exist already*:

```

	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"

```

Here's what the example looks like afterwards. *Please note that this is from my configuration, and so you might not need everything listed here.*

```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

```

Before rebooting, **print these instructions out** just in case something crashes and you can't log in to the graphical display.

Now reboot your computer.

**If you cannot login at all** (possibly X crashes) then push Ctrl+Alt+F1, and login there for the rest of this HOWTO.

**If you can log in**, goto Applications -> Accessories -> Terminal, and type this in:

```

glxinfo | grep direct

```

If it says "direct:Yes", then your all set. If your card is **not** the Radeon M6 LY, and you are getting direct rendering, please undo everything you've done in Section "Device" (you can leave the Section "Module" alone) and use a different HOWTO. This HOWTO disables certain features, and lowers the quality of colors to get direct rendering to work. (Note that you almost can't see the difference in colors.)

[INDENT]**If you don't have direct rendering** (scroll down past this indented part if you have direct rendiring), run this command:
```

cat /var/log/Xorg.0.log | grep EE

```

If the output has this somewheres...:
```

(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth.

```

...then continue. Otherwise, post your /var/log/Xorg.0.log file, your /etc/X11/xorg.conf file, and anything else you can provide.

If you found the above "buffer" error, then find any "subsections" in /etc/X11/xorg.conf that tells Xorg that you can use Depth 24 or higher, like this:
```

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```

...and then comment them out, like so: (you can also delete them completely, but that is not recommended)
```

#       SubSection "Display"
#               Depth           24
#               Modes           "1024x768" "800x600" "640x480"
#       EndSubSection

```

This effectly forces Xorg to use depths below 24. This will reduce screen quality (not too much, though).

Reboot your computer again. If you still get a "no" when you punch in the command "glxinfo | grep direct", then post your /etc/X11/Xorg.0.log file, your /etc/X11/xorg.conf file, and anything else you can provide.
[/INDENT]

**_[SIZE="3"]Part 2 - Making the Computer Stop Crashing[/SIZE]**_

**_[SIZE="2"]Dapper Users[/SIZE]_**
We need to upgrade the drivers. Doing so will break a few other things, which we will also upgrade. Run the following commands:

```

sudo apt-get install nano
sudo nano /etc/apt/sources.list

```

Now replace any mention of "dapper" with "edgy", except for the cdrom entry, and remove any single "#".

Type in the following commands:
```

sudo apt-get update
sudo apt-get install libgl1-mesa-dri
sudo apt-get install locales
sudo apt-get install gtk2-engines-ubuntulooks

```

(The locales and ubuntulooks need to be updated, since they break after installing the new X version.)

_NOTE:_ If it says that it cannot find packages, or they are broken, etc, please check to be sure that there are no single "#" in your /etc/apt/sources.list and that "dapper" is replaced by "edgy" everywhere! (IOW, make sure that all the repositories are uncommented.) If you still have issues, post the errors, and your /etc/apt/sources.list file.

That should do it. Replace "edgy" with "dapper" in the /etc/apt/sources.list file again, and restart your computer.

**_[SIZE="2"]Edgy Users[/SIZE]_**
You are done. That's right. Done. Everything should work at this point.

**_[SIZE="3"]Some Final Notes[/SIZE]_**
[list][*]If you had the "buffer" error before in Part I, and had commented out the "Depth 24" lines in your xorg.conf file, try uncommenting this to see if you can get better quality now that you've upgraded drivers.[*]If you have issues, please post the output of /var/log/Xorg.0.log and the file /etc/X11/xorg.conf.[*]Also, be sure to let me know if your card works, and also qualifies for the "Cards that Work in this HOWTO" section at the top.[/list]




**_(OPTIONAL) MergedFB and Xinerama_**
Let's say you are working on a document, or chatting with a friend. Suddenly you need to be able to view two windows at the same time. Wouldn't it be nice if you could have a screen twice as big so that you could have the two windows side by side?

OK, you get the point. MergedFB and Xinerama both provide you with two screens. The main difference between the two is the fact that MergedFB provides 3D acelleration, while Xinerama does not. MergedFB can only be used on the M6 LY card if you run at 800x600 (if your card only has 8MB, like mine), but for some it might be what you want.

Follow this HOWTO for Xinerama and/or MergedFB. Just be sure not to use any others besides Xinerama or MergedFB, since the others are meant for NVidia cards.
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

If you configured MergedFB, but it won't work, or 3D won't work in it, please be sure you commented out any resolutions higher then 800x600 for 8 MB cards. To tell if you need to do this, look for any warnings about "At least xxxxx kB of video memory needed" in your /var/log/Xorg.0.log file.

You can post at this HOWTO for support for either of these methods if you want.

**_(OPTIONAL) Beryl**_
You might've heard about Beryl. You might've even seen screenshots or videos. If you didn't know about Beryl until now, then you are missing out big time! Beryl is a new window manager that provides different cool stuff for your desktop. The best way to know what it is to go here: [http://www.beryl-project.org/features.php](http://www.beryl-project.org/features.php)

Alright, so you are probably ready to go. First read the following notes which are really important:
[list][*]Never ever ever EVER install fglrx. I'm speaking from experience. :)
[*]You need to follow instructions for AiGLX, and not XGL![/list]

Now you are ready. Follow this HOWTO:
**The HOWTO is missing! Help me find a decent HOWTO to link to!**
If you have issues, you should really post on Beryl's forums or mailing lists.




**_[SIZE="3"]Troubleshooting[/SIZE]_**
[list][*]
**Radeon Mobility IGP340 chip Users**
User kingkookie reported that his card didn't work fully until he changed "AGPSize '32'" to "AGPSize '8'" in xorg.conf. If you have this card and are having issues, try this.
[*]
**After Applying Latest Update To fglrx Kernel, 3D Acceleration Is Lost**
User spaceghoti reported that "after applying the latest update to wine and the fglrx kernel, all of a sudden I've lost my 3D acceleration." If this sounds like your situation, [read this for the complete details on the problem]("http://www.ubuntuforums.org/showpost.php?p=1996088&postcount=154") and *make sure that this is really truly what is going on for you*. Then [follow the solution he listed]("http://www.ubuntuforums.org/showpost.php?p=1998140&postcount=155").[/list]

**_[SIZE="3"]Special Application Notes[/SIZE]_**
If you find any more applications to add to the list, _AND_ your card is/qualifies to be in the "Cards that Work in this HOWTO" list at the top of this HOWTO, then please let me know. Include your card name, the application, and the notes.

[LIST]
[*]**Scorched3D**
If the terrain and/or other items appear white with no texture, make sure AGPSize is at or above 32. If AGPSize is correctly set, try bringing the quality down one option at a time. Also, you must install this program while you still have "edgy" punched into the /etc/apt/sources.list file. The reason is that Scorched3D from Dapper has some bugs that are fixed in the new one. So far it has been completely stable for me, whereas Dapper's Scorched3D would crash at times.
[*]**BZFlag**
I noticed that if I don't let the Server List or the Message of the Day (in the lower right corner) load before I start moving, it sometimes crashes.
[/LIST]

**_[SIZE="3"]Revisions[/SIZE]_**
May 12, 2007 - Added Feisty support, and made some minor modifications everywhere.
March 14, 2007 - _(Thanks to ppietryga)_ Added xlibmesa-dri to list of things to install to be sure 3D drivers are installed.
January 13, 2007 - _(Thanks to spaceghoti)_ Added new item called "After Applying Latest Update To fglrx Kernel, 3D Acceleration Is Lost" to Troubleshooting section.
December 30, 2006 - _(Thanks to [email]ryanjdill@gmail.com[/email])_ Changed the fglrx warning to be less "must reinstall" and more "good idea to reinstall", since some users reported 3D still worked even when system had fglrx on it, but was removed.
December 26, 2006 - _(Thanks to ac251404)_ Added a note about fglrx under "Important Stuff to Read".
December 9, 2006 - Added Beryl, MergedFB, and Xinerama support.
December 6, 2006 - _(Thanks to 2hansen)_ New xorg.conf, which works a LOT better.
December 6, 2006 - Edgy's included drivers are best - updated HOWTO accordingly.
November 26, 2006 - Changed "driver-ati" to "video-ati" for some apt-get commands.
November 5, 2006 - Added BZFlag to list of "Special Application Notes".
November 5, 2006 - Added Edgy support, and made HOWTO easier to read and more organized.
October 29, 2006 - Added nnote that this most likely won't work in Edgy.
October 22, 2006 - _(Thanks to Efrain Valles)_ Added the "change 'Driver "ati"' to 'Driver "radeon"'" to Part I.
October 22, 2006 - _(Thanks to kingkookie)_ Added first item in Troubleshooting section.
October 19, 2006 - Did some organizing to make this HOWTO a bit easier to read.
September 15, 2006 - _(Thanks to altern)_ Fixed the typo where I said "AGPSize 32" in one example, and "AGPSize 16" in another.
September 10, 2006 - _(Thanks to Beanalby)_ Added the "static buffer" error fixes at the end of Part I and Part II.
September 3, 2006 - _(Thanks to Cinquero)_ Added a note in the "Important Stuff" section saying that this tutorial won't solve all freezing issues.
September 1, 2006 - _(Thanks to Eladan)_ Added a paragraph and note after the "apt-get install libgl1-mesa-dri", etc., commands.
September 1, 2006 - Added the "Special Application Notes" section.
September 1, 2006 - Added last paragraph and a,b,c list to bottom of "Cards that Work" to clarify what I meant by "works with this tutorial"
September 1, 2006 - Changed AGPSize from 16 to 32 - more stable this way.
August 30, 2006 - _(Thanks to termite)_ Added "Radeon 7000" to the list of compatible cards. *This change was undone - it didn't actually fully qualify for the list.*

---

### Post by termite on 2006-08-30
confirmed works on Mobility Radeon 7000 IGP

---

### Post by javaJake on 2006-08-30
> **termite said:**
> confirmed works on Mobility Radeon 7000 IGP

Thanks a lot for your feedback!

Did the card freeze after Part 1, or did it just work? If so, try playing around with the "More stable" options to see if your card can handle the unstable but neat/faster features.

---

### Post by termite on 2006-08-31
seems to just work.

---

### Post by Eladan on 2006-09-01
HP pavilion ze5185 (ATI Mobility Radeon M6 LY 32Mb) - works
but not all was fine.
I had several errors while installing packages from edgy
It is looks like there are broken dependences in repository (gcc-4.1* and libgcc*) or missing packages, so i used 
--fix-missing.
after returning to dapper I had several problems with installing new packages.

[B]Now 3D acceleration and hibernate works!!! 
Thank you very much!!![/B]

**P.S.** As I understand 
```
sudo apt-get install libgl1-mesa-dri
```

installs updated driver

but what is the purpose of these commands?

```
sudo apt-get install locales
sudo apt-get install gtk2-engines-ubuntulooks
```

---

### Post by javaJake on 2006-09-01
> **Eladan said:**
> HP pavilion ze5185 (ATI Mobility Radeon M6 LY 32Mb) - works
but not all was fine.
I had several errors while installing packages from edgy
It is looks like there are broken dependences in repository (gcc-4.1* and libgcc*) or missing packages, so i used 
--fix-missing.
after returning to dapper I had several problems with installing new packages.

It may be too late to ask you this, but did you uncomment (remove single "#") all the repositories in the etc/apt/sources.list file? It _should_ work (worked for me). gcc must also be upgraded, so you probably just didn't have /etc/apt/sources.list.

Can you post your /etc/apt/sources.list file?

> **Eladan said:**
> 
what is the purpose of these commands?

```
sudo apt-get install locales
sudo apt-get install gtk2-engines-ubuntulooks
```

When you upgrade your drivers, it must upgrade X as well. This breaks the theme, and locales, so you upgrade them as well to keep them compatible.


I'm happy that you got your 3D to work! It makes me feel all warm and fuzzy inside to know it. Seriously. It's great!!! :D

I'll update my HOWTO according to what you've posted here. See the "Revisions" section to see what changes I made.

---

### Post by Eladan on 2006-09-02
yes, you are right I commented out backports and forgot about it.

trying to fix it now. (I'm unable to build anything)

---

### Post by Cinquero on 2006-09-03
I didn't try Ubuntu, but basically the same xorg.conf. You also need to be aware that no graphics support is activated before X11 (ie. console fb -- maybe vesa fb works).

Unfortunately, the system still crashed from time to time -- a lot less frequently, but also without GLX enabled.

I don't really care any more, but any of you should post here whether they had any crashes at all since following this guide. As far as my experience with ATI cards is: don't buy them. Good low-end solutions seem to be Intel GMA and, of course, nVidia chips (although the nForce boards should not be used with nVidia graphics chips under Linux).

---

### Post by javaJake on 2006-09-03
I have found that activating console framebuffer before X11 starts hasn't caused any issues.

I do still get crashes. It's going to happen. (I forgot to include this - thanks for reminding me.) It's just a matter of making the crashes fewer to be able to live with 'em.

> **Cinquero said:**
> I didn't try Ubuntu, but basically the same xorg.conf. You also need to be aware that no graphics support is activated before X11 (ie. console fb -- maybe vesa fb works).

Unfortunately, the system still crashed from time to time -- a lot less frequently, but also without GLX enabled.

I don't really care any more, but any of you should post here whether they had any crashes at all since following this guide. As far as my experience with ATI cards is: don't buy them. Good low-end solutions seem to be Intel GMA and, of course, nVidia chips (although the nForce boards should not be used with nVidia graphics chips under Linux).

---

### Post by PSyMastR on 2006-09-04
Ive got a "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]", would that work, its still a 9000 mobility, but different model...?

---

### Post by javaJake on 2006-09-05
> **PSyMastR said:**
> Ive got a "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]", would that work, its still a 9000 mobility, but different model...?

Go through Part I of the HOWTO. If your computer starts crashing randomly (how to tell is at the end of Part I) then you should continue using this HOWTO.

---

### Post by Beanalby on 2006-09-10
Followed the steps, no 3d for me. :(  This is a Dell Inspiron 4000 with a Radeon Mobility M6 LY.

the driver is installed:

```
ninji@littlebean:~$ sudo apt-get install libgl1-mesa-dri
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa-dri is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
ninji@littlebean:~$

```

I made the changes to xorg.conf, but no direct rendering.

```
ninji@littlebean:~$ glxinfo | grep rendering
direct rendering: No
ninji@littlebean:~$

```

Xorg.0.log is available at:
[http://webhome.beanalby.net/Xorg.0.log]("http://webhome.beanalby.net/Xorg.0.log")

ati module loads and the changes to xorg.conf are definitely there.  Don't know what else to check.

---

### Post by javaJake on 2006-09-10
> **PSyMastR said:**
> Ive got a "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]", would that work, its still a 9000 mobility, but different model...?

If you get through Part I (I can give you "reverse" instructions if you want) and your computer is crashing, then this HOWTO is for you. Otherwise, you should use something different.

Let me explain this a different way...

Certain cards require certain tweaking to get 3D to work. These tweaks decrease or disable certain features. You don't neccessarily want to decrease preformance unless you have to.

To tell if you have to decrease preformance, complete Part I. If you get 3D accelleration, congrats. You can quit this tutorial. If you get extremely unstable 3D accelleration, complete the rest of the tutorial.

---

### Post by javaJake on 2006-09-10
> **Beanalby said:**
> Followed the steps, no 3d for me. :(  This is a Dell Inspiron 4000 with a Radeon Mobility M6 LY.

Xorg.0.log is available at:
[http://webhome.beanalby.net/Xorg.0.log]("http://webhome.beanalby.net/Xorg.0.log")

ati module loads and the changes to xorg.conf are definitely there.  Don't know what else to check.

AHA! Here's the trouble!

```

(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.

```

This tells me that your resolution or depth is too high. The video card just doesn't have enough memory to handle it. I ran into this exact same situation. It's an easy fix. It's a fix I forgot to include in the HOWTO.

First, though, have you followed both Part I and Part II yet? If you have followed Part II as well, then you didn't get the latest drivers. (If you've only followed Part I, then skip this paragraph.) Please follow the steps that work with /etc/apt/sources.list, and follow the instructions from there.

Here's what to do (if you've only followed Part I)...

Find any "subsections" that tells Xorg that you can use Depth 24 or higher, like this:
```

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```

...and then comment them out, like so:
```

#       SubSection "Display"
#               Depth           24
#               Modes           "1024x768" "800x600" "640x480"
#       EndSubSection

```

This effectly forces Xorg to use depths below 24. This will reduce screen quality (not too much, though).


If you are confused, let me know. I am known to make things more complicated then they should be. :)

**EDIT:** I will add this to the HOWTO. Thanks for your help! (Yes, you help by posting your issues. :) )

---

### Post by Beanalby on 2006-09-11
> This tells me that your resolution or depth is too high. The video card just doesn't have enough memory to handle it.

Ah, that makes sense!  1400x1050 would be a bit rough on 16Mb. :-\" 

I commented out the 24bit lines as reccomended, and I also had to set
the DefaultDepth off of 24 too.

```
        DefaultDepth    16
```

That did it!  glxinfo shows direct, and glxgears is smooth as budda.  Thanks!

---

### Post by javaJake on 2006-09-12
> **Beanalby said:**
> Ah, that makes sense!  1400x1050 would be a bit rough on 16Mb. :-\"  Uh... Hold on... you could keep the 24 bit depth if you reduce your resolution. Or do you not want to do this? :D

BTW, lucky you. Apparently there are two different M6 cards - 8 MB or 16 MB. I have the 8 MB one. :frown:

---

### Post by Beanalby on 2006-09-12
> Uh... Hold on... you could keep the 24 bit depth if you reduce your resolution. Or do you not want to do this? 

I can't tell the difference between 16bit and 24bit, and you'll have to pry my 1400x1050 from my cold, dead fingers!  :)   I very much like the extra real estate.

Thanks for the help!

---

### Post by javaJake on 2006-09-13
> **Beanalby said:**
> I can't tell the difference between 16bit and 24bit, and you'll have to pry my 1400x1050 from my cold, dead fingers!  :)   I very much like the extra real estate.

Thanks for the help!

ROFL. OK, that's fine then. I could see a minor difference in some of my games, but, hey, if you are fine with it, I'm fine with it.

Enjoy. :)

---

### Post by altern on 2006-09-15
hi

i am on a IBM thinkpad X24 which has a radeon M6 LY. I am running ubuntu dapper just updated all packages yesterday, I havent been able to get hardware acceleration at no point with ubuntu. However with a live cd from another linux distro I do get hardware acceleration.

I followed the tutorial up to commenting this out on the xorg.conf 
#       SubSection "Display"
#               Depth           24
#               Modes           "1024x768" "800x600" "640x480"
#       EndSubSection

as 'cat /var/log/Xorg.0.log | grep EE' did return me
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth.

However i dont get direct rendering.

I cannot find the xorg.0.log but my xorg.conf file is like this 


#############################

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load 	"Glcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


#Section "Device"
#        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#        Driver          "radeon"
#        BusID           "PCI:1:0:0"
#EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
	
	Option		"BusType" "PCI"
	Option		"AGPMode" "4"
	Option		"AGPSize" "32" # default: 8
	Option		"AGPFastWrite" "false" # More stable this way.
	Option		"SWcursor" "true" # More stable this way.
	Option		"EnablePageFlip" "true" # Faster.
	Option		"EnableDepthMoves" "false" # More stable this way.
	Option		"RenderAccel" "false" # More stable this way
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
	Option		"DDCMode"
	Option		"SubPixelOrder" "NONE"
	Option		"ColorTiling" "false" # More stable this way.
	Option		"DynamicClocks" "true"
	Option		"bioshotkeys"   "True"
	Option		"XAANoOffscreenPixmaps" "true" # More stable this way.
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	#SubSection "Display"
	#	Depth		24
	#	Modes		"1024x768"
	#EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

############################################################


and this is the glxinfo

xx@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None



any help would be apreciated.

thanks

---

### Post by altern on 2006-09-15
ok, now i changed 
DefaultDepth 24
to
DefaultDepth 16 
and it does work

any chances to get it to get 24 by some means?

I also noticed that in the tutorial it the first steps of xorg.conf configuration says
Option "AGPSize" "32"
and later it says 
Option "AGPSize" "16"

---

### Post by javaJake on 2006-09-15
> **altern said:**
> ok, now i changed 
DefaultDepth 24
to
DefaultDepth 16 
and it does work

any chances to get it to get 24 by some means?


The issue here is that your video card can't hadle the big resolution + big depth. You either need to sacrifice your resolution, or color depth. Since most people are attached to their 1024x768 resolution, I assumed they'd rather sacrifice a few colors they rarely notice anyway.

I forgot to include that you should change the DefaultDepth... thanks for pointing that out!

> **altern said:**
> 
I also noticed that in the tutorial it the first steps of xorg.conf configuration says
Option "AGPSize" "32"
and later it says 
Option "AGPSize" "16"

This is a mistype. If you reduce AGPSize to 16, then some games will not show certain graphics (NeverBall's title and sometimes menu is replaced by solid rectangles filled with gradients, and Scorched3D's landscape comes up as white), so I later increased it to 32, but forgot to check the rest of the HOWTO for any other AGPSize stuff. Thanks for pointing *that* out as well. :)

---

### Post by PSyMastR on 2006-09-15
My AGP card has 128mb of memory, does that AGP size talking about this or no is that something different.

---

### Post by javaJake on 2006-09-16
> **PSyMastR said:**
> My AGP card has 128mb of memory, does that AGP size talking about this or no is that something different.

It is something different. I don't know exactly what it is - I know it has to do with the transition between the video memory and the screen. Generally people say not to set this, but it makes the M6 LY card more stable. I'd leave the AGPSize out for your card.

---

### Post by Matyy on 2006-09-17
hi,

I can't get that direct rendering to work. There is one error in the Xorg.0.log:
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

My Xorg.conf:
[http://www.ubuntuusers.de/paste/3632/?format=txt](http://www.ubuntuusers.de/paste/3632/?format=txt)

and the full Xorg.0.log:
[http://www.ubuntuusers.de/paste/3633/?format=txt](http://www.ubuntuusers.de/paste/3633/?format=txt)

fglrx is not installed
I tried it with those radeon drivers, too, same problem.

Any ideas?

---

### Post by Rob2687 on 2006-09-17
^Remove the GLCore extension.


Why don't you use the "radeon" driver instead of the "ati" driver?

The bustype PCI thing disables AGP mode so all the other agp options are kind of pointless....

---

### Post by PSyMastR on 2006-09-17
Um, this isn't working at all.  Im testing with Scorched3d and Warcraft 3 TFT 1.20e under cedega.  I tried part 1, it didn't crash.  It didn't become unstable, it said I had hardware rendering, but I didn't.  So meh.

---

### Post by Matyy on 2006-09-18
I just followed this HOWTO - before I tried different things, I tried the 'radeon' driver. Same thing.

---

### Post by canardo on 2006-09-18
works a dream on the Compaq N410c which has the 16mb M6 Thanks a lot!

---

### Post by javaJake on 2006-09-18
> **PSyMastR said:**
> Um, this isn't working at all.  Im testing with Scorched3d and Warcraft 3 TFT 1.20e under cedega.  I tried part 1, it didn't crash.  It didn't become unstable, it said I had hardware rendering, but I didn't.  So meh.

I cannot guarantee results beyond the cards that are listed in "Cards That Work In this HOWTO" at the top of the HOWTO.

---

### Post by javaJake on 2006-09-18
> **Matyy said:**
> hi,

I can't get that direct rendering to work. There is one error in the Xorg.0.log:
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

My Xorg.conf:
[http://www.ubuntuusers.de/paste/3632/?format=txt](http://www.ubuntuusers.de/paste/3632/?format=txt)

and the full Xorg.0.log:
[http://www.ubuntuusers.de/paste/3633/?format=txt](http://www.ubuntuusers.de/paste/3633/?format=txt)

fglrx is not installed
I tried it with those radeon drivers, too, same problem.

Any ideas?

Did you really follow Part I all the way through? Did you run this command?

```

sudo apt-get install libgl1-mesa-dri

```

---

### Post by javaJake on 2006-09-18
> **Rob2687 said:**
> ^Remove the GLCore extension.


Why don't you use the "radeon" driver instead of the "ati" driver?

The bustype PCI thing disables AGP mode so all the other agp options are kind of pointless....

Two excellent points... I'll try them out myself.

[COLOR="Silver"]Everyone who has followed this HOWTO and has hardware acceleration: please try changing the option "Driver" under the section "Device" from "ati" to "radeon" and report results.[/COLOR]

**Edit:** LOL... Rob2687, you are mistaken. The HOWTO already asks people to use the "radeon" driver. The other point is also invalid. AGPSize clearly affects my card, since when I reduce AGPSize to 16 Scorched3D loses its terrain textures and NeverBall's title and sometimes menu items become solid shapes with gradients.

---

### Post by javaJake on 2006-09-18
> **Matyy said:**
> I just followed this HOWTO - before I tried different things, I tried the 'radeon' driver. Same thing.

You can try removing "GLCore" from the xorg.conf, but I think this disables OpenGL....

---

### Post by Matyy on 2006-09-19
I have exactly the same problem with a laptop that has an RV350 chip. Both laptops had breezy installed and were than upgraded. I will try more tomorrow...

---

### Post by n00b@linux on 2006-09-20
It seems to work on my ATi Radeon Mobility M7 LW (AGP) (ChipID = 0x4c57).
Thanks for the HOWTO :).

---

### Post by javaJake on 2006-09-20
> **Matyy said:**
> I have exactly the same problem with a laptop that has an RV350 chip. Both laptops had breezy installed and were than upgraded. I will try more tomorrow...

Hmmmm... I don't know what to say. GLCore is an Xorg module that should come with Ubuntu, I *think*... correct me if I'm wrong.

This could mean only one thing, in my opinion - corrupt Xorg installation. Please contact others before assuming this is it. I have very little knowledge about GLCore, unfortunately. (Education is welcome. :D )

---

### Post by javaJake on 2006-09-20
> **n00b@linux said:**
> It seems to work on my ATi Radeon Mobility M7 LW (AGP) (ChipID = 0x4c57).
Thanks for the HOWTO :).

Glad to hear this!

Did your computer start crashing randomly after you followed Part I? If not, try removing/changing the options marked "More stable this way". They are usually extra features that are disabled to make things more stable.

If you say yes to the above option, I will add your card to the "Cards that Work in this HOWTO" section at the top.

---

### Post by PowerRanger on 2006-09-20
I have an inspiron 5000 laptop with an  "ATI Technologies, Inc. Rage Mobility P/M AGP 2x" chip-- note my investigation so far has revealed this is actually a Mach64 chip.  I have installed edgy knot 3 and can't get 3d acceleration.  The native resolution of the LCD is 1400x1050 and my default depth is set to 16.  If I try to start x with this resolution, I get the Static buffer allocation failed.   I dropped down to 800x600 and no longer get that error but I get other errors:
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1 (No such device or address)
drmOpenDevice: open result is -1 (No such device or address)
drmOpenDevice: Open Failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1 (No such device or address)
drmOpenDevice: open result is -1 (No such device or address)
drmOpenDevice: Open Failed
[drm] failed to load kernel module "Mach64"

```
I've tried modprobing the module, but that doesn't work (not found).
I've tried compiling my own mach64 module, but that errors with a "'struct page' has no member named 'count' "-- I've seen where other ppl have this same error with 2.6.x but I haven't found a resolution.  Does anybody have any ideas how I can get 3d accereration going here?  

Also are the "RADEON" drivers from the gatos project?  Are "ATI" the proprietary drivers and "MESA" the open drivers?  Any help would be appreciated.
TIA
Mike

---

### Post by javaJake on 2006-09-21
> **PowerRanger said:**
> I have an inspiron 5000 laptop with an  "ATI Technologies, Inc. Rage Mobility P/M AGP 2x" chip-- note my investigation so far has revealed this is actually a Mach64 chip.

Actually, there is a HOWTO for your specific card: [http://ubuntuforums.org/showthread.php?t=7200](http://ubuntuforums.org/showthread.php?t=7200)

Enjoy. :D

---

### Post by jms830 on 2006-09-22
following this guide requires that I upgrade some packages to the edgy version. whats the risk of doing that, and can I easily undo it? It seems to install a lot of packages

---

### Post by javaJake on 2006-09-22
> **jms830 said:**
> following this guide requires that I upgrade some packages to the edgy version. whats the risk of doing that, and can I easily undo it? It seems to install a lot of packages

Answer #1: Well, everyone else here hasn't had any issues. I've been using this ever since this HOWTO was first made, which is at least a month. Statistically, it is unlikely you'll run into any issues.

Answer #2: You cannot easily undo it. You can downgrade, but that is definately NOT recommended! It would be better to reinstall.

If you are worried about losing your stuff, here's what I'd do: back up your home directory (including hidden files), make the plunge, and see what happens. I'd rather try to get 3D acelleration!


Let me know what you decide to do.

---

### Post by dansherman on 2006-09-23
I followed the guide (excellent writing, by the way) but still no 3D. 
```
dan@dan-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```
No errors or significant warnings in Xorg.0.log 
```

cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux dan-laptop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
dan@dan-laptop:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled

```
Xorg.0.log and xorg.conf are attached.

Any thoughts?

---

### Post by javaJake on 2006-09-23
> **dansherman said:**
> I followed the guide (excellent writing, by the way) but still no 3D.

Any thoughts?

Check out this chunk of log:
```

(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration disabled
...later on....
(II) RADEON(0): Acceleration enabled

```

For some reason, you don't get 3D acelleration even though the log says you do. I'll do some more research... you haven't heard the last of me. :)

(BTW, thanks for the compliments.)

---

### Post by dansherman on 2006-09-24
I noticed that, but what about this?
```
dan@dan-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by javaJake on 2006-09-24
> **dansherman said:**
> I noticed that, but what about this?
```
dan@dan-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

Your hardware is just like mine, so it has just got to work. Very strange. I think it might be your installation (have you messed around with it?) but I want to leave that as my last option, since I'm sure you hate it when people say that. :)

What I will do is try out your configuration. I'll see if anything is wrong with your xorg.conf code.

Meanwhile, would you mind posting as many specs about your video card, and your laptop brand and model? This will help a lot in my research.

I will try to get results out to you by tomorrow, but things have been so busy I haven't been able to do stuff I want to do.

---

### Post by dansherman on 2006-09-24
My install is only a few hours old (or it was yesterday).  The only thing I've done to xorg.conf is change the mouse settings.  

It's a Gateway 450SX, 512MB RAM.  I'm don't know much about the video card, sorry.  Let me know if there's any other info you want.

Thanks for all the work you're putting into this.

---

### Post by dansherman on 2006-09-26
I was looking in Xorg.0.log and noticed this line
```
(**) RADEON(0): Forced into PCI mode
```
Might this be causing issues?

---

### Post by javaJake on 2006-09-26
> **dansherman said:**
> I was looking in Xorg.0.log and noticed this line
```
(**) RADEON(0): Forced into PCI mode
```
Might this be causing issues?

Maybe... try commenting out (placing a "#" in front of) the "BusType 'PCI'" line I had you add in the HOWTO. It causes my laptop to become highly unstable, but it is worth a shot to see if we are any closer.

I still haven't gotten round to trying out your configuration yet... be assured that it is _on my list of things to do!_ I don't forget people that easily. :)

---

### Post by dansherman on 2006-09-26
Well, that didn't do it..  glxinfo returns the same info.

---

### Post by javaJake on 2006-09-27
> **dansherman said:**
> Well, that didn't do it..  glxinfo returns the same info.

I'm punching in your configuration now, so hang tight... I'll post my results in an hour or so.

---

### Post by javaJake on 2006-09-27
[COLOR="Silver"]> **dansherman said:**
> Well, that didn't do it..  glxinfo returns the same info.

I'm punching in your configuration now, so hang tight... I'll post my results in an hour or so.[/COLOR]

Whoops... sorry about this duplicate.

---

### Post by javaJake on 2006-09-27
> **dansherman said:**
> It's a Gateway 450SX, 512MB RAM.  I'm don't know much about the video card, sorry.
I need to know what the model number is that works on this website:
[http://support.gateway.com/support/supinfo/index.asp?pg=2&file=mo.html](http://support.gateway.com/support/supinfo/index.asp?pg=2&file=mo.html)

That way I can look up how much memory your card has. There are two different MY L6 cards - one wiht 8 MB RAM, and one with 16 MB RAM. There's no other difference as far as I know. The people who have 16 MB RAM can use the 24-bit depth, others have to use 16-bit because of memory restrictions. (I'm one of them unlucky 8 MB people.)

---

### Post by javaJake on 2006-09-27
> **dansherman said:**
> I noticed that, but what about this?
```
dan@dan-laptop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

OK, I've found the problem. It's so simple, I didn't even see it. You are using the ati driver, and I'm using the radeon driver. I guess the other guy's suggestion was right after all (can't remember his name).

Change the "Driver 'ati'" line to "Driver 'radeon'".

---

### Post by dansherman on 2006-09-29
Well, I haven't had a chance to fiddle with it in a few days because my hard drive kicked the bucket.  I did notice when I booted from the LiveCD that it worked just fine.. go figure.

Thanks for all the help though!

---

### Post by kise on 2006-10-04
Any one running ubuntu on compaq Evo N410c?
If so can you please send me your xorg.conf file?
[email]christjk@start.no[/email]

I have tryed to reconfig the file, but i am doing somthing wrong, and i cant figure out what.

Sinserrely 
Christopher

---

### Post by javaJake on 2006-10-04
> **kise said:**
> Any one running ubuntu on compaq Evo N410c?
If so can you please send me your xorg.conf file?
[email]christjk@start.no[/email]

It would be helpful if you posted the /var/log/Xorg.0.log, and /etc/X11/xorg.conf file. If your device isn't related what-so-ever to the ATI Radeon group, this is the wrong thread.

---

### Post by KAOZ23 on 2006-10-16
Good nights 4 everybody:
First of all, i'm Spanish (my English it's no so good enough)

My problem/s:
I had spent about 6-8 hours trying to load radeon driver in my Ubuntu Dapper, but i think it's impossible (but i don't know the reason):
Before, I'm a "newbie" in linux*ubuntu, but I have brain inside my head.

My configuration:
AMD Athlon XP 2000+
MotherBoard ASUS XV7 (or something like that)
Graphic Card (from xorg.conf): ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]
kernel: 2.6.15-27-k7
Ubuntu dapper 6.06 fully updated + Gnome 2.14.3


My xorg.conf (not all, but the most important):
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load 	"GLcore"
EndSection
###########***Check this-----
########################################################

Section "Extensions"
 Option "RENDER" "Enable" 
EndSection
#####################################################

Section "InputDevice"
###bla
EndSection

Section "InputDevice"
#bla
EndSection
Section "InputDevice"
#####bla bla bla wacom bla bla bla
Section "InputDevice"
###more bla bla bla
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"radeon"
	BusID		      "PCI:1:0:0"
	Option		"BusType" "PCI"
	Option		"AGPMode" "4"
	Option		"AGPSize" "32" # default: 8
	Option		"AGPFastWrite" "false" # More stable this way.
	Option		"SWcursor" "true" # More stable this way.
	Option		"EnablePageFlip" "true" # Faster.
	Option		"EnableDepthMoves" "false" # More stable this way.
	Option		"RenderAccel" "false" # More stable this way
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
	Option		"DDCMode"
	Option		"SubPixelOrder" "NONE"
	Option		"ColorTiling" "false" # More stable this way.
	Option		"DynamicClocks" "true"
	Option		"bioshotkeys"   "True"
	Option		"XAANoOffscreenPixmaps" "true" # More stable this way.
##############################################Option "VideoOverlay" "on"
##############################################Option "OpenGLOverlay" "off"
##############################################Option "UseInternalAGPGART" "no"
###############################################Option "UseFBDev" "true"
#	Option         "AGPMode" "4"
#	Option         "DynamicClocks" "True"
#	Option         "AGPSize" "64" # default: 8
#	Option         "AGPFastWrite" "True"
#	Option	       "BusType" "auto detect"
#	Option         "RingSize" "8"
#	Option         "BufferSize" "2"
#	Option         "EnablePageFlip" "true"
#	Option         "EnableDepthMoves" "true"
#	Option         "RenderAccel" "true"
#	Option	       "UseInternalAGPGART" "yes"
#	Option		"ColorTiling" "on"
EndSection

Section "Monitor"
	Identifier	"StudioWorks"
	Option		"DPMS"
	HorizSync	30-61
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"StudioWorks"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Group   0
	Mode	0666
EndSection
*********************************************************

```

This xorg.conf is a mix of many configurations that i've found about Ati 3D acceleration.

glxinfo says:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

"cat /var/log/Xorg.0.log | grep EE" says:
```

Current Operating System: Linux Ubuntu-desktop 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

"sudo lspci -vv" says:
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
        Subsystem: Hightech Information System Ltd.: Unknown device 2001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at d800 [size=256]
        Region 2: Memory at d6000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d7fe0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
                Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

"dmesg | grep agp" says:
```

[17179594.212000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.252000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179594.268000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179611.504000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179611.504000] agpgart: Device is in legacy mode, falling back to 2.x
[17179611.504000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179611.504000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17180311.436000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180311.436000] agpgart: Device is in legacy mode, falling back to 2.x
[17180311.436000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17180311.440000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

```

"lsmod | grep agp" says:
```

via_agp                10560  1
agpgart                37072  2 drm,via_agp

```

libgl1-mesa-dri is updated from repositories


Somebody could help me?????I want to install beryl-manager, but my screen only blinks and goes back to metacity.

---

### Post by javaJake on 2006-10-16
LOL... that's got to be the biggest list of logs I've seen yet, but you forgot one that I need: "cat /var/log/Xorg.0.log | grep WW".

---

### Post by javaJake on 2006-10-18
**_Coming Soon To A HOWTO Thread Near You ;)_**

I've just gotten two different configurations working on the Radeon M6 LY: MergedFB, and Xinerama. It won't be long untl I have either an extra HOWTO or an added section to this HOWTO. Either way, you'll learn how to add an extra monitor to your laptop/desktop and then install a script that'll allow you to choose one of these two configurations at startup. 8)

---

### Post by kingkookie on 2006-10-18
Had a little trouble with my Radeon Mobility IGP340 chip, but it was resolved by changing the AGPSize setting to the default "8".  Now everything is perfect.  Thanks.

---

### Post by javaJake on 2006-10-18
> **kingkookie said:**
> Had a little trouble with my Radeon Mobility IGP340 chip, but it was resolved by changing the AGPSize setting to the default "8".  Now everything is perfect.  Thanks.

Have you tried other HOWTOs, and they failed, while this one worked? Or did you just try this one? Either way, let me know. If you haven't tried any other HOWTO, you should look at the "More stable this way" options, and mess around with those - hardware mouse pointers and stuff might work on your system, and are nice little things to have. :)

---

### Post by KAOZ23 on 2006-10-21
> **javaJake said:**
> LOL... that's got to be the biggest list of logs I've seen yet, but you forgot one that I need: "cat /var/log/Xorg.0.log | grep WW".

More information = more possibilities.
I've learned this in many others forums that I've posted or ¿¿helped?? (my english teacher wasn't so good :) :) )


Here it is:
```

 (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled

```


Secondary monitor? I've never configured this!!

Some help?

---

### Post by javaJake on 2006-10-21
OK, the secondary monitor thing doesn't have anything to do with this. (Although if you want one, I'm writing an optional section for this HOWTO that'll do it!)

I'll be sure to look into your logs, and see what I can do.

---

### Post by javaJake on 2006-10-21
Alright, I want you to remove the Extensions section, since it isn't part of this HOWTO.

What I'll do (as I did for someone else) is integrate your xorg.conf into mine, keeping the monitor configurations, etc. Then I'll see what's up from there... whatever's wrong should come up then.

---

### Post by Efrain Valles on 2006-10-21
Hey :)
 
NO RENDERING (and it's back to it's crashing ways...)

here is [my xorg]("http://paste.ubuntu-nl.org/27733/")

here is [my xorg.0.log]("http://paste.ubuntu-nl.org/27734/")

I hoe you still have enough fuzzy feelings to help me out here... :)

Efff..

:S

EDIT: looking tohrough the stuff... I found I have his same problem... look at this...

```
valles@voices:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabledvalles@voices:~$

```

Thanks

---

### Post by javaJake on 2006-10-22
> **Efrain Valles said:**
> Hey :)
 
NO RENDERING (and it's back to it's crashing ways...)

here is [my xorg]("http://paste.ubuntu-nl.org/27733/")

here is [my xorg.0.log]("http://paste.ubuntu-nl.org/27734/")OK, first thing I noticed right off is you didn't change ati to radeon. I'm pretty sure that's in the HOWTO, but I'd better check again...

> **Efrain Valles said:**
> I hoe you still have enough fuzzy feelings to help me out here... :)You betcha. :)

Efff..

:S

> **Efrain Valles said:**
> HEDIT: looking tohrough the stuff... I found I have his same problem... look at this...

```
valles@voices:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabledvalles@voices:~$

```

ThanksActually, that doesn't matter. It's just letting you know that you don't have a second monitor, and so it won't be cloning your first screen. How to configure a second monitor is coming soon to this HOWTO... stay "tuned". :D

---

### Post by Efrain Valles on 2006-10-22
I changed to radeon an Still no luck... I changed it after I posted my xorg... no rendereringyet... the computer hasn't crashed yet... thoughh... 

any other thoughts???

EDIT:

I have updeated [ My xorg.conf]("http://paste.ubuntu-nl.org/27807/")

Edit II:

[COLOR="Orange"]that[/COLOR] makes my card 8 mbytes no?
(II) RADEON(0): Page flipping enabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video [COLOR="Orange"]RAM=8192K[/COLOR], accessible=65536K (PCI BAR=131072K) 
(--) RADEON(0): Mapped VideoRAM: 8192 kByte (32 bit DDR SDRAM)

---

### Post by alxbob on 2006-10-22
I have sold this problem thx too javajake!!
thx a lot the linux community and free out the software :D

---

### Post by javaJake on 2006-10-22
> **alxbob said:**
> I have sold this problem thx too javajake!!
thx a lot the linux community and free out the software :D

So, the HOWTO solved the problem? Or you found a solution? If you found one, let us know so we can benefit. :)

Also, if you could let me know A) what card you have and/or B) if you had issues with other HOWTOs before coming to this one. Thanks a lot!

---

### Post by javaJake on 2006-10-22
> **Efrain Valles said:**
> I changed to radeon an Still no luck... I changed it after I posted my xorg... no rendereringyet... the computer hasn't crashed yet... thoughh... 

any other thoughts???I'm going to import your xorg.conf into my config, and see what's up. I've done it before, and it helped, so it should work again...

> **Efrain Valles said:**
> Edit II:

[COLOR="Orange"]that[/COLOR] makes my card 8 mbytes no?
(II) RADEON(0): Page flipping enabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video [COLOR="Orange"]RAM=8192K[/COLOR], accessible=65536K (PCI BAR=131072K) 
(--) RADEON(0): Mapped VideoRAM: 8192 kByte (32 bit DDR SDRAM)Yea... so is my card, so that means that we both have the same exact card. That's a good thing. :D (BTW, AGPSize has nothing to do with the card size, I don't think. Googling produces a fuzzy answer.)

---

### Post by javaJake on 2006-10-24
> **KAOZ23 said:**
> Somebody could help me?????I want to install beryl-manager, but my screen only blinks and goes back to metacity.

I'm going to troubleshoot your card the best I can, but results are not likely. First of all, your card isn't supported by this HOWTO. (Whether or not I should support it can be proven - see the "Cards that Work with this HOWTO" section at the top of the HOWTO.) Second, your card is different then what I've got, so my troubleshooting can only go so far. So far your logs show nothing out of the ordinary, and your xorg.conf configuration appears to be fine.

I'll let you know what the results from my troubleshooting are sometime today or tomorrow.

---

### Post by javaJake on 2006-10-24
> **Efrain Valles said:**
> I changed to radeon an Still no luck... I changed it after I posted my xorg... no rendereringyet... the computer hasn't crashed yet... thoughh... 

I haven't forgotten you, and will get down to troubleshooting your card later today, after KAOZ23's card is troubleshooted (he got here first :) ).

---

### Post by javaJake on 2006-10-24
KAOZ23, unfortunately my card ran just fine with your configuration. Without any errors from logs, either on my side or yours, I can't do anything. You could try removing every resolution above 1024x768, and try that, but I doubt that'll work.

Your case is closed, unless you have any errors that might help. Sorry. Try contacting people who appear to have Radeon 7000 working on their machine.

:(

---

### Post by javaJake on 2006-10-24
> **Efrain Valles said:**
> I changed to radeon an Still no luck... I changed it after I posted my xorg... no rendereringyet... the computer hasn't crashed yet... thoughh... 

OK, this is really wierd. Your xorg.conf file checked out on my system, but it is almost exactly like mine, down to mice and keyboard configurations! Do you by any chance have a Compaq 1700 laptop? :D

Anyway, yea, the fact that your xorg.conf file checked out is not good - it means I've just run out of ideas, short of you either reinstalling to get a clean system, or you upgrading your DRI modules (Part II of HOWTO).

If you do have a Compaq 1700 laptop, then there's good news - it's 99.9% likely that we can get this to work, just a matter of how.

---

### Post by Efrain Valles on 2006-10-24
I do have a compaq t1700 :) ... and it has been my loyal friend... it does not do aceel ... shall I go with step 2.... ???

eff

---

### Post by javaJake on 2006-10-25
> **Efrain Valles said:**
> I do have a compaq t1700 :) ... and it has been my loyal friend... it does not do aceel ... shall I go with step 2.... ???

eff

Compaq, I heard, has the best Linux laptop driver support. The video card needed this fix that I mentioned in this HOWTO, but that's ATI's fault, really.

I'd say go for Step 2. If that doesn't work, what I recommend is you reinstall your system upgrading to Edgy in the process when Edgy is released. It should work! I know it should! :)

---

### Post by javaJake on 2006-10-25
**_Attention Users Who Have Successfully Used this HOWTO_**

I will be upgrading to Edgy later this week to get ahead the official release, so I can prepare this HOWTO for Edgy. If  you like to adventure out into the unkown, and know how to use Google's and these forums' search functions to your advantage, then go for it! It's likely this HOWTO will work anyway.

---

### Post by Efrain Valles on 2006-10-25
Well. could you post your xorg... so that I can see it. maybe something is wrong... we dafinetely have the same laptop... 

but I am not going through with the edgy upgrade. I don't know if all the flashy stuff will make my machine a wounded turtle... :( .. I'm getting a beautifull hp compaq :) intel video card... wish me luck....

 Eff

thanks for getting me off the vesa driver... :)

---

### Post by javaJake on 2006-10-25
:-# > **Efrain Valles said:**
> Well. could you post your xorg... so that I can see it. maybe something is wrong... we dafinetely have the same laptop... 

I've uploaded my xorg.conf. It's got some edits that I've commented out (I tried to use Compiz) so you have to kind of see beyond those. Once you remove those commented out parts, you'll find our configuration is almost exactly the same! I'd say you could just replace yours with mine! :D

**Edit:** I forgot to upload the attachment. I haven't ever remembered to upload an attachment until after I make the post. :oops:

xorg.conf.3D is my xorg configuration.
xorg.conf.diff is the difference between my configuration and yous (once you strip the extra commented parts).

---

### Post by zanglang on 2006-10-25
Does Compiz/XGL works on the Compaq 17xx for you guys? I've tried out Beryl a few days ago, but it doesn't seem to render correctly (showing just a black screen with weird color artifacts while moving my mouse around). :/

Oddly enough I got direct rendering working a few days ago on mine, but after yesterday's Edgy update everything seems to be broken. Maybe I need to try going through the guide again and see what happens.

Edit: Woot! Had to remove the fglrx packages that I was trying out earlier, at least glxinfo no longer crashes now. :D

---

### Post by javaJake on 2006-10-26
> **zanglang said:**
> Does Compiz/XGL works on the Compaq 17xx for you guys? I've tried out Beryl a few days ago, but it doesn't seem to render correctly (showing just a black screen with weird color artifacts while moving my mouse around). :/I've been trying to get this to work, but I get the "no-window-border" affect, as I call it. It apparently can be fixed (I didn't install what I was supposed to).

I will be updating this HOWTO with Xinerama and MergedFB support. After that I hope to work on one of those fancy window managers. If you want, you can help me... there's so many choices (AIGLX, Compiz, Beryl) that I don't know where to begin. :) 

> **zanglang said:**
> Oddly enough I got direct rendering working a few days ago on mine, but after yesterday's Edgy update everything seems to be broken. Maybe I need to try going through the guide again and see what happens.I hope you read the "Important Stuff to Read" section. In there I mentioned that, when I tried Edgy Knot 1 (OK, so that's old, but it should be a pretty good indication, right?) things were not happy.

> **zanglang said:**
> Edit: Woot! Had to remove the fglrx packages that I was trying out earlier, at least glxinfo no longer crashes now. :D

Can you explain your problem and solution so I can stick this in the troubleshooting section at the bottom of the HOWTO? I'm slightly confused about what your problem was, and what is fixed now.

---

### Post by javaJake on 2006-10-26
> **Efrain Valles said:**
> but I am not going through with the edgy upgrade. I don't know if all the flashy stuff will make my machine a wounded turtle... :(Tell you what, I'll let you know by way of PM what went wrong, and how I fixed it, so you can have a nice stable Edgy machine. :)

---

### Post by KAOZ23 on 2006-10-26
OK, thanks **javaJake ** for your attention....

I'm only 1 month with Ubuntu-linux, and my knowledge is far away to be good . I've resolved maaaaany problems in my PII-350 Mhz PC, with Win-dong (my AGP port go to Heaven, after disconnect graphic card with the computer TURNED ON, and PCI (not PCI express) cards,yes, (they already exists), doesn't work so fine (8 MB+Win-dong XP PRO), but finally I did it.


But I don't know why I can't install beryl, and get working with it...](*,) ](*,) ](*,) in my girlfriend's PC...

---

### Post by zanglang on 2006-10-27
> **javaJake said:**
> I've been trying to get this to work, but I get the "no-window-border" affect, as I call it. It apparently can be fixed (I didn't install what I was supposed to).

I will be updating this HOWTO with Xinerama and MergedFB support. After that I hope to work on one of those fancy window managers. If you want, you can help me... there's so many choices (AIGLX, Compiz, Beryl) that I don't know where to begin. :) 
Ah, so it's possible to get XGL on this card! All hope is not lost :D Beryl seems to be the more popular choice recently, but I'll start looking at other options. Will keep you updated if things go well ;)

> **javaJake said:**
> I hope you read the "Important Stuff to Read" section. In there I mentioned that, when I tried Edgy Knot 1 (OK, so that's old, but it should be a pretty good indication, right?) things were not happy.

Can you explain your problem and solution so I can stick this in the troubleshooting section at the bottom of the HOWTO? I'm slightly confused about what your problem was, and what is fixed now.
Oh that would be my fault I guess. I didn't realize that not all Radeon Mobility models work with fglrx and tried installing it, after which the xserver wouldn't boot or would freeze constantly even after changing back to radeon. It worked fine once I removed fglrx. Good lesson learnt!

---

### Post by Efrain Valles on 2006-10-29
Ok .. I have been plying around wih settings and I notices this... 

Xlib extension missing?????

valles@voices:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
valles@voices:~$

---

### Post by javaJake on 2006-10-29
**_It Works In Edgy... Barely_**
It crashes a ton, however, so everyone has three options:

[list][*]Upgrade to Edgy, and just use default configuration - without 3D[*]Upgrade to Edgy, and use 3D config - it might crash a lot![*]Stick with Dapper.[/list]

I am working on this constantly, as it is about as important to me as everyone else. :)

---

### Post by javaJake on 2006-10-29
> **Efrain Valles said:**
> Ok .. I have been plying around wih settings and I notices this... 

Xlib extension missing?????

valles@voices:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
valles@voices:~$

Did you upgrade to Edgy? If so, this error is very strange... DRI modules come with Edgy.

Try installing the following packages, restarting X after each installation. (I sorted the packages from most likely to least likely to help.)

```

xlibmesa-dri
xlibmesa-gl
xlibmesa-glu

```

---

### Post by Efrain Valles on 2006-10-29
to install those paquages do I have to be in edgy... 
No ... I didn´t upgrade to edgy.... I only got that error message trying different depths... 16, 15 so on and so forth... but I remember getting that error alot befor when using the radeon driver and trying to do get accel... 
way back in hoary... :)

I will try installing those packages and see....

---

### Post by Efrain Valles on 2006-10-29
the packages are not in the repositories for Drapper... they must be edgy then...
:(

---

### Post by javaJake on 2006-10-30
> **Efrain Valles said:**
> the packages are not in the repositories for Drapper... they must be edgy then...
:(

The fact that you are getting it, and I'm not, and we are using identical computers says something, I dare say. It says "you need to reinstall". I'm fairly certain your installation has been shoved around a lot, since you've tried so many HOWTOs. Try reinstalling, and then punch in this HOWTO again.

Unfortunately I cannot think of anything else. :(

---

### Post by wk2001 on 2006-11-03
Hello,

i don't really know if i'm right here, but i've read all the pages and maybe somebody could help me with my problem.

problem: direct rendering doesn't work... :)
my system: edgy... (upgraded from dapper upgraded from breezy)
my graphics adapter: ati mobility radeon 9000 (M9) with 64mb ram
driver: i want to get open source radeon driver running

here my xorg.conf: [http://www.ubuntuusers.de/paste/4867/](http://www.ubuntuusers.de/paste/4867/)
here my Xorg.0.log: [http://www.ubuntuusers.de/paste/4868/](http://www.ubuntuusers.de/paste/4868/)

and the output of glxinfo: [http://www.ubuntuusers.de/paste/4869/](http://www.ubuntuusers.de/paste/4869/)

enabling "GLcore" in the xorg.conf caused X-restart on glxinfo or glxgears... that's why i disabled it.

ps: the fglrx driver was running but i want to get running aigxl and i need the radeon driver for this...

i hope, someone could help me...

thank you very much!

---

### Post by javaJake on 2006-11-05
These instructions are not needed, actually, or even produce any results.

[COLOR="Silver"]**_HOWTO Updated - Edgy Support Added_**
Edgy's been added as a supported OS, but crashing is pretty bad. I'm working every day on this because I'm affected all the time by this.

Also, I added a section everyone needs to follow - a bug is hanging around that will cause your card to crash randomly. You have to apply a patch manually, but it isn't difficult at all.

The section you need to follow is the "All Users - Dapper and Edgy" one just before "Some Final Notes". I've copied it below for your convenience.

**_[SIZE="2"]All Users - Dapper and Edgy[/SIZE]_**
At this point you think you are done. You've just completed the installation of new drivers that are just about the latest. Your card is probably the most stable yet. (Some maybe not.)

Well, the point is that there is a bug fix that was never included in this release. That's right. You heard me. A bug fix was accidentally left out that directly affects us. You know what that means? We get out some sources and compile. Muhahahaha.

No, seriously, it's not that hard. Apt-get does all the downloading we need, you'll do a copy and paste, run a few commands, and boom. Done.

So let's get started. Run the following commands:

```

sudo apt-get install nano
sudo nano /etc/apt/sources.list

```

Now replace any mention of "dapper" with "edgy", except for the cdrom entry, and remove any single "#". (It's OK if you replace that too... we'll be changing it back later.) Now run the following:

```

sudo apt-get update

```

Run the following command. This command will download everything we need to compile the drivers.

```

sudo apt-get build-dep xserver-xorg-video-ati

```

Once that's done, run...

```

sudo apt-get source xserver-xorg-driver-ati

```

This downloads the source for the ati drivers. The ati drivers include radeon.

Alright, next we have to apply the patch that was never applied. Run the following command to jump down to the folder where we need to be:

```

cd xserver-xorg-driver-ati-6.5.7.3/

```

OK, now, see this page here? [http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=blobdiff;h=6d6270187e048138463c6b913449083b2c8ad355;hp=03d1e8972b689150c59619762674f07b8ca356cf;hb=10ba4f0a435d7c1ed9f4a36a8d607f0f0b63be30;f=src/radeon_driver.c](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=blobdiff;h=6d6270187e048138463c6b913449083b2c8ad355;hp=03d1e8972b689150c59619762674f07b8ca356cf;hb=10ba4f0a435d7c1ed9f4a36a8d607f0f0b63be30;f=src/radeon_driver.c)
Well, that's the patch that was never applied. We'll have to apply it ourselves.

Run the following command:
```

sudo gedit src/radeon_driver.c

```

Select the menu Search -> Go to Line... and punch in 2296.
You should see some resemblance between this and the page I showed you above. Most users should be able to do this next part on their own, but I'll lead you step-by-step to be sure. (Basically, any line that has "-" and is red, we remove, and "+" and green lines we add.)

Remove this line...
```
    unsigned long agp_size, agp_base, mem_size;
```
...replace it with this line...
```
    unsigned long mem_size;
```
...and add this line.
```
    CARD32 aper_size;
```
Select the menu Search -> Go to Line... and punch in 2306. Just after this line...
```
    mem_size = INREG(RADEON_CONFIG_MEMSIZE);
```
...add this line.
```
    aper_size = INREG(RADEON_CONFIG_APER_SIZE);
```
Just after this line...
```
             mem_size = 0x800000;
```
...add these lines.
```
    /* Fix for RN50, M6, M7 with 8/16/32(??) MBs of VRAM - 
       Novell bug 204882 + along with lots of ubuntu ones */
    if (aper_size > mem_size)
        mem_size = aper_size;

```
Just after this line...
```
     if (info->directRenderingEnabled && !info->newMemoryMap) {
```
...add this line.
```
            CARD32 aper_size = INREG(RADEON_CONFIG_APER_SIZE);
```
Click the Save button in the toolbar. You've just applied a patch. Congrats. :)

Here's the next part. This part is tricky - you either get no errors, and have a great time, or you get a lot of errors, and end up Googling a lot. We are now going to compile. **Scary music**

Wait... nearly forgot... we should really back up our drivers. Run the following commands to do just that:
```

mkdir ~/xserver-xorg-drivers_BAK/
cp -R /usr/lib/xorg/modules/drivers/* /home/jacob/xserver-xorg-drivers_BAK/

```

Now you can compile:
```

sudo ./configure
sudo make
sudo make install

```

Replace "edgy" with "dapper" in the /etc/apt/sources.list file again, and restart the computer. You are done. You now have patched drivers. **Be warned** that every time you update xserver-xorg-drivers-ati, or install a new OS, you'll have to apply this patch, unless they have the patch already.

Also be warned that I have not been free of crashes, but I do have some current ideas that reduce crashing:

[list]
[*]Don't multitask. As soon as I have 5 windows or more open, I am 75% sure to crash at any momeny.[*]Try not to move the mouse or do things while windows or lists, etc., are loading. This one's strange, and may not be true, but it is worth a shot.[/COLOR]

---

### Post by wk2001 on 2006-11-07
Hello,

```
sudo apt-get build-dep xserver-xorg-driver-ati
```

This didn't work for me on edgy...
First of all: In edgy there is no xserver-xorg-driver-ati package any more but xserver-xorg-video-ati instead. 

But executing:
```
sudo apt-get build-dep xserver-xorg-video-ati
```
I get the error from apt-get that it could not accomplish the build-dependencies...

Do you have some other suggestions, and do you think this would fix my problem with my radeon M9 (see above)?

Lot of thanks!

---

### Post by impactdni on 2006-11-07
Wanted to add a bit of info on edgy.

Up to date repos give a ati driver with the above patch applied (6.6.2)

I still get crashes...

Also looks like [https://bugs.freedesktop.org/show_bug.cgi?id=6429](https://bugs.freedesktop.org/show_bug.cgi?id=6429)
is dealing with this problem as well...

---

### Post by javaJake on 2006-11-08
> **wk2001 said:**
> Hello,

```
sudo apt-get build-dep xserver-xorg-driver-ati
```

This didn't work for me on edgy...
First of all: In edgy there is no xserver-xorg-driver-ati package any more but xserver-xorg-video-ati instead. 

But executing:
```
sudo apt-get build-dep xserver-xorg-video-ati
```
I get the error from apt-get that it could not accomplish the build-dependencies...

Do you have some other suggestions, and do you think this would fix my problem with my radeon M9 (see above)?

Lot of thanks!

OK, about that first part, that's my fault. Apparently Dapper and Edgy have two different sources or names for the drivers. I'll edit this in the HOWTO.

About your not being able to accomplish build-dependencies, I was able to on a system with just the included sources.list file (uncommenting everything, of course). I'd check to be sure sources.list doesn't have any single "#" in it.

And, yes, I do have a suggestion that I picked up from Google. You must have xorg-driver-fglrx uninstalled before installing the radeon driver. This means you should uninstall fglrx, and then reinstall the radeon drivers.

---

### Post by javaJake on 2006-11-08
> **impactdni said:**
> Wanted to add a bit of info on edgy.

Up to date repos give a ati driver with the above patch applied (6.6.2)

I still get crashes...

Also looks like [https://bugs.freedesktop.org/show_bug.cgi?id=6429](https://bugs.freedesktop.org/show_bug.cgi?id=6429)
is dealing with this problem as well...

I've actually already seen that bug, and is the basis for this entire HOWTO. The bug you mentioned applies to Dapper's Xorg, which is exactly why I have you upgrade Dapper's Xorg DRI drivers to Edgy's. Edgy users don't need to do this in the first place.

---

### Post by 2hansen on 2006-11-10
First of all I want to say that I am very happy that you are working with making the M6 work with 3D acceleration. I am using the latest Edgy on my Sony PCG-V505AP which is equipped with an ATI M6 LY (Radeon 9000) with 16 MB.

This post just to confirm that I understand the current status correctly:

- At the moment the 3D acceleration does not work in latest Edgy with the ATI Mobility M6 LY (Radeon 9000)?

- The part 2 of the HOWTO is currently not working for latest Edgy (changed package names, change content of packages etc.?)

And then onto to the more specific stuff:

I am running in a dual monitor set-up using the mergedFB option of the Radeon driver. This gives me the internal 1024x768 and an external 1280x960.

I had a lot of trouble with the Dapper version of Ubuntu because of some problems with the radeon-driver and dual screen set-up, but these seem to have been corrected with the final Edgy.

With this setup I have no 3D acceleration:

```
:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

which I assume is caused by

```
:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 25920 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable

```

However, if I change into single screen mode I can manage to have no errors (EE) in my Xorg.0.log

but instead I get this

```
:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Mode 1280x960 1024x768 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
(WW) (1280x960,CRT2 Monitor) mode clock 148.5MHz exceeds DDC maximum 140MHz
(WW) (1280x1024,CRT2 Monitor) mode clock 157.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 189MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 202.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 229.5MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,CRT2 Monitor) mode clock 204.8MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,CRT2 Monitor) mode clock 261MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,CRT2 Monitor) mode clock 218.3MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,CRT2 Monitor) mode clock 288MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 234MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 297MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 155.8MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 184MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,CRT2 Monitor) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,CRT2 Monitor) mode clock 193.16MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,CRT2 Monitor) mode clock 230MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 341.35MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,CRT2 Monitor) mode clock 266.95MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,CRT2 Monitor) mode clock 340.48MHz exceeds DDC maximum 140MHz
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
```

and if I try to run glxinfo my system freezes - and a reboot is necessary.

Is this the way it "should be" the current state of Edgy and radeon drivers taken into consideration?

Please let me know if you have any suggestions or if I can help you test out new possible solutions.

---

### Post by javaJake on 2006-11-10
> **2hansen said:**
> First of all I want to say that I am very happy that you are working with making the M6 work with 3D acceleration. I am using the latest Edgy on my Sony PCG-V505AP which is equipped with an ATI M6 LY (Radeon 9000) with 16 MB.

This post just to confirm that I understand the current status correctly:

- At the moment the 3D acceleration does not work in latest Edgy with the ATI Mobility M6 LY (Radeon 9000)?
Well, it works, but shakily. (I despise the "edgily" joke - it's way overused.) If you must upgrade to Edgy, that's how you'll at least solve the immediate crashing.

> **2hansen said:**
> - The part 2 of the HOWTO is currently not working for latest Edgy (changed package names, change content of packages etc.?)It works. There's one small issue where Dapper and Edgy have different package names for the same driver, and I only provided the Edgy one. :)

> **2hansen said:**
> And then onto to the more specific stuff:

I am running in a dual monitor set-up using the mergedFB option of the Radeon driver. This gives me the internal 1024x768 and an external 1280x960.

I had a lot of trouble with the Dapper version of Ubuntu because of some problems with the radeon-driver and dual screen set-up, but these seem to have been corrected with the final Edgy.I've been absolutely fine in Edgy. Very strange. It could be you messed something up in your xorg.conf file - it's super easy to do that with the complex stuff you end up doing.

> **2hansen said:**
> With this setup I have no 3D acceleration:

```
:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

which I assume is caused by

```
:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 25920 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable

```It absolutely is the cause. I will be writing sections on how to do Xinimera and MergedFB (and hopefully Beryl) on the Radeon M6 LY cards.

The problem here is that your card has only 8 MB of memory (or is it 16 MB?) and you are asking it to use 25 MB of memory. You'll have to reduce your resolution even further to 860x640 if you are to get DRI with MergedFB.

Personally, I don't care. I just want it to work, and the fact that it does is awesome for me. :p 

> However, if I change into single screen mode I can manage to have no errors (EE) in my Xorg.0.log

but instead I get this

```
:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Mode 1280x960 1024x768 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
(WW) (1280x960,CRT2 Monitor) mode clock 148.5MHz exceeds DDC maximum 140MHz
(WW) (1280x1024,CRT2 Monitor) mode clock 157.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 189MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 202.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,CRT2 Monitor) mode clock 229.5MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,CRT2 Monitor) mode clock 204.8MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,CRT2 Monitor) mode clock 261MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,CRT2 Monitor) mode clock 218.3MHz exceeds DDC maximum 140MHz
(WW) (1856x1392,CRT2 Monitor) mode clock 288MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 234MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 297MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 155.8MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,CRT2 Monitor) mode clock 184MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,CRT2 Monitor) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,CRT2 Monitor) mode clock 193.16MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,CRT2 Monitor) mode clock 230MHz exceeds DDC maximum 140MHz
(WW) (1920x1440,CRT2 Monitor) mode clock 341.35MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,CRT2 Monitor) mode clock 266.95MHz exceeds DDC maximum 140MHz
(WW) (2048x1536,CRT2 Monitor) mode clock 340.48MHz exceeds DDC maximum 140MHz
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
```X is warning you that those modes and sync rates are too high/low for the screen you have. Check your xorg.conf and be sure that your resolution and sync rates are within your monitor's/screen's requirements.

> **2hansen said:**
> and if I try to run glxinfo my system freezes - and a reboot is necessary.

Is this the way it "should be" the current state of Edgy and radeon drivers taken into consideration?

Please let me know if you have any suggestions or if I can help you test out new possible solutions.Uh... no, this isn't the way it should be. You shouldn't have a complete crash with glxinfo.

But, yes, I do have a new solution that I really need testing. I've gotten 3D Acelleration fully stable on my computer IF I run the 3D app in Failsafe Terminal. I am also working on a script that allows you to select a configuration right at startup. This configuration requires you do not have the word "quiet" in your grub boot list. (You can find this at the login screen, at the menu Options -> Session Types (or something like that) -> Failsafe Terminal.)

I'll PM you the instructions once I'm done making them. I guarantee you'll run into errors, but 99% chance I've already figured them out.


Thanks for volunteering right in the nick of time!!!

---

### Post by chortya on 2006-11-15
hm, I've also got complete freeze after ":~$ glxinfo | grep direct"
Thinkpad X22 ATI Mobility Radeon M6 LY.
What the best driver/options for 2D btw?

---

### Post by javaJake on 2006-11-15
> **chortya said:**
> hm, I've also got complete freeze after ":~$ glxinfo | grep direct"
Thinkpad X22 ATI Mobility Radeon M6 LY.
What the best driver/options for 2D btw?

I'm working on a new method that is much much more stable, so we'll give that a shot. The problem with complete freezes is that no logs are made, and I absolutely depend on logs to figure things out.

While you wait, try commenting out different options in xorg.conf that you think might be causing issues, and _reboot_ between each edit.

---

### Post by 2hansen on 2006-11-15
I experienced the total freezes too (see previous [post]("http://ubuntuforums.org/showpost.php?p=1739384&postcount=96")), but managed to find a  way to avoid them.

I stripped down the "Device" section of my xorg.conf to the minimum, and used trial and error until it worked. With the following configuration I am having no crashes/freezes (Unfortunately the 3D doesn't work in dual head mode, but that's another issue).

```
Section "Device"
	Identifier	"ATI 0"	
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"BusType" "PCI"
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
EndSection
```

I guess that one or more  of the options specified in the HOWTO in the beginning of this thread are the reason to the freezes, but I am still in the process of locating precisely which. I promise to be back, when I have found out more.

Hope it'll help you a bit further...

---

### Post by javaJake on 2006-11-15
Experimenting with different options will help for other users who come along and have the same issues. Please continue. Also, I'll be releasing some new instructions for beta testing very soon, so would you mind testing your configuration ideas on that as well, and see if it is more stable, and/or what options make the new instructions more stable?

Thanks! :)

---

### Post by chortya on 2006-11-16
> **2hansen said:**
> 

I stripped down the "Device" section of my xorg.conf to the minimum, and used trial and error until it worked. 
```
Section "Device"
	Identifier	"ATI 0"	
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"BusType" "PCI"
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
EndSection
```


cool! works now for me too. Getting following error when starting glxgears:
```
libGL warning: 3D driver claims to not support visual 0x4b
```
But don't think its really important... Will also try different combinations of options.

---

### Post by javaJake on 2006-11-16
The errors you are getting are not important at all. It simply means your card doesn't support different effects. If you look in your xorg.conf, you will most likely find at least 5 of these warnings.

Please continue to experiment. I will try out your ideas on my system as well, and see if it makes me any more stable or unstable, and edit the HOWTO accordingly. Thanks a lot for your support!

---

### Post by 2hansen on 2006-11-17
Ok, so now I have been trying out various combinations of the parameters in the "Device" section of the xorg.conf, and the following seems to produce the best results (for me):

```
Section "Device"
#Info from http://www.ubuntuforums.org/showthread.php?t=246746
#More info from http://www.die.net/doc/linux/man/man4/radeon.4.html
#Even more info from http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver#Using_Xinerama

#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]" #(too) long name
	Identifier	"ATI 0"	
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
#	Option		"XAANoOffscreenPixmaps" "off" #Accordingly to /var/log/Xorg.0.log not used
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"

#Uncomment to enable radeon specific xinerama
#	Option          "MergedFB" "true"
#	Option          "MergedNonRectangular" "true"
#	Option          "MetaModes" "1024x768-1280x960"
#	Option          "CRT2Position" "RightOf"
EndSection

```

Please note! I have left all my own comments and reminders in this cut-out - they might be wrong or misleading.

---

### Post by javaJake on 2006-11-19
I will try this myself, but could someone who's had glxinfo freezing
issues try this out as well? Be sure to remove the "Screen" Option - I promise I'll make a HOWTO on the subject of multiple screens for the M6 LY. Just a matter of time.


P.S. Sorry the new instructions are taking so long to develop. I just got a job, so my life has been a bit of a whirlwind re-organizing everything to my new schedule.

---

### Post by 2hansen on 2006-11-19
Congratulations with your new job!

As mentioned in [previous]("http://www.ubuntuforums.org/showpost.php?p=1739384&postcount=96") I had the glxinfo freezes, but with this [this config]("http://www.ubuntuforums.org/showpost.php?p=1770186&postcount=104") they seem to have gone - no matter the screen option.

---

### Post by javaJake on 2006-11-19
Thanks for the input! I'll definately include this at least in the Troublehsooting section, which WILL be referenced to everywhere to be sure people visit it.

BTW, the instructions are really really close to being done. Just a last few things to research and type in. I should be posting it sometime this week, if time allows.

---

### Post by wingnut_nz on 2006-11-25
Hi there,

I have a Sony Vaio PCG-C1MT, for which I am not able to get DRI to work as yet.

The chipset is an M6 wiht 8MB of video memory.
lspci | grep VGA
0000:00:0c.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I see the following error messages from the log.
cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux Vaio-PCG-C1MT 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) RADEON(0): Unknown DDCType 6 found
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:0:12:0"
	Option		"BusType" "PCI"
	Option		"AGPMode" "4"
	Option		"AGPSize" "32" # default: 8
	Option		"AGPFastWrite" "false" # More stable this way.
	Option		"SWcursor" "true" # More stable this way.
	Option		"EnablePageFlip" "true" # Faster.
	Option		"EnableDepthMoves" "false" # More stable this way.
	Option		"RenderAccel" "false" # More stable this way
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
	Option		"DDCMode"
	Option		"SubPixelOrder" "NONE"
	Option		"ColorTiling" "false" # More stable this way.
	Option		"DynamicClocks" "true"
	Option		"bioshotkeys"   "True"
	Option		"XAANoOffscreenPixmaps" "true" # More stable this way.
EndSection


I'd be keen to get this working. What other information could I provide to assist ?
Thanks in advance for your assistance, and great work on the documentation so far.

Cheers.
Mike.

---

### Post by javaJake on 2006-11-26
Can you give me a copy of syslog? I once had this issue before where it was actually something almost outside of X crashing that reported to syslog, not to Xorg.0.log.

I'll keep looking over the stuff you've posted now and see what I can figure out.

**Edit:** Yea, I'm getting "deja vu" looking at your logs. I had that situation once before... can't remember what went wrong. I'm pretty sure syslog will give me just the information I need to figure this out.

---

### Post by javaJake on 2006-11-26
The instructions below are no longer needed, and never were. If you followed them, you'll be fine - you only upgraded your drivers.

I've kept them here just in case anyone wants to use them, but they are still not fully tested, so be careful! I will answer any questions you may have about anything in these instructions.

[COLOR="Silver"][SIZE="3"]**_New Instructions - Beta Version - Testers Needed_**[/SIZE]
Please help me test out these instructions by following them below. Thanks!
Once you guys are done testing, and have worked out all the kinks, I'll paste this into the current HOWTO.

**_[SIZE="2"]All Users - Dapper and Edgy[/SIZE]_**
[indent]**Attention!** This section is not complete. I don't mean that it will crash your system. If you have the supported setup (Ubuntu, Xorg, and one of the cards in the "Cards that work with this HOWTO" section) then you shouldn't get any issues. What I mean by not complete is I don't remember what things you needed to fully complete this section. When (and I mean *when*) you run into an error, please post it. I've already gone through all the errors saying you are missing something, and should know what to do.

**I would really really appreciate if you help me get this section complete! We'll be making backups of everything that is overwritten, so if you need to you can revert anything here!**[/indent]

Well, it turns out that, even though Edgy is supposedly the latest, it isn't the latest in the X world. Very very recently (and I mean first week of November) they just completed a huge batch of bug fixes for the cards that this HOWTO deals with. In order to take advantage of this, however, we have to completely recompile drm, Mesa, and xf86-video-ati modules. (Basically, we recompile 3D Acelleration modules, and the ati/radeon drivers.) The drivers have been much more stable for me then the ones included in Edgy.

We'll be using stuff from Edgy (again) so...

```

sudo apt-get install nano
sudo nano /etc/apt/sources.list

```

Now replace any mention of "dapper" with "edgy", except for the cdrom entry, and remove any single "#". (It's OK if you replace that too... we'll be changing it back later.) Now run the following:

```

sudo apt-get update

```

We need to install different things before we begin:
```
sudo apt-get install cvs git-core autoconf automake1.9
sudo apt-get build-dep xserver-xorg-video-ati libgl1-mesa-dri
```

Once that's done, complete the following commands, which download the modules into a new directory...
```

mkdir ~/3DModules_source
cd ~/3DModules_source
mkdir ~/backups_drm/
mkdir ~/backups_Mesa/
mkdir ~/backups_drv/
git clone git://anongit.freedesktop.org/git/mesa/drm 
git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-ati
cvs -d:pserver:anonymous@anoncvs.freedesktop.org:/cvs/mesa login
cvs -z3 -d:pserver:anonymous@anoncvs.freedesktop.org:/cvs/mesa co Mesa

```


First, we have to build DRM, since Mesa and the ati drivers depend on it. To build DRM, run:
```

cd ~/3DModules_source/drm
./autogen.sh
./configure --prefix=/usr --exec-prefix=/

```
_Note:_ If you get errors here, STOP! You won't get any farther. See the Troubleshooting section at the bottom of this HOWTO. (You can safely ignore all warnings.)

We should back up your existing drivers just in case this doesn't work.
```

cd ~/backups_drm/
cp /usr/lib/libdrm.* ~/backups_drm/
cp /usr/include/xf86drm.h ~/backups_drm/
cp /usr/include/xf86mm.h ~/backups_drm/ *(I couldn't find this on my system - ignore if you can't)*
mkdir ~/backups_drm/drm
cp /usr/include/drm/* ~/backups_drm/drm
cp /usr/lib/pkgconfig/libdrm.pc ~/backups_drm/drm

```

Now for the big leap...
```

cd ~/3DModules_source/drm
make install

```
_Note:_ If you get errors here, STOP! You won't get any farther. See the Troubleshooting section at the bottom of this HOWTO. (You can safely ignore all warnings.)

Alrighty, we can build our drivers now. Because we are overwriting drivers you are currently using, X will crash if it is still running. Print out these instructions (click here for a printable view). Log out so that you go back to Ubuntu's login screen, and punch Ctrl+Alt+F1, and login there. Run the following commands to shut X down safely:
```

sudo /etc/init.d/gdm stop
sudo killall gdm

```

Now run the following:
```

cd ~/3DModules_source/xf86-video-ati
./autogen.sh
./configure --prefix=/usr --exec-prefix=/

```
_Note:_ If you get errors here, STOP! You won't get any farther. See the Troubleshooting section at the bottom of this HOWTO. (You can safely ignore all warnings.)

Let's backup our existing drivers. To do so, run the following commands:
```

cd ~/backups_drv/
cp -R /lib/xorg/modules/* ./

```

Now you can install the drivers. Run the following commands to do so:
```

cd ~/3DModules_source/xf86-video-ati
make
sudo make install

```
_Note:_ If you get errors here, STOP! You won't get any farther. See the Troubleshooting section at the bottom of this HOWTO. (You can safely ignore all warnings.)

Restart your computer to see if the new drivers work. If you at least get to the login screen, congrats. If not, please do not continue, and see the Troubleshooting section at the bottom.

OK, now that we've got the latest DRM and ati drivers installed, we need the latest Mesa installed. Run the following:
```

cd ~/3DModules_source/Mesa
make

```
You'll get a nice long list of different platforms you can compile for. If you don't know which one to use, "linux-dri" is a generally safe option. For any Pentium (anything Intel) users, you'll want "linux-dri-x86". Replace "<whatToCompile>" with the "linux-dri" thing you just figured out.
```

make <whatToCompile>

```
Most users can run this if you don't know:
```

make linux-dri

```
You can safely ignore all warnings presented. If you get an error, please please please let me know about it.

OK, so now you've got some dandy Mesa stuff. Let's back up our existing drivers just in case.
```

mkdir ~/backups_drm/GL
cp /usr/include/GL/* ~/backups_drm/GL
mkdir ~/backups_drm/dri
cp /usr/X11R6/lib/modules/dri/* ~/backups_drm/dri
cp /usr/lib/libGLU.* ~/backups_drm/
cp /usr/lib/libglut* ~/backups_drm/
cp /usr/lib/libGLw.* ~/backups_drm/

```

Now we need to install Mesa. Run the following commands to do so:
```

make install

```
_Note:_ If you get errors here, STOP! You won't get any farther. See the Troubleshooting section at the bottom of this HOWTO. (You can safely ignore all warnings.)


You are done compiling in new 3D drivers. Restart your computer, and try them out. If games still run slowly, or you get other issues, please see the Troubleshooting section at the bottom of this HOWTO.[/COLOR]

---

### Post by javaJake on 2006-11-26
> **2hansen said:**
> Ok, so now I have been trying out various combinations of the parameters in the "Device" section of the xorg.conf, and the following seems to produce the best results (for me)

*<snip>*

Please note! I have left all my own comments and reminders in this cut-out - they might be wrong or misleading.

Alright, now that I have the new instructions posted, I'll try out your configuration, and add it to the Troubleshooting section at the least. At the most, your config will replace mine in the entire HOWTO. 8)

---

### Post by wingnut_nz on 2006-11-27
> **javaJake said:**
> Can you give me a copy of syslog? I once had this issue before where it was actually something almost outside of X crashing that reported to syslog, not to Xorg.0.log.

I'll keep looking over the stuff you've posted now and see what I can figure out.

**Edit:** Yea, I'm getting "deja vu" looking at your logs. I had that situation once before... can't remember what went wrong. I'm pretty sure syslog will give me just the information I need to figure this out.

Cool, thanks for your help.
Unfortunately  the syslog is clean,
Nov 27 22:45:37 Vaio-PCG-C1MT syslogd 1.4.1#17ubuntu7: restart.
Nov 27 22:45:37 Vaio-PCG-C1MT anacron[4663]: Job `cron.daily' terminated
Nov 27 22:45:37 Vaio-PCG-C1MT anacron[4663]: Normal exit (1 job run)
syslog (END)

I have attached the kern.log and the dmesg in case they are of any use.

Cheers,
Mike

---

### Post by 2hansen on 2006-11-28
Hi! Always willing to help I tried out your instructions, but didn't get far:

after ```
./autogen.sh
``` I receive ```
./autogen.sh: 9: autoreconf: not found
``` and nothing further happens.

btw. With the previously mentioned configuration I am able to run XGL and Beryl - not as fast as wanted, but I assume the card has it's limits. I followed [this guide]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") to enable XGL and Beryl.

---

### Post by javaJake on 2006-11-29
> **wingnut_nz said:**
> Cool, thanks for your help.
Unfortunately  the syslog is clean,
Nov 27 22:45:37 Vaio-PCG-C1MT syslogd 1.4.1#17ubuntu7: restart.
Nov 27 22:45:37 Vaio-PCG-C1MT anacron[4663]: Job `cron.daily' terminated
Nov 27 22:45:37 Vaio-PCG-C1MT anacron[4663]: Normal exit (1 job run)
syslog (END)

I have attached the kern.log and the dmesg in case they are of any use.

Cheers,
Mike

Can you attach the entire Xorg.0.log file? Please note that you must make a copy of the log when you see the login screen with your 3D configuration, and not after you reboot! Otherwise Xorg.0.log gets replaced with a new one.

---

### Post by wingnut_nz on 2006-12-01
> **javaJake said:**
> Can you attach the entire Xorg.0.log file? Please note that you must make a copy of the log when you see the login screen with your 3D configuration, and not after you reboot! Otherwise Xorg.0.log gets replaced with a new one.

Cool, thanks for your help. Attached is a copy of the Xorg.0.log file.
Mike

---

### Post by javaJake on 2006-12-02
**_[SIZE="2"]ATTENTION All Edgy Users!!![/SIZE]_**
I just tried reinstalling on my new hard drive, and my 3D works beautifully without any modification to the drivers themselves! If your card is stable right now with all games, please do not try my instructions!

---

### Post by javaJake on 2006-12-02
> **2hansen said:**
> Ok, so now I have been trying out various combinations of the parameters in the "Device" section of the xorg.conf, and the following seems to produce the best results (for me):

```
Section "Device"
#Info from http://www.ubuntuforums.org/showthread.php?t=246746
#More info from http://www.die.net/doc/linux/man/man4/radeon.4.html
#Even more info from http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver#Using_Xinerama

#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]" #(too) long name
	Identifier	"ATI 0"	
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
#	Option		"XAANoOffscreenPixmaps" "off" #Accordingly to /var/log/Xorg.0.log not used
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"

#Uncomment to enable radeon specific xinerama
#	Option          "MergedFB" "true"
#	Option          "MergedNonRectangular" "true"
#	Option          "MetaModes" "1024x768-1280x960"
#	Option          "CRT2Position" "RightOf"
EndSection

```

Please note! I have left all my own comments and reminders in this cut-out - they might be wrong or misleading.

Hey, I think your xorg.conf is what's making this so stable! I didn't realize until after I made the above announcement!

---

### Post by javaJake on 2006-12-02
> **2hansen said:**
> Hi! Always willing to help I tried out your instructions, but didn't get far:

after ```
./autogen.sh
``` I receive ```
./autogen.sh: 9: autoreconf: not found
``` and nothing further happens.

btw. With the previously mentioned configuration I am able to run XGL and Beryl - not as fast as wanted, but I assume the card has it's limits. I followed [this guide]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") to enable XGL and Beryl.

After further research, I found out that this error is because I forgot to ask you guys to install some stuff. Run the following commands to install the missing whatnot:

```

sudo apt-get install git-core autoconf automake1.9
sudo apt-get build-dep xserver-xorg-video-ati libgl1-mesa-dri

```

Thanks for being so patient. My time's being zapped horribly.

**Edit:** I've updated the beta instructions above.
**Another Edit:** You also need to install libgl1-mesa-dri's dependancies as well... I added this in my post and beta instructions.

---

### Post by casano on 2006-12-05
I have a thinkpad x23, with the ATI Mobility Radeon M6 LY (9000),
with edgy installed, and I have been trying out your suggestions,
but so far with no luck.

I have come to a point where glxinfo, glxgears freezes the machine.

I noticed you now get it working on a clean install,
is it possible you can write up a guide, how to get
3D working from a clean install, I'm sure it will
help a lot.

Thanks for working on this.

---

### Post by wk2001 on 2006-12-07
> **casano said:**
> I have a thinkpad x23, with the ATI Mobility Radeon M6 LY (9000),
with edgy installed, and I have been trying out your suggestions,
but so far with no luck.

I have come to a point where glxinfo, glxgears freezes the machine.

I noticed you now get it working on a clean install,
is it possible you can write up a guide, how to get
3D working from a clean install, I'm sure it will
help a lot.

Thanks for working on this.

On a clean install of edgy the radeon driver is activated as default! You have nothing to do to get direct rendering and 3d working! I have also an ati mobility radeon m9 (9200, but same as chip as 9000) in my HP nx7000. Berylworks now perfectly!

---

### Post by javaJake on 2006-12-07
> **wk2001 said:**
> On a clean install of edgy the radeon driver is activated as default! You have nothing to do to get direct rendering and 3d working! I have also an ati mobility radeon m9 (9200, but same as chip as 9000) in my HP nx7000. Berylworks now perfectly!

Unfortunately this is not true. Most M6 LY cards don't have enough memory to support the default 3D settings, mainly because 24 bit depth is too high. Also, all M6 LY cards crash within the hour without the correct options and updated drivers. This HOWTO wouldn't exist if it weren't for that.

---

### Post by javaJake on 2006-12-07
> **casano said:**
> I have a thinkpad x23, with the ATI Mobility Radeon M6 LY (9000),
with edgy installed, and I have been trying out your suggestions,
but so far with no luck.

I have come to a point where glxinfo, glxgears freezes the machine.

I noticed you now get it working on a clean install,
is it possible you can write up a guide, how to get
3D working from a clean install, I'm sure it will
help a lot.

Thanks for working on this.

The guide does help you get started from a clean install. In fact, it is encouraged to use a clean install!

Your problem came up earlier in this thread, and was solved someway which is also mentioend. My time's been crushed lately (thus slow replies) but never fear - I will get to you eventually and help you out. Probably Saturday.

Thanks for the patience!

---

### Post by javaJake on 2006-12-07
**_WARNING - Attention All Potential Beryl Users!_**
**Do NOT install fglrx! Do NOT install it!** You cannot rid your system of it once installed! I've tried everything, but a complete reinstallation of Ubuntu was necessary for me! Some users have reported being able to get it to work. (If anyone knows how to rid yourself of fglrx's junk, let me know.)

Fglrx just plain messes with Beryl, so **if you are going to install Beryl, use the instructions for "AiGLX", NOT "XGL"**! I will get around to making a section on Beryl soon, since this card doesn't like Beryl to start (like 3D).  *Rolls eyes*

---

### Post by javaJake on 2006-12-09
**_New "Better" Instructions Cancelled_**
I've found that the whole cause of my Edgy issues with this card has been because of a bad installation. Sorry for the trouble I've caused anyone. It turns out you do not need to install anything at all on Edgy, but merely configure your xorg.conf.

The HOWTO will be updated accordingly. Thanks for the support everyone!

---

### Post by javaJake on 2006-12-09
> **2hansen said:**
> Ok, so now I have been trying out various combinations of the parameters in the "Device" section of the xorg.conf, and the following seems to produce the best results (for me):

```
Section "Device"
#Info from http://www.ubuntuforums.org/showthread.php?t=246746
#More info from http://www.die.net/doc/linux/man/man4/radeon.4.html
#Even more info from http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver#Using_Xinerama

#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]" #(too) long name
	Identifier	"ATI 0"	
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
#	Option		"XAANoOffscreenPixmaps" "off" #Accordingly to /var/log/Xorg.0.log not used
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"

#Uncomment to enable radeon specific xinerama
#	Option          "MergedFB" "true"
#	Option          "MergedNonRectangular" "true"
#	Option          "MetaModes" "1024x768-1280x960"
#	Option          "CRT2Position" "RightOf"
EndSection

```

Please note! I have left all my own comments and reminders in this cut-out - they might be wrong or misleading.

Your xorg.conf has replaced mine in the HOWTO, since it works much much better, and has much much better comments.

I've removed the Xinerama support for right now - I'll be posting an Xinerama section for this HOWTO soon, along with the MergedFB and Beryl sections. (Stay tuned. :) )

---

### Post by javaJake on 2006-12-09
**_Beryl, MergedFB, and Xinerama Support Have Been Added_**

Enjoy, and send me some feedback if anything goes awry! :D

---

### Post by csk on 2006-12-09
hi all. this is a great guide but i still cant seem to get mine to work.
Here is my /etc/X11/xorg.conf 

"
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load 	"GLcore"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#	Option		"UseFBDev"		"true"
#EndSection



Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection








Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	#SubSection "Display"
	#	Depth		24
	#	Modes		"1400x1050"
	#EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
"

and my /etc/X11/Xorg.0.log is empty. can anyone please help? 

cheers

---

### Post by wingnut_nz on 2006-12-10
> **wingnut_nz said:**
> Cool, thanks for your help. Attached is a copy of the Xorg.0.log file.
Mike

DRI now works !
I decided to do a fresh install of Edgy. I setup my xorg.conf as detailed in the documents, with the only exception being that I set the default colour depth to 16, not 24 as I needed more memory to run my desired resolution.

Only test so far has been to run glxgears for an hour with no problems. I'll do some other tests and post results later.
So far so good. 

Thanks to javaJake and all those who have helped contribute.

---

### Post by wingnut_nz on 2006-12-11
> **javaJake said:**
> **_WARNING - Attention All Potential Beryl Users!_**
**Do NOT install fglrx! Do NOT install it!** You cannot rid your system of it once installed! I've tried everything, but a complete reinstallation of Ubuntu was necessary! (If anyone knows how to rid yourself of fglrx's junk, let me know.)

Fglrx just plain messes with Beryl, so **if you are going to install Beryl, use the instructions for "AiGLX", NOT "XGL"**! I will get around to making a section on Beryl soon, since this card doesn't like Beryl to start (like 3D).  *Rolls eyes*

Has a matter of interest, did you successfully get the fglrx drivers to run on the M6 LY, on an install without Beryl ? If you did was there any noticable performance gain using this driver?
Cheers,
Mike.

---

### Post by msak007 on 2006-12-11
> **wingnut_nz said:**
> Has a matter of interest, did you successfully get the fglrx drivers to run on the M6 LY, on an install without Beryl ? If you did was there any noticable performance gain using this driver?
Cheers,
Mike.
I could be mistaken, but I don't believe that the fglrx driver even supports this card. I attempted to install it once before I knew that and didn't get very far. 3D acceleration was working out of the box on 2 different laptops (with a Mobility M6 LY) I installed Kubuntu on. Neither required any tweaking, and I installed Beryl on one of them. It runs OK, but you can't expect a card with 8 MB of video memory to be smooth with all the fancy animations and it does a lot better than I expected.

---

### Post by wingnut_nz on 2006-12-12
> **msak007 said:**
> I could be mistaken, but I don't believe that the fglrx driver even supports this card. I attempted to install it once before I knew that and didn't get very far. 3D acceleration was working out of the box on 2 different laptops (with a Mobility M6 LY) I installed Kubuntu on. Neither required any tweaking, and I installed Beryl on one of them. It runs OK, but you can't expect a card with 8 MB of video memory to be smooth with all the fancy animations and it does a lot better than I expected.

Thanks for that. Yes, I was unsucessful with fglrx drivers as well. I was not sure at the time when I had a go, if the driver did support mobility or not. Rechecking the AMD site now, it certainly seems that it does not.
Thanks for your help.
Mike.

---

### Post by javaJake on 2006-12-14
> **wingnut_nz said:**
> Has a matter of interest, did you successfully get the fglrx drivers to run on the M6 LY, on an install without Beryl ? If you did was there any noticable performance gain using this driver?
Cheers,
Mike.

fglrx is an nVidia driver. The Radeon M6 LY card mentioned here is an ATI card, so installing fglrx in the first place is way off the mark.

But the real reason I posted that announcement was because the drivers *will* mess up your system to the point where Beryl won't work. The only known fix is a complete reinstallation, so therefore **do not install fglrx no matter what**. :)

---

### Post by javaJake on 2006-12-14
> **msak007 said:**
> \3D acceleration was working out of the box on 2 different laptops (with a Mobility M6 LY) I installed Kubuntu on. Neither required any tweaking, and I installed Beryl on one of them. It runs OK, but you can't expect a card with 8 MB of video memory to be smooth with all the fancy animations and it does a lot better than I expected.

Can you send me the xorg.conf from those two machines? It may be that Kubuntu automatically sets the depth to 16, which is all that is necessary for 3D to work at the bare minimum.

---

### Post by 2hansen on 2006-12-14
> **javaJake said:**
> fglrx is an nVidia driver. The Radeon M6 LY card mentioned here is an ATI card, so installing fglrx in the first place is way off the mark.

Sorry, but the fglrx is an ATI driver - it is the "ATI Proprietary Linux Driver". But unfortunately it does not support the M6 LY - and probably [never will]("http://ati.amd.com/products/catalyst/linux.html#2").

---

### Post by 2hansen on 2006-12-14
Btw. I can't get Beryl to work with AIGLX, but would be happy know if someone else with an M6 LY has?

As mentioned in a previous post, I had it working with XGL - but (I don't know much about this) that the "default" AIGLX would be preferable?

---

### Post by msak007 on 2006-12-14
Yes fglrx is the proprietary ATI driver, but it does not support all the ATI cards and recently dropped support for some older cards that are supported by the open source radeon driver.
 
**2hansen**: I got Beryl working in Edgy with AIGLX and yes, it is preferred over XGL.

---

### Post by 2hansen on 2006-12-15
Just a short comment on the HOWTO's optional mergedfb section.

My M6 LY has 16MB and I have no trouble using a dual screen setup with 1024x768 (laptop screen) and 1280x960 (external LCD) simultaneously.

But with these settings the 3D does not work, since dual screen is not supported by the driver - however I just have two different xorg.conf's and switch whenever necessary (e.g. for work: dual screen, for Google Earth: single screen and 3D).

This is just to avoid discouraging someone from using mergedfb, as the current HOWTO's wording suggests that only 2 x 800x600 is possible.

---

### Post by 2hansen on 2006-12-15
And to **msak007**: Are you using the M6 LY with the radeon driver for running Beryl?

If so I would really appreciate your guidance to make it work for me as well.

With my current settings (followed the guide pointed to by this HOWTO) whenever I try the ```
beryl
``` commando, my X just restarts.

My Xorg.0.log says:

```
(**) Option "AIGLX" "true"
(**) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so

```

so I assume that AIGLX is working?

However, in my syslog I have 

```
Dec 15 09:23:02 localhost gconfd (bo-4820): Received signal 15, shutting down cleanly
Dec 15 09:23:02 localhost gconfd (bo-4820): Exiting
Dec 15 09:23:03 localhost gdm[4745]: Error reinitilizing server
Dec 15 09:23:05 localhost kernel: [17179862.444000] mtrr: 0xf0000000,0x8000000 overlaps existing 0xf0000000,0x1000000
Dec 15 09:23:05 localhost last message repeated 2 times
Dec 15 09:23:05 localhost kernel: [17179863.036000] [drm] Setting GART location based on new memory map
Dec 15 09:23:05 localhost kernel: [17179863.036000] [drm] writeback test succeeded in 1 usecs
```

And as mentioned my X just quits and restarts?

---

### Post by javaJake on 2006-12-15
> **2hansen said:**
> With my current settings (followed the guide pointed to by this HOWTO) whenever I try the ```
beryl
``` commando, my X just restarts.

If Beryl crashes, it doesn't save its output to a log. In order to catch this output, please do the following:
[list=1][*]Push Ctrl+Alt+F1.[*]Log in to your normal username.[*]Run: ```
DISPLAY=:0 beryl-manager
```[/list]

BTW, you really want to run beryl-manager, not beryl, so you get the Beryl icon in your notification area.

---

### Post by 2hansen on 2006-12-18
Thank you for your reply.

When I ```
alt+f1
DISPLAY=:0 beryl-manager
``` nothing happens until I ```
alt+f7
```. Then X crashes (I just have the time to see the beryl-manager's gem in the notification area).

The output on tty1 is this:

```
:~$ DISPLAY=:0
:~$ libGl warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGl warning: 3D driver claims to not support visual 0x4b
beryl-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
emerald: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
X connection to :0.0 broken (explicit kill or server shutdown).
The application 'emerald' lost its connection to the display :0.0; most likely the X server was shutdown or you killed/destroyed the application.
:~$
```

---

### Post by 2hansen on 2006-12-19
And after X restarts I can view the differences between Xorg.0.log.old and Xorg.0.log:

> Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fe6c8)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xffff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Ok, leaving now...
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(**) RADEON(0): RADEONEnterVT
(**) RADEON(0): RADEONModeInit()
1024x768       65.00  1024 1040 1176 1344   768  771  777  806 (24,32)
1024x768       65.00  1024 1040 1176 1344   768  771  777  806 (24,32)
(**) RADEON(0): Pitch = 8388736 bytes (virtualX = 1024, displayWidth = 1024)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81ff078
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff078)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xf3fff000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 200a5c5c to 20115c5c
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONSaveScreen(2)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libGLcore.so(_tnl_install_pipeline+0x5d) [0xb7b5d6ed]
3: /usr/lib/dri/radeon_dri.so(radeonCreateContext+0x4de) [0xb451a57e]
4: /usr/lib/dri/radeon_dri.so [0xb4516263]
5: /usr/lib/xorg/modules/extensions/libglx.so [0xb7ca7e2e]
6: /usr/lib/xorg/modules/extensions/libglx.so(DoCreateContext+0x10e) [0xb7c8247e]
7: /usr/lib/xorg/modules/extensions/libglx.so(__glXCreateContext+0x44) [0xb7c82c74]
8: /usr/lib/xorg/modules/extensions/libglx.so [0xb7c8530a]
9: /usr/X11R6/bin/X(Dispatch+0x18f) [0x808693f]
10: /usr/X11R6/bin/X(main+0x485) [0x806e715]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dc38cc]
12: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fe6c8)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xffff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Ok, leaving now...

---

### Post by javaJake on 2006-12-21
OK, sounds like what I had. Install the attached .deb files, then let the Update Manager update you.

**Edit**: DARN DARN DARN! I deleted the .deb files!!! DRAT!
Well, the last resort is Google. The fact that you and I had the same issue says something, doesn't it? :)

**Another Edit:** Thank GOODNESS for cache! I grabbed what I think may be the .deb files I was talking about above, and uploaded them here:
[http://expandapps.org/beryl-0.1.2.tar.bz2](http://expandapps.org/beryl-0.1.2.tar.bz2)

Tell me if it works out.

---

### Post by 2hansen on 2006-12-23
Thanks for the link, but the deb's contained there are version 0.1.2 and the ones I have installed (from [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) repo's) are version 0.1.3 - isn't it better with the latter - viz. highest version number?

---

### Post by javaJake on 2006-12-24
> **2hansen said:**
> Thanks for the link, but the deb's contained there are version 0.1.2 and the ones I have installed (from [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) repo's) are version 0.1.3 - isn't it better with the latter - viz. highest version number?

I know it is strange, but those debs made things work. Remove the current version you have, and all its stuff, then install these. After that you should be able to upgrade without issues.

---

### Post by medix on 2006-12-25
I'd like to add to the list that this howto worked for the ATI Radeon Mobility IGP320M (U1) running Edgy on an eMachines m5310. It seems that most of the howto was already configured for the card when Edgy was installed! I had to add a few things and change from the default 'ati' driver to 'radeon'. The other thing to note is that I compiled and installed libdrm-2.3.0 (I'm assuming this is the latest version) while trying to figure out how to make the mesa3d drivers work. I hadn't realized that they were already installed/included, however Xorg.0.log shows that the compiled module was loaded without any errors. 

glxgears runs very smoothly! 

I can post my xorg.conf and Xorg.0.log if anyone so wishes.

Thanks again,
  - Medix 8)

---

### Post by javaJake on 2006-12-26
> **medix said:**
> I'd like to add to the list that this howto worked for the ATI Radeon Mobility IGP320M (U1) running Edgy on an eMachines m5310.

I have a few questions, just to see if this card should go in the "Cards that Work with this HOWTO" list:

[list][*]Did you try other HOWTOs, and they didn't help resolve crashing? In other words, is this the only HOWTO that will work for you?[*]Did you have to do anything this HOWTO to get your card to work?[/list]

---

### Post by medix on 2006-12-28
> **javaJake said:**
> I have a few questions, just to see if this card should go in the "Cards that Work with this HOWTO" list:

[list][*]Did you try other HOWTOs, and they didn't help resolve crashing? In other words, is this the only HOWTO that will work for you?[*]Did you have to do anything this HOWTO to get your card to work?[/list]


Ah, I seem to have missed the point.. 

I apologize. I had spent several hours trying to sift through all of the information available for ATI cards. There is alot of information on the proprietary fglrx driver, however I wasn't able to determine (or got impatient with the ambiguity of the documentation) whether or not this driver would work with my particular card. The IGP320M is somewhat older, and most of the HOWTO's and guides seemed to be for newer higher-end cards. 

I chose this one since it seemed to be clear and concise and required the *least* amount of major modifications to my system (I prefer to do it RIGHT the first time ;) ).

For the most part, basic 3D hardware support was already working when I installed Edgy 6.10 (possibly due to the older, and possibly well-tested hardware?). I added only a few lines..

Under the section "Module"
Added:     Load, "GLcore"

Under section "Device"
Changed driver from "ati" to "radeon"

also added:
#Optimized values (changed from driver default)
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "on" #Faster than default (off)
        Option          "SWcursor" "off" #Faster than default (on)
        Option          "EnablePageFlip" "on" #Faster than default (off)
        Option          "AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
        Option          "DynamicClocks" "on"
        Option          "BIOSHotkeys"   "on"
#These are not mentioned in man page for driver
        Option          "AGPSize" "32" # default: 8
        Option          "EnableDepthMoves" "true"

After making these changes, there was no noticeable change in hardware performance (at least when running glxgears), however I did notice that the processor on my laptop was maxed out continuously and the machine was running quite hot. I'm guessing that the above values are not the optimized settings for this card. Since I haven't had too much time (or ambition) due to the holidays, I haven't investigated this further and switched back to my original xorg.conf. 

Hopefully this helps.. 

I should also note that I did not have any prior problems with the system crashing or freezing.. the video on this machine has been one of the most reliable and stable parts of the hardware (I've had more problems with the faulty cooling system.. if you own a m53xx series and it hasn't happened yet, beware.. you're in for a long haul.. )

Thanks for the effort even though this wasn't quite the response you were expecting.. 

- Medix :cool:

---

### Post by javaJake on 2006-12-30
No, it wasn't quite the response, but hey, I got the answers I was looking for. :)

Since this HOWTO does not support your card, I will not be adding your mods or instructions.

---

### Post by TheJackofClubs on 2007-01-03
i dont know if this is actually working or not because the only reason im following this how to is to get beryl on my laptop. its an dell c610 laptop with a 16mb ati radeon mobility m6 ly that runs at 1400x1050 (surprisingly high). i followed this guide and the edgy aiglx beryl guide at [http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX) . i was fine up until i ran beryl-manager and xserver crashed. im posting the xorg configuration file and log on my server if some one has a free chance to look at them and see if i messed something up or if its just not going to work. thanks.

[http://www.thejackofclubs.net/crapile/ati/xorg.conf](http://www.thejackofclubs.net/crapile/ati/xorg.conf) (/etc/X11/xorg.conf)
[http://www.thejackofclubs.net/crapile/ati/Xorg.0.log](http://www.thejackofclubs.net/crapile/ati/Xorg.0.log) (/var/log/Xorg.0.log)

edit:: i installed google earth and i know i dont have 3d accelleration. somethings wrong but i dont know what.

---

### Post by songochain on 2007-01-03
Hi, i'm trying to run beryl+aiglx with a radeon mobility 9700 but i cant. Beryl+xgl works fine but i get a slow performance...
I've installed all i need (i guest): xserver-xorg-driver-ati, beryl, xorg modified... but it doesnt work :( Also, if i use ati module on section device, laptop fan sets to 100% (fix??)
Here's my xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
	Option	"AIGLX"	"true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"

# This two lines are (presumably) needed to prevent fonts from being scrambled
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
	#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

Thanks!

---

### Post by javaJake on 2007-01-05
> **songochain said:**
> Hi, i'm trying to run beryl+aiglx with a radeon mobility 9700 but i cant. Beryl+xgl works fine but i get a slow performance...
I've installed all i need (i guest): xserver-xorg-driver-ati, beryl, xorg modified... but it doesnt work :( Also, if i use ati module on section device, laptop fan sets to 100% (fix??)

I'm sorry, but I really don't know a thing about your card. What I'd say you need to do is look for others who've also tried to get this working. Search these forums first, possibly with the words "radeon 9700 beryl" (without quotes) and then try Google. Your card seems to be rather popular - I got two or three requests for help here with that same card.

---

### Post by songochain on 2007-01-06
Thanks dude, i understand :P
But, may be u can resolve this problem:
```
link@ximian64:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

```

Any idea?
Thanks

---

### Post by javaJake on 2007-01-07
Well, a quick Google brings this up. Don't know if you've read it already.
[http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00227.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00227.html)

Click on the links under "Follow-ups" to keep following the discussion. They eventually get an answer, but they seem to know what they are doing. Try each thing they try to see if any of it works.

Essentially, this error probably means your fglrx and/or libGL drivers are messed up. I assume you've used a different HOWTO from before that's done this.

---

### Post by spaceghoti on 2007-01-10
After applying the latest update to wine and the fglrx kernel, all of a sudden I've lost my 3D acceleration.  I am running an IBM T42 with an ATI RV350 NP [Mobility Radeon 9600/9700 M10/M11] card.  To get 3D acceleration working before I had to apply the fglrx driver through the Kubuntu repositories and have been working for the past few weeks.  I have now tried your HOWTO and didn't crash or return any errors, with the following exceptions:

```
kurgan@Snoopy:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
kurgan@Snoopy:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: DRI module not loaded
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
kurgan@Snoopy:~$ glxgears &
[1] 4887
kurgan@Snoopy:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X connection to :0.0 broken (explicit kill or server shutdown).

[1]+  Exit 1                  glxgears
```

My xorg.conf is now as follows:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "Files"

  # path to defoma fonts
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "dbe"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
  Identifier "stylus"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
  Identifier "eraser"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
  Identifier "cursor"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  VendorName "Generic"
  ModelName "Flat Panel 1280x1024"
  HorizSync 31.5 - 90.0
  VertRefresh 60.0 - 60.0
  Gamma 1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
EndSection

Section "Monitor"
  identifier "monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Monitor"
  identifier "aticonfig-Monitor[0]"
  vendorname "IBM"
  modelname "IBM 9514-B TFT Panel"
  HorizSync 48.0-65.0
  VertRefresh 60.0-75.0
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Device"
  Identifier "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
  Driver "radeon"
  BoardName "radeon"
  option "MergedFB" "off"
  option "AGPMode" "4"
  option "AGPFastWrite" "on"
  option "SWcursor" "off"
  option "EnablePageFlip" "on"
  option "AccelMethod" "EXA"
  option "DynamicClocks" "on"
  option "BIOSHotkeys" "on"
  option "EnableDepthMoves" "true"
  BusID "PCI:1:0:0"
EndSection

Section "Device"
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "fglrx"
  screen 1
EndSection

Section "Device"
  identifier "aticonfig-Device[0]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "fglrx"
  screen 0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    Virtual 1920 1440
    Depth 24
    Modes "1280x1024@60" "1600x1200@60" "1024x768@60" "1792x1344@60" "800x600@60" "1856x1392@60" "640x480@60" "1920x1440@60"
  EndSubSection
EndSection

Section "Screen"
  #
  Identifier "screen1"
  Device "device1"
  Monitor "monitor1"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "640x480@60"
  EndSubSection
EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]"
  Device "aticonfig-Device[0]"
  Monitor "aticonfig-Monitor[0]"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@72"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "false"
EndSection

Section "ServerFlags"
EndSection
```

Any help would be appreciated.

Also found this:

```
tail -1000 /var/log/Xorg.0.log | grep EE
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(EE) AIGLX: Screen 0 is not DRI capable
```

So...um...it seems the latest fglrx update made the kernel module incompatible.  Unfortunately, I'm stumped for thoughts on how to fix it.

---

### Post by spaceghoti on 2007-01-11
Fixed!  Apparently, the apt-get update installed a new copy of the fglrx driver within /lib/modules, and the two versions conflicted.  Per [http://www.thinkwiki.org/wiki/Problems_with_fglrx#Known_Troubles_and_Solutions](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Known_Troubles_and_Solutions) I searched for them and deleted the version with the older timestamp.  Then I ran sudo depmod and rebooted.  Hardware acceleration is restored.

---

### Post by javaJake on 2007-01-12
That's great! I'll post this under the Troubleshooting section later. :)

---

### Post by astronafft on 2007-01-13
Worked for me with no problem, ATI Mobility Radeon M22 X300

thanks for this howto, i can finally try Beryl

regards

---

### Post by legine on 2007-01-15
Hello all,

Sure that the downgradeing from Dapper to edgy is still necessary?

I did the First Part and encoutered no Problems whatso ever on my Inspiron 4100 with a ATI mobility  Radeon M6 LY graphiccard. I will see later when I try some games with real 3D needs.

For Beryl:
> Option  "XAANoOffscreenPixmaps"

Does not realy fit to the Option:
> Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult

Or doesnt this matter and they just look similar on first glance.

Cheers
Legine

---

### Post by javaJake on 2007-01-15
> **legine said:**
> Hello all,

Sure that the downgradeing from Dapper to edgy is still necessary?

I did the First Part and encoutered no Problems whatso ever on my Inspiron 4100 with a ATI mobility  Radeon M6 LY graphiccard. I will see later when I try some games with real 3D needs.The thing is with the old Dapper drivers, those games crash a lot more then Edgy ones. I'd be suprised if you had no issues.

And you are right about that XAANoOffscreenPixmaps option - it doesn't affect anything.

---

### Post by legine on 2007-01-17
Then be surprised.
I realy had no Issues yet :)
Well the only graphic Issue is that I had to reduce my resolution from 1400x1200 to 1024x786 in order to have X accept the 24 bit mode. Exept to that and the Memory / swaping problem (only have 125 MB RAM :( ) the Laptop is fighting with, everything runs fine. I still have to test Massive 3d usage thought. Just tried one Game with wine yet. And that had not a playable performance for my box. simply not enough RAM.

I try to install Beryl and see if that leads to any Problems. :cool: 

I keep you informed :)

---

### Post by 2hansen on 2007-01-17
Sorry to get back so late, but I've been away for while. My [problems]("http://www.ubuntuforums.org/showpost.php?p=1901114&postcount=140") with Beryl seems to have gone now with aid from this [forum]("http://forum.beryl-project.org/viewtopic.php?f=36&t=1004&p=8020#p8020")

I now have a working Beryl on my laptop, and a little script helps me switch from two display mode to accelerated mode (unfortunately the radeon driver can't accel more than one screen).

---

### Post by legine on 2007-01-18
I realy had Issues with getting Beryl to run. But the fault was thateven Xorg-air has been installed the old Xorg still got loaded by gdm.
I removed the /usr/bin/X file and put a link there that Points to /usr/bin/Xorg-air, and all crashes solved. Now I still have not seen any crash on this laptop since 3D drivers have been activated.

Thought Beryl is complaining a bit:

```
libGL warning: 3D driver claims to not support visual 0x4b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

```
But works fine. (Not mentioning all on 125 MB RAM :) )

How do I activate transparent backrounds in (example aterm, xterm.)?

ty for tipps.
Legine

---

### Post by 0p3r4 on 2007-01-19
Hello, really neat guide you got going here, however, i'm having a bit of trouble getting this to work. After following the guide up to the point where I check for direct rendering it tells me the following:

```
direct rendering: No
```

And this seems okey, and in-line with the guide. However, when i issued the  cat /var/log/Xorg.0.log | grep EE - command, i got the following: 
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
```

There seems to be some trouble loding the glcore-module yet libgl1-mesa-glx seems to be installed (if thats the  package thats supposed to supply that file).

Anyone know what might be the cause of this? I'm running Ubuntu Edgy Eft on a Thinkpad R40. lspci reports the following card: ```
VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
```

If someone has an idea to why this error occurs, please let me know

---

### Post by javaJake on 2007-01-19
> **legine said:**
> I still have to test Massive 3d usage thought.

One game that'll really test your configuration is BZFlag, and VegaStrike. Both are intense 3D games.

---

### Post by javaJake on 2007-01-19
> **2hansen said:**
> Sorry to get back so late, but I've been away for while. My [problems]("http://www.ubuntuforums.org/showpost.php?p=1901114&postcount=140") with Beryl seems to have gone now with aid from this [forum]("http://forum.beryl-project.org/viewtopic.php?f=36&t=1004&p=8020#p8020")

I now have a working Beryl on my laptop, and a little script helps me switch from two display mode to accelerated mode (unfortunately the radeon driver can't accel more than one screen).

OK, I'll review the configuration, and consider it for the Troubleshooting section.

Thanks for the input! Quite a few people have had this issue now, so it'll be nice to finally have an answer. :P

---

### Post by javaJake on 2007-01-19
> **legine said:**
> I realy had Issues with getting Beryl to run. But the fault was thateven Xorg-air has been installed the old Xorg still got loaded by gdm.
I removed the /usr/bin/X file and put a link there that Points to /usr/bin/Xorg-air, and all crashes solved. Now I still have not seen any crash on this laptop since 3D drivers have been activated....hmmm... yet another solution for Beryl crashing.

> **legine said:**
> Thought Beryl is complaining a bit:

```
libGL warning: 3D driver claims to not support visual 0x4b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

```
But works fine. (Not mentioning all on 125 MB RAM :) )

How do I activate transparent backrounds in (example aterm, xterm.)?

ty for tipps.
Legine

Well, as for the warnings, ignore those. It's just saying certain cool affects aren't supported by the card. the libGL warning about the visual 0x4b you'll get all the time, and the stencil buffer hasn't seemed to do anything to me yet, besides pixel-ish windows.

BTW, it won't matter how much RAM you have on your laptop, since all graphical stuff (I believe) will be sent to the card's memory.

The transparent backgrounds can be set for any window. If you want terminal windows specifically, then load up the Terminal, goto the menu Edit -> Profiles, click Edit, and then the tab "Effects". You'll find two different effects there. To do transparent windows, right click on the upper-left corner of the window (where the window's icon is) and if you look through those menus, you'll find the Transparency, Opacity, and Focus settings there.


Enjoy! :D

---

### Post by javaJake on 2007-01-19
> **0p3r4 said:**
> And this seems okey, and in-line with the guide. However, when i issued the  cat /var/log/Xorg.0.log | grep EE - command, i got the following: 
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
```

There seems to be some trouble loding the glcore-module yet libgl1-mesa-glx seems to be installed (if thats the  package thats supposed to supply that file).

Anyone know what might be the cause of this? I'm running Ubuntu Edgy Eft on a Thinkpad R40. lspci reports the following card: ```
VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
```

If someone has an idea to why this error occurs, please let me know

According to one search result, it could be you are using the wrong driver. Drivers that don't support glcore will produce this error. Check to be sure you are using "Driver radeon" in xorg.conf.

---

### Post by grahams on 2007-01-24
I followed this guide, ran into the freeze with glxinfo | grep direct and glxgears, editted my xorg.conf and removed all but the 3d enabling parts and it still freezes. 

Is there actually a way to make this graphics chip work in 3d?

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

I've attached my xorg.conf

---

### Post by grahams on 2007-01-24
I booted from Mandrake One 2007 live cd and had 3d rendering working 1st time and it looks lie their using the open source ATI. 

Why is this so difficult in Ubuntu ?

---

### Post by 0p3r4 on 2007-01-25
> **javaJake said:**
> According to one search result, it could be you are using the wrong driver. Drivers that don't support glcore will produce this error. Check to be sure you are using "Driver radeon" in xorg.conf.

The driver is indeed set to "radeon", Here you can find my current xorg.conf and the error-log:

[http://komsi.se/debug/xorg.conf](http://komsi.se/debug/xorg.conf)
[http://komsi.se/debug/Xorg.0.log](http://komsi.se/debug/Xorg.0.log)

I can't seem to figure this one out myself, and any help will be greatly appreciated, thanks for taking the time to reply.

---

### Post by javaJake on 2007-01-25
> **grahams said:**
> I booted from Mandrake One 2007 live cd and had 3d rendering working 1st time and it looks lie their using the open source ATI. 

Why is this so difficult in Ubuntu ?

Mandrake might detect and configure your card correctly. Ubuntu does not. In the future this should be fixed (Ubuntu Project Wisdom.... *ahem* :D ) but for now us users have to do it manually.

Unless someone were to make a nice script... hmmm.... :)

---

### Post by javaJake on 2007-01-25
> **grahams said:**
> I followed this guide, ran into the freeze with glxinfo | grep direct and glxgears, editted my xorg.conf and removed all but the 3d enabling parts and it still freezes. 

Is there actually a way to make this graphics chip work in 3d?

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

I've attached my xorg.conf

Hmmm, one other fellow had this issue, but he never solved it, it seems.

I'll dig around in your xorg.conf. In the meantime, what is the model of your computer/laptop?

---

### Post by javaJake on 2007-01-25
**_Anyone who's waiting for a reply Please Read!_**

I need to finish some stuff over the weekend, so that means I probably won't be able to help around here until Monday or beyond. When I have time I'll scan through the last few pages of this thread for anyone I've forgotten. I recommend you PM me if you haven't gotten a response yet to ensure that you'll get a reply.

Sorry for the inconveniance, but when life gets busy, I have no choice. I'm sure many understand that one. :D

---

### Post by grahams on 2007-01-25
Thanks

My laptop is an HP omnibook 6100.

I just booted Feisty on this machine and 3D rendering works 1st time. Maybe I should just wait.

---

### Post by grahams on 2007-01-28
I followed the guide at the url below and got 3d working fine on my laptop with Edgy. 

[https://help.ubuntu.com/community/RadeonDriver?highlight=%28driver%29%7C%28radeon%29#head-839ea46a1da3bee0839b28a9595722a9cdf07797](https://help.ubuntu.com/community/RadeonDriver?highlight=%28driver%29%7C%28radeon%29#head-839ea46a1da3bee0839b28a9595722a9cdf07797)

I think my missing step was to force removing any flgrx driver modules in the kernel.  I do not remember ever installing and lsmod |grep flgrx didn't show it, but after following this guide 3d started to work.

---

### Post by TheJackofClubs on 2007-02-07
i tryed this guide first and it didnt work... then i tryed the ati proprietary drivers and it didnt work... then i checked out that guide and tryed the open source drivers (uninstallation of fglrx in that guide) and it still doesnt work. i think i need to wipe linux out and redo starting with that opensource driver guide and if that doesnt work then try back here but this is sorta frustrating. i dual boot with windows xp and it only took a simple exe that took less than a minute to download and i got 3d acceleration. i got a free copy of vista coming and i might wipe my hard drive install that then install feisty (when it comes out) which im hearing has the open source drivers automatically setup by default. and to think all i wanted was beryl to show off to people.

---

### Post by javaJake on 2007-02-08
Sorry you are having issues. Are you using the ATI Radeon M6 LY card?

If you would like, follow my guide all the way through, then try to run 3D graphics again. Post a copy of /var/log/Xorg.0.log and /var/log/syslog when you've logged in with the 3D configurations in place. This should tell me what's going on.

And, yes, a reinstall after trying different guides with different drivers is probably a good idea. :)

---

### Post by salvodam on 2007-02-09
Thanks a lot. Now my ATI card works!

---

### Post by javierfh on 2007-02-10
Hi,

i have tried to follow that tutorial, but no success.
I modified the xorg.conf as you instructed to do, but still when i try glxinfo i still get the direct rendering NO
I post here my xorg.conf as you adviced in case we modify the default depth from 24 to 16 (but still didnt help)

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"


EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1400x1050"
#	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#        Option  "Composite" "Disable"
#EndSection

#Section "ServerFlags"
#        Option  "AIGLX" "off"
#EndSection



I tried to find that log file but there wasnt at least under /etc/X11/
and for reference, i have ibm t30 


Thanks in advance, 

Javi

---

### Post by javaJake on 2007-02-10
> **javierfh said:**
> I tried to find that log file but there wasnt at least under /etc/X11/

The logs can be found at /var/log/Xorg.0.log

Also, I noticed that you are you using a M7 card, not an M6. You might want to look around for a different HOWTO, since I think these cards are significantly different. However, I can still help you here if you want. :)

---

### Post by javierfh on 2007-02-11
Hi,

thanks for your interest and help..and yes, by all means i accept your help.
The truth is that i have laptop, IBM T30 and i guess that the card is ATI mobility radeon 7500 or at least thats what everyone around claims. If i remember right, that's also what i saw while i was using windows XP, but the other day when formatting i did some mistake...and now is gone :D (not that i miss it :D)
So to my surprise, yesterday is when i saw that xorg.conf says i have that M7.
Do you think that it is the right card? 
Anyway how can i proceed next?
I try to attach here the log file you asked for, hopping that this will help.

Thanks a lot,

Javi

---

### Post by TheJackofClubs on 2007-02-11
ok well i wiped and reinstalled ubuntu and the first thing i tryed was this guide, not installing anything else not even updates. i seem to get stuck now after commenting the 24bit depth mode. it told me to do "glxinfo | grep" and it says "direct rendering: NO / OpenGL Rendering string: Mesa GLX Indirect". my card reads as "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]" so it is an m6 ly. :P

in my many attempts to get it working here is my xorg.conf and Xorg.0.log (also found at [http://www.thejackofclubs.net/crapile/xorg.conf](http://www.thejackofclubs.net/crapile/xorg.conf) and [http://www.thejackofclubs.net/crapile/Xorg.0.log](http://www.thejackofclubs.net/crapile/Xorg.0.log))

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value
#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1400x1050"
#	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

i cut out most anything that was not EE in the log since i couldnt fit it into this post.
```

(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument

```

you know if someone had a working xorg.conf file i could just appropriate from this would be easier. :|


i tryed using the one from [http://jaredquinn.info/it-related/technical/unix/2006.06.07/xorg-configuration-for-ati-radeon-mobility-m6-ly/](http://jaredquinn.info/it-related/technical/unix/2006.06.07/xorg-configuration-for-ati-radeon-mobility-m6-ly/) and it STILL doesnt work. :(

---

### Post by ingo on 2007-02-17
@ javierfh
Hi, I'm suffering the same as you, Radeon Mobility 7500 on a TP41 and although I appear to be able to run 3D applications and glxgears there is no support for direct rendering. Have you managed to get it working?

---

### Post by javaJake on 2007-02-17
> **TheJackofClubs said:**
> i cut out most anything that was not EE in the log since i couldnt fit it into this post.
```

(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable
```


What do we have here? You need to reduce either your resolution or depth to make this work. (Sorry for the slow response, BTW.)

---

### Post by sirbats on 2007-02-21
> **javaJake said:**
> According to one search result, it could be you are using the wrong driver. Drivers that don't support glcore will produce this error. Check to be sure you are using "Driver radeon" in xorg.conf.

Hi Javajake,

I faced the same thing : see below output :
tj@TJ-UBUNTU:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
tj@TJ-UBUNTU:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
tj@TJ-UBUNTU:~$

My device section :

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

My box did not FREEZE, everything fine :=))

Any Idea ?

rgds
SIR BATS

---

### Post by javaJake on 2007-02-23
Very strange! Are you sure you're coming from a relatively clean install of Ubuntu? It could be you both are missing something or something isn't tweaked just right. Did you follow other HOWTOs before coming here? Could you link me?

Also, right after you login with the 3D configuration, give me the complete files /var/log/syslog, /var/log/Xorg.0.log, and /etc/X11/xorg.conf.3D, and the complete output of glxinfo. That'll help me figure this out.

---

### Post by lordf on 2007-02-25
Hi there, 

I have the same problems with my Thinkpad T30 but could not be a solution, to use standard RAM for grafical temporary space? I do not want to reduce my pixels I have an SXGA display and i want to use it :-) 
If anybody have an idea I will test it, 

Thanks for answer. 

Lordf

---

### Post by javaJake on 2007-02-25
> **lordf said:**
> Hi there, 

I have the same problems with my Thinkpad T30 but could not be a solution, to use standard RAM for grafical temporary space? I do not want to reduce my pixels I have an SXGA display and i want to use it :-)

I'm sorry, but I don't understand what you are trying to do. Can you explain what you mean by "use standard RAM for graphical temporary space"? Do you mean you want to use your RAM as shared memory?

---

### Post by lordf on 2007-02-27
yes this I want to try. Can zou help me to set this settings ? Since few days I`m searching for an explenation, but I found nothing.

---

### Post by javierfh on 2007-03-04
Hello,

i have found this thread here and Burnick claims that he made it work 

[http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/](http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/)

Can anyone try if you can make it work?
So far my laptop seems to have problem and i cant install the updates, gives some error.

I would appreciate if any of you can try that link..burnick claims that it works.

Javi

---

### Post by javaJake on 2007-03-04
> **javierfh said:**
> Hello,

i have found this thread here and Burnick claims that he made it work 

[http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/](http://corvillus.com/2006/08/03/how-to-set-up-aiglx-and-compiz-on-ubuntu-606-running-gnome/)

Can anyone try if you can make it work?
So far my laptop seems to have problem and i cant install the updates, gives some error.

I would appreciate if any of you can try that link..burnick claims that it works.

Javi

It probably does, however I already posted instructions on this HOWTO for Beryl that work perfectly with the M6 LY card, and are on the official Beryl Wiki. Also, the instructions you posted require that you install xorg-air. While you might need that for other cards, this card does not need it.

However, come to think of it, many users have reported Beryl crashing when they follow the instructions. When I get Feisty, I'll test my instructions again. If they crash, I'll test yours, and see if yours crash or not.

Again, thanks for the input! I really appreciate it! :D

---

### Post by ppietryga on 2007-03-04
My config:
DELL Latitude c610 with ATI Radeon M6LY. Edgy Eft
Your HOWTO worked like a charm. After completing Part 1 I got the error saying it can't load libGLcore.so.
What I did was:
```
aptitude purge linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common fglrx-control xorg-driver-fglrx
```
And that didn't work. Than I saw a tip: to install xlibmesa-dri.
After:
```
aptitude install xlibmesa-dri
/etc/init.d/kdm restart
```
It just :guitar: 
I got Direct rendering: Yes
in glxgears -printfps I get about 2000fps (I know glxgears is not a benchmark, but before this HOWTO I only got 300fps).

And my computer does not freeze. Next week I'll try some of those "unstable" config options :twisted: 

**javaJake** I want to thank You very VERY much for this guide. I've been FIGHTING with direct rendering since upgrade to Dapper and YOU (and the community) made it work.
Now after I pass a few exams I'm gonna try AIGLX.

Thank you UBUNTU :)

---

### Post by zcal on 2007-03-12
I've got a ThinkPad R40 with a 16mb M6 LY, and I've never been able to get good framerate in opengl games (if they even got started without freezing X with garbage all over the screen), until now.  Your HOWTO fixed the freezing issue, but I still never got good framerates in opengl, testing with Quake III Arena.  I had direct rendering right off the bat, by the way.

So anyway, I've upgraded to Edgy, which seems to have better graphical support.  I've enabled AIGLX (not using Beryl, by the way) and made a few easy modifications to xorg.conf, and now I've got fast framerates in Quake III and I never crash on going to fullscreen opengl.  I'm not sure why it works, but it does.  So, if anybody's got a laptop with a card like mine, you should try out what I did if you're looking to play some games.

Use Edgy, or follow this HOWTO's guide on upgrading to Edgy graphical drivers.
[Enable AIGLX.]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy?highlight=%28aiglx%29")
And here's my xorg.conf (optimized for a 16 mb card I think)...

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	# Acceleration
	Option		"AGPMode" "4"
	Option		"AGPSize" "64" # default: 8
	Option		"RingSize" "8"
	Option		"BufferSize" "2"
#	Option		"SWcursor" "off"
#	Option		"EnablePageFlip" "true"
#	Option		"ColorTiling" "on"
#	Option		"EnableDepthMoves" "true"
	# Enable (partial) PowerPlay features
	Option		"DynamicClocks" "on"
	# Use bios hot keys on ThinkPad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
	# Enable AIGLX
	Option		"XAANoOffscreenPixmaps" "true"
	Option		"DRI" "true"
EndSection

---

### Post by javaJake on 2007-03-14
> **ppietryga said:**
> My config:
DELL Latitude c610 with ATI Radeon M6LY. Edgy Eft
Your HOWTO worked like a charm. After completing Part 1 I got the error saying it can't load libGLcore.so.
What I did was:
```
aptitude purge linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common fglrx-control xorg-driver-fglrx
```
And that didn't work. Than I saw a tip: to install xlibmesa-dri.
After:
```
aptitude install xlibmesa-dri
/etc/init.d/kdm restart
```
It just :guitar: 
I got Direct rendering: Yes
in glxgears -printfps I get about 2000fps (I know glxgears is not a benchmark, but before this HOWTO I only got 300fps).

WOW! This is one of the big unsolved mysteries, and you just solved it. Thanks!!

---

### Post by qyte on 2007-03-14
after the reboot i get the following error...
libGL warning: 3D driver claims to not support visual 0x4b
Direct Rendering : YES!!!
but i have still very slow framerates in glxgears :( well like 350 fps.
Is there anything to speed it up???
does this warning mean something?
Is it possible to check out how much ram my card has?

---

### Post by spaceghoti on 2007-03-15
> **qyte said:**
> but i have still very slow framerates in glxgears :( well like 350 fps.
Is there anything to speed it up???Wow, I wish I got as much as 350 fps on my card!  I usually get 250.

---

### Post by qyte on 2007-03-15
well the other guy (ppietryga) got 2000.
And generally the whole system is EXTREMELY slow although my cpu seems to handle it
so does my ram. As far as i can tell from within System Monitor.
Dragging windows around is very laggy :(
So i blame my graphic accelarator. I had the same problem EXACTLY with winxp until
i found the proper ati driver there. here though things are quite different.

---

### Post by spaceghoti on 2007-03-15
I seem to have the opposite problem.  My framerates are incredibly slow, resulting in occasional problems playing WoW (like now, my system chokes at semi-regular intervals making it dangerous to go adventuring) but everything else runs smoothly, even when my processor seems to be running flat out.  It took quite a bit of work to get the ATI drivers to work that much.  I tried the libmesa driver instructions posted above and it just crashed my system until I restored the original ATI setting.  It may be that I have to wipe the system clean and install libmesa from the beginning, but I don't have the patience for that right now.

I'd LOVE to have 2000 fps on my laptop's Radeon 9700, but until we get better vendor support I just don't see that happening.

---

### Post by javaJake on 2007-03-16
If you get Direct Rendering saying yes, and your speeds did increase after the HOWTO, then that's all I can do. Unfortunately all I can say is to play with the options listed in the xorg.conf file, since most actually slow down things.

If anyone has any tips, let us know

**Please, whenever you mention your FPS or your tips for the xorg.conf file, mention what card model you have.** The M7 model seems to be much better then the M6 model (makes sense), so the FPS on those cards are obviously different.

---

### Post by javaJake on 2007-03-16
> **qyte said:**
> well the other guy (ppietryga) got 2000.
And generally the whole system is EXTREMELY slow although my cpu seems to handle it
so does my ram. As far as i can tell from within System Monitor.
Dragging windows around is very laggy :(
So i blame my graphic accelarator. I had the same problem EXACTLY with winxp until
i found the proper ati driver there. here though things are quite different.

If you are talking about Beryl, then yes, there is plenty of lag. Unfortunately with a card as old as the M6 LY, you won't be pulling many FPS in intensive programs such as Beryl.

---

### Post by javaJake on 2007-03-16
> **qyte said:**
> but i have still very slow framerates in glxgears :( well like 350 fps.
Is there anything to speed it up???Try playing around with the xorg.conf file. Posting your /var/log/Xorg.0.log file would also help me figure out if something is crashing.
> **qyte said:**
> after the reboot i get the following error...
libGL warning: 3D driver claims to not support visual 0x4b
does this warning mean something?Yes, it means that your card doesn't support a certain effect, in this case effect 0x4b (don't ask what it is).
> **qyte said:**
> Is it possible to check out how much ram my card has?Yea, run the following command _exactly_ as shown. That means watch your capital letters!

```
cat /var/log/Xorg.0.log | grep VideoRAM
```

This will only work for the ati or radeon driver as far as I know.

---

### Post by qyte on 2007-03-16
> **javaJake said:**
> If you are talking about Beryl, then yes, there is plenty of lag. Unfortunately with a card as old as the M6 LY, you won't be pulling many FPS in intensive programs such as Beryl.

NO i have not beryl enabled. If i enable it we are then talking of EXTREME lag :(

> **javaJake said:**
> Try playing around with the xorg.conf file. Posting your /var/log/Xorg.0.log file would also help me figure out if something is crashing.

see attachment


> **javaJake said:**
> Yea, run the following command _exactly_ as shown. That means watch your capital letters!

```
cat /var/log/Xorg.0.log | grep VideoRAM
```

This will only work for the ati or radeon driver as far as I know.

thanks it worked i have 16MB. At least now i know...

---

### Post by trippinnik on 2007-03-17
Wow, thanks for the howto.  The first time through I was only able to get 3D accell, but with the new Xorg 7.2 (check trevino's repository) and beryl .20 I've got Beryl running on a ATI Mobility M6LY 8MB card.  I didn't think it would work.  It's got decent speed too.

---

### Post by javaJake on 2007-03-17
> **trippinnik said:**
> Wow, thanks for the howto.  The first time through I was only able to get 3D accell, but with the new Xorg 7.2 (check trevino's repository) and beryl .20 I've got Beryl running on a ATI Mobility M6LY 8MB card.  I didn't think it would work.  It's got decent speed too.

Xorg v7.2 is also in the Feisty repositories - when I reformat my computer for Feisty, I'll do some playing around to see if I can't figure out why Beryl crashes the first time I and many others tried to use it.

---

### Post by javaJake on 2007-03-17
> **qyte said:**
> see attachment

Thanks, I'll take a look.

---

### Post by trippinnik on 2007-03-18
> **javaJake said:**
> Xorg v7.2 is also in the Feisty repositories - when I reformat my computer for Feisty, I'll do some playing around to see if I can't figure out why Beryl crashes the first time I and many others tried to use it.

Yeah, had heard that I just didn't want to do a full distribution upgrade for and alpha distribution.  It's probably fine, but I figured this way was easier to roll back.  At this point I probably basically am running fiesty.. as I built the 2.6.20 kernel a while back to get my wireless to work.  Anyway it's way better performance than I expected, I think it handles moving windows around as fast as Metacity, but there's no artifacts.

Also I had to change my xorg.conf to use
 #Option "AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
EXA apparently isn't working so well with Xorg 7.2.  After that I just ran through the Howto on the Beryl site:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Computer companies would die if this became popular considering I can get it running on a 5 year old laptop (p3 733 and 8mb ati card)... What does Vista need?

---

### Post by javaJake on 2007-03-21
> **qyte said:**
> see attachment

Alright, I took a look, and there are _no_ errors. Everything reports success. :?

Could you send me /etc/X11/xorg.conf?

---

### Post by qyte on 2007-03-21
unfortunately i am downloading feisty right this moment and i have already formatted edgy :(

---

### Post by javaJake on 2007-03-24
> **qyte said:**
> unfortunately i am downloading feisty right this moment and i have already formatted edgy :(

That's fine. I'll probably doing the same too to maintain support for my HOWTOs.

---

### Post by Excentrik on 2007-03-26
Hi all!

I've been having some troubles with the graphics in my computer.

So, first things first.

My config:
Laptop with an ATI X700
Ubuntu Edgy with Xorg7.2
using radeon driver
(no composite manager whatsoever)

Now, the problems. "Only" two.

First one. My Xorg is very slow (scrolling uses 100% CPU for instance).
After a while, the memory use increases to 20% ...
All opengl applications are "slow" and use lots of CPU.

Second problem. Multiscreen (or MergeFB)
Since I've a laptop, multiscreen comes in handy once in a while.
Anyway, everytime I try to plug in an external screen to the VGA conector and boot into X, I always get a variety of errors, and the external screen ends up being just a clone of the laptop LCD.
You can see the errors in the Xorg.0.log that I post here.
I've tried to set up higher frequency ranges and so on, but I always get the same errors, plugging a CRT, an LCD, ...

So, if anyone has any ideas about how to solve these problems, I would appreciate.

P.S. My glxgears gives ~2000FPS

xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
	Load    "type1"
        Load    "i2c"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
EndSection


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		 "radeon"
	Option          "EnablePageFlip" "true"
        Option          "BIOSHotkeys" "true"                # [<bool>]
        Option          "LVDSProbePLL"               # [<bool>]
        Option          "ColorTiling" "on"
        Option          "RenderAccel" "true"
        Option          "XAANoOffscreenPixmaps" "true"
	Option          "AccelDFS"    "1"
	Option          "EnableDepthMoves" "true"
        Option          "DPMS" #support for VESA's Display Power Management Specification
        Option          "DynamicClocks" "on" # problems on latest git - disable with glitches
	BusID		"PCI:1:0:0"
EndSection



Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option          "MonitorLayout" "LVDS,CRT"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Part of Xorg.0.log
```

.....
(II) RADEON(0): Port0: DDCType-0, DACType-0, TMDSType--1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0, DACType--1, TMDSType--1, ConnectorType-7
(**) RADEON(0): MonitorLayout Option: 
	Monitor1--Type LVDS, Monitor2--Type CRT

(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): Secondary:
 Monitor   -- CRT
 Connector -- LVDS
 DAC Type  -- Unknown
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): ref_freq: 2700, min_pll: 20000, max_pll: 50000, xclk: 40000, sclk: 358.000000, mclk: 345.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=7 min=20000 max=50000; xclk=40000
(WW) RADEON(0): Failed to detect secondary monitor DDC, default HSync and VRefresh used
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 68900
HBlank: 128, HOverPlus: 21, HSyncWidth: 32
VBlank: 16, VOverPlus: 4, VSyncWidth: 4
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1280x800
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 800x600
(II) RADEON(0): Total number of valid FP mode(s) found: 3
(II) RADEON(0): Validating CRTC2 modes for MergedFB ------------ 
(II) RADEON(0): CRT2 Monitor: Using default hsync range of 31.50-37.90 kHz
(II) RADEON(0): CRT2 Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) RADEON(0): Clock range:  20.00 to 500.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (mode clock too high)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (mode clock too high)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (mode clock too high)
(II) RADEON(0): Not using default mode "400x300" (mode clock too high)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x768" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (hsync out of range)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(WW) RADEON(0): Mode pool is empty
(EE) RADEON(0): No valid modes found
(EE) RADEON(0): No valid mode found for CRTC2, disabling MergedFB
(II) RADEON(0): Total of 0 CRTC2 modes found for MergedFB------------ 
(--) RADEON(0): Virtual size is 1280x800 (pitch 1280)
(**) RADEON(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816
(**) RADEON(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   68.90  1024 1301 1333 1408  768 804 808 816
(**) RADEON(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   68.90  800 1301 1333 1408  600 804 808 816
(**) RADEON(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   68.90  640 1301 1333 1408  350 804 808 816
(**) RADEON(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   68.90  640 1301 1333 1408  400 804 808 816
(**) RADEON(0):  Default mode "720x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   68.90  720 1301 1333 1408  400 804 808 816
(**) RADEON(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   68.90  640 1301 1333 1408  480 804 808 816
(**) RADEON(0):  Default mode "832x624": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   68.90  832 1301 1333 1408  624 804 808 816
(**) RADEON(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   68.90  1280 1301 1333 1408  768 804 808 816
(**) RADEON(0):  Default mode "1152x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"   68.90  1152 1301 1333 1408  768 804 808 816
(++) RADEON(0): DPI set to (100, 100)
....

```


glxinfo:
```

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
 ...

```

---

### Post by javaJake on 2007-03-26
> **Excentrik said:**
> Hi all!

I've been having some troubles with the graphics in my computer.

So, first things first.

My config:
Laptop with an ATI X700
Ubuntu Edgy with Xorg7.2
using radeon driver
(no composite manager whatsoever)

Now, the problems. "Only" two.

First one. My Xorg is very slow (scrolling uses 100% CPU for instance).
After a while, the memory use increases to 20% ...
All opengl applications are "slow" and use lots of CPU.

Second problem. Multiscreen (or MergeFB)
Since I've a laptop, multiscreen comes in handy once in a while.
Anyway, everytime I try to plug in an external screen to the VGA conector and boot into X, I always get a variety of errors, and the external screen ends up being just a clone of the laptop LCD.
You can see the errors in the Xorg.0.log that I post here.
I've tried to set up higher frequency ranges and so on, but I always get the same errors, plugging a CRT, an LCD, ...

So, if anyone has any ideas about how to solve these problems, I would appreciate.

P.S. My glxgears gives ~2000FPS

xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
	Load    "type1"
        Load    "i2c"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
EndSection


Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		 "radeon"
	Option          "EnablePageFlip" "true"
        Option          "BIOSHotkeys" "true"                # [<bool>]
        Option          "LVDSProbePLL"               # [<bool>]
        Option          "ColorTiling" "on"
        Option          "RenderAccel" "true"
        Option          "XAANoOffscreenPixmaps" "true"
	Option          "AccelDFS"    "1"
	Option          "EnableDepthMoves" "true"
        Option          "DPMS" #support for VESA's Display Power Management Specification
        Option          "DynamicClocks" "on" # problems on latest git - disable with glitches
	BusID		"PCI:1:0:0"
EndSection



Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option          "MonitorLayout" "LVDS,CRT"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Part of Xorg.0.log
```

.....
(II) RADEON(0): Port0: DDCType-0, DACType-0, TMDSType--1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0, DACType--1, TMDSType--1, ConnectorType-7
(**) RADEON(0): MonitorLayout Option: 
	Monitor1--Type LVDS, Monitor2--Type CRT

(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): Secondary:
 Monitor   -- CRT
 Connector -- LVDS
 DAC Type  -- Unknown
 TMDS Type -- NONE
 DDC Type  -- NONE
(II) RADEON(0): ref_freq: 2700, min_pll: 20000, max_pll: 50000, xclk: 40000, sclk: 358.000000, mclk: 345.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=7 min=20000 max=50000; xclk=40000
(WW) RADEON(0): Failed to detect secondary monitor DDC, default HSync and VRefresh used
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 68900
HBlank: 128, HOverPlus: 21, HSyncWidth: 32
VBlank: 16, VOverPlus: 4, VSyncWidth: 4
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1280x800
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Valid mode using on-chip RMX: 800x600
(II) RADEON(0): Total number of valid FP mode(s) found: 3
(II) RADEON(0): Validating CRTC2 modes for MergedFB ------------ 
(II) RADEON(0): CRT2 Monitor: Using default hsync range of 31.50-37.90 kHz
(II) RADEON(0): CRT2 Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) RADEON(0): Clock range:  20.00 to 500.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (mode clock too high)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (mode clock too high)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (mode clock too high)
(II) RADEON(0): Not using default mode "400x300" (mode clock too high)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x768" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (hsync out of range)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(WW) RADEON(0): Mode pool is empty
(EE) RADEON(0): No valid modes found
(EE) RADEON(0): No valid mode found for CRTC2, disabling MergedFB
(II) RADEON(0): Total of 0 CRTC2 modes found for MergedFB------------ 
(--) RADEON(0): Virtual size is 1280x800 (pitch 1280)
(**) RADEON(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   68.90  1280 1301 1333 1408  800 804 808 816
(**) RADEON(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   68.90  1024 1301 1333 1408  768 804 808 816
(**) RADEON(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   68.90  800 1301 1333 1408  600 804 808 816
(**) RADEON(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   68.90  640 1301 1333 1408  350 804 808 816
(**) RADEON(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   68.90  640 1301 1333 1408  400 804 808 816
(**) RADEON(0):  Default mode "720x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   68.90  720 1301 1333 1408  400 804 808 816
(**) RADEON(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   68.90  640 1301 1333 1408  480 804 808 816
(**) RADEON(0):  Default mode "832x624": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   68.90  832 1301 1333 1408  624 804 808 816
(**) RADEON(0):  Default mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   68.90  1280 1301 1333 1408  768 804 808 816
(**) RADEON(0):  Default mode "1152x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1152x768"   68.90  1152 1301 1333 1408  768 804 808 816
(++) RADEON(0): DPI set to (100, 100)
....

```


glxinfo:
```

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
 ...

```

Let me first mention you are using a Mobility Radeon X7000, not a Mobility Radeon M6 (or 9000). Therefore your card is not guaranteed to work with this HOWTO.

The glxgears report of 2000 FPS is strange. That sounds accellerated to me.

The Xorg.0.log chunk said that it couldn't find the secondary monitor, and that several modes didn't work on your first monitor.

I'll look into this more later...

---

### Post by dragnazz5.0 on 2007-04-02
has anyone gotten this to work with fiesty?  or is there a thread that i overlooked that handles this?

---

### Post by trippinnik on 2007-04-04
I've got it working in Feisty.  It's better because of the updates to Xorg and Mesa, but I needed to disable EXA and use the default.

---

### Post by dragnazz5.0 on 2007-04-07
i tried to get it to work but im either doing something wrong or my computer just cant handle 3d acceleration for whatever reason.  but ive got the exact same ati mobility radeon m6 ly that is in the title.  i dont know...i might try again sometime

---

### Post by tcv on 2007-04-08
Just a quick note to let you guys know that I've successfully applied this to my VAIO z1wamp. Direct Rendering is on and the biggest concern I had about my install of Edgy was the overall feeling of sluggishness in the video. But now it feels fine. I did have to drop down to 16-bit, but that's okay. ;-)

Cheers,

Mike...

---

### Post by freeqaz on 2007-04-08
I love you. Thank you SOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO much. I thought that I wouldnt be able to run Mint. But now I can with 3D accel. I love you! 
Im using a Mobility Radeon X7000 IGP 64MB W/ AGP-4X
Thank you SOOO much!
If anyone needs help with this card please feel free to email me. [email]00free@gmail.com[/email]
Thank you,
             -Free

---

### Post by javaJake on 2007-04-11
> **freeqaz said:**
> I love you. Thank you SOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO much. I thought that I wouldnt be able to run Mint. But now I can with 3D accel. I love you!

That's great! I love to hear this response!

Because you aren't using the M6 LY card (which is what this HOWTO was designed for) you should try playing around with the different Options part I had you paste in the xorg.conf file. The comments should explain most of it. Just try switching things on, and seeing what gives you better results. (Restart your computer or X after each change.) You might be able to squeeze a few more frames depending on what games you play.

---

### Post by TheJackofClubs on 2007-04-22
fiesty: confirmed?

---

### Post by javaJake on 2007-04-22
> **TheJackofClubs said:**
> fiesty: confirmed?

Almost. I'm going to attempt the switch today (Sunday), so you should hear from me soon. No guarantees, so I give you the permission to bug me Monday. :)

---

### Post by spaceghoti on 2007-04-22
> **TheJackofClubs said:**
> fiesty: confirmed?I've seen quite a bit on the forums talking about Feisty screwing up ATI systems, but after upgrading my system is working 100%.  Possibly even better.

---

### Post by TheJackofClubs on 2007-04-22
man i could not get this to work on edgy. i tried several times and it never worked. i tried it on feisty using the exact same steps and it actually works and beautifully. im actually getting better performance than on my desktop with a 128mb geforce 4000 at a lower resolution which nobody could explain. after it was done i was not able to switch up to 24bit and keep direct rendering. which is not that big a deal i can just run at 16. what i really wanted was beryl which will not work and i dont know why so if anyone has any ideas your help would be appreciated. thanks :)

---

### Post by javaJake on 2007-04-22
> **spaceghoti said:**
> I've seen quite a bit on the forums talking about Feisty screwing up ATI systems, but after upgrading my system is working 100%.  Possibly even better.

If anyone can confirm the **ATI Radeon Mobility M6 LY (9000)** card is working on a **fresh install of Ubuntu Feisty (7.04)**, I will announce support of Feisty. I'm downloading the ISO now... 30 minutes to go. :)

---

### Post by javaJake on 2007-04-22
> **TheJackofClubs said:**
> what i really wanted was beryl which will not work and i dont know why so if anyone has any ideas your help would be appreciated. thanks :)

I had issues getting Beryl on myself, but somehow I got by the errors with a .deb package... I don't have the package anymore, but I will try it when I get my system up and running.

**Edit:** Almost forgot - if you can provide any exact error messages and/or Xorg logs, that would be great.

---

### Post by ehntoo on 2007-04-22
> **javaJake said:**
> If anyone can confirm the **ATI Radeon Mobility M6 LY (9000)** card is working on a **fresh install of Ubuntu Feisty (7.04)**, I will announce support of Feisty. I'm downloading the ISO now... 30 minutes to go. :)

It works out of the box, with Compiz, but to get Beryl working better (there are some bugs with fullscreen apps) and have better performance, you should probably add 'Option  "AGPMode"  "4"' and 'Option "AGPSize"  "32"' to the Device section of your xorg.conf.

Other than that, it's been fine.  I don't think I've changed anything else on my Evo n410c.

---

### Post by theRaven13 on 2007-04-23
Hi JavaJake, 
I have been trying to get 3D Acceleration to work on my R40 to no avail.

I have a 16mb ATI Mobility Radeon. My OS is feisty with all upgrades available to date.

I did fiddle with fglrx after I first tried this tutorial and then once again before I tried this tutorial again. I do not know if this is the problem and if this may be the problem, I am down for a reinstall. However, here is the code from  

cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) No Input driver matching `synaptics'
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

and attached is the xorg.conf file.
Please let me know if you would want any other information to assist your understanding of this problem, which is driving me nuts.

I would be much grateful to receive any help or advice you have to dispense. Thank you.

---

### Post by Excentrik on 2007-04-23
> **javaJake said:**
> Let me first mention you are using a Mobility Radeon X7000, not a Mobility Radeon M6 (or 9000). Therefore your card is not guaranteed to work with this HOWTO.

The glxgears report of 2000 FPS is strange. That sounds accellerated to me.

The Xorg.0.log chunk said that it couldn't find the secondary monitor, and that several modes didn't work on your first monitor.

I'll look into this more later...

Hi again

I've made a fresh install of feisty during the weekend to try to solve these bugs (and others).
Now, the problem of the slowness and memory is gone (I think and hope) but the multiscreen problem continues.
I'm starting to wonder if this is a regression bug in Xorg 7.2 since it didn't occur in 7.1.1.
I've tried looking in bugs.freedestkop to see if anyone was having the same problem, but no luck.
Anyway, if someone has any idea about the what/where/who of the problem, please let me know.

Regards

---

### Post by javaJake on 2007-04-23
> **theRaven13 said:**
> I did fiddle with fglrx after I first tried this tutorial and then once again before I tried this tutorial again.

It is my first suspicion. Your xorg.conf file is all set, as far as I can see. Your /etc/X11/Xorg.0.log file would be good to have as well. A reinstallation is definately a good idea if you can manage it!

---

### Post by tcv on 2007-04-23
When I upgraded to Feisty from Edgy, the graphics performance was _DREADFUL_ and I had tweaked my XORG to enable direct rendering. 

I did a clean install of Feisty because that machine -- a VAIO laptop -- is just a toy for web browsing and Linux-learning and the performance is much better. Direct rendering, however, according to glxinfo is OFF. :-(

I began to redo the tweak, but it didn't work and I got nervous and reverted back to the original conf. I tried to enable "Desktop Effects" and that just produces a white Gnome background with the pointer and nothing else. Esc brings me back to life.

One question for the thread participants:

Whenever I try to enable direct at the resolution of the monitor, it always reports it needs more memory. Can  I not just GRANT more memory to video? Anyway to do that? 

Cheers,

Mike...

---

### Post by theRaven13 on 2007-04-23
Hey man, thanks for the reply. I am attaching my Xorg.0.log, let me know if something gives you an indication of the problem. Thanks again.

PS. Gzipped the file because of limit on size of .txt uploads

---

### Post by theRaven13 on 2007-04-24
JavaJake, your initial suspicion was indeed on the money. I uninstalled all the fglrx things from spynaptic and followed the HOwto and lo and behold direct rendering 

# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:

Thanks you so much.

---

### Post by TheJackofClubs on 2007-04-25
damn it if firefox crashes one more time while trying to post this then ill be so pissed. :mad: i dont even remember all that i typed. anyways yeah. i still dont have beryl or compiz working and i dont know why. i was wondering if anyone else was having issues with visual elements acting weird. im getting weird lines and stuff on my buttons and menus. it only happens when im in 16bit mode and not 24. its not that big a deal it just looks kinda ugly. i included a screenshot of it that i had just taken (its not the best example but its there :P ). also included is a working xorg.conf file if anyone wants to compare. there is something i noticed in thats not in the guide and thats when you are commenting out the 24bit color depth mode, you also need to change you defaultdepth from 24 to 16 cause itll still try to run in 24 bit mode (it did for me anyways). that may solve some peoples problems. and lastly i attached a copy of the xorg log that i havent looked through yet and took me forever to actually get attached. if anyone gets beryl or compiz working on this card please tell me. thanks. :)

---

### Post by stinkyj on 2007-04-27
i installed Feisty tonight, and i have this card:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])

with AccelMethod set to EXA, Xorg was using > 90%, all the time. i changed it to XAA and it seems to have settled down. time will tell....

glxgears says about 500fps...

so that's good? :)

---

### Post by TheJackofClubs on 2007-04-27
major win! i changed it to xaa and even though i dont get as good framerate, my comp is running faster and both beryl and compiz are working. :D the buttons and stuff lost the messed up lines and stuff too. compiz was running a lot faster than beryl and i didnt understand why until i changed texture filtering from good to best and now it runs nice and fast. i wish i could run in 24bit since its very noticeable that im running in 16bit but its doing exactly what i wanted it to do so im not complaining. :) peace out and thanks for all the help.

---

### Post by javaJake on 2007-04-27
> **TheJackofClubs said:**
> major win! i changed it to xaa and even though i dont get as good framerate, my comp is running faster and both beryl and compiz are working. :D the buttons and stuff lost the messed up lines and stuff too. compiz was running a lot faster than beryl and i didnt understand why until i changed texture filtering from good to best and now it runs nice and fast. i wish i could run in 24bit since its very noticeable that im running in 16bit but its doing exactly what i wanted it to do so im not complaining. :) peace out and thanks for all the help.

Your welcome, though really you figured it out in the end yourself. Congratulations! :)

---

### Post by zx6zx6 on 2007-04-28
I have Radeon Mobility M6 LY (8Mb) and Feisty. After hours trying follow this HOWTO, the system still unstable after direct rendering is enabled, even after Part 2 of this guide.
However, while experimenting options in xorg.conf, I found out that my box could enable direct rendering just by reduce depth or resolution. But it's still very unstable (glxgears hung right after the first try) in both method.
It looks like the system would become unstable whenever direct rendering is enabled.
Is there anyone have the same problem? Pls provide help.
Thanks.

---

### Post by javaJake on 2007-04-28
> **zx6zx6 said:**
> I have Radeon Mobility M6 LY (8Mb) and Feisty. After hours trying follow this HOWTO, the system still unstable after direct rendering is enabled, even after Part 2 of this guide.
However, while experimenting options in xorg.conf, I found out that my box could enable direct rendering just by reduce depth or resolution. But it's still very unstable (glxgears hung right after the first try) in both method.
It looks like the system would become unstable whenever direct rendering is enabled.
Is there anyone have the same problem? Pls provide help.
Thanks.

Sorry, I haven't had the same issue myself. Without logs or an idea of how to help, all I can do is redirect you to the [mailing list]("http://dri.freedesktop.org/wiki/MailingLists") or IRC channel called #xorg or #ati

---

### Post by zx6zx6 on 2007-04-30
Thanks for your guidance.
I attach my Xorg.0.log and xorg.conf with this message.
Please tell me if there is any problem in this file.
I've also found out another strange fact:
The configuration in attached xorg.conf works well if I boot in recovery mode :confused: (I have to increase AGPsize to 64, switch off AGPFastWrite and using XAA instead of EXA to make it work)
Can you tell me the differences between normal boot and recovery boot mode?
At this time, I don't know how to log in as root in normal boot to test. Can you tell me how to do it as well?
Thank you very much.

---

### Post by javaJake on 2007-04-30
> **zx6zx6 said:**
> Thanks for your guidance.
I attach my Xorg.0.log and xorg.conf with this message.
Please tell me if there is any problem in this file.It looks like you are using an old version of my HOWTO. Look through my HOWTO again for a new updated, more stable version of the xorg.conf configuration.

> **zx6zx6 said:**
> I've also found out another strange fact:
The configuration in attached xorg.conf works well if I boot in recovery mode :confused: (I have to increase AGPsize to 64, switch off AGPFastWrite and using XAA instead of EXA to make it work)
Can you tell me the differences between normal boot and recovery boot mode?Absolutely. Normal boot runs quietly with a splash screen. Recovery mode runs without the splash, and with as much noise as possible. This is so you can debug startup issues. Recovery mode also runs a root terminal (runlevel 1 I believe) before launching into runlevel 2. (See the Wikipedia entry [here]("http://en.wikipedia.org/wiki/Runlevel") for more info. Click on the "Debian" link in the Contents after reading the intro.)

This makes your discovery strange - single mode isn't much different besides launching a terminal before continuing its merry way.


> **zx6zx6 said:**
> At this time, I don't know how to log in as root in normal boot to test. Can you tell me how to do it as well?
Thank you very much.

You shouldn't have to log in as root. I wouldn't want to test this since this disables one of Ubuntu's security programs - sudo - and turns it into a supposedly less secure program - su.

What do you do when you go into recovery mode exactly?

I looked at your log, and I found a warning that I have not seen before:
[code]
(WW) RADEON(0): Unknown DDCType 7 found
(WW) RADEON(0): LCD DDC Info Table found!

*...later on... related?*
(WW) RADEON(0): No valid DDCType is given for DDC2, try vbe probing ...
[/quote]

I don't know what DDCType is, but according to some preliminary Google searches, I think this could be the issue.

I'll look into this further.

---

### Post by fred the wise on 2007-05-04
Hi All..
I've follow the instruction correctly but when I type in the consolle: 
  "glxinfo | grep direct"
it replies:

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

My Mobility Radeon M6 LY works perfectly on Ubuntu, I wanted only to activate the 3D acceleration...
thanks_

---

### Post by javaJake on 2007-05-04
> **fred the wise said:**
> Hi All..
I've follow the instruction correctly but when I type in the consolle: 
  "glxinfo | grep direct"
it replies:

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

My Mobility Radeon M6 LY works perfectly on Ubuntu, I wanted only to activate the 3D acceleration...
thanks_

Your card is working! It has direct rendering - this is what you want. :)

The "driver claims to not support visual" message is normal. It just means your video card doesn't support certain effects, like water ripples, etc.

---

### Post by fred the wise on 2007-05-04
thanks, you're great :)  bye

---

### Post by jivemuffin on 2007-05-12
Guys, I need some help :( I have followed these instructions directly (though I am on Feisty), and can't get indirect rendering to turn on. The instructions I followed were those in the first post. Are those the most updated instructions? I do have the M6 LY (Dell C610). Thanks so much for the help! I don't need the super-cube or anything, but I would like access to things like the OSX dock.

---

### Post by javaJake on 2007-05-12
> **jivemuffin said:**
> Guys, I need some help :( I have followed these instructions directly (though I am on Feisty), and can't get indirect rendering to turn on. The instructions I followed were those in the first post. Are those the most updated instructions? I do have the M6 LY (Dell C610). Thanks so much for the help! I don't need the super-cube or anything, but I would like access to things like the OSX dock.

Unfortunately without any information I can't do much. If you give me /var/log/Xorg.0.log, and /etc/X11/xorg.conf, I should be able to help out.

---

### Post by javaJake on 2007-05-12
_**Finally, Feisty Is Support by this HOWTO**_

After a long delay, I'm happy to announce that Feisty will work with this HOWTO. It should work better then Edgy, since Feisty is using the new Xorg 7.2 with all of its bug fixes, etc.

Enjoy! :)

---

### Post by jivemuffin on 2007-05-13
Much thanks to you. I'm sure I'll figure all this out one day, but right now it would help me love Ubuntu just to get things running the way I want them to! I've attached the files here.

---

### Post by jivemuffin on 2007-05-13
Ah, never mind, figured it out! My default depth was still 24. Changing it to 16 solved my issue. Thanks though!

---

### Post by javaJake on 2007-05-13
> **jivemuffin said:**
> Ah, never mind, figured it out! My default depth was still 24. Changing it to 16 solved my issue. Thanks though!

You're welcome. Enjoy!

---

### Post by n0xie on 2007-05-22
Thank you very much for this guide. I got direct rendering working thanks to your how-to.

I'm running aiglx on a Sony Vaio Z1 with the ati mobility M6 card on a fresh (X)ubuntu feisty install.

I tried to run beryl but it crashes when i start, although it seems the 'checklist' doesn't show anything missing, but that's not why I'm posting.

My question is, is the response time of others slowed down dramatically when using direct render? When using the default ati drivers on depth 24 it was ruining quite nicely. Sometimes a small slowdown but nothing worth mentioning.

But after using radeon driver and fiddling with aiglx for a while, despite having to go back to 16 depth, the system is responding very slow. Lagging behind when I type fast in a terminal, and it seems to have difficulties when switching from one window to the other, slowly building up the window. Also moving around the window has lag.

I was under the impression that 3D acceleration should, you know, accelerate ;)

Am I doing something wrong or is this normal?

---

### Post by tcv on 2007-05-23
I continue to not understand why I can get such a high-resolution (1400x1050) with seemingly fast video in Windows but am relegated to 1024x768 with direct rendering in Feisty. (I realize it's not "Feisty" or "Ubuntu" that's the problem.)

I just don't understand why this is. I have, I suppose, the 8mb version of the card, but still, it worked in windows.

I'm just venting, but can someone please explain this discrepancy? Is it simply because the driver doesn't support the higher resolution?

Cheers,

m

---

### Post by xflbret on 2007-05-23
confirmed does NOT work with ati radeon mobility

---

### Post by javaJake on 2007-05-26
> **tcv said:**
> I continue to not understand why I can get such a high-resolution (1400x1050) with seemingly fast video in Windows but am relegated to 1024x768 with direct rendering in Feisty. (I realize it's not "Feisty" or "Ubuntu" that's the problem.)

I just don't understand why this is. I have, I suppose, the 8mb version of the card, but still, it worked in windows.

I'm just venting, but can someone please explain this discrepancy? Is it simply because the driver doesn't support the higher resolution?

I'm not too sure about how OpenGL works and all that, but it *could* be the PageFlip and/or "DepthMoves" that's killing a lot of space, and perhaps other things. Windows, or the Intel drivers provided, must not accellerate certain things to let you use all resolutions, or at least a lot of them.

I'm sure someone else could tell you for sure, but that's my idea.

---

### Post by javaJake on 2007-05-26
> **xflbret said:**
> confirmed does NOT work with ati radeon mobility

Looking at your profile, you've posted the same at another Radeon 9000 thread. This is not the way to do things, especially if you see others have success in the thread, me included!

If you post /var/log/Xorg.0.log and /etc/X11/xorg.conf, I'll see what I can do.

---

### Post by tehbeermang on 2007-05-27
How do I find out what chip/card/etc. I have? I know it's a "mobile radeon" through the winXP device manager, but it doesn't tell me anything more.

Windows looks "crisper" than Ubuntu (fonts a bit garbled, colors look "washed out", etc.) on this dual boot laptop. I don't realize it until I boot into windows.

---

### Post by tehbeermang on 2007-05-27
my xorg.conf says it's the m6 ly.

I tried the OP's instructions and I could log in, but it sent me back to the log in screen. I tried ctrl-alt-f1 and it froze.

I rebooted into recovery mode and removed the changes to xorg.conf through vi and it boots/ logs in.

It's a Dell Latitude C610, I have no idea which radeon chip it uses. I've read it's either M6P or M6 LY. Dell's website is of no use. It tells me the same thing the BIOS and WinXP tell me: Radeon Mobile, with nothing else.

Any ideas?

---

### Post by MiniZiper on 2007-05-28
OK. I got the error with xxxxxx KB necessary thing. I deleted the 24 bit option in xorg.conf.
but stil got it again.

>   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 9216 kB of video memory needed at this resolution and depth.
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom


As you can see.... I get "(EE) AIGLX: Screen 0 is not DRI capable" << Whats that all about??
And I still get the memory error, when I deleted the option of 24-bit from the xorg.conf file...

> Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"ATI Radeon Mobility LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon Mobility LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


??
Any ideas??:)

---

### Post by javaJake on 2007-05-29
> **MiniZiper said:**
> OK. I got the error with xxxxxx KB necessary thing. I deleted the 24 bit option in xorg.conf.
but stil got it again.

First, check to be sure you are really changing the /etc/X11/xorg.conf file. I've edited the wrong file before myself. :p

If you are editing the right file, the only thing left for you to do is to lower the depth, and then resolution, until the error disappears. Your computer is telling you there just isn't enough memory to handle the resolution and depth you are asking for, so you have to reduce either one, or both.

---

### Post by javaJake on 2007-05-29
> **tehbeermang said:**
> my xorg.conf says it's the m6 ly.

I tried the OP's instructions and I could log in, but it sent me back to the log in screen. I tried ctrl-alt-f1 and it froze.

I rebooted into recovery mode and removed the changes to xorg.conf through vi and it boots/ logs in.

It's a Dell Latitude C610, I have no idea which radeon chip it uses. I've read it's either M6P or M6 LY. Dell's website is of no use. It tells me the same thing the BIOS and WinXP tell me: Radeon Mobile, with nothing else.

Any ideas?

To find out if you have the right card, run "lspci" in a terminal and send me the results.

If you have the right card, we'll look through the changes you made to see what's making it crash.

---

### Post by MiniZiper on 2007-05-30
No... I went to the lowest resolution avalible, restarted, and no DRI.

I think the error lies on this:

> (EE) AIGLX: Screen 0 is not DRI capable

God... This is the only thing I don't like about Linux :/

---

### Post by MiniZiper on 2007-05-30
nvm.
I fixed it!!

I HAVE DRI!!
i just have to add extensions and ut options compis false.
google helped :P
Thanks!!

---

### Post by MiniZiper on 2007-05-30
Blah :(
By having DRI. I get the same problem as in Windows. The screen goes black out of nowhere, as if the computer shuts down, but the fan keeps going.
Now I know defenetly thats the video card.
I guess now I have to disable it lol

EDIT: Yup. It's DRI. After I shut it off, the problem stopped.
Bleh :/
Does DRI improve overall system performace? Or just 3D Apps?

---

### Post by tehbeermang on 2007-05-30
I got it working. Changing color depth to 16 and changing to the radeon driver makes it far crisper, though my fonts still look goofy.

Others with the same laptop are running 1400x1050 resolution, I know the win32 partition can handle it. (I cranked it up to 1600x1200 in Windows, but that's hard to read on a 15" monitor.)

It doesn't give me the option in my system-preferences-screen resolution, even after the changes. How do I enable that resolution?

my xorg.conf file:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#defaults
#	Load	"i2c"
#	Load	"bitmap"
#	Load	"ddc"
#	Load	"dri"
#	Load	"extmod"
#	Load	"freetype"
#	Load	"glx"
#	Load	"int10"
#	Load	"vbe"
#/defaults
# from ubuntuforums
	Load "GLcore"
	Load "i2c"
	# Load "bitmap"
	Load "ddc"
	Load "dri"
	SubSection "extmod"
		Option "Omit xfree86-dga"
	EndSubSection
	Load "freetype"
	Load "glx"
	# Load "int10"
	Load "type1"
	Load "vbe"
#/from ubuntuforums
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
# from ubuntu forums, remove if broken
	#Option "RenderAccel" "true"
	#Option "SubPixelOrder" "NONE"
	#Option "MergedFB" "false"
	Option "BackingStore" "true"
	#Option "Accel"
	Option "AGPMode" "4"
	#Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "true"
	#Option "ForcePCIMode" "true"
	#Option "EnableDepthMoves" "true"
	#Option "NoBackBuffer" "false"
	Option "UseInternalAGPGART" "no"
	Option "AllowGLXWithComposite" "true"
#/remove
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
# default settings
#	DefaultDepth	24
#	SubSection "Display"
#		Depth		1
#		Modes		"1024x768"
#	EndSubSection
#	SubSection "Display"
#		Depth		4
#		Modes		"1024x768"
#	EndSubSection
#	SubSection "Display"
#		Depth		8
#		Modes		"1024x768"
#	EndSubSection
#	SubSection "Display"
#		Depth		15
#		Modes		"1024x768"
#	EndSubSection
#	SubSection "Display"
#		Depth		16
#		Modes		"1024x768"
#	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1024x768"
#	EndSubSection
#/defaults

# from ubuntuforums, remove if broken
	DefaultDepth 16
	SubSection "Display"
		Depth 1
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1400x1050"
	EndSubSection
#/remove
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tehbeermang on 2007-05-31
Nevermind, According to information from support.dell.com after putting in my machine's service tag, it's the XGA monitor. Not the upgraded monitor.

I'm going to put a few things back tonight.

---

### Post by majornoob on 2007-06-20
Using this HOWTO, i managed to 3d acceleration working (i think).
*glxinfo | grep direct* returns "direct rendering: yes" and *glxinfo | grep vendor* makes no mention of ATI, but rather SGI (which, I have read, is a good thing).  So far so good, but I cannot get beryl or compiz to work.  When trying to use either, the screen distorts badly and the X server resets.  I would like to get "Desktop Effects" (compiz, i think) working - I don't really want beryl.  Any help or advice? My xorg.conf is below:

> Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
	Option		"TappingOff"		"1"
	Option		"MaxTapTime"		"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1400x1050"
#	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by majornoob on 2007-06-20
I got everything working perfectly now at 1400x1050, using this xorg.conf:

> 
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
#	Load	"GLcore"
# Beryl/Compiz Desktop Effects
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
	Option		"TappingOff"		"1"
	Option		"MaxTapTime"		"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"DynamicClocks"		"on"
	#Beryl / Compiz
	Option		"TripleBuffer"		"true"
	Option		"ColorTiling"		"on"
	Option		"DRI"			"true"
	Option		"EnablePageFlip"	"true"
	Option		"AGPFastWrite"		"on"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPSize"		"16"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	Option		"AddARGBGLXVisuals"	"true"
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
#	SubSection "Display"
#		Depth		24
#		Modes		"1400x1050"
#	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


I also had to create **/etc/drirc** containing:
> 
 <driconf>
    <device screen="0" driver="radeon">
       <application name="all">
           <option name="allow_large_textures" value="2" />
       </application>
    </device>
 </driconf>


Now you can go to System -> Preferences -> Desktop Effects and enable.  To get the cube working (for some reason, compiz starts with only 1 workspace), type (in the terminal):

*gconftool -s /apps/compiz/general/screen0/options/hsize --type int 4*

And now everything should work without a glitch (at least for me).

---

### Post by zx6zx6 on 2007-06-23
> **javaJake said:**
> It looks like you are using an old version of my HOWTO. Look through my HOWTO again for a new updated, more stable version of the xorg.conf configuration.

Absolutely. Normal boot runs quietly with a splash screen. Recovery mode runs without the splash, and with as much noise as possible. This is so you can debug startup issues. Recovery mode also runs a root terminal (runlevel 1 I believe) before launching into runlevel 2. (See the Wikipedia entry [here]("http://en.wikipedia.org/wiki/Runlevel") for more info. Click on the "Debian" link in the Contents after reading the intro.)

This makes your discovery strange - single mode isn't much different besides launching a terminal before continuing its merry way.




You shouldn't have to log in as root. I wouldn't want to test this since this disables one of Ubuntu's security programs - sudo - and turns it into a supposedly less secure program - su.

What do you do when you go into recovery mode exactly?

I looked at your log, and I found a warning that I have not seen before:
[code]
(WW) RADEON(0): Unknown DDCType 7 found
(WW) RADEON(0): LCD DDC Info Table found!

*...later on... related?*
(WW) RADEON(0): No valid DDCType is given for DDC2, try vbe probing ...


I don't know what DDCType is, but according to some preliminary Google searches, I think this could be the issue.

I'll look into this further.[/QUOTE]

Dear javajake,
I've posted my problem here
[http://ubuntuforums.org/showpost.php?p=2563295&postcount=237]("http://ubuntuforums.org/showpost.php?p=2563295&postcount=237")
Since that post, I've tried many solution and I found out that:
M6 LY works with Beryl!
My problem is the speedstep_ich - the cpu scaling related modules!
 When I log in with level 1 or level 0, these modules are not loaded, so the fan stormed wildly each time I active Beryl and no crash occurs.
While I login in level 2, these modules are loaded. But when beryl is activated, the video card works harder and its temperature may become to high while the fan (may be controlled by cpu scaling modules) is off. So IMHO, these modules cause this problem. I turned off these modules and now Beryl work well with M6 LY.

Therefore, I have a recommendation: if graphics card hang with Beryl, make an additional check with its temperatures.

---

### Post by javaJake on 2007-06-24
> **zx6zx6 said:**
> 

Dear javajake,
I've posted my problem here
[http://ubuntuforums.org/showpost.php?p=2563295&postcount=237]("http://ubuntuforums.org/showpost.php?p=2563295&postcount=237")
Since that post, I've tried many solution and I found out that:
M6 LY works with Beryl!
My problem is the speedstep_ich - the cpu scaling related modules!
 When I log in with level 1 or level 0, these modules are not loaded, so the fan stormed wildly each time I active Beryl and no crash occurs.
While I login in level 2, these modules are loaded. But when beryl is activated, the video card works harder and its temperature may become to high while the fan (may be controlled by cpu scaling modules) is off. So IMHO, these modules cause this problem. I turned off these modules and now Beryl work well with M6 LY.

Therefore, I have a recommendation: if graphics card hang with Beryl, make an additional check with its temperatures.

NO WAY! I think my card crashes because it gets too hot. I don't care about noise or power consumption (no battery) if the darn thing won't crash.

Thanks a bunch for the tip!!!

BTW, did I ever talk to you further about the DCC problem? That might've gotten lost. :P

---

### Post by Hyperactiveman on 2007-06-29
THX!
Your HOW-TO worked for me! (Radeon Mobility M6)

nguns

---

### Post by SpikoPath on 2007-07-24
I'm a bit of a newbie when it comes to all this stuff so bear with me,

I'm running a compaq evo N600c laptop
This has under its hood a ATI Radeon Mobility M6 LY (AGP) 16MB

I want to be able to use Kubuntu with this laptop, I get none direct rendering working fine because it chooses ati as its default and this is at a 1024x768 resolution If I select ati radeon, I get direct rendering at a resolution of 640x480 and any resolution above that the screen is garbled.

I have one slight bugbear, I have installed Xubuntu previously and that runs direct rendering fine as I have been able to use xgl at a resolution of 1024x768.

I've tried following the How to with no joy, KDE just wouldn't load, I did try to follow the CTRL+ALT+F1 section of the how to but no joy, I just get an error of "Unable to open display (null)"

I have re-built the laptop with kubuntu again so I can use it, any help with this I would be most grateful.

---

### Post by warcow105 on 2007-07-30
Hey everybody...need some help.  I have a Gateway 400sd4 laptop with a 32MB ati m6 graphics chipset.  After messing around with my xorg.conf I finally got DRI to work, ~660FPS in glxgears, fired up synaptic and installed beryl...started right up and performs well.  The only problem is that when I run someting that uses GL I get lines through the image, I grabbed 2 screenshots when I was using beryl to show what I mean.  Here are my various logs and conf files, any help would be appreciated.

lspci
```
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by SpikoPath on 2007-08-06
Ok, story so far, when I enter all the xorg.conf entries (copy&Paste)from this Howto, I do a restart and my x-server crashes and a log is created, here is the contents of said log.

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux spike-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  6 19:21:42 2007
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "ATI Technologies Inc Radeon Mobility M6 LY" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

Here is my Xorg.conf file if only slightly reorganised:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
	Load	"dri"
	Load	"dbe"
	Load	"glx"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"radeon"
#	BusID		"PCI:1:0:0"
#	Option 		"AddARGBGLXVisuals" "True"
#	Option          "XAANoOffscreenPixmaps"
#EndSection

#Edited Here

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

Optimized values (changed from driver default)
	Option 		"AddARGBGLXVisuals" "True"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#These are not mentioned in man page for driver
	Option		"AGPSize" "16" # default: 8
	Option		"EnableDepthMoves" "true"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

EndSection

#Edit Ends Here

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

It has me scratching my head a bit because I don't know what to change to make it work.

Any time on this would be greatly appreciated :smile:

---

### Post by veebis on 2007-08-10
Thinkpad T41, ATI Radeon FireGL 9000 R250 (r.2) @ 1400x1050

Everything's peachy, don't need desktop fx, loving it, EXCEPT:
**No resume after suspend.** 
Bluetooth lights up, drive spins up, apparently everybody "wakes up" but the screen, which remains completely black (no back light). 
NOTHING wakes it; I have to hard power down and reboot.

It's been weeks.
Latest Feisty updates, nothing custom (stock driver), no major tweaks.
Don't need hibernate, just need **ram** suspend to work...

_Any_ help at all would be greatly, greatly appreciated!
TIA,
-Vb

---

### Post by javaJake on 2007-08-12
Apparently this is a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77736](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77736)

They'll want you to "add the full output of 'lspci -vv' and 'lspci -vvn' to your bug report as an attachment" (first comment down).

Knowing what computer you have would help as well to find a solution. If you create a new thread with the information you've already provided and the model of your computer, and link to it here, I'll visit it and continue to help you out however I can.

---

### Post by cmlewin on 2007-08-17
will this allow me to get beryl/compiz like effects? or even just a damn dock :) ?

---

### Post by rexy on 2007-08-18
i have a Dell C610(P3,1Ghz)  with a 16Mb ATI mobility radeon M6 LY.

I finnally got the radeon driver to work. Odly the ati driver said i had direct rendering too, not sure what that means, but compiz doesnt work with that.

anyway, the radeon drivers prove unstable, i get artifacts and within a few minutes the system hangs, i do have a samsun 19" mon connected on the secondary output. But no fbthingy or xinerama configured. WHat can i do to make the radeon driver stable. I am running feisty 7.04 with all patches.

---

### Post by tyggna1 on 2007-08-31
Javajake:  You're my new best friend!

I can game again--and I can play a FPS game on my machine--which is  better than it could do in windows.

Thanks!

---

### Post by angelsneverdie on 2007-09-03
thanks for the guide

---

### Post by rockett15 on 2007-09-10
I have got 3d acceleration working fine. See below for my xorg.conf

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

However, as soon as I go to enable Beryl. It loads, the effects are active. However, the screen starts to go garbled - see screenshot below. Anyone seen this and has a solution?

[[IMG]http://img76.imageshack.us/img76/9125/screenshotqz2.th.png[/IMG]](http://img76.imageshack.us/my.php?image=screenshotqz2.png)

---

### Post by ckgreenman on 2007-10-15
Ok,  Here's a wierd one.   I have a Toshiba Satellite 1905-S303 with a Radeon Mobility M6 LY.  I followed the steps outlined in the HOWTO but the I run glxinfo it says direct rendering is not enabled.

$ glxinfo -display :0 |grep direct
direct rendering: No


but when I look in the Xorg.0.log file it says it IS enabled:

$ grep Direct /var/log/Xorg.0.log
(II) RADEON(0): Direct rendering enabled


Which one do I believe and is direct rendering truly enabled?

---

### Post by kk_furtiva on 2007-10-15
hi everybody!

i finally got my  ATI Mobility Radeon M6 LY to properly work under Feisty.

I'm getting 425 FPS with glxgears. Does anybody knows if this is OK? Because i've tried with tons of combinations and I can't get more FPS than these...

Here's my xorg.conf file.

Cheers,
kk_furtiva

---

### Post by elmo2k3 on 2007-10-16
> **ckgreenman said:**
> Ok,  Here's a wierd one.   I have a Toshiba Satellite 1905-S303 with a Radeon Mobility M6 LY.  I followed the steps outlined in the HOWTO but the I run glxinfo it says direct rendering is not enabled.

$ glxinfo -display :0 |grep direct
direct rendering: No


but when I look in the Xorg.0.log file it says it IS enabled:

$ grep Direct /var/log/Xorg.0.log
(II) RADEON(0): Direct rendering enabled


Which one do I believe and is direct rendering truly enabled?
Hi,

just the same Problem here. I'm using Gutsy Gibbon ...

---

### Post by dscoular on 2007-10-20
Hi All,
Here's a weird one...

I have a Sony Vaio PCG-C1MT (aka PCG-C1MV in the US) with a:

00:0c.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

Direct rendering with the "radeon" driver worked perfectly after following this guide with Feisty but after upgrading to Gutsy and trying various combinations from the guide I'm getting no joy:

(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 9000 kB of video memory needed at this resolution and depth.

The resolution is 1280x600x16... which WAS working fine under Feisty,
this is an 8MB Radeon that had no problem with DRI before.

Also, my ALi5451 audio now plays very wobbly, warbly sound where it used to be perfect under Feisty:

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)

Guess I'll try the downgrade Gutsy to Feisty steps found at:

[http://ubuntuforums.org/showpost.php?p=2604826&postcount=2](http://ubuntuforums.org/showpost.php?p=2604826&postcount=2)

:confused:

Cheers,

Doug

---

### Post by itsbradman on 2007-10-26
Did this work?  Were you using compiz in feisty and did downgrading allow it to work again?

---

### Post by itsbradman on 2007-10-27
I did it!!! OK, the prob is with the new drivers that comae with gutsy and xgl itself. If everything was working in feisty and you are using a radeon m9000 with the "mesa" problem, what you do is uninstall xgl "sudo apt-get remove xserver-xgl". Then you have to unistall the new drivers and reinstall the open source drivers from feisty. A walkthrough is on this page:[http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon](http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon)
everything is working like a charm now!!!!

---

### Post by dscoular on 2007-10-27
Hi All,

itsbradman wrote:
 >Did this work? Were you using compiz in feisty and did downgrading 
> allow it to work again? 

After following the apt "pinning" instructions and trying various different methods I just could not get my machine to downgrade back to Feisty.

Then I saw your next posting and checked that I didn't have the
xserver-xgl (which I don't). So I'm kind of stuck with no 3D direct
rendering, no XV 2D graphics and no decent audio. Sheesh.

Cheers,

Doug

---

### Post by itsbradman on 2007-10-27
> **dscoular said:**
> Hi All,

itsbradman wrote:
 >Did this work? Were you using compiz in feisty and did downgrading 
> allow it to work again? 

After following the apt "pinning" instructions and trying various different methods I just could not get my machine to downgrade back to Feisty.

Then I saw your next posting and checked that I didn't have the
xserver-xgl (which I don't). So I'm kind of stuck with no 3D direct
rendering, no XV 2D graphics and no decent audio. Sheesh.

Cheers,

Doug

follow the link I provided on how to install the open source driver.  it worked for me.

---

### Post by itsbradman on 2007-10-27
for some reason the link keeps getting truncated.  Here it is again.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by dscoular on 2007-10-30
Hi All,
The solution for my Sony Vaio PCG-C1MT (aka PCG-C1MV in the US)
DRI issue was given to me by Alex Deuchar on the dri-users list.

The error below:

(EE) RADEON(0): Static buffer allocation failed. Disabling DRI.
(EE) RADEON(0): At least 9000 kB of video memory needed at this resolution and depth.

Is caused because the new xrandr module doesn't detect the
weird 1280x600 dimensions: here's what Alex said plus the solution:

Alex Deucher wrote:
>  > Add the following line to the display subsection of the screen section
>  > of your config:
>  >
>  > Virtual 1280 600
>  >
>  > With the new randr code we pre-allocate a framebuffer until we get ttm support.

So now I have glxgears running at a hair raising 400fps instead
of an underwhelming 30fps.

Cheers,

Doug

---

### Post by Quash on 2007-11-10
I must say, this guide works.  But my sony z1va  is extremely slow with 3d performance enabled.  Its unbearable, thus I have uninstalled it all.  Also when I change the depth from 24 to 16, I just get a white screen.  Did anyone else encounter this?

---

### Post by Dr.Suave on 2007-11-14
I followed part one of your tutorial your tutorial exactly (except I installed the 3D Driver last instead of first) - but here's what I get with the  cat /var/log/Xorg.0.log | grep EE command:
```

wilf@ubuntu-laptop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Loading extension MIT-SCREEN-SAVER
```

Here's my xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section	"InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"		"xorg"
	Option		"XkbModel"		"pc105"
	Option		"XkbLayout"		"gb"
EndSection

Section	"InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section	"InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"stylus"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"eraser"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"cursor"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

#Section	"Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section	"Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section	"Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection	"Display"
	Modes		"1400x1050"
	EndSubSection
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section	"ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice	"stylus"	"SendCoreEvents"
#	InputDevice	"cursor"	"SendCoreEvents"
#	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

What's going on!?:confused:
Thanks for the great tutorial - lets hope I can make it work too.

PS I'm on Gutsy using an ATI Mobility Radeon M6 LY on a Dell Inspiron 4100

Any more info needed and I will gladly provide!

EDIT:

Maybe this could help:

```
wilf@ubuntu-laptop:~$ LIBGL_DEBUG="verbose" glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: radeon_dri.so
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: radeon_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
wilf@ubuntu-laptop:~$
```

---

### Post by javaJake on 2007-11-18
Sorry about not responding, folks! My e-mail hasn't been notifying me of responses lately. :(

> **rockett15 said:**
> I have got 3d acceleration working fine. See below for my xorg.conf



However, as soon as I go to enable Beryl. It loads, the effects are active. However, the screen starts to go garbled - see screenshot below. Anyone seen this and has a solution?

[[IMG]http://img76.imageshack.us/img76/9125/screenshotqz2.th.png[/IMG]](http://img76.imageshack.us/my.php?image=screenshotqz2.png)

itsbradman recommended a solution at this link: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

While I haven't tried it (I'm using Gutsy, in which Beryl does not exist) itsbrainman says it worked for him.

> **ckgreenman said:**
> Ok,  Here's a wierd one.   I have a Toshiba Satellite 1905-S303 with a Radeon Mobility M6 LY.  I followed the steps outlined in the HOWTO but the I run glxinfo it says direct rendering is not enabled.

$ glxinfo -display :0 |grep direct
direct rendering: No


but when I look in the Xorg.0.log file it says it IS enabled:

$ grep Direct /var/log/Xorg.0.log
(II) RADEON(0): Direct rendering enabled


Which one do I believe and is direct rendering truly enabled?

The first one, and no, direct-rendering is not enabled. If you give me the entire Xorg.0.log, I'll be able to further help you.

> **kk_furtiva said:**
> hi everybody!

i finally got my  ATI Mobility Radeon M6 LY to properly work under Feisty.

I'm getting 425 FPS with glxgears. Does anybody knows if this is OK? Because i've tried with tons of combinations and I can't get more FPS than these...

Here's my xorg.conf file.

Cheers,
kk_furtiva

Thanks for your xorg.conf. 400+ is unusual for the M6 LY card, so I'll be taking a look at your configuration. :D

> **itsbradman said:**
> for some reason the link keeps getting truncated.  Here it is again.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

Thanks for that link! I'll place this in the Troubleshooting section.

> **dscoular said:**
> Hi All,
The solution for my Sony Vaio PCG-C1MT (aka PCG-C1MV in the US)
DRI issue was given to me by Alex Deuchar on the dri-users list.

The error below:

(EE) RADEON(0): Static buffer allocation failed. Disabling DRI.
(EE) RADEON(0): At least 9000 kB of video memory needed at this resolution and depth.

Is caused because the new xrandr module doesn't detect the
weird 1280x600 dimensions: here's what Alex said plus the solution:

Alex Deucher wrote:
>  > Add the following line to the display subsection of the screen section
>  > of your config:
>  >
>  > Virtual 1280 600
>  >
>  > With the new randr code we pre-allocate a framebuffer until we get ttm support.

So now I have glxgears running at a hair raising 400fps instead
of an underwhelming 30fps.

Cheers,

Doug

Interesting... what version of Ubuntu are you running?

> **Dr.Suave said:**
> I followed part one of your tutorial your tutorial exactly (except I installed the 3D Driver last instead of first) - but here's what I get with the  cat /var/log/Xorg.0.log | grep EE command:
```

wilf@ubuntu-laptop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Loading extension MIT-SCREEN-SAVER
```

Here's my xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section	"InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"		"xorg"
	Option		"XkbModel"		"pc105"
	Option		"XkbLayout"		"gb"
EndSection

Section	"InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section	"InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"stylus"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"eraser"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

Section	"InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"		"/dev/input/wacom"
	Option		"Type"			"cursor"
	Option		"ForceDevice"		"ISDV4"		# Tablet PC ONLY
EndSection

#Section	"Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section	"Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section	"Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section	"Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection	"Display"
	Modes		"1400x1050"
	EndSubSection
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section	"ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice	"stylus"	"SendCoreEvents"
#	InputDevice	"cursor"	"SendCoreEvents"
#	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

What's going on!?:confused:
Thanks for the great tutorial - lets hope I can make it work too.

PS I'm on Gutsy using an ATI Mobility Radeon M6 LY on a Dell Inspiron 4100

Any more info needed and I will gladly provide!

EDIT:

Maybe this could help:

```
wilf@ubuntu-laptop:~$ LIBGL_DEBUG="verbose" glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: radeon_dri.so
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: radeon_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
wilf@ubuntu-laptop:~$
```

It looks like you've put your system through the ringer with all kinds of fixes and hacks. There's a lot of files that are incorrect or missing, possibly because you tried unofficial driver repositories, you compiled your own, or, worst of all, you tried the fglrx drivers (which are bad luck as far as I know). You will most likely need to make a new installation. :(

---

### Post by wingnut_nz on 2007-12-01
> **dscoular said:**
> Hi All,
The solution for my Sony Vaio PCG-C1MT (aka PCG-C1MV in the US)
DRI issue was given to me by Alex Deuchar on the dri-users list.

The error below:

(EE) RADEON(0): Static buffer allocation failed. Disabling DRI.
(EE) RADEON(0): At least 9000 kB of video memory needed at this resolution and depth.

Is caused because the new xrandr module doesn't detect the
weird 1280x600 dimensions: here's what Alex said plus the solution:

Alex Deucher wrote:
>  > Add the following line to the display subsection of the screen section
>  > of your config:
>  >
>  > Virtual 1280 600
>  >
>  > With the new randr code we pre-allocate a framebuffer until we get ttm support.

So now I have glxgears running at a hair raising 400fps instead
of an underwhelming 30fps.

Cheers,

Doug


I also have a Sony Vaio PCG-C1MT and did a fresh install of Gusty.
I followed the guide up to the (EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth point then tried Doug's suggestion of adding the Virtual 1280 600 reference and it worked sweet.

I also struck problems with the sound card. Does not yet work on my fresh install, but used to run under Feisty. I will have to have a play see what is wrong. Thought I'd install Quake3 and see what frame rate I get from that.
Currently getting around 320 FPS with glxgears.

---

### Post by Papa-san on 2007-12-05
Doing the dapper to edgy apt-get update frogged up my entire system.

My error is```
 (EE) Unable to find a valid framebuffer device
(EE) RADEON(0): failed to open framebufferdevice cosult warnings and/or errors above for possible reasons
```
The warnings and 'Information' list is 400 to 600 lines long. (at a guess.. it takes a full minute to scroll from the top to bottom)

---

### Post by craigtyson on 2007-12-05
Cool.  HW acceleration backup and running on my IBM X31 laptop running gutsy

Followed the instructions on page 1.  

For info was able to get this running even after having previously installing the ATI driver from AMD.  The uninstall works (use the envy package if unsure)

Cheers and AAAARRRRRRGGGG open arena here I come.......

---

### Post by soviet911 on 2008-01-02
TThank you helped my Mobility Radeon M6 LY on HP omnibook 6100 running on Gutsy. :popcorn:

---

### Post by stillka on 2008-01-04
Hello,

thank you very much for the great tutorial. Compiz-fusion is working very well on my Compaq n410C with 16bit colors. (cca 85fps in desktop in compiz benchmark)

Bye

---

### Post by Onyros on 2008-01-04
> **craigtyson said:**
> Cool.  HW acceleration backup and running on my IBM X31 laptop running gutsy

Followed the instructions on page 1.  

For info was able to get this running even after having previously installing the ATI driver from AMD.  The uninstall works (use the envy package if unsure)

Cheers and AAAARRRRRRGGGG open arena here I come.......Can you set your resolution to 100 DPI, using the DisplaySize setting in your xorg.conf?

I'm having trouble with that ever since the upgrade to Gutsy, which makes my fonts in Fluxbox and Awesome (WM) look worse than they would @ 100 DPI.

xdpyinfo always throws out a "96 x 96 DPI" resolution, and I want it @ 100 x 100 DPI (1024 x 768 - therefore with DisplaySize  260 195 in my xorg.conf, Monitor section).

The strange thing is this is working for me in my Arch installation, with the exact same xorg.conf.

I've tried modelines, the works, but haven't found a way to correct this. Also, ever since the upgrade to Gutsy when I try running some apps in fullscreen they come out grainy as if they're being extended from a lower resolution (e.g., xmame games in fullscreen).

---

### Post by Dngrsone on 2008-01-05
I'm running fresh Ubuntu 7.10 (Gutsy Gibbon) on a Dell Latitude C610 with a Radeon M6 LY (16MB).

I have compiz and Emerald installed, but having problems getting 3D to work so I can take advantage of those modules.

First, my xorg.conf:

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

#       FontPath        "/usr/share/X11/fonts/cyrillic"
        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
	Load  "GLcore"
EndSection
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB Receiver" 
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
	Identifier "ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Driver "radeon"
	BusID "PCI:1:0:0"
	#Option "RenderAccel" "true"
	#Option "SubPixelOrder" "NONE"
	#Option "MergedFB" "false"
	Option "BackingStore" "true"
	#Option "Accel"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "true"
	#Option "ForcePCIMode" "true"
	Option "EnableDepthMoves" "true"
	#Option "NoBackBuffer" "false"
	Option "UseInternalAGPGART" "no"
	Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies, Inc. Radeon Mobility 9000 (M6 LY)"
	Monitor "Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x640" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x640" "640x480"
	EndSubSection
	SubSection "Display" #Not recommended - might overload framebuffer
		Depth		24
		Modes		"1024x768" "800x640" "640x480"
	EndSubSectionEndSection


Section "DRI"
        Mode         0666
EndSection
```

My Xorg.0.log is attached.

glxinfo:

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Lastly, the dialog when I force compiz to work:

```
$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (512): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald


```

I get effects when I run this, but the cube, for instance, is very choppy and rough.

I read this entire thread, and tried to do everything that would seem to help (I think), so what have I missed or screwed up?

---

### Post by craigtyson on 2008-01-08
> **Onyros said:**
> Can you set your resolution to 100 DPI, using the DisplaySize setting in your xorg.conf?

I'm having trouble with that ever since the upgrade to Gutsy, which makes my fonts in Fluxbox and Awesome (WM) look worse than they would @ 100 DPI.

xdpyinfo always throws out a "96 x 96 DPI" resolution, and I want it @ 100 x 100 DPI (1024 x 768 - therefore with DisplaySize  260 195 in my xorg.conf, Monitor section).

The strange thing is this is working for me in my Arch installation, with the exact same xorg.conf.

I've tried modelines, the works, but haven't found a way to correct this. Also, ever since the upgrade to Gutsy when I try running some apps in fullscreen they come out grainy as if they're being extended from a lower resolution (e.g., xmame games in fullscreen).

What happens if you startx  using the override switches or 100dpi?

---

### Post by Onyros on 2008-01-08
> **craigtyson said:**
> What happens if you startx  using the override switches or 100dpi?Ah ha, bingo! I used

```
startx -- -dpi 100
```

and it gave me the right resolution (100 x 100 DPI). I'm using GDM as login manager, are there any override settings I should look into to make sure X starts @ 100 x 100 DPI?

edit: OK, I nailed it. I edited the gdm.conf at /etc/gdm, so that the standard server starts at 100 DPI.
```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 100
```

Many thanks for your help, mate :)

But I suppose this is a little unexpected, shouldn't the xorg.conf DisplaySize setting get this right instead?

---

### Post by Dngrsone on 2008-01-09
I found [this bug report](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519) pertaining to the line I am failing (including a couple posts specifying the Radeon M6 LY) and wonder if the suggested hack would be a good idea.

> try to comment out lines 229 to 232 in /usr/bin/compiz and see if it enables composition

---

### Post by javaJake on 2008-01-12
> **Dngrsone said:**
> I found [this bug report](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/124519) pertaining to the line I am failing (including a couple posts specifying the Radeon M6 LY) and wonder if the suggested hack would be a good idea.

It's worth a shot, but I would suggest first making a copy of the original file first before making changes.

The people in launchpad.net usually know more about this than I, so I'd trust their opinion if they think it might fix something.

---

### Post by mrbubbles on 2008-01-14
I've got a HP Pavilion ze5000s with an ati radeon mobility m6 16mb (I believe... I'm not sure how to find out how much memory it has :P)

anyway, here's xorg:
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
#	DefaultDepth	24
#	SubSection "Display"
#		Modes		"1400x1050"
#	EndSubSection
EndSection
	
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


Any ideas?  I still get a NO when i check for direct rendering.

thanks!

---

### Post by Dngrsone on 2008-01-14
> **javaJake said:**
> It's worth a shot, but I would suggest first making a copy of the original file first before making changes.

The people in launchpad.net usually know more about this than I, so I'd trust their opinion if they think it might fix something.

So far it is working fine in default depth 24 @ 1024x768  [img]http://xs117.xs.to/xs117/07270/nod.gif[/img]

---

### Post by neil_mcd on 2008-01-15
Hi, thanks for the tutorial,

Followed all steps for my Sony Vaio PCG-Z1VCP (Mobility M6 LY 16mb, Ubuntu 7.1) to enable visual effects etc. No stability problems prior to upgrade.
Had to knock down colour depth to 16bit (DefaultDepth setting) in order to enable direct rendering (native resolution is 1400x1050).
Unfortunately I encountered slow scrolling of web pages and slow effects with Visual Effects enabled.
This method works, but my machine is just not up to snuff.

Cheers all the same,

Neil

---

### Post by jon.reeve on 2008-03-26
Has anyone got 3d / compiz to work with the ATI Mobility Radeon M6 LY in Hardy? I had mine working in gutsy but since I upgraded it hasn't worked. I heard something about the radeon driver being blacklisted (?!). I have no idea what to do about this.

---

### Post by majornoob on 2008-03-27
I've got DRI working on Kubuntu Hardy Beta, but no Compiz yet.  When I try to start effects, the screen flickers for a sec but nothing really happens.  Still working on it.  I'll post my xorg.conf if you need it.

---

### Post by majornoob on 2008-04-04
I got Compiz to start (Kubuntu Hardy).  After enabling DRI and adding the Composite extension (see xorg.conf attached), I had to remove the ATI blacklist from /usr/bin/compiz by commenting out lines 269-278 (see attached).  To start the effects, use the normal method for your distro (Kubuntu: Menu -> System -> Desktop Effects).

It doesn't work well right now, but you can flip the desktop and stuff around.  I'll work on fine-tuning it, but I'm still not good at any of this stuff.

I couldn't upload the files with the names as-is, so just ignore the .txt extension.

---

### Post by majornoob on 2008-04-13
I've changed my (Kubuntu Hardy) xorg setup to more closely reflect the advice in the first post of this thread.  Seems to work better, but I don't know what most of the stuff in the file does.

Latest update to compiz also seems to be more stable.  Remember to comment out the lines in *usr/bin/compiz* as in my previous post.

There are still a few bugs, but it is now pretty usable at 1400x1050x16.

xorg.conf:
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"	"on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen		0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
	Option		"DynamicClocks"	"on"
	Option		"TripleBuffer"	"true"
	Option		"ColorTiling"	"on"
	Option		"DRI"		"true"
	Option		"EnablePageFlip" "true"
	Option		"AGPFastWrite"	"on"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPSize"	"16"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
	Option	"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	16
	Option		"AddARGBGLXVisuals" "true"
	SubSection "Display"
		Depth	16
		Virtual	1400	1050
		Modes	"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
#	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
	Load		"dbe"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection



---

### Post by Alan Coleman on 2008-05-13
Hi havin a bit o problem with 3d and have posted some info as suggested.
onwards!


summer@summer-laptop:~$ sudo gedit /etc/X11/xorg.conf
[sudo] password for summer: 
summer@summer-laptop:~$ glxinfo | grep direct
direct rendering: Yes
summer@summer-laptop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
summer@summer-laptop:~$ 

                          ---------------

It would seem I have Direct Rendering. But the next part isnt happening??
note: Im using Hardy. The moduals section was not listed in the  /etc/X11/xorg.conf  file. so ignored that part...onwards

Bellow the file its self.
                         -----------------

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"

EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

 so so you get the idea, any insight greatly appreciated.

Alan C
is this what you ment when you said post the file?

---

### Post by bucky0 on 2008-05-16
I just wanted to say that I was having tons of trouble getting 3D acceleration, but I reinstalled from the new 8.04 release and everything works great with one minor change in the xorg.conf. I have the radeon m6 LY 16 mb on a dell c610. I had upgraded from 6.04 all the way to 8.04 little by little over the past two years which I think caused things to get wonky.

Attached is my xorg.conf. Hope it helps.

amelo@amelo-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
    [B]SubSection "Display"
	    Depth           16
	    Modes           "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection[/B]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by ergosteur on 2008-05-20
i have a Fujitsu lifebook e6644 with the Radeon M6 LY running a clean install of Hardy. I was wondering what effect this howto has on the new xorg features in 8.04 seeing as most of the configuration options have been removed from the xorg.conf in favour of xrandr.

---

### Post by coombesy on 2008-06-18
Mobilty M6 LY not working.

Hi,
I've been trying to get this to work but no joy.
Ubuntu Hardy (updated)
Sony Vaio PCG-Z1SP
16MB graphics ram
512MB system ram
1.5 ghz centrino

i've gone through both parts and
> cat /var/log/Xorg.0.log | grep EE

still returns:
> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 19800 kB of video memory needed at this resolution and depth.


i've turned of my resolution and screen sizes in xorg.conf but still no joy. I think i may have found a card that just won't work?
my xorg.conf is:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ie"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY [Radeon Mobility 7500]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"BusType" "PCI"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#	Option		"UseFBDev"		"true"
#EndSection

Section "Module"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection	

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
#	DefaultDepth	24
#	SubSection "Display"
#		Modes		"1400x1050"
#	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

it seems that dri needs 19MB of memory, is there a way to share my on board ram with my graphics?

---

### Post by bucky0 on 2008-06-18
This is what works with my card.

amelo@amelo-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 L


> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "radeon"
	Option "VideoKey" "0x01"
#	Option "GartSize" "128"
	Option "AGPSize" "64"
    
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
    SubSection "Display"
	    Depth			16
	    Modes           "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection



---

### Post by bucky0 on 2008-06-18
Most importantly, you need to drop down the color depth or resolution (to be able to fit 2 buffers into video ram) and add some more AGP memory to give compiz enough room for textures.

The videokey line enables hardware accelerated video playback.

---

### Post by coombesy on 2008-06-18
hi bucky0,

i tried your configuration, no joy. After logging on my screen went completely blank. Could use my shortcut keys to open the terminal but only a white box on a black sreen appeared.

Went through the main differences between our conf's at recovery shell and i've implemented what works.

But still no dri!
> 
:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 19800 kB of video memory needed at this resolution and depth.
:~$ 


my config so far is:
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ie"
#	Option		"XkbVariant"	"ie"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

#Section "Device"
#	Identifier	"Configured Video Device"
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "64" # default: 8
	Option		"EnableDepthMoves" "true"
	Option		"VideoKey" "0x01"
EndSection

Section "Module"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

but one that your advice has done is speed things up, but its still not workable.

About adding more AGP memory to compiz? is that "Option AGP SIZE 64"? or do i have to change another setting?

i'm grateful for your time,
cheers.

---

### Post by bucky0 on 2008-06-18
coombesy-

I'd try two things:

Firstly, you need to change your color depth in the Screen section. That non-enough-memory for DRI error is because at your current color depth and resolution, there isn't enough video memory to keep two screen-sized buffers in video ram. Bump it down to 16bit color instead of 24 bit color and that should get your DRI going.

Additionally, I'd strip out the extra Options in your Device section. When I was trying to get my 3D working, I found that a lot of those options caused stability problems. We're probably working off the same howto's, some of them are particularly old and don't really match up with the current driver versions.

Yeah, the AGP option will add more memory for texturing, which is necessary.

HTH, let me know if it doesn't.

---

### Post by coombesy on 2008-06-18
unfortunately still no joy,

bumped the color to 16 bit, and as soon as i do i only get a blank screen after logging in.
Kept it at 16 and tried setting the resolution but still the same. Turned off all the extras i had from the how to and still the same prob.

Its same as before, screen goes blank and if i hit a shortcut key (ie the one i set up for terminal) i get a white box with no window forms!

Tried to see if i could manualy change the resolution:
System->Preferences->Screen Resolution
and got this error
> The X Server does not support the XRandR extension.
Runtime resolution changes to the display size are not available

Think i might be onto something, maybe i have the wrong server running or something.

---

### Post by bucky0 on 2008-06-18
Can you try using the xorg.conf I posted, restarting your X server then sending me your Xorg.log? you might have to go to one of the consoles to copy /var/log/Xorg.0.log to a different place since when you restart it, it will nuke your logs.

---

### Post by coombesy on 2008-06-18
i've done that, and put the log files on
[http://www.geocities.com/coombes_d/index.htm]("http://www.geocities.com/coombes_d/index.htm")

not too sure if i done i right.
saved the log file
then changed my conf file
restarted X server (ctrl - alt - backspace)
then saved the conf file
restarted my machine and got the same problem, black screen.

---

### Post by bucky0 on 2008-06-18
Quickly looking, for some reason, your screen section isn't clicking. In the 'after' log, it's still saying that it's setting a depth of 24bpp, which is incorrect. It's also saying that it didn't find valid resolutions, which isn't what we want.

Try replacing your entire Screen section with:
> 
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
EndSection

can you do a lspci -v and post that as well?

---

### Post by coombesy on 2008-06-19
> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information
	Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d8000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d0200000-d02fffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: medium devsel, IRQ 255
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at d0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: medium devsel, IRQ 9
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation PCG-Z1SP laptop
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 9
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2

02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at d0203000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00004400-000044ff
	I/O window 1: 00004800-000048ff
	16-bit legacy interface ports at 0001

02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d0202000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 66, IRQ 9
	Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 4000 [size=64]
	Capabilities: [dc] Power Management version 2

02:0b.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Unknown device 2596
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d0201000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2


prob a long shot but is there any bios settings that could be the prob, forcing it to 24b? i'm using a vaio pcg-z1sp

---

### Post by coombesy on 2008-06-19
tried setting the default depth for the screen and left rest as is. restarted (ctrl alt backspace) and rebooted. Got the same blank screen, problem with any windows i open showin as a white box.

thought maybe a bios setting was causing it (might be goin a bit too deep?)
pheonix bios version R0041G0
only setting i saw was 
'LCD Screen Expansion' 'Yes'

lspci -v:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d8000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d0200000-d02fffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: medium devsel, IRQ 255
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at d0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: medium devsel, IRQ 9
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation PCG-Z1SP laptop
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 9
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at d0203000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 00004400-000044ff
	I/O window 1: 00004800-000048ff
	16-bit legacy interface ports at 0001

02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d0202000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
	Subsystem: Sony Corporation Unknown device 8140
	Flags: bus master, medium devsel, latency 66, IRQ 9
	Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 4000 [size=64]
	Capabilities: <access denied>

02:0b.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Unknown device 2596
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d0201000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by bucky0 on 2008-06-19
No, it's not a bios item (unless you have the world's strangest bios).

Perhaps those aren't the logs you were wanting, or it's pulling setting from another log somewheres. Try putting this (below) in /etc/X11/xorg.conf and then check the clock before you restart the server, look at /var/log/Xorg.0.log and /var/log/Xorg.0.log.old .

just to check, you're completely replacing the xorg.conf and not just hand-editing it, right? The sections might not line up right since you and I have things named differently. Actually, I think that might've been what was it, if the identifiers in your screen, monitor and device sections are different, xorg won't know to put them together.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "radeon"
#	Option "VideoKey" "0x01"
#	Option "GartSize" "128"
#	Option "AGPSize" "64"
#	Option "AGPMode" "4"
#	Option "AGPFastWrite" "true"
#	Option "DynamicClocks" "true"
#    Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
    SubSection "Display"
	    Depth			16
	    Modes           "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection


```

---

### Post by Dngrsone on 2008-06-19
> **bucky0 said:**
> I just wanted to say that I was having tons of trouble getting 3D acceleration, but I reinstalled from the new 8.04 release and everything works great with one minor change in the xorg.conf. I have the radeon m6 LY 16 mb on a dell c610. I had upgraded from 6.04 all the way to 8.04 little by little over the past two years which I think caused things to get wonky.

Attached is my xorg.conf. Hope it helps.

amelo@amelo-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]

Bucky, I have the same machine as you, but things aren't working for me since I went to Hardy.

I made the change to the stock xorg.conf as you outlined above, but no change.  I check for errors and run compiz from a terminal and it outputs:

> 
~$ cat /var/log/Xorg.0.log | grep EE 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


~$ compiz
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 



Any ideas what I'm doing wrong?

---

### Post by bucky0 on 2008-06-19
Dngrsone-

/usr/bin/compiz mistakenly blacklists laptops running with the radeon drivers. There's a bugzilla report about it, but it's not been fixed yet. I've attached my modified version that works.

let me know if that helps.

it wouldn't let me attach it directly, I'm gonna cut and paste it below:

```
#!/bin/sh
# Compiz Manager wrapper script
# 
# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#
# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages
#
# Much of this code is based on Beryl code, also licensed under the GPL.
# This script will detect what options we need to pass to compiz to get it
# started, and start a default plugin and possibly window decorator.
# 


COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

if [ -x $METACITY ]; then
	FALLBACKWM="${METACITY}"
elif [ -x $KWIN ]; then
	FALLBACKWM="${KWIN}"
else
	FALLBACKWM=true
fi
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS="core"
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Default X.org log if xset q doesn't reveal it
XORG_DEFAULT_LOG="/var/log/Xorg.0.log"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
	if [ "x$VERBOSE" = "xyes" ]; then
		printf "$*"
	fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 0;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

# Check for non power of two texture support
check_npot_texture()
{
	verbose "Checking for non power of two support: "
	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for presence of FBConfig
check_fbconfig()
{
	verbose "Checking for FBConfig: "
	if [ "$INDIRECT" = "yes" ]; then
		$GLXINFO -i | grep -q GLX.*fbconfig 
		FB=$?
	else
		$GLXINFO | grep -q GLX.*fbconfig 
		FB=$?
	fi

	if [ $FB = "0" ]; then
		unset FB
		verbose "present. \n"
		return 0;
	else
		unset FB
		verbose "not present. \n"
		return 1;
	fi
}


# Check for TFP
check_tfp()
{
	verbose "Checking for texture_from_pixmap: "
	if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		if [ "$INDIRECT" = "yes" ]; then
			unset LIBGL_ALWAYS_INDIRECT
			INDIRECT="no"
			return 1;
		else
			verbose "Trying again with indirect rendering:\n";
			INDIRECT="yes"
			export LIBGL_ALWAYS_INDIRECT=1
			check_tfp;
			return $?
		fi
	fi
}

# Check wether the composite extension is present
check_composite()
{
	verbose "Checking for Composite extension: "
	if xdpyinfo -queryExtensions | grep -q Composite ; then
		verbose "present. \n";
		return 0;
	else
		verbose "not present. \n";
		return 1;
	fi
}

# Detects if Xgl is running
check_xgl()
{
	verbose "Checking for Xgl: "
	if xvinfo | grep -q Xgl ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		return 1;
	fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
    if [ ! -x "$NVIDIA_SETTINGS" ]; then
	return 0
    fi

	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
	if [ $MEM -lt $NVIDIA_MEMORY ]; then
		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
		return 1;
	fi
	return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
		return $NVIDIA_INTERNAL_TEST;
	fi
	verbose "Checking for nVidia: "
	if xdpyinfo | grep -q NV-GLX ; then
		verbose "present. \n"
		NVIDIA_INTERNAL_TEST=0
		return 0;
	else
		verbose "not present. \n"
		NVIDIA_INTERNAL_TEST=1
		return 1;
	fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	fi
	verbose "Passed.\n"
	return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
	LOG=$(xset q|grep "Log file"|awk '{print $3}')
	if [ "$LOG" = "" ]; then
	    verbose "xset q doesn't reveal the location of the log file. Using fallback $XORG_DEFAULT_LOG \n"
	    LOG=$XORG_DEFAULT_LOG;
	fi
	if [ -z "$LOG" ];then
		verbose "AIEEEEH, no Log file found \n"
		verbose "$(xset q) \n"
	return 0
	fi

	#don't run on laptops using ati driver
	if laptop-detect; then
		for DRV in ati radeon; do
	                if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
        	           ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG;
                	then
				verbose "Found laptop using ${DRV} driver. \n"
	                        return 1
        	        fi
		done
	fi

	for DRV in ${WHITELIST}; do
		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
		then
			return 0
		fi
	done
	verbose "No whitelisted driver found\n"
	return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
	OUTPUT=$(lspci -n)
	for ID in ${BLACKLIST_PCIIDS}; do
		if echo "$OUTPUT" | egrep -q "$ID"; then
			verbose "Blacklisted PCIID '$ID' found \n"
			return 0
		fi
	done
	OUTPUT=$(lspci -vn | grep -i VGA)
	verbose "Detected PCI ID for VGA: $OUTPUT\n"
	return 1
}

build_env()
{
	if check_nvidia; then
		ENV="__GL_YIELD=NOTHING "
	fi
	if [ "$INDIRECT" = "yes" ]; then
		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
	fi
	if check_xgl; then
		if [ -f ${LIBGL_NVIDIA} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
			verbose "Enabling Xgl with nVidia drivers...\n"
		fi
		if [ -f ${LIBGL_FGLRX} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
			verbose "Enabling Xgl with fglrx ATi drivers...\n"
		fi
	fi

	ENV="$ENV FROM_WRAPPER=yes"

	if [ -n "$ENV" ]; then
		export $ENV
	fi
}

build_args()
{
	if [ "x$INDIRECT" = "xyes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if check_nvidia; then
		if [ "x$INDIRECT" != "xyes" ]; then
			COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
		fi
	fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
	test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
	abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
	INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
	# if vesa or vga are in use, do not even try glxinfo (LP#119341)
	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
		abort_with_fallback_wm
	fi
	# check if we have the required bits to run compiz and if not, 
	# fallback
	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
		abort_with_fallback_wm
	fi

	if check_nvidia && ! check_nvidia_memory; then
		abort_with_fallback_wm
	fi

	if ! check_fbconfig; then
		abort_with_fallback_wm
	fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

if [ "x$CM_DRY" = "xyes" ]; then
	verbose "Dry run finished: everything should work with regards to Compiz and 3D.\n"
	exit 0;
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

```

---

### Post by Dngrsone on 2008-06-19
I cut and pasted your script into /usr/bin/compiz, saved and rebooted, but there is no change, Bucky.  Am I supposed to load or enable XGL or something?

I tried doing skip checks, with the following result (video is unstable after doing this):
 
> ~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered


---

### Post by bucky0 on 2008-06-20
What do you mean unstable? Do windows turn black if you make them too large? If so, try making your AGPSize value in xorg.conf larger.

---

### Post by Dngrsone on 2008-06-20
> **bucky0 said:**
> What do you mean unstable? Do windows turn black if you make them too large? If so, try making your AGPSize value in xorg.conf larger.

Unstable as in every time the machine does a redraw, I end up with a black screen and have to mouse over everything and hope that the window will reappear bit by bit.

---

### Post by coombesy on 2008-06-20
BukyO,

sorry for late reply. Got sick of so done a complete re-install from cd (previous Hardy was an update).
got dri working!! (happy days), screen resolution is back (set it to 1024x800)

updated and installed:
compiz
compizconfig-settings-manager
emerald

but now, can't get desktop effects to enable. Only error i'm getting is the popup "Desktop effects could not be enabled"

```
:~$ glxinfo | grep direct
direct rendering: Yes

:~$ glxgears
2439 frames in 5.0 seconds = 487.711 FPS
2514 frames in 5.0 seconds = 502.608 FPS
2517 frames in 5.0 seconds = 503.283 FPS
2519 frames in 5.0 seconds = 503.610 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 31980 requests (31172 known processed) with 0 events remaining.


```and the above is my glxgears output.

Looks like you might have been right about conflicting xorg.conf's on my old setup ;)

thanks again for your help

*** one more thing i needed to do ***
incase anybody else has the same problem, after getting the above to work i had to follow instruction from:
[HowTo: Compiz Fusion in Hardy on cards with "ati"/"radeon" open source drivers]("http://ubuntuforums.org/showthread.php?t=764633")
which mainly says - in a terminal->
:~$mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

and this one every time i login
:~$compiz --replace &

have a possible solution to my problem. I had tried so many different tutorial etc there's a good change i had the drivers blacklisted!
for anyone else with similar frustrations check:
/etc/modprobe.d/
and see if the radeon or any other necessary drivers are there. (hope this helps ppl, wish i tought of it before i re-installed)

---

### Post by Dngrsone on 2008-07-01
> **Dngrsone said:**
> I cut and pasted your script into /usr/bin/compiz, saved and rebooted, but there is no change, Bucky.  Am I supposed to load or enable XGL or something?

I tried doing skip checks, with the following result (video is unstable after doing this):

I guess my problem isn't interesting enough...

---

### Post by bucky0 on 2008-07-01
No need to be pouty over it. I asked you some questions, you didn't answer them. I neither develop compiz nor the drivers for your video card, so it's hard for me to diagnose anything.

---

### Post by Dngrsone on 2008-07-01
> **bucky0 said:**
> No need to be pouty over it. I asked you some questions, you didn't answer them. I neither develop compiz nor the drivers for your video card, so it's hard for me to diagnose anything.

[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

My apologies... I've been offline for a week and haven't had time to mess with computers lately.  I haven't an AGPSize value right now;  I suppose I should fix that.

---

### Post by bucky0 on 2008-07-01
coombesy-

glad it worked :)

---

### Post by ajc347ha on 2008-07-03
new user to the ubuntu running hardy i followed the how to part 1 when i run glxinfo | grep direct the output says yes but when i go to enable compiz it says that i cannot enable them. my xorg.conf is 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Module"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection


EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

my computer is a dell c610 with ati radeon m6 ly

what do i need to do

---

### Post by bucky0 on 2008-07-03
Use the xorg.conf I posted above. Specifically, change your default depth from 24 to 16.

---

### Post by Dngrsone on 2008-07-03
Okay, so... here's where I am now:


From terminal:

```
~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

/etc/X11/xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Module"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"

	Option "AGPSize" "32" # default: 8

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 16
	SubSection "Display"
		Depth 16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

The AGPSize option did fix the window instability problem, it appears.  So, the question is, how do I get the machine to run compiz normally, instead of forcing it?  This is a Dell Latitude C610 running the M6 LY.

I tried the script for getting around the blacklist, but the machine rejected it and installed the default generic xorg.conf in its place.

---

### Post by bucky0 on 2008-07-03
>> I tried the script for getting around the blacklist, but the machine rejected it and installed the default generic xorg.conf in its place.

I'm confused, it replaced your xorg.conf? That shouldn't happen (read all the warnings at the top of xorg.conf about needing to run a command to have ubuntu update it)

Did you replace your /usr/bin/compiz script with the one I put in? You could also just put a line at the top that says SKIP_CHECKS=1.

Also: The native resolution of this laptop (I have the same one) is 1400x1050, try running in that mode.

---

### Post by Dngrsone on 2008-07-03
> **bucky0 said:**
> >> I tried the script for getting around the blacklist, but the machine rejected it and installed the default generic xorg.conf in its place.

I'm confused, it replaced your xorg.conf? That shouldn't happen (read all the warnings at the top of xorg.conf about needing to run a command to have ubuntu update it)

Did you replace your /usr/bin/compiz script with the one I put in? You could also just put a line at the top that says SKIP_CHECKS=1.

Also: The native resolution of this laptop (I have the same one) is 1400x1050, try running in that mode.

Doh!  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

I put the script in the wrong place!  No, I have it in /usr/bin/compiz... put SKIP_CHECKS=1 right after the paths, still have to force compiz with [COLOR="Green"]SKIP_CHECKS=yes compiz --replace[/COLOR], but now, I get this:

```
~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 
```

There *is* something different going on, I see momentary noise patterns occasionally when opening windows or dropping down the task bar.

When I go to System, Preferences, Screen Resolution, I don't get the option for 1400x1050, even with that value added to the xorg.conf, even with compiz running.

---

### Post by bucky0 on 2008-07-03
Please just replace your xorg.conf with mine, something is futzed up. I have the exact same laptop as you, so it will work.

in the /usr/bin/compiz, just replace the first line of abort_with_fallbackwm to return 1.

---

### Post by Dngrsone on 2008-07-03
> **bucky0 said:**
> Please just replace your xorg.conf with mine, something is futzed up. I have the exact same laptop as you, so it will work.

in the /usr/bin/compiz, just replace the first line of abort_with_fallbackwm to return 1.

Replaced my xorg.conf with the one posted. Assuming this was the change you wanted to compiz:

```
# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 1;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}
```

[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]  No good, no change.

---

### Post by Dngrsone on 2008-07-03
Ah, there was no setting for the Radeon driver... not that adding it helped:

```
~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by bucky0 on 2008-07-03
> **Dngrsone said:**
> Replaced my xorg.conf with the one posted. Assuming this was the change you wanted to compiz:

No, change like this
```
# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
        #THE LINE BELOW###
        return 1;
        #THAT WAS IT###
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 1;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}
```

---

### Post by Dngrsone on 2008-07-03
> **bucky0 said:**
> No, change like this
```
# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
        #THE LINE BELOW###
        return 1;
        #THAT WAS IT###
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 1;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}
```

[IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]  That's what I put...

Double checked, still the same.

---

### Post by bucky0 on 2008-07-03
what's the error if you try to run compiz from the command line (without the SKIP_CHECKS part

---

### Post by Dngrsone on 2008-07-03
> **bucky0 said:**
> what's the error if you try to run compiz from the command line (without the SKIP_CHECKS part

```
~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity 
```

```
~$ compiz
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: /usr/bin/metacity  
```

---

### Post by bucky0 on 2008-07-03
There must be either an error with the way you typed the changes or you're editing the same file.

If the first statement in the function abort_with_fallback_wm() is "return 1;" and it's still falling through to the if case below, then something is ballsed up with the file your editing.

Make sure the ouput from "which compiz" matches the file you are editing.

---

### Post by Dngrsone on 2008-07-03
> **bucky0 said:**
> There must be either an error with the way you typed the changes or you're editing the same file.

If the first statement in the function abort_with_fallback_wm() is "return 1;" and it's still falling through to the if case below, then something is ballsed up with the file your editing.

Make sure the ouput from "which compiz" matches the file you are editing.

I only changed the 0 to a 1... that's all.  There's no error log we could check?

[COLOR="Green"]which compiz[/COLOR] gets me the path to the file I edited: /usr/bin/compiz

---

### Post by bucky0 on 2008-07-03
_Please_ read the changes I marked below:

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{[B]
        #THE LINE BELOW###
        return 1;
        #THAT WAS IT###[/B]

if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 1;
	fi
	
	if [ "x$CM_DRY" = "xyes" ]; then
		verbose "Dry run failed: Problems detected with 3D support.'n"
		exit 1;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

---

### Post by Dngrsone on 2008-07-03
Okay, got it working, now.  Note to self-- Attention to detail!  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/doh.gif[/IMG]

Thanks for your time and patience, bucky!  I appreciate it a lot.

---

### Post by SneakPeak on 2008-07-05
Thank you JavaJake

This worked for me on an HP omnibook xt6200.  I am running Hardy 8.04.  I had the fglrx drivers installed but it seems I got rid of them successfully with:

sudo apt-get remove --purge xorg-driver-fglrx

I also made sure that the "mesa" drivers were there with:

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

I only did the first part up to:

glxinfo | grep direct

Initially the direct rendering was not working.  But the command:

cat /var/log/Xorg.0.log | grep EE

told me that things only worked with 24 or 16 color depth.  I had set the color depth lower because it was the only way I could get in without the system crashing.  I edited the xorg.conf file and put the color depth on 16.  I then got in no problem and direct rendering was working.  I also cranked the resolution up to 1400x1050.  Previously the best I had been able to achieve was 1024x768

Thanks again

Sneaks:)

---

### Post by coorior on 2008-08-24
hi guys , 
i opened a new tread on how to get M6 LY card working on IBM X31 ( probably it will work on other computers , but you have to make all necessary changes yourself ) . on IBM X31 it works perfectly . my how-to is very easy and doesn't require any specific knowledge .

[http://ubuntuforums.org/showthread.php?t=899178](http://ubuntuforums.org/showthread.php?t=899178)

hope this can help you guys.

P.S. i'm also a newbie . i just found how-to on chinese and followed it . works perfectly , so i decided to translate it .

---

### Post by majornoob on 2008-11-16
Hello again everyone.  I seem to be getting serious problems when adding "DefaultDepth 16" to the Ubuntu Intrepid xorg.conf.  Specifically, no window borders are drawn, and white boxes appear instead of notifications (e.g. updates) and gnome-terminal.  DRI works OOB on Intrepid without "DefaultDepth 16", but glxgears reports ~120 fps without this option vs. ~400 fps with it enabled.

Strangely enough, the problem seems to be solved with a "metacity --replace" (with "DefaultDepth 16") after logging into the desktop, so I have added this command to session startup.  This seems like a hackish solution, however, not to mention adding a second or so to login.  Any ideas to solve this problem more elegantly?

---

### Post by underwaterdream on 2008-11-19
[B]is the radeon m6 ly the same has the 7000? i cant be shure.
if it is i guess it means its supported by the new ati beta drivers
anyone ear about that yet ?  can someone answer?

ty alot[/B]

---

### Post by ergosteur on 2008-11-21
> **underwaterdream said:**
> [B]is the radeon m6 ly the same has the 7000? i cant be shure.
if it is i guess it means its supported by the new ati beta drivers
anyone ear about that yet ?  can someone answer?

ty alot[/B]

Yes, the Mobility Radeon M6 LY is the Radeon 7000, although it's  ususally just called "Mobility Radeon". It's based on the desktop Radeon VE (which was renamed to 7000), codenamed RV100.

---

### Post by underwaterdream on 2008-11-30
The ati proprietary linux drivers (catalyst) didnt work with my m6 ly
i had to try it to be shure..(but theres a beta version for windows that supports the 7000 (m6 ly)) does anyone knows about that ? ne1 can answer ? :)  .. and in the ati web page at an linux support driver secction.. clicking on "faq" there's 2 links for alternative drivers (3d accelaration)
the DRI project and another.. "utah.." (something). Id be so aprecciated 
if someone had any infomation about that..

ty all

---

### Post by underwaterdream on 2008-11-30
btw id like to say im very glad with my new OS (ubuntu)

---

### Post by Rogbert on 2009-01-09
Does anyone know if this works in 8.10?  Was working perfect in Gutsy, but then I upgraded.  Now compiz works, but really slow.

---

### Post by r2cool on 2009-02-05
I have a Sony Vaio PCG - Z1AP - using Ubuntu 8.04, lspci shows up a Radeon M6 LY card. I followed your instructions and got the following error message on glxinfo 
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 19800 kB of video memory needed at this resolution and depth.

Should I try to get rid of the Type 1? 

I do not have a subsection in my xorg.conf file that configures depth 

Do you want the entire xorg.0.log file (that is huge)? 
Here is the xorg.conf file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#Optimized Values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"
# Left to driver default default 
# 	Option	"RenderAccel" "on" #Default is "on"
# 	Option	"DMAForXv" "on" #Default is on, use default value
#	Option	"SubPixelOrder" "RGB" 
#	Option	"ColorTiling" "on" 
#	Option	"DDCMode" "off" 
# These are not in man pages for driver
	Option	"AGPSize" "32" # default: 8
	Option	"EnableDepthMoves" "true"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Shadowking on 2009-06-05
I'm trying to get my ATi Radeon Mobility M6 LY card working. But every time I change the xorg.conf file, it never gets saved; even after I save it in root. 

I've been trying to solve this in my thread ([http://ubuntuforums.org/showthread.php?t=1178267&page=3](http://ubuntuforums.org/showthread.php?t=1178267&page=3)). If anyone can tell me how to save the changes to my xorg.conf file, I'll be grateful.

---

### Post by scottyec on 2009-06-12
By "save it in root" do you mean you did the command: sudo gedit /etc/X11/xorg.conf ?

I had a problem like yours, it said the file was read-only, so I did that and it works now. 

Scott,

---

### Post by zarej on 2009-06-13
> **Shadowking said:**
> I'm trying to get my ATi Radeon Mobility M6 LY card working. But every time I change the xorg.conf file, it never gets saved; even after I save it in root. 

I've been trying to solve this in my thread ([http://ubuntuforums.org/showthread.php?t=1178267&page=3](http://ubuntuforums.org/showthread.php?t=1178267&page=3)). If anyone can tell me how to save the changes to my xorg.conf file, I'll be grateful.


Try:
$sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

---

### Post by Flake Remix on 2009-06-14
Hello,

I try to get compiz working on my Compaq Evo N160 and Kubuntu 9.04. I have already done the steps from the first post, set DefaultDepth to 16, Direct Rendering is there but still nothing works.

```

$ glxinfo | grep direct
direct rendering: Yes

$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```

I tried compize two ways. First is System Settings -> Desktop -> Enable Desktop Efefcts.

The second: compiz --replace &

Compiz log:
```

Checking for Xgl: not present.    
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log                                                                          
Detected PCI ID for VGA:                                                        
Checking for texture_from_pixmap: not present.                                  
Trying again with indirect rendering:                                           
Checking for texture_from_pixmap: present.                                      
Checking for non power of two support: present.                                 
Checking for Composite extension: present.                                      
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.                                                                     
Checking for Software Rasterizer: Not present.                                  
Checking for nVidia: not present.                                               
Checking for FBConfig: present.                                                 
Checking for Xgl: not present.                                                  
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32                 
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x1a001a6 to texture                                                                        

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x1a00142 to texture                                                                        

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x1a001a6 to texture                                                                        


```

---

### Post by kitor on 2009-06-15
But what's wrong? Looking on your compiz output, you have it running - but without window decorations?

---

### Post by Flake Remix on 2009-06-15
Kind of yes, I don't have window decorations with OpenGL mode, I do have everything working with XRender but it's really really slow (I switch between Xrender and OpenGL in Desktop->Advanced (KDE4)). So the problem is not much about decorations.

I wonder why it says: Checking for texture_from_pixmap: not present.

I also tried: SKIP_CHECKS=yes compiz --replace --indirect-rendering, tried with emerald and what so ever.

To say more, messages "No GLXFBConfig for depth 32" go in an endless loop and they fill any console I open. Untill I kill compiz or replace with kwin.

---

### Post by zx6zx6 on 2009-10-15
> **Flake Remix said:**
> Hello,

I try to get compiz working on my Compaq Evo N160 and Kubuntu 9.04. I have already done the steps from the first post, set DefaultDepth to 16, Direct Rendering is there but still nothing works.



I also have Evo N160, but it's running Xubuntu 9.04. Compiz performs quite well, but my system will hang if I don't use recovery mode (that means the system run in level 1 or 2 with root privilege).
Could you please provide glxinfo output of your system ?
Coz I found that in ubuntu 9.04, glxinfo always gives us "direct rendering: Yes" even when it uses software Mesa lib.

---

### Post by Alex22 on 2009-10-29
> **Flake Remix said:**
> Kind of yes, I don't have window decorations with OpenGL mode, I do have everything working with XRender but it's really really slow (I switch between Xrender and OpenGL in Desktop->Advanced (KDE4)). So the problem is not much about decorations.

I wonder why it says: Checking for texture_from_pixmap: not present.

I also tried: SKIP_CHECKS=yes compiz --replace --indirect-rendering, tried with emerald and what so ever.

To say more, messages "No GLXFBConfig for depth 32" go in an endless loop and they fill any console I open. Untill I kill compiz or replace with kwin.

1. To get frames, maybe you could try compiz-fusion icon (from repo, blue cube as an icon). This small systray program helps to choose or reload window manager (2D or compiz), also choose window decorator. 
Both reloading compiz and choosing other window decorator (if installed) helped me.

2. There is also an option for xorg.conf: 
**Option "AddARGBGLXVisuals" True**
It helped me with my nVidia card.

3. As to the color depth error mesage,  you could set a lower number in your xorg.conf. Like 24 or 16.
Maybe you can paste it here (whole file)?
Do you use Catalyst to tweak?

---

### Post by rrnwexec on 2009-11-16
Since this thread is now up to 37 pages and no mention of 9.10 Karmic Koala, perhaps it's time to move to a database, and freshen the info? This thread might deter a lot of new users.

I've posted the new question here so that we can gather all the 9.10 Karmic Koala information for "ATI Mobility Radeon M6 LY" in one place.

Here's the link: [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/89915](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/89915)

Cheers,
Randall
... in Vancouver

---

### Post by petitchevalroux on 2009-11-27
Hi all, thanks for this thread, it helped me to solve some display artifacts on my Thinkpad X31 (With a ATI Technologies Inc Radeon Mobility M6 graphic card).

I just want to notice you that with Karmic some driver options are no more available :
From my xorg log :
```

(WW) RADEON(0): Option "DynamicClocks" is not used
(WW) RADEON(0): Option "BIOSHotkeys" is not use

```
I replaced Option "DynamicClocks" by :
```

Option          "DynamicPM" "true"

```
Can someone confirm me that both previous options are similar ?

Reading  my Xorg Log, i found some modules have disapear :
#Does not exist Load    "freetype"
#Doest not exist  Load    "type1"
So I recommend to remove it from Xorg config.
      
I made some test with all options from the page 1 and I identify which one
stopped display artefacts (on wifi notification, gnome-do, ressource manager graphics...)

All the artefacts have been remove adding only this option :
```

Option          "AccelMethod" "EXA"

```
I noticed some graphic improvement adding the other options from page 1 at this point here is my device and module xorg.conf section :
```

Section "Device"
 Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon Mobility M6 LY"
        BusID       "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option         "AGPFastWrite" "on"
        Option          "SWcursor" "off" #Faster than default (on)
        Option          "EnablePageFlip" "on" #Faster than default (off)
        Option          "AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is default
        Option          "AGPSize" "32" # default: 8
        Option          "EnableDepthMoves" "true"
        Option          "DynamicPM" "true" 
EndSection
Section "Module"
#Modules loaded from default xorg file
        Load  "record"
        Load  "dbe"
        Load  "extmod"
        Load  "dri"
        Load  "glx"
        Load  "dri2"
#Modules added from page 1
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "int10"
        Load    "vbe"
        Load    "GLcore"
EndSection

```

At the moment, I get a nice working display without compiz and gnome FX (without artefacts).

Enabling compiz or gnome FX (from administration pannel) make my computer crash : display freeze nothing else works => hard reboot :'(

I still need some help to get compiz working (i will try decrease color deph) but i do not know how to get compiz output. Can someone tell me where compiz log ?

I succeed to get some output from compiz before it crashed using : 
```

compiz > compiz.log

```
Here is the log, but i do not found error on it :'( :
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator

```

---

### Post by zcacogp on 2009-11-28
Petitchevalroux, 

I'm more of a beginner than you (as you post testifies!), but I am trying to run Karmic on my X31 as well, and it seems that although it runs, the screen does funny things (distortion, odd lines, very slow performance) if Compiz is switched on. For now I have switched Compiz off, and all is fine, but I'd like those effects back too ... 

I'm going to keep an eye on here and try any suggestions. 


Oli.

---

### Post by petitchevalroux on 2009-11-28
@zcacogp what do you mean by compiz switch off ? (from the GUI System>Preferences>Display ... Desktop effects? or other magical tips :D

with compiz off did you get some strange artefacts on wifi notifications or in the system monitor graphics ? (I ask you because on my X31 it happens with a fresh karmic install)



As you read in my last post I only succeed to stop this artefacts (on notifications with fx off) and freeze my computer when enabling desktop effects ... so i suggest you to don't try my xorg tuning at home for the moment ;)

---

### Post by utnubuuser on 2009-11-29
here is yet another X31 M6 LY xorg.conf file.  --- I don't use 3d on the desktop, ie. compiz-fusion, nor do I play any 3d games, so I can't report on performance in those environments, but for a straight up desktop, this is the fastest, cleanest configuration I've been able to achieve.  Also, I still have a bit of an issue with the notification pop-ups, which were working pretty much perfectly in 9.10 with the fix provided in this thread> [http://ubuntuforums.org/showthread.php?p=8392785]("http://ubuntuforums.org/showthread.php?p=8392785")

here is my current xorg.conf  -- fast and stable (including when in dual screens)> #Thinkpad X31 xorg.conf file/ OS: Ubuntu Lucid Lynx (dev) 10.04 LTS

Section "Device"
Identifier "ATI Radeon M6 LY"
Driver "radeon"
BusID "PCI:1:0:0"
 Option "EnablePageFlip" "on"
 Option          "AccelMethod"    "XAA"
 Option "AGPMode" "4"
 Option "AGPFastWrite" "yes"
 Option "EnablePageFlip" "on"
 Option "RenderAccel" "true"
 Option "DynamicClocks" "on"
 Option "BIOSHotkeys" "on"
EndSection 


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		 "1024x768" "800x600" "640x480"
		Virtual	2048 768
	EndSubSection
E

---

### Post by zcacogp on 2009-11-29
Petitchevalroux, 

As you say, yes - I'm just turning the Compiz effects off by going to System > Preferences > Appearance > Visual Effects and setting it to 'None'. But this means you miss out on all of the Compiz experience - the 3d bits, as well as the more sophisticated window management bits. Which is a shame. 

I've tried to nail down the problem by playing with xorg.conf, and from posts on here it seems that the two key settings are "Accelmethod" (being "XAA" or "EXA") and "Renderaccel" (being "False" or "True"). However, gaving played around with it, none of the combinations allowed me to run compiz - it caused screen oddities on all settings, and with "EXA" and "True", it crashed the machine when I tried to turn compiz on. 

FWIW, here is my xorg file. 

```
Section "Device"
       Identifier      "ATI"
       Driver          "radeon"
       Option          "AccelMethod" "XAA"
       Option          "AGPMode" "4"
       Option          "AGPFastWrite" "yes"
       Option          "EnablePageFlip" "on"
       Option          "RenderAccel" "false"
       Option          "DynamicClocks" "on"
       Option          "BIOSHotkeys" "on"
EndSection



Section "Monitor"
	Identifier	"Configured Monitor"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I'm sure that others, more knowledgable, will tell me that I could do better - in which case I'd like to know! ;)

Utnubuuser - thanks for your xorg copy. You have "XAA" and "True", whereas I have "XAA" and "False", and some other bits. 

In searching, I did find this: 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/391461](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/391461)

... which seems to suggest that there was a known problem with the configuration we have, and it is related to the kernel. I have kernel 2.6.31-15-generic, which is listed as being problemmatical in that post, but the thread goes on to suggest that the problem is fixed, which means that I am probably reading it wrongly. 

All suggestions welcomed. I'm in the same boat as Utnubuuser - I don't use the 3d bits, but it would be nice to have them working (particularly as they worked in 9.04.) 


Oli.

---

### Post by petitchevalroux on 2009-11-29
New tests made today, and new stuff to say : 

DynamicPM option seems to have some problems in Karmic, When I enable it and my screen go to sleep mode I can't wake it up ... So i just turn it off.

utnubuuser reading your xorg.conf file i just have 2 or 3 things to say :

In order to stop notifications artefacts I changed :
```

Option "AccelMethod" "XAA"

```
to 
```

Option "AccelMethod" "EXA"

```
XAA seems to be the default accel method so write it in the conf file seems to be useless to me.

As i sayed in my previous post the following options are not anymore recognized by xorg ati drivers :
```

Option "DynamicClocks" "on"
Option "BIOSHotkeys" "on"

```
So you may remove it without trouble.

From your xorg.conf, i tried adding the RenderAccel settings, and enabling desktop fx but it still freezing my laptop :'(

So at the moment my xorg device settings are :
```
 
Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon Mobility M6 LY"
        BusID       "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "True" #Faster than default (off)
        Option          "SWcursor" "True" #Faster than default (on)
        Option          "EnablePageFlip" "True" #Faster than default (off)
        Option          "AccelMethod" "EXA"
        Option          "RenderAccel" "True"
        Option          "AGPSize" "32" # default: 8
        Option          "EnableDepthMoves" "True"
        #Option          "DynamicPM" "True" Disable because unable to wake up from screen sleep mode

```

---

### Post by SeePU on 2009-11-29
> **utnubuuser said:**
> here is yet another X31 M6 LY xorg.conf file.  --- I don't use 3d on the desktop, ie. compiz-fusion, nor do I play any 3d games, so I can't report on performance in those environments, but for a straight up desktop, this is the fastest, cleanest configuration I've been able to achieve.  Also, I still have a bit of an issue with the notification pop-ups, which were working pretty much perfectly in 9.10 with the fix provided in this thread

here is my current xorg.conf  -- fast and stable (including when in dual screens)
You don't use 3D because then your laptop would crash! 
:rolleyes:

---

### Post by zcacogp on 2009-11-30
> **petitchevalroux said:**
> 

So at the moment my xorg device settings are :
```
 
Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon Mobility M6 LY"
        BusID       "PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "True" #Faster than default (off)
        Option          "SWcursor" "True" #Faster than default (on)
        Option          "EnablePageFlip" "True" #Faster than default (off)
        Option          "AccelMethod" "EXA"
        Option          "RenderAccel" "True"
        Option          "AGPSize" "32" # default: 8
        Option          "EnableDepthMoves" "True"
        #Option          "DynamicPM" "True" Disable because unable to wake up from screen sleep mode

```

PCR, 

Can you post the whole of your xorg.conf file ... when I tried that (above), my machine refused to work at all and would only boot to a Unix prompt ... 


Oli.

---

### Post by zcacogp on 2009-11-30
Gottit! 

This thread here: 

[http://ubuntuforums.org/showthread.php?p=8416481#post8416481](http://ubuntuforums.org/showthread.php?p=8416481#post8416481)

... gave me the answer. It now looks like Karmic works fine, with Compiz, on my X31! I am VERY pleased (many thanks to buellman, if he reads this.) 

FWIW, my entire xorg.conf file now looks like this: 

```
Section "Device"
	Identifier 	"Radeon7500"
	Driver 		"ati"
	BusID 		"PCI:1:0:0"
EndSection 


Section "Device"
	Identifier	"Configured Video Device"
	Option		"AGPMode"		"4"        # optional
	Option		"AGPSize"		"32"      # optional
	Option		"DRI"			"true"    # imprtant
	Option		"DRI2"			"false"  # important
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Does this help anyone else here? 


Oli.

---

### Post by utnubuuser on 2010-03-15
Here is my xorg.conf in Karmic Koala

Fixes OSD corruption issue and results in good frame rates

######################################################################

#Optimized xorg.conf file for X31 with ATI Radeon M6 LY

> #brad@brad-laptop:~$ lspci -nn | grep ATI
#01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]

> #Privides:
#brad@brad-laptop:~$ glxgears
1047 frames in 5.0 seconds
1092 frames in 5.0 seconds
1093 frames in 5.0 seconds
1092 frames in 5.0 seconds
#and temperatures around 53 - 58 Celsius, while all other configurations
#resulted in frame-rates around 400 and temperatures of 68+ Celsius
#This also cures the corrupted OSD Notifications as by using EXA instead of XAA (thanks petitchevalroux)

> Section "Device"
	Identifier 	"Configured Video Device"
	Driver 		"ati"
	BusID 		"PCI:1:0:0"
Option "AccelMethod" "EXA"
Option "RenderAccel" "on" 
Option          "SubPixelOrder" "NONE"
Option		"AGPMode"		"4"        # optional
Option		"AGPSize"		"32"       # optional
Option		"DRI"			"true"     # important
Option		"DRI2"			"false"    # important
     
EndSection

---

### Post by matt! on 2010-03-20
> **utnubuuser said:**
> Here is my xorg.conf in Karmic Koala

Fixes OSD corruption issue and results in good frame rates

######################################################################

#Optimized xorg.conf file for X31 with ATI Radeon M6 LY

Unfortunately this crashes my machine - X31 with same GPU. It hangs at black desktop background when reloading window manager through Compiz Fusion Icon.

I'll try to figure out which line is the cause.

matt

---

### Post by kamkar1 on 2010-04-02
Good day, 
I am fairly new with Linux and trying to learn more about video cards by practice. 
I have a compaq N410C, and I am trying to use the video out option on the TV screen.
My function keys are working, unfortunately FnF4 does not display the screen on Video out (TV), I get a black screen and have to restart to get laptop screen active.

I followed your instructions and modified my xorg.conf as  instructed, to my surprise, ubuntu version of xorg.conf was mostly  generic (no substance). 

After modification per your instructions, 
 command: glxinfo | grep direct
result : direct rendering: Yes
Now at start up linux box 9.10 I can see the logo and the text on the screen and GNOME takes over, Video out is tuned off and FnF4 is no longer functional and have to restart to get laptop screen active.

Here is some info, not sure it is helps:
Command : glxinfo | grep renderer
Result: OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE NO-TCL

Content of my xorg.conf is as follow:
--------------------------------------------------------------
# original ubuntu graphic command
#Section "Device"
#    Identifier    "Configured Video Device"
# EndSection

# Abuntu forum 3D acceleration recommendatiom

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
#Optimized values (changed from driver default)
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "on" #Faster than default (off)
    Option        "SWcursor" "off" #Faster than default (on)
    Option        "EnablePageFlip" "on" #Faster than default (off)
    Option        "AccelMethod" "EXA" # or XAA, EXA, XAA more stable, XAA is deafult
    Option        "DynamicClocks" "on"
    Option        "BIOSHotkeys"   "on"

#Left to driver default
#    Option        "RenderAccel" "on" #Default is "on"
#    Option        "DMAForXv" "on" #Default is on, use default value
#    Option        "SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#    Option        "ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#    Option        "DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
    Option        "AGPSize" "32" # default: 8
    Option        "EnableDepthMoves" "true"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "freetype"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "dri"
    Load    "extmod"
    Load    "glx"
    Load    "GLcore"
EndSection


Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---------------------------------------------------------


any help is most appreciated ..

thank you

---

### Post by kamkar1 on 2010-04-03
good moring all,

first, thank you for the post. It was a great place to start.

On the positive side of things I have spent few hours searching the net  and have now come up with additional data. FnF4 works and I have Tv-out  low resolution 800X600. but it requires reboot to either:
A. Normal usage : set high resolution for lcd but video out is not  working or
B. Low res with video out working, and deal with ubuntu error messages.

so, below is a quick description of my journey...
1- download and install atitvout, in many instances this has worked for  many, did not work for me. 
the command is:  sudo apt-get install atitvout
Now visit url: [http://who.is.free.fr/dokuwiki/doku.php?id=TvOut](http://who.is.free.fr/dokuwiki/doku.php?id=TvOut)
for instructions and command types.
 
2- Visit ubuntu forum
url: [http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746) 
it provides instruction on how setup xorg.conf, modifications did not  work for me, but since ubuntu's version was so bland, I accepted to run  linux box. at this time, I am unable to get Video out working. 

3- finally, I can across, url: [http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV) 
I followed the instructions and modified /etc/X11/xorg.conf ( see  attached) and to my surprise the FnF4 was functional and TV was working  low res 800x600.


Bugs: Ubuntu does not like the low resolution, and keeps attempting to  modify and change the setting. I don't know how to maintain high res for  the laptop and low res for video out.
For now, I have three versions of /etc/X11/xorg.conf
1. The Ubuntu std version
2. The high resolution
3- Low res with FnF4 working.
when, I want to project data to TV, I'll have to reboot with the new  xorg.conf 


I'll attach all just in case someone else has the same problem.

ps: to edit, copy or move /etc/X11/xorg.conf you have to be root 

Attachment:
xorg_ub.conf, Ubuntu version as installed
xorg_joe.conf, updated based on modifiaction of step 2
xorg_joe2.conf, final version with active FnF4


if you guys were abe to solve the problem send me an email, [email]kamkar1@yahoo.com[/email]
regards
jk

---

### Post by Issssy on 2010-08-06
Running 10.04 LTS on a X31 with the Radeon M6. driver "radeon" open source installed, direct rendering. Updated my xorg.conf based on this thread.  

Display set at 1024x768, depth 16

glxinfo yields:
direct rendering: yes
server glx:  SGI 1.2
client glx: Mesa Project and SGI 1.4
OpenGL Version: 1.3 Mesa 7.7.1

No video errors when I look at the xconf log.

I can run glxgears, but can't get over 75 frames.

What am I missing?

Bill

---

### Post by jpxsat on 2010-08-27
Hi...

I have a Compaq 1700 and i have a mobility radeon m6 ly and somethings are shown wrong, others are not shown... others slow...
Well, my problem when i tried to do this howto is that... xorg.conf doesn't exist in /etc/x11/!! :(:(:(

I'm using lubuntu 10.04

Help please!

---

### Post by aagsar on 2010-10-07
Hi, i have a toshiba satellite 1900-102 with that videocard and this "howto" works amazingly and i had my 3d acceleration working, but anyway there was something not entirely right whith the perfomance (lets say didnt match windows perfomance) especially mp4 playbacks. I just changed the agpfastwrite to "off" and surprise, now its PERFECT . Maybe dont work for you ,but now you have something else to try.

For the guy above yeah doesn`t exist but dont bother just 
sudo gedit /etc/X11/xorg.conf

and copy and paste the configuration, save and you got it

---

### Post by executorvs on 2010-10-18
hey. I've got a 1905-s301 and was wondering if you're using 10.10 or 10.04? also could you post your xorg.conf? I've got my custom form 9.04 and have been playing with one for 10.10 and would like to see how they compare.

---

