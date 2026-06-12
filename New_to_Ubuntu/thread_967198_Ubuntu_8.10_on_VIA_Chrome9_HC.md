---
title: "Ubuntu 8.10 on VIA Chrome9 HC ?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by krtica on 2008-11-01
Did anyone succeed to install Ubuntu 8.10 on laptop with this graphic card?
:confused::(

---

### Post by Yar4ek on 2008-11-03
> **krtica said:**
> Did anyone succeed to install Ubuntu 8.10 on laptop with this graphic card?
:confused::(

It was entered on the page linux.via.com.tw. I found the drivers to Via Chrome9 graphics cards for Ubuntu 8.10 it is Version Alpha. :)

```
http://linux.via.com.tw/support/downloadFiles.action
``` :) 


PZDR

---

### Post by krtica on 2008-11-03
I tried to install that driver.
I have laptop with VN896 and Chrome9 HC (*some rubbish from Fujitsu Siemens: Amilo Pro V3515*).

I followed instructions and I was able to see installation process, but that's all.
After I reboot into a system - I couldn't see anything, just some flickering white stripes.

So I used recovery mode to install VIA drivers from CD. But again, after reboot I had only "***big black***" - monitor was turned off.

I tried to edit xorg.conf file and I put Subsection "Display" in Section "Screen" with:
[I]Depth 24
Modes "1280x800"[/I]
Again reboot and again black, turned off.

Then I tried with adding line *Option "ForceLCD" "TRUE"* in Section "Device". :confused:

etc. etc.

But it simply doesn't work, and I'm not surprised. :D

Anyway, I'm noob and probably I done a lot of stupid things, but without ANY results.

---

### Post by zvacet on 2008-11-03
Can you revert changes you did in xorg.conf file? If yo do after that back it up like this ( in terminal)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

After that 

```
sudo /etc/init.d/ gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by JoshuaRL on 2008-11-03
> **zvacet said:**
> Can you revert changes you did in xorg.conf file? If yo do after that back it up like this ( in terminal)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

After that 

```
sudo /etc/init.d/ gdm stop
```

```
sudo dpkg-reconfigure xserver-xorg
```

I may be speaking out of turn (not running Intrepid yet) but I don't think that will work.  With the updated Xorg, the emphasis is put on autodetection instead of xorg.conf.  And the reconfigure doesn't reset the video settings anymore.  I believe XRandR is the desired approach to changing settings, with this if you need help actually changing the xorg.conf settings:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by krtica on 2008-11-04
I tried everything what I could find on forum and what uncle Google offer me. But, there are no results.
If I use VESA - I have flickering screen.
If I use VIA driver - I have turned off lcd on laptop.
I even tried to do Manual Install from [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). It solved problems in 8.04, but in 8.10 I get message that there is no xserver-xorg-video-via in repositories or wherever it is...

But at least - I found soundtrack for this drama: *Amy Winehose - **Back To Black***.
:D

Thank you people for your advices.

---

### Post by krtica on 2008-11-04
Ok. Last 48h I spent mostly on trying to see ANYTHING in 8.10.
VIA have new "alfa" on [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action), but it still does not work for VN896/Chrome9_HC.
I'm trying to understand log files...
:shock:

Is there any "Safe Mode", I'm really tired of terminal and *nano*? :D

---

### Post by ozfalcon on 2008-11-04
> **krtica said:**
> Ok. Last 48h I spent mostly on trying to see ANYTHING in 8.10.
VIA have new "alfa" on [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action), but it still does not work for VN896/Chrome9_HC.
I'm trying to understand log files...
:shock:

Is there any "Safe Mode", I'm really tired of terminal and *nano*? :D



Hi,
I'm running HP 2133 with 8.10 Intrepid and can only use vesa driver at the moment. I had to install with xforcevesa.
Vesa driver works ok, But video playback can not be scaled etc.
OpenChrome from the repos (903) simply crashes my laptop.
And just tried the new 2d driver from Via Portal:
85a-43862-u810-2d-bin.tar.gz  --> FAILED with some strange graphic colour cycling.

Will post again after more testing.

---

### Post by handydan918 on 2008-11-04
> **krtica said:**
> 

Is there any "Safe Mode", I'm really tired of terminal and *nano*? :D

Hmmm. 
More bad news, I'm afraid.



That IS safe mode.

---

### Post by zvacet on 2008-11-05
@ **krtica**

>  I get message that there is no xserver-xorg-video-via

I´m afraid that means that via is not supported in 8.10.Under screens& graphic try select openchrome and see if you get any result.

---

### Post by krtica on 2008-11-05
I found adequate "Safe Mode". I just put some stupid line in xorg.conf, and Ubuntu offers me to troubleshoot problem. :D It's easier to watch xorg.0.log and xorg.conf at same time...

I'm aware of fact that VIA never had good support for Linux and probably never will. I managed to make it work under 8.04, so I thought that it will work at least with vesa driver. But strange thing is that I can't see anything. I tried a lot of changes in xorg.conf using [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html), but without success.

Is there any way, any tool built in Ubuntu (command line) which could give me precise parameters for my lcd screen? I thought that I could maybe force hsync and vsync trough xorg.conf. :confused:

I already try searching forums and googling, but I didn't find any "howto"... Or I'm just stupid, sucking and linux-inexperienced...

---

### Post by Yar4ek on 2008-11-05
Please behold my xorg may be useful to someone. :)
It is for drivers openchrome.
Already I have everything nicely resolution just yet but I have not refresh (Unless you have any suggestions).
I still do not work to me effects (compiz), but in Ubuntu 8.04 I was able to run effects.:)
It may be useful to someone. :)
(Sorry for My English is not good)

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"via"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
	Option		"PreferredMode" "1280x800@60"
modeline  "1280x800@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
        Option          "AddARGBVisuals" 	"true"
        Option          "AddARGBGLXVisuals" 	"true"
	SubSection "Display"
		Viewport 0 0
		Depth 24
		Virtual	1280	800
		Modes		"1280x800@60"
	EndSubSection
EndSection
```


P.S
My version Linux Ubuntu is 8.10. :]

PZDR

---

