---
title: "Dual Monitor Woes"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by AustenG on 2012-08-02
Hi, 

I'm running into an issue when trying to set up my dual monitors with 12.04. I'm using Unity with Lightdm, and my second monitor (with desired 1920x1080 resolution) is only 640X480! Also, the second monitor is completely white with a black x for a cursor. Can anyone tell me why this is happening?

Output for xrandr -q:

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 disconnected (normal left inverted right x axis y axis)
DFP7 disconnected (normal left inverted right x axis y axis)
DFP8 disconnected (normal left inverted right x axis y axis)
DFP9 disconnected (normal left inverted right x axis y axis)
DFP10 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)


I've also tried AMD Catalyst Control and nothing seemed to take.


Thanks for any help.

---

### Post by QIII on 2012-08-02
What is the model of your graphics card?

How did you install the driver?

From the AMD website?

From the repo through "Additional Drivers"?

Basic or Post Release Update?

From the command line?

fglrx and fglrx- amdcccle?  fglrx-updates and fglrx-amdcccle-updates?

Did you remember to do

```
sudo aticonfig --initial
```Are you starting CCC in administrative mode?

---

### Post by AustenG on 2012-08-02
All good questions.

1) Radeon HD 7970
2) Originally from website, but have since messed up things and now it was done through the additional drivers tab
3) Basic
4) Didn't do --initial, but I will give that a shot
5) I am starting in administrative mode

---

### Post by QIII on 2012-08-02
Did you uninstall the one you installed from the AMD site before trying over with the repo?

To uninstall the one you installed from the website

```
sudo aticonfig --uninstall
```Have a look at the ATI wiki in my signature and read the section entitled "Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"  Using the "Additional Drivers" method does not work sometimes.  Why it doesn't beats me.  The -updates version also causes many users problem.  Again, I have no idea why.

There was initially some confusion with the HD 7xxx series cards.  ATI put the product in the breach and pulled the lanyard before the Linux driver actually worked.  The poor souls who spent a lot of money on them brought them home to find they wouldn't work on Linux.  I believe that is resolved, but it might not be.  That could be a problem if the 12.4 driver (which is in the repo) is the one that didn't work.  I don't think that is the case because people were getting no output at all and you are getting at least something.

---

### Post by erupter on 2012-08-10
I've installed AMD 12.6 as per the Wiki.

Yet with a 7970 I'm unable to concurrently run my two monitors:
Dell U2412M (1920x1200)
Asus VW222S (1680x1050)

When I set Multi-Display Desktop and restart, the login screen is correctly showing the background on both screens, when the desktop loads though only the main screen stays on, the other gets turned off and the configuration gets suspended.
I've seen the "not enough memory" messages before installing the 12.6 Catalyst.
Here is my  fglrxinfo
```

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.11733 Compatibility Profile Context


```

---

