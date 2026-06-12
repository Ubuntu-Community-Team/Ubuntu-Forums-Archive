---
title: "FAQ: Why is my monitor refresh / resolution too low?  I know it can do better."
date: 2004-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Rancoras on 2004-11-21
Make sure your monitor's settings for HorizSync and VertRefresh in /etc/X11/XF86Config-4 match the settings in your owner's manual.  If you don't have your manual, you can usually get the information from the manufacturer web site.

---

### Post by onestep on 2004-11-21
My monitor is a CTX5655. The manufacturer spec's are HorizSync 30-55, VertRefresh 50-110, & DPMS = Y. When using the LiveCD my screen resoulution is 1024x768 @ 60hz. On my hardrive installation my only options are 640x480 or 800x600. I've checked the XF86Config-4 on both the LiveCD and hardrive installations and they both agree with the mfg specs... now what? I would really like to run 1024x768.

---

### Post by Rancoras on 2004-11-22
You may be missing a mode for 1024x768.  Here's that section from my config file:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-95
	VertRefresh	50-180
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

### Post by onestep on 2004-11-22
this is what mine looks like: 

```
Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-55
	VertRefresh	50-110
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 530/620 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
```

---

### Post by Rancoras on 2004-11-22
I see only a subsection for color depth "1".  What do you have in the subsection for color depth "24"?

---

### Post by onestep on 2004-11-22
Color depth 24 is the same as 1... I didn't post it all to save space.
This really has me puzzled... as it does for others too.

---

### Post by onestep on 2004-11-23
When I go to "Computer, System Configuration, Screen Resolution" I'm given a choice of 2 screen resolutions, 800x600 and 640x480.
When I look at the XF86Config-4 it shows 1024x768 and 800x600. 

Why doesn't the "Screen Resolution" box display the same values of "XF86Config-4"? 

Is there another file somewhere that needs updating to allow me to use 1024x768 like I'm able to do with the LiveCD -or-  is there something I could copy from the LiveCD settings and paste into the Hard Drive install that would allow 1024x768?

Aside from this,I really like Ubuntu...

---

### Post by Rancoras on 2004-11-23
I think the screen resolution applet works independently of X.  Try pressing CNTRL+ALT++ or - and see if that has any effect.  If the 1024 resolution is listed first, X should use it by default.  Other than that, I'm out of ideas.

---

### Post by IchaBOB on 2004-11-24
[QUOTE=onestep]When I go to "Computer, System Configuration, Screen Resolution" I'm given a choice of 2 screen resolutions, 800x600 and 640x480.
When I look at the XF86Config-4 it shows 1024x768 and 800x600. 

Why doesn't the "Screen Resolution" box display the same values of "XF86Config-4"? 

Is there another file somewhere that needs updating to allow me to use 1024x768 like I'm able to do with the LiveCD -or-  is there something I could copy from the LiveCD settings and paste into the Hard Drive install that would allow 1024x768?

Aside from this,I really like Ubuntu...[/QUOTE]


I have the same problem!

---

### Post by daniels on 2004-11-25
[QUOTE=Rancoras]Make sure your monitor's settings for HorizSync and VertRefresh in /etc/X11/XF86Config-4 match the settings in your owner's manual.  If you don't have your manual, you can usually get the information from the manufacturer web site.[/QUOTE]Even better, just delete the things and let X work it out for itself, which it can do unless your monitor was made in 1993 by people who have absolutely no clue about how to make monitors.  It's going away in the next X release, which I hope to upload today or tomorrow or so.

---

### Post by onestep on 2004-11-25
> Even better, just delete the things and let X work it out for itself,  
Is this what your suggesting I delete... 
> Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-55
	VertRefresh	50-110
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 530/620 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" 
or the whole  XF86Config-4 file?
also
> It's going away in the next X release, which I hope to upload today or tomorrow or so. 
How do I apply the next release... apt-get ???, synaptic upgrade ??

Thanks!
Another newbie hack at Linux knowledge!

---

### Post by daniels on 2004-11-25
[QUOTE=onestep]Is this what your suggesting I delete...[/QUOTE]Nope, just the lines starting with 'HorizSync' and 'VertRefresh'.
 > How do I apply the next release... apt-get ???, synaptic upgrade ??If you're running Hoary, Synaptic's Smart Upgrade will do it.