### Post by krtica on 2008-11-05
I really tried to change xorg.conf line by line, but it seems like it doesn't change anything. Regardless of parameters I change or add, there is always same result. Apparently, the only thing that is relevant is driver only.
I tried "vesa", "openchrome" and "via".
I even tried to change /boot/grub/menu.lst and add vga=3B6, vga=3B7 and vga=3B8 in the end of kernel line. That probably doesn't have sanse, but I had to try. :D
So, for now, it seems that there is no solution for VIA CN986 / VT8237 / Chrome9 HC... :(

**@[COLOR="DarkRed"]Yar4ek[/COLOR]:** Which chipset/graphic you have?

---

### Post by ozfalcon on 2008-11-05
Yar4ek

Your xorg.conf file does not have an entry for Drivers under the Device section.

Is this on purpose? 

KR

---

### Post by ozfalcon on 2008-11-05
> **krtica said:**
> I really tried to change xorg.conf line by line, but it seems like it doesn't change anything. Regardless of parameters I change or add, there is always same result. Apparently, the only thing that is relevant is driver only.
I tried "vesa", "openchrome" and "via".
I even tried to change /boot/grub/menu.lst and add vga=3B6, vga=3B7 and vga=3B8 in the end of kernel line. That probably doesn't have sanse, but I had to try. :D
So, for now, it seems that there is no solution for VIA CN986 / VT8237 / Chrome9 HC... :(

**@[COLOR="DarkRed"]Yar4ek[/COLOR]:** Which chipset/graphic you have?


krtica,
It seems the via 8.10 drivers are borked for both
CN896/Chrome9 HC
P4M900/Chrome9 HC (I get colour cycling on boot. tty still works)

If anyone is interested, Here are the hwinfo of P4M900/Chrome9_HC from my machine.

Apparently openchrome supports P4M900/VN896, However when I try the openchrome drivers. My system crashes. No tty, Just a Hard reboot.

What happens with openchrome with your machine?

---

### Post by ozfalcon on 2008-11-05
hwinfo for P4M900/Chrome9_HC

---

### Post by ozfalcon on 2008-11-05
> **krtica said:**
> 
I even tried to do Manual Install from [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome). It solved problems in 8.04, but in 8.10 I get message that there is no xserver-xorg-video-via in repositories or wherever it is...

You mention you tried the manual install of openchrome.
Did you try the openchrome-stable.sh from [http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)
This may not work for 8.10 because there is no xserver-xorg-video-via in the 8.10 repos. I have modified the script and am trying it soon (next post).

However, The are is a xserver-xorg-video-openchrome package in 8.10 repos (installed in 8.10 by default). The 8.10 repo version is 0.2.903.
The same as the latest openchrome website release:
[http://www.openchrome.org/releases/xf86-video-openchrome-0.2.903.tar.gz](http://www.openchrome.org/releases/xf86-video-openchrome-0.2.903.tar.gz) 

So all you need to do to enable the openchrome 2.903 driver is to change the line in xorg.conf from "vesa" or "via" to "openchrome". 

Also, If you want to try the latest svn. Then I'd guess the dependancies of xserver-xorg-video-openchrome should satisfy the openchrome-stable-sh script. Just modify/remove the references to xserver-xorg-video-via
Example modified openchrome-stable.sh script attached (Not yet tested to even run!)


Will let you know how the openchrome-stable(8.10).sh goes for me.

---

### Post by ozfalcon on 2008-11-05
ok Results on the openchrome-stable(8.10).sh

Previously, Using the openchrome 0.2.903 drivers from 8.10 repos - My laptop would crash. Requiring a hard reboot.

After running openchrome-stable(8.10).sh, My system no longer crashes on boot.
It boots to the login screen, However the login screen is badly corrupted.

I can start to login. ie the desktop background comes up and the bottom panel appears. Then the system freezes. Hard reset required.

Also from the login screen, ctrl-alt-F1 to tty then ctrl-alt-F7 to GDM crashes the system. Hard reset required.

---

### Post by krtica on 2008-11-06
I tried "openchrome".
Same thing happened to me.
So, final score look like this:

If I use **VESA** - I have flickering screen (just some white lines over lcd).
If I use **VIA** driver - I have turned off lcd on laptop.
If I use **OPENCHROME** - the system freezes at login screen. (Also corrupted and hard reset required.)

If I don't find any solution till weekend, I'll probably go back to 8.04...

---

### Post by ozfalcon on 2008-11-06
> **krtica said:**
> I tried "openchrome".
Same thing happened to me.
So, final score look like this:

If I use **VESA** - I have flickering screen (just some white lines over lcd).
If I use **VIA** driver - I have turned off lcd on laptop.
If I use **OPENCHROME** - the system freezes at login screen. (Also corrupted and hard reset required.)

If I don't find any solution till weekend, I'll probably go back to 8.04...

Hi,
I take it when you say you **have turned off lcd on laptop**, That an external monitor attached to this laptop works with the via driver? if so, what is the status of mplayer with the via driver.

When using vesa, can you confirm:
1.flickering screen (sync?) on laptop lcd
2.no display at all on external monitor


**Some improvement for me:**
I tried the Via driver with an external monitor plugged in.
on boot, the login is shown on the external monitor. resolution does not look correct. But I can login.
At the same time, the laptop LCD is cycling colors.
After logging in the screen is set to the correct res for the external monitor.
Playing a video with mplayer yields the following results:
(using via 2d driver for 8.10)
x11: movie displays ok but no resizing. (same result as vesa)
xv:  video kind of works, display is cut in half - resizing works
 a little but starts vertically chopping the smaller the resize.

---

### Post by ozfalcon on 2008-11-06
The 2d via driver is now working perfectly for me.
After finding this thread:
[http://forums.mininoteuser.com/viewtopic.php?f=11&t=614&st=0&sk=t&sd=a&start=20](http://forums.mininoteuser.com/viewtopic.php?f=11&t=614&st=0&sk=t&sd=a&start=20)


Have a look at the xorg.mini or just try it for chance (I know your laptop is not hp2133).

---

### Post by krtica on 2008-11-06
Yes, you are right - external monitor attached to this laptop works with the via driver. But only up to 800x600.
Sorry for my ignorance, I nave no enough experience with Ubuntu/Linux, so I'm not sure what do you mean by "the status of mplayer with the via driver". If its movie player, than I'm unable to see video. I'm getting message "An error occurred: Failed to connect stream."

Ant to be honest, I didn't try to attach external monitor using vesa driver. So I tried.
I'm getting always and only to the "Ubuntu is running in low-graphic mode" screen.
I tried different options:
Reconfigure graphics -> Use default (generic) configuration
Reconfigure graphics -> Create new configuration for this hardware
I tried also changing xorg.conf file, but it seems that it don't have influence at all.

@ozfalcon: Last 1-2 h I tried different options from that thread, but LCD is still OFF.

---

### Post by Yar4ek on 2008-11-06
> **krtica said:**
> I really tried to change xorg.conf line by line, but it seems like it doesn't change anything. Regardless of parameters I change or add, there is always same result. Apparently, the only thing that is relevant is driver only.
I tried "vesa", "openchrome" and "via".
I even tried to change /boot/grub/menu.lst and add vga=3B6, vga=3B7 and vga=3B8 in the end of kernel line. That probably doesn't have sanse, but I had to try. :D
So, for now, it seems that there is no solution for VIA CN986 / VT8237 / Chrome9 HC... :(

**@[COLOR="DarkRed"]Yar4ek[/COLOR]:** Which chipset/graphic you have?

I have the VN896(CE) (VIA CN896/P4M900/PT890Pro/VN896)chipset
And the Graphic Card I Via Chrome9. :)

> **ozfalcon said:**
> Yar4ek

Your xorg.conf file does not have an entry for Drivers under the Device section.

Is this on purpose? 

KR

	
I know that there is no Device Driver. But even after the installation of ubuntu were with me, the default drivers openchrome. So I found that there is no need to type in the Device Driver "openchrome."


PZDR

---

### Post by ozfalcon on 2008-11-06
> **krtica said:**
> Yes, you are right - external monitor attached to this laptop works with the via driver. But only up to 800x600.
Sorry for my ignorance, I nave no enough experience with Ubuntu/Linux, so I'm not sure what do you mean by "the status of mplayer with the via driver". If its movie player, than I'm unable to see video. I'm getting message "An error occurred: Failed to connect stream."

Ant to be honest, I didn't try to attach external monitor using vesa driver. So I tried.
I'm getting always and only to the "Ubuntu is running in low-graphic mode" screen.
I tried different options:
Reconfigure graphics -> Use default (generic) configuration
Reconfigure graphics -> Create new configuration for this hardware
I tried also changing xorg.conf file, but it seems that it don't have influence at all.

@ozfalcon: Last 1-2 h I tried different options from that thread, but LCD is still OFF.

Hi, Sorry I was not very clear.
Does mplayer resize the video correctly?
Go to preferences/video and select video out driver to either x11 or xv.

---

### Post by ozfalcon on 2008-11-06
> **krtica said:**
> Yes, you are right - external monitor attached to this laptop works with the via driver. But only up to 800x600.
Sorry for my ignorance, I nave no enough experience with Ubuntu/Linux, so I'm not sure what do you mean by "the status of mplayer with the via driver". If its movie player, than I'm unable to see video. I'm getting message "An error occurred: Failed to connect stream."

Ant to be honest, I didn't try to attach external monitor using vesa driver. So I tried.
I'm getting always and only to the "Ubuntu is running in low-graphic mode" screen.
I tried different options:
Reconfigure graphics -> Use default (generic) configuration
Reconfigure graphics -> Create new configuration for this hardware
I tried also changing xorg.conf file, but it seems that it don't have influence at all.

@ozfalcon: Last 1-2 h I tried different options from that thread, but LCD is still OFF.

Hi, Sorry I was not very clear.
Does mplayer resize the video correctly?
Go to preferences/video and select video out driver to either x11 or xv.

have you tried just copying the xorg.mini to xorg.conf with no changes?

---

### Post by krtica on 2008-11-06
I did try to just copy xorg.mini to xorg.conf.
I have no video in any case.

I don't have enough knowledge or experience with Ubuntu/Linux, and I need to do more things then just trying to see anything on 8.10 so I'm back on 8.04. I'm sorry but I must admit defeat. :(

Anyway, I did learn a lot (for me "a lot") about Ubuntu/Linux, and I hope that I'll manage now to install everything in 8.04 more easier then ever before. :)

Thank you people for your help. Thank you very much. I hope that you will help me when I post question again. :D

---

### Post by nagim on 2008-11-06
Hello guys. Sorry for my English (Im from Russia). I have russain 'copy' of krtica's laptop (Roverbook V512L) with VIA Chrome 9HC videocard.
And I did run GDM on this machine twice! After installing ubuntu I did replace xorg.conf and I did run GDM, however GDM didn't run after reboot.
So I have this problems too:

--
If I use VESA - I have flickering screen (just some white lines over lcd).
If I use VIA driver - I have turned off lcd on laptop.
If I use OPENCHROME - the system freezes at login screen. (Also corrupted and hard reset required.)
--

I think this problen have solution. Now I can run GDM in recovery mode (startx) with vesa, but keyboard and mouse dont work...

---

### Post by obrer on 2008-11-09
Have installed the beta driver in Ubuntu 8.10, screen is O.K. but cannot view videos in Totem.

Has anyone had the same issue, my xorg.cong file is:

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
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Driver "via"
	VendorName  "VIA Tech"
	BoardName   "via"
	Identifier	"Configured Video Device"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"800x600@60"	"1280x768@60"	"800x600@75"	"1280x720@60"	"800x600@72"	"1280x800@75"	"800x600@56"	"1280x768@75"	"1280x800@60"	"1440x900@75"	"1440x900@60"	"1600x1024@60"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by killwin on 2008-11-11
> **krtica said:**
> Did anyone succeed to install Ubuntu 8.10 on laptop with this graphic card?
:confused::(

Hello,
    some days ago I wrote about problems in my laptop with this card but now all goes right. Here I explain how to get it (I've got an Amilo li1705 Notebook). Perhaps it is usefull for you:

1) Install Ubuntu (I use alternate CD).
2) In first boot, select "safe mode"
3) From menu, select "root" to enter as root into a console terminal
4) Go to /etc/X11
5) Edit xorg.conf (with "vi xorg.conf" for example)
6) Add in "Device" section one new entry:
    Option "XaaNoImageWriteRect"