### Post by AustenG on 2012-08-12
erupter, just so you have the same information as I do, I found this about the 7970HD card:[http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")
It says that for full support install Catalyst 12-1. I have no idea what this means, but _nothing_ I've done so far has gotten my dual-monitor setup to work. I've tried 12-1, but something else was giving me a hard time, so I got frustrated and moved back to the latest Catalyst (12-6).

---

### Post by AustenG on 2012-08-12
Okay, even with Catalyst 12-6 I think I have made some forward progress. I'm not there yet, but I spent a lot of time figuring out what my xorg.conf should look like with dual 23inch monitors (1920x1080; one connected through dvi, and one through mini-display port) with the 7970hd card.

What happens now is that upon boot it takes me to a black screen where it checks battery state [ok], and says a whole bunch of other stuff and eventually hangs on: 
```
 stopping sysytem V runlevel compatibility 
```

What I do next is to ctr-alt-f1 into a terminal and log in that way, and run:
```
 startx 
```
Then it takes me to the desktop which is now set up the way I'd like - side by side both with resolution of 1920x1080, and mouse can scroll between the two very nicely. A couple of smaller things don't work as well, such as windows don't maximize/get bigger if you drag them to a border. Not exactly sure why, or what I did/didn't put in my xorg.conf file.

Anyway, if somebody can take a look and let me know if they see anything wrong with the file it would be appreciated:

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" RightOf "amdcccle-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP10"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP10" "0-DFP10"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3960 1080
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by erupter on 2012-08-12
I followed the guide to install 12.1
I now have a watermark saying the hardware is not supported, but the dual screen works.
Although it works only with the same resolution on both monitors, which sucks as the bigger one blurs noticeably.

I suppose this way it would work with 12.6 too, but I am uncertain whether to try or not.

---

### Post by AustenG on 2012-08-12
It won't let you change the resolution? Have you tried editing the xorg.conf file manually to change the resolution? I'd make a backup copy of it (cp xorg.conf xorg.conf.bak), then modify one copy to the right resolution (making sure that this one is named xorg.conf). Give it a shot and see what happens. If it doesn't work you can always return the backup copy to the one your system boots with. 

As for the watermark, I have no idea. Where is the watermark, on the desktop?

---

### Post by erupter on 2012-08-13
> **AustenG said:**
> It won't let you change the resolution? Have you tried editing the xorg.conf file manually to change the resolution? I'd make a backup copy of it (cp xorg.conf xorg.conf.bak), then modify one copy to the right resolution (making sure that this one is named xorg.conf). Give it a shot and see what happens. If it doesn't work you can always return the backup copy to the one your system boots with. 

As for most recent ubuntu versions (I think from 10.04?) I don't have a xorg.conf.
Anyway I think the problem is supporting different resolutions.
Right now I have both screens at the same resolution and it works.
Does ubuntu officially support spanning the desktop over different resolution monitors?
That's the question.
Because if I try to use both at their native res, I'm greeted with an error message referring to insufficient memory.
Obviously that is not really the case here: the 7970 itself has 3gb, my pc as 8gb, and besides windows has no problem doing it.
So it is something inside the Ubuntu desktop management.


> **AustenG said:**
> As for the watermark, I have no idea. Where is the watermark, on the desktop?
Am not the only one, if you look around the 7970 is shown as unsupported hardware with catalyst 12.1.

---

### Post by AustenG on 2012-08-14
Is there an option to enable the use of Xinerama? I believe that will allow you to use multiple different monitors (with different resolutions) as one big desktop. I believe this should be an option in catalyst. If it doesn't work, then go back to Xinerama being disabled.

---

### Post by erupter on 2012-08-16
I have the xinerama option, but strangely enough the transparency effects get glitchy with it enabled: the launcher isn't transparent anymore, it's just black.

---

### Post by AustenG on 2012-08-16
hmm. better not mess with it then - I'm no expert of Xinerama. I just try and see what works. Are you able to boot properly with dual monitors, or does it hang in a particular place?

---

### Post by erupter on 2012-08-17
No hangs, just that 3D acceleration is disabled, thus some effects don't work (transparency) and the antialiasing on fonts is wrong, but the configuration sticks at boot.
It may all be confined to the 7970 for what I know though.

Anyway for now I decided to stick with the same resolution on both monitors (sacrificing the newer one): it works good and without any bad graphics.
Only thing it doesn't stuck at boot: you have to manually reset it every time.
But using hibernation I'm able to delay that quite a bit.
Linux from this point of view is better than any windows: I can hibernate and resume for lots of times before actually needing a restart.

On the video drivers side though linux (or at least Ubuntu) plainly sucks: don't know how Valve can even think of porting Steam to linux...

For your reference ->[here](http://ubuntuforums.org/showthread.php?t=2040490)<- is the thread I created where I reported my findings.

---

### Post by AustenG on 2012-08-23
Thanks for the pointer. I hope this clears up soon. Just my luck - I chose a graphics card that required more setup and messing around than most...

I think you should view having Steam on Linux machines as a sign of good things to come. People will have to spend more time to actually make sure ALL graphics cards will work right from the box - no messing around with config files..

---

### Post by tbone3421 on 2012-09-21
Hi,

I'm also having trouble with a second monitor in a fresh installation of 12.04LTS.  I'm on a desktop with an ATI Radeon 7500 and I have two identical LG monitors that each support 1920x1080.   The second monitor is connected with HDMI and seems to work fine at resolutions less than 1920x1080.  The DVI monitor is working correctly at 1920x1080.  I've been trying to follow various posts on these forums, installing fglrxinfo and the updated version as well.  I've also set the resolution for both monitors in the Catalyst Control Center as well as in the Ubuntu Displays setting.  Am I missing a modeline or something?  

Can anyone tell me why the monitor works for everything except this resolution? I'm pretty stuck at this point.   Thanks so much in advance for any advice at all.

---

### Post by erupter on 2012-09-22
I found in my case (desktop 7970) the solution was to ditch the HDMI output and use the DisplayPort.

---