---

### Post by ale on 2004-11-27
people should also try to restart X after changing stuff in xorg.conf or xfree86.conf. to restart X without rebooting , press CTRL+ALT+BACKSPACE. the resoutions listed in Gnome are not always correct.

i also have some problem here

all other window managers except for Gnome will use 72 dpi for GTK and QT - i suspect all freetype2 apps! this is annoying, fonts will look way too small. the only way i know to fix this is to start the Gnome Control Center and click on "fonts". this will make everything update and screen will switch to 96 dpi. also the GTK2 theme gets loaded - by default it's the default grey theme.
 
can someone please tell me how to make this 96 dpi default in all window managers - i also like WindowMaker. and the theme thing, how to make it work in all window managers

thanks a lot!

---

### Post by dr.diesel on 2004-11-27
Hi @LL,

at first I'd like to say, that today I installed Ubuntu after trying on LiveCD - with some probs, but I tried to install on local PC otherwise, where was MDK before and I was quite fed up with it  :???:  . But Ubuntu seems user-friendly, easy-to-use and easy-to-configure distro. Thx !

The problem in MDK and in Ubuntu is, that I can't go in 100Hz Vfreq despite with LiveCD yes. I tried to delete freq config in XF86Config-4 file but I still can run only at 85Hz. The resolutions there are also different from those, which X allows (X allows more ;-) ) . Any ideas about VFreq?

BTW I'm going yo finish configuring Ubuntu using tweak HOWTO from this forum (which looks like a big source of info  
 :) 

Now I'm going to sleep, 4.24AM   ;-)

---

Today I made it using XF86Config-4 file from LiveCD. I found info in [http://www.ubuntuforums.org/showthread.php?t=5608](http://www.ubuntuforums.org/showthread.php?t=5608)

Great distro - on 1 CD...  =D>

---

### Post by diebels on 2004-11-30
[QUOTE=ale]can someone please tell me how to make this 96 dpi default in all window managers - i also like WindowMaker. and the theme thing, how to make it work in all window managers[/QUOTE]put "Xft.dpi: 96" in ~/.Xresources , for the theme thing I'm not sure. Maybe link from /usr/share/themes/$YOURPREFERREDTHEME to /usr/share/themes/Default

---

### Post by LinuxDev on 2004-12-02
Thanks for that ;)

I'm not a linux guru, but I knew that :)

For those who have the IIyama Vision Master Pro 454 (HM903DT) and are Linux beginner :

```

Section "Monitor"
	Identifier	"HM903DT"
	HorizSync	30-130
	VertRefresh	50-200
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA"
	Monitor		"HM903DT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600""
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

```

It works fine in 1600*1200 at 85 Hz ;)

---

### Post by ale on 2004-12-06
thank you!

it is also possible to change the dpi to 96 or anything in the /etc/gdm/gdm.conf file. there is this section

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 -dpi 96
flexible=true

also, for the theme stuff, i found you can edit the gtkrc files but that kinda sucks - no easy way to set it. the gtk-theme-switch won't work. and i grew so tired of googling around - for tv, for v4l, for fonts and everything. the gconf is impenetrable, the admin guide is a joke. i'm too stupid tio "tune" linux, i'll just keep the defaults  :-$

---

### Post by PatrickT on 2004-12-23
Hello!

I am very new to Linux and i heard that Ubuntu would be the right thing for me. So I am tryin the live-cd right now but i have the same problem: max resolution of 800x600. Looks quite poor on my native 1280x1024 tft.  :cry: 

So what can i do or what do i have to change to run the live-cd in a better resolution? what more information do i have to give you to help me solve this problem?  :confused: 

-Patrick-

---

### Post by pseudonym on 2005-01-21
If you are editing XF86Config-4 to put in your monitor's actual frequency ranges make sure to add your model name in the two sections which ask for it (shown a few posts up) rather than leave it at 'Generic Monitor'. Also make sure that both entries match exactly otherwise X won't start! (I found that out through bitter experience :) ).

---

### Post by daniels on 2005-01-21
Patrick, are you using the Warty or Hoary live CD?  The Warty one was the one sent out and professionally pressed; the Hoary live CD is the current development one (you'd know if you downloaded it).  If Warty, it's almost certainly fixed on the Hoary live CD.  If Hoary, I'd be really interested to find out more.

---