7) Whith this, all goes right but I add two new lines:
    Option "HWCursor" "false"
    Option "SWCursor" "true"

    These lines are to get cursor visible in my notebook when it disappears in flash movies, for example.
8) As my Notebook is 1280x800 and driver gives me more resolution, I add this into "Screen" section:
    SubSection "Display"
        Virtual 1280 800
    EndSubSection

Now, you can write "exit" and select "resume" from menu or reboot your machine and gdm will be shown.

I hoppe this will be useful and a help for you an other people whith this kind of problem.

Regards.

---

### Post by Maverickprowls on 2008-11-11
> **killwin said:**
> Hello,
    some days ago I wrote about problems in my laptop with this card but now all goes right. Here I explain how to get it (I've got an Amilo li1705 Notebook). Perhaps it is usefull for you:

1) Install Ubuntu (I use alternate CD).
2) In first boot, select "safe mode"
3) From menu, select "root" to enter as root into a console terminal
4) Go to /etc/X11
5) Edit xorg.conf (with "vi xorg.conf" for example)
6) Add in "Device" section one new entry:
    Option "XaaNoImageWriteRect"
7) Whith this, all goes right but I add two new lines:
    Option "HWCursor" "false"
    Option "SWCursor" "true"

    These lines are to get cursor visible in my notebook when it disappears in flash movies, for example.
8) As my Notebook is 1280x800 and driver gives me more resolution, I add this into "Screen" section:
    SubSection "Display"
        Virtual 1280 800
    EndSubSection

Now, you can write "exit" and select "resume" from menu or reboot your machine and gdm will be shown.

I hope this will be useful and a help for you an other people with this kind of problem.

Regards.

I have exactly the same laptop and I'm having considerable trouble getting the display to work (See my amateurish attempts [here]("http://ubuntuforums.org/showthread.php?t=976397").)  I've tried adding the lines you mention to my xorg.conf, but as I've already been fiddling with it considerably I think I may have broken some things whilst fixing others.

What other steps did you take to get your screen working, and would you mind posting your whole xorg.conf so I can copy it directly into my installation?  I presume that as our machines are identical, our xorg.confs can be as well.

