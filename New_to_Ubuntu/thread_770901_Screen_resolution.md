---
title: "Screen resolution"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by gaby PR on 2008-04-27
I installed Ubuntu 8.04 few minutes ago.  Is only give me the option of 800x600 resolution.  I tried dpgk-reconfigure xorg..... but only gave me option to reconfigure the keyboard.  This never happen before with the other versions of ubuntu.  Any suggestion will be help full.

---

### Post by Joeb454 on 2008-04-27
you didn't really specify the command you used. Did you use ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Martin Witte on 2008-04-27
did you already try in the menu:System - Preferences - Screen Resolution?

---

### Post by muted1987 on 2008-04-27
now i know just about nothing but but maybe you havnt got the graphics card drivers enabled after update. i know in a fresh install you have t enable. hope this helps.

---

### Post by islandis on 2008-04-27
I had a similar issue the first time I rebooted my new 8.04 installation.  Would only let me get to a max of 960x540 or some other such ridiculous resolution.  Tried playing around with some settings to no avail. Magically corrected itself after rebooting again, though.

Not sure if it had something to do with me having to install in Safe Graphics Mode or what...

---

### Post by gaby PR on 2008-04-27
This the output after do the command.
 
sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080427140723

with  sudo dpkg-reconfigure xserver-xorg only give me options to reconfigure  the keyboard.  I am using the onboard video.

---

### Post by sailor2001 on 2008-04-27
ddo this:  /usr/applications/screen & graffics

---

### Post by MaindotC on 2008-04-27
OP can you please describe your hardware, especially the type of video card?  You may need a restricted driver.

---

### Post by gaby PR on 2008-04-27
output 

/usr/applications/screen & graffics
bash: /usr/applications/screen: No such file or directory
[1] 6858
[1]+  Exit 127                /usr/applications/screen
bash: graffics: command not found
[1]+  Exit 127                /usr/applications/screen

---

### Post by muted1987 on 2008-04-27
can you see a picture on the top bar of a lil chipboard if so then you can get your restricted drivers from there

---

### Post by i586 on 2008-04-27
Try editing your /etc/X11/xorg.conf file by adding (within the **Monitor** section) the following values (or change them if they're already set):

```

HorizSync
VertRefresh 

```When you're done, just restart X using CTRL+ALT+BACKSPACE. Then try to change the resolution the way you attempted before: System > Preferences > Screen Resolution.

PS: Of course you need to change (or set up) those values according to your monitor. If that does not work then try installing your card driver.

Regards.

---

### Post by gaby PR on 2008-04-27
This is my xorg.conf file.  There is something wrong here because do not like the others of my previous installations.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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
EndSection

---

### Post by i586 on 2008-04-27
Have you tried what I suggested?
Please, if you do, post back your results so we can help you.

Regards.

---

### Post by playinpearls on 2008-04-27
i had this problem too a couple of days ago. I have an nvidia driver, and i dont know what exactly the case was but i went to systems>appearance> effects and put the effects at the highest level. This prompted ubuntu to install the exact driver that i needed and all my resolution problems went away.

---

### Post by gaby PR on 2008-04-27
> **i586 said:**
> Have you tried what I suggested?
Please, if you do, post back your results so we can help you.

Regards.

Problem fixed with your suggestion.  Thanks.

---

### Post by abhiroopb on 2008-04-27
The command: sudo dpkg-reconfigure -phigh xserver-xorg does not work in hardy. The best thing to do is use the screen and graphics command.

---

### Post by c.pergiel on 2008-09-06
Linux is as lovely as Windows is wonderful. I'm running Horrible Harry, or whatever version H is called.

I have dots. Many dots. 1024 x768 dots exactly.

Took a while to get here.

First of all I tried the "System/Appearance/Visual Effects" trick recommended by playinpearls. It did indeed cause a new Nvidia driver to be installed, but it cut my choices of screen resolution down to 2. No real help there, and now I don't know which version of the video driver I'm running.

But now, thanks to this thread, this page:

[https://help.ubuntu.com/community/FixVideoResolutionHowto#Undetected%20Monitor%20Specs](https://help.ubuntu.com/community/FixVideoResolutionHowto#Undetected%20Monitor%20Specs)

and a Princeton data sheet, I have dots.

I added these two lines to the monitor section of /etc/X11/xorg.conf

	HorizSync	30-96
	VertRefresh	50-160

The instructions in this thread only mentioned the two key words, they did not say anything about having to append anything, much less what form those values needed.

The web page helped there.

So I put these values in and now I can get 1024 x 768, which is entirely adequate, but nowhere near the top resolution of this monitor (Princeton VF912) which is 1600 x 1200. Further, on "System/Preferences/Screen Resolution" when you try to select the resolution, a list appears with a large empty white space at the top. Clicking on "Refresh Rate" gives you a list of five values: 50 thru 55 Hz.

I just realized these limitations may be due to the video card. It looks like there is a way to put in your monitor name and model, but where's the list of valid values?

And why can't you do this super user stuff from a GUI? Why does it have to done from the command line?

Oh well, at least I have dots.

---

