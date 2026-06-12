---
title: "Hardy Heron on T61"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by neurostu on 2008-04-26
So I just did a fresh install of Hardy Heron on my thinkpad T61.

It is working great. I did get an error message when I woke it up from suspend about suspend not working properly.

Has anybody else installed Hadry Heron on their T61?  If you have what has your experience been?  Any inputs?

---

### Post by feeshy on 2008-04-27
I have a T61 with Nvidia NV140M graphics.  Everything works well with a default install, both suspend and hibernate.  All functions except wi-fi LED and HDAPS.  This is with the standard driver so no compiz.  With compiz and proprietary Nvidia drivers everything works, but no suspend or hibernate.  I haven't got round to the hacks listed elsewhere.  I'm running without proprietary drivers just fine.

---

### Post by neurostu on 2008-04-27
So things run pretty well for you without the nvidia driver? How does power consumption compare with and without the proprietary driver compare?

---

### Post by feeshy on 2008-04-28
power use with ubuntu driver isn't great probably around 2h45 vs 3h30 in windows xp.  busy trying the proprietary driver now (ubuntu repos not the nvidia one).  had to fix the "pink shadow" compiz bug, but already i think battery life will be better - laptop is cooler.  now to fix the suspend problem - i'm not even going to try getting hibernate working ;)

---

### Post by feeshy on 2008-04-28
suspend works following these instructions:

[http://rende.se/index.php?n=Main.UbuntuHardyOnT61](http://rende.se/index.php?n=Main.UbuntuHardyOnT61)

i get a white screen on resume, but just typing your password takes you back to the desktop just fine (or you can push alt-s)

the lack of hibernation is a worthwhile tradeoff as the proprietary drivers make the ui a lot more responsive even without any compiz stuff turned on...

this one's a keeper for me

---

### Post by feeshy on 2008-04-28
the white screen problem goes away after installing new drivers using envyng

---

### Post by neurostu on 2008-04-28
Thanks for the update!

---

### Post by nowhere@cox.net on 2008-05-01
You all install 32bit or 64?  Anyone got 64 running on a T61 to see how the flash and Java situation pans out?

Thanks,
Eric

---

### Post by neurostu on 2008-05-01
I installed 32 bit.  In the future I will probably go to 64 bit as I have 4gb of ram installed.  In the end I actually went back to Gutsy. The wireless driver for 3495 is better in Hardy then Gutsy but a few other things weren't working for me so I went back.

---

### Post by nowhere@cox.net on 2008-05-01
What wasn't working correctly? I'm trying to decide whether to do a fresh install or spend a ton of time trying to get my Gutsy fixed.

---

### Post by neurostu on 2008-05-02
I was getting a lot of segmentation faults.  I couldn't use gedit without it crashing. Some of the compiz things were a little weird, when I would change desktops the viewport switcher (I think thats its name) would show up and would go away, I had to disable all desktop effects to get it to go away.  Also I was getting a pink haze around all of my windows.

---

### Post by neocortex on 2008-05-14
Hello ALL!
I just want to share my experience with Hardy on T61 with Nvidia. In general, things are fine, but I still have few very annoying problems that I could not solve.

First, suspend/resume (not to think about hibernate): I tried various things (a) Lenovo driver at [HTML]http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-69135[/HTML], and (b) Ubuntu repository driver (System -> Administration -> Hardware Drivers). Then, tweaking /etc/defaults/acpi-support, as explained at [HTML]http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61#How_to_Suspend_with_nVidia_140m.2F570m[/HTML], and for Hardy at [HTML]http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61[/HTML] (look for "Working on hardy final"). (Also, I could suggest you to look also at [HTML]http://rende.se/index.php?n=Main.UbuntuHardyOnT61#suspend-resume[/HTML].) At the end, my T61 cannot resume.

Second, Trackpoint mid-button scroll is not working, although I did proper changes in /etc/X11/xorg.conf adding
```

Section "InputDevice"
	Identifier	"Trackpoint"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel"          "true"
	Option		"EmulateWheelButton"    "2"
EndSection

```
In addition to that, some weird problems occur if you use more than one keyboard layout. Switching is not working always, ordering of keyboards changes by some magic etc.

Third, I cannot get rid of mandatory password enter for default keyring in Evolution, when it starts for a first time (after starting Ubuntu).

In conclusion, I am not happy nor sad, but some things are really annoying. Moreover, there is not clear and direct howto fix things. If anyone can give me advice(s) -- since, I am not an expert, I would appreciate that very much.
I read that both suspend and hibernate are working if you not use Nvidia driver. However, someone pointed out that then heating increases. Is that the fact?
For Trackpoint and keyboard layout I have no idea at all.

Best,
PM

---

### Post by pflanzenmoerder on 2008-05-16
Suing this command "hal-device |grep system.hardware.product" I got the following ID for my T61: 7662CTO
This id is not contained in /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-lenovo.fdi.
I tried all the turorials I found so far.
Suspending works but the thinkpad can't come back.
I get a blinking cursor and that's it.
Any hints?

---

### Post by neocortex on 2008-05-16
Yes, that's pretty much it - I run into a same problem with suspend.
What about original, not Nvidia, driver? Is that true that you can do suspend and hibernate, but heating is the problem?

Best,
PM

---

### Post by pflanzenmoerder on 2008-05-16
The open source drivers are no option for me as I code 3D apps, so I never tried,

---

### Post by nowhere@cox.net on 2008-05-16
Both suspend and hibernate worked fine when on the open source (non-3d) drivers. For me with the restricted drivers, the laptop suspends fine and about 50% of the time resumes with a totally white screen. The dialog box is there and I can type my password to get in but cannot see it.  If for some reason the password dialog behind the white screen doesn't have focus, I can move the mouse until I see the cursor change to the little line, indicating it is hovering over a text area, click and then type my password and I can get in.

I used envy to install (just today) the nvidia drivers with HARDY-proposed enable to resolve an envy bug and still have the same problem.

One other problem is with gnome-panel. Occasionally, on resume it freezes and I cannot kill and rerun it. 

BTW With a very minor tweak to a config (I forget which but it's one listed in this thread and others) and using envy with the latest nvidia drivers, suspend worked flawless in Gutsy...

Let's keep plugging at it and see if a solution comes up!

---

### Post by smellydog on 2008-05-17
I just got a T61 pre-installed with SUSE 10.  I then installed Hardy as the sole OS.  It's a 32 bit processor with the Intel graphics.  3d accel works pretty much on install with no pink shadows and wireless worked from the start.  the only thing that i messed around with was with the trackpoint getting the middle button to work.  It has a dual layer dvd burner and i CAN NOT get it to read encrypted DVDs!  I have the latest libdvdread3 and libdvdcss2, but it refuses to read my movies.  I was wondering if anybody else had the same issue?

---

### Post by smellydog on 2008-05-17
I figured it out.  My DVD was not set to a region.  I ran regionset and changed it.  now it plays my dvds

---

### Post by neurostu on 2008-05-29
I finally decided it was time to do a clean install. I backed up everything, repartitioned my HDD and just finished installing Hardy.  Hopefully with all the updates that have been released over the last 3-6 weeks things should work for me better this time around.

---

### Post by neurostu on 2008-05-29
I just installed Hardy Heron, no problems with anything.  I used suspend resume successfully on the first try.

---