---

### Post by killwin on 2008-11-11
> **Maverickprowls said:**
> I have exactly the same laptop and I'm having considerable trouble getting the display to work (See my amateurish attempts [here]("http://ubuntuforums.org/showthread.php?t=976397").)  I've tried adding the lines you mention to my xorg.conf, but as I've already been fiddling with it considerably I think I may have broken some things whilst fixing others.

What other steps did you take to get your screen working, and would you mind posting your whole xorg.conf so I can copy it directly into my installation?  I presume that as our machines are identical, our xorg.confs can be as well.

Now I'm now with my Notebook but if you can, please, put your xorg.conf here and I'll review it and include what I've got in my computer.

Regards.

---

### Post by Maverickprowls on 2008-11-11
My current xorg.conf is attached as a text file.

I've tried to take the file back to basics, so it pretty much only includes the advice you gave before.

I should add that the screen is still unusable with this current config, and still crashes as soon as gdm starts.

Many thanks in advance for your help.

---

### Post by killwin on 2008-11-11
> **Maverickprowls said:**
> My current xorg.conf is attached as a text file.

I've tried to take the file back to basics, so it pretty much only includes the advice you gave before.

I should add that the screen is still unusable with this current config, and still crashes as soon as gdm starts.

Many thanks in advance for your help.

Hello again :-)

I've reviewed your xorg.conf. I've change Driver option. It has to be "openchrome". I send it to you.
Please, tell me if it's ok. If not, I'll try to help you and in last option, when I'll get at home I'll take my Notebook (I don't know what is your hour. I'm in Spain).
xorg.conf I send you is changed in Windows (sorry) and I supose it'll have car returns.

---

### Post by Maverickprowls on 2008-11-11
Many thanks for that.  
I'm working in SuSE now, so it will take me a few mins to reboot and test this.

BTW: I'm in the UK, so I'm only an hour behind you.

---

### Post by Maverickprowls on 2008-11-11
It works!

I duplicated all the settings from your file into my xorg.conf

Thank you so much for helping me out with this.

I'm now typing from my shiny new Intrepid Ibex desktop, and incidentally, what is that on m wallpaper, it looks like a coffee stain in the shape of a screaming man?

---

### Post by killwin on 2008-11-11
> **Maverickprowls said:**
> It works!

I duplicated all the settings from your file into my xorg.conf

Thank you so much for helping me out with this.

I'm now typing from my shiny new Intrepid Ibex desktop, and incidentally, what is that on m wallpaper, it looks like a coffee stain in the shape of a screaming man?

Perfect!!!!

;-)

I'm happy you get Intrepid Ibex running... Yes, really, it's a very, very strange image. It seems to me that a cup was spilt of him and he scanned directly the sheet. Or... perhaps... An animal roaring with horns (maybe)... I don't know. I have always preferred the realistic painting to the abstract one.

:-)

---

### Post by Yar4ek on 2008-11-11
It is :):):):)
I managed to do me to have a Refresh. :)
Here's my xorg.conf(killwin) modification. :)
It may be useful to you. :)




PZDR

---

### Post by killwin on 2008-11-11
> **Yar4ek said:**
> It is :):):):)
I managed to do me to have a Refresh. :)
Here's my xorg.conf(killwin) modification. :)
It may be useful to you. :)




PZDR

Thanks a lot.
I've tried your xorg.conf and first all seems to go right but with some applications (klear and totem) I get bad refresh (mixed image with green).

---

### Post by krtica on 2008-11-12
Greetings good people!
I just wanna to tell that my biggest problem is not just chipset or graphic - it is laptop generally. I always used "openchrome" on 8.04. When I couldn't resolve problems on 8.10 I reinstalled 8.04 and when I tried to use "via" drivers, I have no picture on lcd, same as on 8.10.
So, if you wanna have Linux instead of Windows, think twice before you buy Fujitsu Siemens. :D

---

### Post by Yar4ek on 2008-11-12
> **krtica said:**
> Greetings good people!
I just wanna to tell that my biggest problem is not just chipset or graphic - it is laptop generally. I always used "openchrome" on 8.04. When I couldn't resolve problems on 8.10 I reinstalled 8.04 and when I tried to use "via" drivers, I have no picture on lcd, same as on 8.10.
So, if you wanna have Linux instead of Windows, think twice before you buy Fujitsu Siemens. :D

	
Exactly. :)
I, unfortunately, I have a notebooks Aristo Smart 360 and this unfortunate Graphics Via. :)
So, if in the future, I will buy a notebook is certainly no longer commit this error now. :)



PZDR

---

