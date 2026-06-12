---
title: "Video is very choppy"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by holdie on 2008-07-29
So I've been trying to watch a few movies and I noticed that the video on my comnputer tends to take up nearly all of the CPU and runs very choppy...I know this is a relatively common complaint, but I'm not running any desktop effects and I've got the Envy ATI driver installed...

any ideas as to what else might be causing this slowness?

---

### Post by pi.boy.travis on 2008-07-29
Could we get some additional information/specs about your computer please?

---

### Post by holdie on 2008-07-29
sure, I've got a Dell Inspiron 6000 with an ATI Radeon X300 (I'm pretty sure) graphics card and about 1.25 GB of RAM...I'm running Hardy Heron

anything else I should add?

---

### Post by pi.boy.travis on 2008-07-29
What kind of videos are we talking about here?  Are these flash videos in a browser, or files you have stored on your computer?  If so, what application are you using to watch them?

---

### Post by PmDematagoda on 2008-07-29
Did you try viewing the videos with the radeonhd driver?

You can try the radeonhd driver with:- 
Install the radeonhd driver with:-
```
sudo apt-get install xserver-xorg-video-radeonhd
```
and run:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the driver as radeonhd, then reboot the system and see if the videos play any better.

---

### Post by Mister.Vash on 2008-07-29
Have you tried it with non-proprietary drivers for a comparison?  I had the official ATI drivers on my system and cpu was pegged and many dropped frames.  I removed those and use the default and it no works better.  

I tested it out again about two weeks ago with the new ATI build and it was still the same thing

---

### Post by Mister.Vash on 2008-07-29
Forgot to mention I have one of the Radeo X300 cards

lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]



Post the out from your system of 
lspci | grep ATI

---

### Post by holdie on 2008-07-29
I'm running videos I've got stored on my computer (aka DIVX and such), I'm using VLC for playing them

also, how can I reset my video driver back to its default setting (as in reset it and start with a blank slate)...I think some stuff may have been messed with during the switch to proprietary drivers a while back

---

### Post by holdie on 2008-07-29
lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

---

### Post by holdie on 2008-07-29
sorry, one last thing, I tried the reconfigure method and found that it now stops after reconfiguring the keyboard...a google search told me this was because the distros after gutsy don't support it any longer

---

### Post by PmDematagoda on 2008-07-29
> **holdie said:**
> sorry, one last thing, I tried the reconfigure method and found that it now stops after reconfiguring the keyboard...a google search told me this was because the distros after gutsy don't support it any longer

Then try this:-
1) Boot Ubuntu in Recovery Mode.
and
2) Select "xfix".

Then reboot Ubuntu and see if the videos play any better, also post the output of:-
```
cat /etc/X11/xorg.conf
```

---

### Post by holdie on 2008-07-29
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

this is after using xfix, although it hasn't seemed to help anything.  The screen still slows down on exceptionally active moments of the movie, and occasionally freezes for like 10 seconds or so, at which point CPU usage goes down to 0

---

### Post by holdie on 2008-07-29
Alright, video seems to be doing alright, however I'm still having significant problems playing MKV files...I've tried VLC, but it runs extremely slowly (with ffmpeg codecs installed and such)...I've also tried using Mplayer, which works a bit better, but still skips considerably on the more active parts...

any ideas?

---

### Post by makkan77 on 2008-07-30
I had a similar problem although on very old hardware. I couldn't even move a window in X without having the whole screen flicker like crazy. This was with the default near empty xorg.conf file. When I reverted to using my old xorg.conf file from gutsy all problems with flickering were gone. 


Don't know if this helps you but it might.

---