### Post by obrer on 2008-12-02
[http://linux.via.com.tw/support/beginDownload.action?eleid=221&fid=482](http://linux.via.com.tw/support/beginDownload.action?eleid=221&fid=482)

Will try to make it work this afternoon, it seems you can enable compiz, if anyone has already install it please comment results

---

### Post by x-to-tha-t on 2008-12-05
Hi, just thought I'd give anybody a hand who needs it... I wrote a blog post on how to do it in Slackware... It's not necessarily for the faint of heart. Requires some fiddling with the kernel, and the guide needs changing slightly for Ubuntu. Anyway... Get the full skinny here:

[http://n00bsys0p.wordpress.com/2008/10/07/compiz-on-slackware-with-via-chrome9/]("http://n00bsys0p.wordpress.com/2008/10/07/compiz-on-slackware-with-via-chrome9/")

If anybody needs any help with Ubuntu, I have a happy as larry 8.04 system running the drivers, so just shout me. Also, the 8.10 Alpha driver didn't support the VN896 chipset, but there has just been a new beta version released a couple of days ago on [http://linux.via.com.tw/]("http://linux.via.com.tw/"), but I haven't tested it. I'd imagine as they've given it a beta tag, it probably supports the whole lot.

Anyway. Hope I've been of help to people.

X-T

---

### Post by gh1234 on 2008-12-13
Any results with the new driver yet?
I just tried it out! No success, only some strange stripes on the upper side of my display, but the System is still working. I heard some sounds of welcome screen and after CRTL+ALT+F1 and CRTL+ALT+DEL the system did a normal reboot.
I found a solution somewhere, it's a working xorg.conf (for me) but flash is lagging in full screen:
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

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"openchrome"
	Option		"ActiveDevice" "LCD,CRT"
	Option		"NoDDCValue" "true"
	Option		"XaaNoImageWriteRect" "true"
	Option		"SWCursor"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"PreferredMode" "1280x800"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
	InputDevice	"Synaptics Touchpad"
EndSection

```
Not my work, found it on [http://forum.ubuntuusers.de/topic/openchrome-fuer-vn896-auf-terra-mobile-2104-v/?highlight=updat+auf#post-1661154](http://forum.ubuntuusers.de/topic/openchrome-fuer-vn896-auf-terra-mobile-2104-v/?highlight=updat+auf#post-1661154)
But I want to see a working driver of VIA wich contains 3D support.

Sorry if my english is to bad, I'm german but this Theard is exactly matching with my problem.

---

### Post by doubledrop on 2008-12-13
If you want 3d desktop effects on VIA Chrome9 alpha drivers be ready to see strange cursor in compiz, but without compiz glxgears get 1000 fps instead 150 on openchrome drivers.

There is 2 things, that you need to do:
1. Get GFX Drive and Source code of drm from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) (second needed if drm module don't load at boot, see in /var/log/Xorg.0.log to check it).
2. Install GFX Drivers and make drm module.
To make drm module (via_chrome9.ko) you need linux-headers, and root access.

To install gfx: 
```
sudo ./vinstall
```
How to make drm and install read in readme in archive.

And last thing: add in xorg.conf in Section "Device" this line:
```
Option "SWCursor" "true"
```
If you don't add this option you don't see your mouse cursor.

No XaaNoImageWriteRect needed.

P.s. It works for me, I have Ubuntu 8.10 and P4M900 graphic chipset, but in drivers readme plenty of other chipsets supported.

---

### Post by gh1234 on 2008-12-15
@doubledrop: I checked out both and did exactly what the readme said... only some Stripes...
I dont even need compiz, but I need Flash without lagging in fullscreen... 3D would be even better ;)
My Chipset: VN896

EDIT: In fact, I don't see anything, black with stripes, upperside my LCD maybe you thaught there are some over the Display

2nd EDIT: Sorry, didn't read your post carefully ;) I'll check out the DRM source... thaught that would be did by vinstall... sorry ;)
*hopefully* Push Vista away, forever (With Intrepid I can use my Wireless card :PP)

---

### Post by obrer on 2008-12-16
For VIA CN896/VN896/VX800 chipset


Made some advances, can get direct rendering and compiz working, have the famous cube, this what I have done but still encounter big problems that are being studied now: 

A) From [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) download the 
Unified GFX driver Ver 85a-44597 for Ubuntu 8.10(02Dec08) (3.4M) unpack cd to the driver directory and sudo ./vinstall

B) From  [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) download the Stable Chrome9 DRM source for kernel 2.6.27(12Dec08) (31.2K) and follow these instructions: 

      
(1) Copy drm-via_chrome9-2.6.27-85a-44411-src.tar.gz to your working directory
(2) Extract the package
    # tar -zxf drm-via_chrome9-2.6.27-85a-44411-src.tar.gz
(3) Enter the directory and build the source
    # cd drm-via_chrome9-2.6.27-85a-44411-src
    # make
(4) Backup the VIA chrome9 DRM module
    # cd /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9
    # mv via_chrome9.ko via_chrome9.ko.bak
(5) Replace VIA DRM module by the new one
    # cp ~/drm-via_chrome9-2.6.27-85a-44411-src/via_chrome9.ko /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9/ NOTE ONCE COPIED YOU HAVE TO CHANGE PERMISSION &#8220;sudo chmod 644 via_chrome9.ko
    # depmod -a


  

NOTE I HAD TO ADD via_chrome9 to /etc/modules since the driver did not load at boot up. 


C) Download the following xorg.conf and replace the original in /etc/X11 [ftp://ftp.mangohabanero.com/public/ubuntu8.10-hp2133-compiz-info-2DEC2008/xorg.conf](ftp://ftp.mangohabanero.com/public/ubuntu8.10-hp2133-compiz-info-2DEC2008/xorg.conf)


Reboot 

(7) Check whether VIA chrome9 DRM module is loaded
    # lsmod |grep via_chrome9
    If you get the output as:
      drm        86056  1 via_chrome9
    that means the VIA chrome9 DRM module is successfully loaded.

and ps aux | grep rendering    GUALA YES, YES, YES

Problems that have to be solved:

a)	When in appearance special effects I put medium or high cannot watch movies in totem (I hear the sound but get black screen)
b)	Webcam does not work says cannot work at a resolution of  2048x2048 this happens even if none special effects are enabled.

---

### Post by ambient_sky on 2008-12-16
Thanks for workaround, peoples! Its working for me (Fujitsu Siemens Amilo La 1703, Ubuntu 8.10, Via UniChrome9 on K8N890CE)

---

### Post by gh1234 on 2008-12-16
OK... got the Alternate Disc now :lolflag:
Hopefully...
But one more question... First sometimes Intrepid Live Disc starts on my Computer with Vesa, but only if I press CRTL+ALT+F1 on startup, now X freezes... don't know ;)
Hope the workaround works... thanks!

EDIT: No success... tried everything... step by step and got this strange stripes... I took a photo, but openchrome fails now, too and I'm writeing this post with my Nintendo Wii ~~

Any ideas?

2nd EDIT: Logile sais (EE only): 3 times Couldn't open "dev/video2"

The last II: VIACloseScreen, ipVIAGraphicInfo->dwXServerEnabled = FALSE

3rd: lsmod &#921;grep via_chrome9
via_chrome9 32908 0
drm 86056 via_chrome9

there are two?!

4: OK now useing Vista ^^ here is the "screenshot" without screen... [IMG]http://img84.imageshack.us/img84/5451/pict0001rq0.th.jpg[/IMG]

---

### Post by marlon89br on 2008-12-17
I did exactly what **obrer** said in his post, but it didn't work.
After rebooting the laptot (Via VN896 video card) the screen flashes before the login screen and it locks... when I move back my original xorg.conf (using openchrome driver) I can't get things normal again, as usually I got when trying these beta drivers. 
I've tried to comment the line via_chrome9 in /etc/modules and again nothing.

Is there anything I can do to fix this driver or at least get my old driver back?
Thanks in advance...

---

### Post by obrer on 2008-12-17
Go to the directory where you unpacked the Unified GFX driver Ver 85a-44597 for Ubuntu 8.10(02Dec08) (3.4M)  and sudo ./vuninstall this should remove the via driver and leave things as before. Also comment out de via_chorme9 from /etc/modules if needed reinstall the xserver-xorg-video-openchrome

Did you use sudo when:

(1) Copy drm-via_chrome9-2.6.27-85a-44411-src.tar.gz to your working directory
(2) Extract the package
# tar -zxf drm-via_chrome9-2.6.27-85a-44411-src.tar.gz
(3) Enter the directory and build the source
# cd drm-via_chrome9-2.6.27-85a-44411-src
# sudo make
(4) Backup the VIA chrome9 DRM module
# sudo cd /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9
# sudo mv via_chrome9.ko via_chrome9.ko.bak
(5) Replace VIA DRM module by the new one
# sudo cp ~/drm-via_chrome9-2.6.27-85a-44411-src/via_chrome9.ko /lib/modules/'uname -r'/kernel/ubuntu/via_chrome9/ NOTE ONCE COPIED YOU HAVE TO CHANGE PERMISSION &#8220;sudo chmod 644 via_chrome9.ko
# sudo depmod -a

Also please try this new xorg.conf file I am trying out now: this was downloaded from [http://www.hp2133guide.com/forums/viewtopic.php?t=1136&postdays=0&postorder=asc&start=20](http://www.hp2133guide.com/forums/viewtopic.php?t=1136&postdays=0&postorder=asc&start=20)

# xorg.conf (X.Org X Window System server configuration file) 
# 
# This file was generated by dexconf, and then by hand by Who 
# Thanks to mikez's docs and examples for teaching me! 


Section "Device" 
   Driver "via" 
   VendorName  "VIA Tech" 
   BoardName   "via" 
   Identifier   "Configured Video Device" 
    
   Option "ActiveDevice" "LCD"          #required to make the resolution correct without RandR 
   Option "DPMS" 
   Option "PanelID" "3"             #SUSE uses this, seems not to be reqd 

   Option "UseRandR12"  # I WANT to use this (it works, almost) 
   #Option "HWCursor" # Doesn't restore cursor 
   Option "SWCursor" # Does restore cursor 
EndSection 

Section "Monitor" 
   Identifier "Monitor" 
   ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497 
   ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597 
   ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497 
   ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497 
   ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497 
   ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync 
   ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync 
   ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531 
   ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync 
   ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync 
   ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync 
   ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync 
   ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746 
   ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795 
   ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync 
   ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync 
   ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync 
   ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087 
   ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync 
   ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync 
   ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync 
   ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync 
   ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118 
   ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync 
   ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502 
   ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602 
   ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502 
   ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502 
   ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535 
   ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802 
   ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096 
   ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807 
   ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103 
   ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505 
EndSection 

Section "Screen" 
   Monitor  "Monitor" 
   SubSection "Display" 
      Modes  "1280x768" 
      Virtual 1280 768 
      Depth  24 
   EndSubSection 
   Identifier   "Default Screen" 
   Device      "Configured Video Device" 
   Option      "ForceLCD"      "true" 
   Option      "ActiveDevice"      "LCD" 
   Option      "VideoOnDevice"      "LCD"    
   Option      "SetMpegFBNumber"   "true" 
EndSection 

Section "Module" 
   Load  "glx" 
   Load  "dri" 
   Load  "extmod" 
EndSection 

Section "DRI" 
   Group 0 
   Mode 0666 
EndSection 

Section "ServerLayout" 
   #Option "RandR" "False" 
   Identifier "main" 
   Screen "Default Screen" 
EndSection

---

### Post by doubledrop on 2008-12-17
> **gh1234 said:**
> 4: OK now useing Vista ^^ here is the "screenshot" without screen... [IMG]http://img84.imageshack.us/img84/5451/pict0001rq0.th.jpg[/IMG]

Nice screen! :) Get same long long time, before starts uses openchrome driver. If you using vesa drivers, screen will be always in this state when you change resolution or go to console.
Hint to you: use openchrome driver with some options. You "Device section" xorg.conf should look like this:
```

Section "Device"
    Driver "openchrome"
    Option "AccelMethod" "EXA"
EndSection

```

How to make drivers from linux arena work see above.

---

### Post by marlon89br on 2008-12-17
OK... I'll try it tonight at home.
Just one question... the xorg.conf that I used to have with openchrome doesn't specify all those resolutions within Monitor section. It has nothing at all. The only part where I have screen resolutions is at the section Screen where I have:

SubSection "Display"
Modes "1280x800"
Virtual 1280 800
Depth 24
EndSubSection 

Is that part full of ModeLine really needed? I can post my xorg.conf later...

---

### Post by doubledrop on 2008-12-17
> **marlon89br said:**
> Is there anything I can do to fix this driver or at least get my old driver back?
Thanks in advance...

Put xorg.conf and /var/log/Xorg.0.log here. Till then I don't know what happening. It look like drm not loaded well, and drivers switch back to vesa or openchrome...

---

### Post by doubledrop on 2008-12-17
> **marlon89br said:**
> The only part where I have screen resolutions is at the section Screen where I have:

SubSection "Display"
Modes "1280x800"
Virtual 1280 800
Depth 24
EndSubSection 

Is that part full of ModeLine really needed? I can post my xorg.conf later...

You need the ModeLine to specif the settings.
Type this in console, to get the ModeLine (works for me always, but not sure about you):
```
gtf 1280 800 70
```
Output should be like this:
```
Modeline "1280x800_70.00"  98.89  1280 1352 1488 1696  800 801 804 833  -HSync +Vsync
```
Copy this line and paste into "Monitor" section in xorg.conf. Then change Modes to "1280x800_70" or rename the modeline to "1280x800".

---

### Post by gh1234 on 2008-12-17
> **obrer said:**
> 
Did you use sudo when:

Root shell ;) No X...
But the Problem seems to be that there isn't /dev/video2 anywhere...
I'll try vuninstall to use openchrome and maybe... the new xorg.conf will fix the Problem, but don't think so because it can't set /dev/video2, can it?
Yeah!!! Openchrome works!!! Greate

OK... even no success!
But here is my Xorg.o.log:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Jonas-Laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 17 21:14:04 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "main"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] rev 1, Mem @ 0xa0000000/0, 0xc9000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "via"

(II) Loading /usr/lib/xorg/modules/drivers//via_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 5.74.255
	Module class: X.Org Video Driver
(II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(==) via(0): Depth 24, (==) framebuffer bpp 32
(==) via(0): RGB weight 888
(==) via(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) via(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) via(0): VESA BIOS detected
(II) via(0): VESA VBE Version 3.0
(II) via(0): VESA VBE Total Mem: 131072 kB
(II) via(0): VESA VBE OEM: VIA N3364


(II) via(0): VESA VBE OEM Software Rev: 1.0
(II) via(0): VESA VBE OEM Vendor: 
(II) via(0): VESA VBE OEM Product: 
(II) via(0): VESA VBE OEM Product Rev: 
(II) via(0): MapBase = 0xb7920000, MmioBase=c9000000
(II) via(0): RegCR08 = 0, RegCR09=4f
(--) via(0): Chipset: "P4M900"
(--) via(0): Chipset Rev.: 0
(**) via(0): Option "SWCursor"
(**) via(0): Option "ActiveDevice" "LCD"
(**) via(0): Option "PanelID" "3"
(**) via(0): Option "SetMpegFBNumber" "true"
(**) via(0): Option "VideoOnDevice" "LCD"
(**) via(0): Option "ForceLCD" "true"
(==) via(0): Not using video BIOS to set modes
(==) via(0): Using XAA acceleration architecture.
(II) via(0): MergedFB mode forced off.
(**) via(0): Active Device is LCD.
(**) via(0): (OPTION) Force enable LCD. 
(**) via(0): (OPTION) LCD Panel ID is 3.
(**) via(0): TV scan mode is 0
(**) via(0): Option SWCursor enabled.
(**) via(0): Option: Cap0 auto detect= 0
(**) via(0): Option: Cap1 auto detect= 0
(**) via(0): Option: Cap0_FieldSwap Disabled
(**) via(0): Option: Cap0_HFilter Enabled
(**) via(0): Option: Cap1_HFilter Enabled
(**) via(0): Option: Capture Over Scan ON
(**) via(0): Option: HQV Filter Manual Select Disabled
(**) via(0): Option: Set MPEG decode frame buffer number Enable
(**) via(0): Option: Capture 1 use H/W auto flip
(**) via(0): Option: Capture 0 use V1 engine : Default path
(**) via(0): Option: HQV Manual Switch Disabled
(**) via(0): Option: No mpeg add one line on bottom = 0
(**) via(0): Option: DeBlocking Disable!!
(**) via(0): DeBlocking Minimum Width Default : 320
(**) via(0): DeBlocking Minimum Height Default: 240
(**) via(0): Option: Use 2D BitBlt method to write event-tag into VQ and make sure MPEG decode END Disable
(**) via(0): Video has been set to LCD
(--) via(0): mapping MMIO @ 0xc9000000 with size 0x9000
(--) via(0): mapping BitBlt MMIO @ 0xc9200000 with size 0x200000
(II) via(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) via(0): Using gamma correction (1.0, 1.0, 1.0)
(--) via(0): videoram =  131072k
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) via(0): I2C bus "I2C bus 1" initialized.
(II) via(0): I2C bus "I2C bus 2" initialized.
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) via(0): DPI set to (96, 96)
(II) via(0): Output CRT using monitor section Monitor
(II) via(0): Output LCD has no monitor section
(II) via(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) via(0): I2C device "I2C bus 1:ddc2" removed.
(II) via(0): Output CRT disconnected
(II) via(0): Output LCD connected
(II) via(0): Using user preference for initial modes
(II) via(0): Output LCD using initial mode 1280x768
(**) via(0): disable DVI Display SW scaling, It isn't HDMI
(II) via(0): VIASetDisplayPath is Single
(II) VIALoadVideoOption
(WW) No Video option file .VIAVIDEORC exist. 
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(--) via(0): mapping framebuffer @ 0xa0000000 with size 0x8000000
(--) via(0): Frame buffer start: 0xaf696000, free start: 0x3c0000 end: 0x8000000
(--) via(0): mapping MMIO @ 0xc9000000 with size 0x9000
(--) via(0): mapping BitBlt MMIO @ 0xc9200000 with size 0x200000
(II) via(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(EE) via(0):  Couldn't open "/dev/video2"
(II) via(0): VIAScreenInit : V4L Disabled : fd2 = -1 
(II) via(0): [drm] Detect H5s1 chipset: 0005  chipid: 3371
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) via(0): [drm] Using the DRM lock SAREA also for drawables.
(II) via(0): [drm] framebuffer handle = 0xa0000000
(II) via(0): [drm] added 1 reserved context for kernel
(II) via(0): X context handle = 0x1
(II) via(0): [drm] installed DRM signal handler
(II) via(0): [drm] drmAgpEnabled succeeded
(II) via(0): [drm] agpAddr = 0xc0000000
(II) via(0): [drm] agpBase = 0x00000000
(II) via(0): [drm] agpAddr = 0xc0000000
(II) via(0): [drm] agpSize = 0x04000000
(II) via(0): [drm] agp physical addr = 0x00000000
(II) via(0): [dri] use agp.
(II) via(0): [dri] frame buffer initialized.
(II) via(0): [dri] visual configs initialized.
(II) via(0): [drm] register handle = 0xc9000000, HostBlt handle = 0xc9200000
(II) via(0): [drm] mmio Registers = 0xc9000000
(II) via(0): [dri] mmio maped.
(II) via(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) via(0): I2C device "I2C bus 2:TV" removed.
(II) via(0): VIASetDisplayPath is Single
(II) via(0): VIALoadUserDuoViewVideoOutputDeviceSetting exit:TVtype=1, TVScan=0
(II) via(0): VIAFindModeUseBIOSTable exit:TVtype=1, TVScan=0
(II) via(0): VIADISP3DScalingParasSetting exit:TVtype=1, TVScan=0
(II) via(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) via(0): I2C device "I2C bus 2:TV" removed.
(II) via(0): I2C device "I2C bus 2:TV" registered at address 0x40.
(II) via(0): I2C device "I2C bus 2:TV" removed.
(II) via(0): VIASetMode exit:TVtype=1, TVScan=0
(II) via(0): into 3D initial...3Dinitial? 0
(II) via(0): H5 3D Engine has been initilized.
(II) via(0): VIAWriteMode exit:TVtype=1, TVScan=0
(II) via(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(EE) via(0):  Couldn't open "/dev/video2"
(II) via(0): VIAModeInit exit:TVtype=1, TVScan=0
(II) via(0): VIAInternalScreenInit
(II) via(0): Frame Buffer From (0,0) To (1280,1177)
(II) via(0): Using 1177 lines for offscreen memory.
(II) via(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Image Writes
	Setting up tile and stipple cache:
		30 128x128 slots
		32 8x8 color pattern slots
(==) via(0): Backing store disabled
(==) via(0): Silken mouse enabled
(II) via(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(II) via(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Apply expand
(II) via(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(**) Option "dpms"
(**) via(0): DPMS enabled
(II) via(0): [DRI] installation complete
(II) via(0): [dri] kernel data initilized.
(II) via(0): direct rendering enabled
(II) via(0): lpVIAGraphicInfo->dwXServerEnabled is 1
(WW) via(0): Option "UseRandR12" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/via_chrome9_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) via(0): Setting screen physical size to 338 x 203
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event9"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) AT Translated Set 2 keyboard: xkb_layout: "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) AT Translated Set 2 keyboard: xkb_variant: "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event2"
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Video Bus: xkb_layout: "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Video Bus: xkb_variant: "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Video Bus: xkb_options: "lv3:ralt_switch"
(II) via(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) via(0): I2C device "I2C bus 1:ddc2" removed.
AUDIT: Wed Dec 17 21:14:12 2008: 5235 X: client 4 rejected from local host ( uid=0 gid=0 pid=5406 )
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) via(0): VIASaveHqv
(II) via(0): Hqv0Saved.hqv_ctl:f6fe244e
(II) via(0): Hqv1Saved.hqv_ctl:0
(II) via(0): VIASaveVideo
(II) via(0): video1 CSC(13000ded,13171000)
(II) via(0): video1 addr0:9ffffffc,addr1:1ffffff8
(II) via(0): video3 CSC(0,0)
(II) via(0): video3 addr0:0,addr1:0
(II) via(0): [drm] Cleaning up DMA ring-buffer.
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) via(0): [drm] removed 1 reserved context for kernel
(II) via(0): [drm] unmapping 8192 bytes of SAREA 0xf890b000 at 0xaf694000
(II) via(0): [drm] Closed DRM master.
(II) via(0): [drm] Freeing agp memory
(II) via(0): [drm] Releasing agp module
(II) via(0): VIACloseScreen
(EE) via(0):  Couldn't open "/dev/video2"
(II) via(0): VIACloseScreen, lpVIAGraphicInfo->dwXServerEnabled = FALSE
```

Hm... the Log sais: (II) via: driver for VIA chipsets: P4M800PRO, CX700, K8M890, P4M890,
	P4M900, VX800, VX855
but my Driver is VN896...

But release_notes.txt sais:

Supported Chipsets
==================
Target system must contain one of the following VIA Chipsets:
       VIA CX700M/VX700/CN700/CN896/VN896/VX800 Chipset
Please check with your system provider to determine which VIA Chipset is used in your system.

```
sudo lspci
[sudo] password for jonas: 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
05:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
06:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

```
If you need more information... ask for ;)
Hm... someone solved this problem with update the kernel... does anyone know wich kernel is supported? I just dated up... no success
```
uname -r
2.6.27-9-generic

```

---

### Post by gh1234 on 2008-12-18
UPS... sorry thaught I used EDIT... No way to delete own posts?!

---

### Post by obrer on 2008-12-20
Solved Totem problem in gstreamer-properties video you have to mark x windows system (no XV)

---

### Post by doubledrop on 2008-12-20
Someone fix the cursor? I still have a box around it, witch slow updates... :(
Upd. To ober: Change to no XV. Ok, I see the video now, but it very slow playing...
Upd2. Get the mplayer, run from console and it's playing fast and smooth :) Nice!

---

### Post by gh1234 on 2008-12-20
@doubledrop: Do you use SWCursor true?!
I don't really know of that will help because the Driver didn't work for me ^^ but that fixed my Problem with openchrome...

---

### Post by doubledrop on 2008-12-20
@gh1234 Of course I am, beacouse with out it cursor is invisible :)

---

### Post by obrer on 2008-12-20
Solved also web cam issue by reinstalling the driver, I have gone back to the 1st xorg.conf I posted and it is working pretty fine for me.

---

### Post by gh1234 on 2008-12-21
> **doubledrop said:**
> @gh1234 Of course I am, beacouse with out it cursor is invisible :)

As I said... I don't had any chance to test it ^^
I hope there will be a stable driver soon... maybe that will work for me :(

---

### Post by gh1234 on 2009-01-03
any walkarounds?!

---

### Post by marlon89br on 2009-01-03
> **gh1234 said:**
> any walkarounds?!
I think the easiest one would be downgrading to Hardy Heron :P
I've done a lot of web searching and spent a few hours trying to edit my xorg.conf and got nothing :(

---

### Post by gh1234 on 2009-01-03
Openchrome is OK (for now) but I still hope there'll be a fix next time (maybe this month because there was a new version every year)...

---

### Post by gh1234 on 2009-01-29
Hi, I found something out! The Driver uses an external display, if I put in one, it works, is there a way to set up wich display the driver schould use=?!

---

### Post by marlon89br on 2009-01-29
Great gh1234! I'm gonna try it at home... how is your xorg.conf? Did you generate it automatically? I was using the same one I used with openchrome, replacing 'openchrome' with 'via' in the driver option. I'm almost sure there is an option to add in xorg.conf so you can choose the display... if I'm not mistaken, the Via driver comes with a help file that lists a lot of options... I'll read it tonight and do some testings

---

### Post by gh1234 on 2009-01-29
Hm... I used that what vinstall do out of the openchrome one...
If I ad ForceLCD at the device section, there isn't the /dev/video2 error anymore. If I do it can't find a workeing modline.
If I type 1280x800 at the subsection the /dev/video2 bug return... very strange ;)
Ok do so I`d be happy if you find a solution ;)

EDIT: My old openchrome one works too but with very bad resolution...

---

### Post by marlon89br on 2009-01-30
Same as you... got it working on an external display, but nothing in the LCD. I've tried some options, but got nothing :(

---

### Post by gh1234 on 2009-01-31
Think we have to wait for the next driver release (there was no in january, I hope for one in febuary).

---

### Post by TsUPeR on 2009-02-04
I've been trying this driver (85a-44597) with my EPIA EN12000eg and a DVI module (ubuntu 8.10). 
My xorg.conf has been modified a few million times but I've never succeeded getting any image from the DVI port (connected to a sony x3500 hdtv). VGA works fine. When opening "Display Settings" I have 3 recognized monitors (2 unkown and one SONY 40")!

Using the vesa driver and a xorg.conf with just 

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
         Depth 24
         Virtual 1280 720
        EndSubSection
EndSection
``` 

Everything works just fine. Without the "Virtual 1280 720" the output is set to 1920x1080 (tested with x11vnc).

Does anyone have suggestions for what I can ad in xorg.conf to get the DVI output to work?

Cheers!

---

### Post by gh1234 on 2009-02-06
I just checked out Jaunty! It works out of the box... I'll see if I can get 3d working...

---

### Post by gh1234 on 2009-02-09
OK... I got direct 3d rendering workeing :D. But compiz didn't work... ^^ I'll see what I can do!

Does Compiz requires something else than direct 3d rendering?

And Why is the Adobe Flash Player so F***ing slow?
I'll do it once again and write down how to :D

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) it's a littlebit out of date... but worked form me!

---

### Post by ricardisimo on 2009-03-02
Quick question: Being that I have never once in my three years on Ubuntu successfully compiled anything from source, should I bother trying to get the Beta driver from the VIA Linux portal installed? Or should I just wait another month to see if 9.04 works it's magic for me? Thanks.

---

### Post by ricardisimo on 2009-03-02
In other words, are these simple instructions that came with the driver download simply NOT going to do the trick?
> 1.1  Uncompress the via driver package
```
	tar zxvf ./5.74.33.85a-44597.tar.gz
```
> 1.2  Install the via linux driver
	```
cd   ./5.74.33.85a-44597
	sudo ./vinstall
```
> Reboot system
Am I going to regret trying this?

---

### Post by ricardisimo on 2009-03-03
Bumpalicious

---

### Post by ricardisimo on 2009-03-04
Who put the bump in the bump-de-bump-de-bump?

---

### Post by ricardisimo on 2009-03-27
Well, I just tried the 9.04 LiveCD, and it looks good. As I recall, 8.04 and 8.10 both gave me video noise, through which I would have to take half-random stabs at buttons during installation, then later change to vesa in text mode. So far so good.

How can I tell, during a LiveCD session, which driver is being used? Thanks.

---

### Post by underdarkonsole on 2009-04-19
hallo...
sorry for my bad in english

i am still got 3d driver not working in my laptop with via Chome9 CN896...
any suggestion where i can find the 3d driver for my via Chrome9

thank's

---

### Post by ricardisimo on 2009-04-27
I am now on Jaunty, and having some issues with the graphics when switching users. Firstly, how do I check to see what driver 9.04 is using? Secondly,... well, I'll wait to see if anyone responds to this question first. Thanks.

---

