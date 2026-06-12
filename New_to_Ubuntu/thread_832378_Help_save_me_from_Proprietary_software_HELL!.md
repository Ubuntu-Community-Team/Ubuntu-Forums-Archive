---
title: "Help save me from Proprietary software HELL!"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Amorget on 2008-06-17
I tried using Vista, I really did, and I tried using Sony's software, but geeze, they both are SO HORRIBLE.  I am attempting to run Ubuntu 8.04 AMD64 on my Sony VGN-AR670.  I am running the drives in Raid 0 (/ has 10 gigs, /home has 186 gigs, and I have 2 swap partitions and one boot partition)  It is my development machine for work, so I am going to be running Windows XP and Vista virtualized.
Here are my problems, though...

Main problem:
I cannot Hibernate/Suspend.  I just get a black screen with blinking cursor.  I am running the -19 kernel.

Other issues:
None of my Fn keys work.
If I enable the nVidia drivers my login screen text for the username and password are huge.  It's just annoying.
My sound is weird... anything below half volume is basically muted, then it gets to a descent volume by the time it is cranked up.

Anyone have any help for me?

Douglas

---

### Post by KenBW2 on 2008-06-17
nvidia you say? I had a problem with nvidia and hibernate - it was something to do with Compiz. Try disabling visual effects. I can't find the page i found my fix at as Launchpad is down, but i think it was this page
[https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/136774](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/136774)

---

### Post by james_vanb on 2008-06-17
To change resolution for your login screen edit xorg.conf as follows:

```
sudo gedit /etc/X11/xorg.conf
```

Under "Screen", you'll find a subsection called "Modes" - the Login page picks up the first resolution after "Modes" - Put the resolution you want the screen set to first in line - Cut and paste.

---

### Post by Fixman on 2008-06-17
> If I enable the nVidia drivers my login screen text for the username and password are huge.  It's just annoying.
Enable the drivers, login, then open a terminal and write
```
 sudo dpkg-reconfigure xserver-xorg 
```

> 
My sound is weird... anything below half volume is basically muted, then it gets to a descent volume by the time it is cranked up.
System->Preferences->Sound, change everything to PulseAudio.

---

### Post by Amorget on 2008-06-17
> **Fixman said:**
> Enable the drivers, login, then open a terminal and write
```
 sudo dpkg-reconfigure xserver-xorg 
```


That works great!!

> **Fixman said:**
> 
System->Preferences->Sound, change everything to PulseAudio.

However, that doesn't work.  No changes to the volume.

---

### Post by Amorget on 2008-06-17
> **KenBW2 said:**
> nvidia you say? I had a problem with nvidia and hibernate - it was something to do with Compiz. Try disabling visual effects. I can't find the page i found my fix at as Launchpad is down, but i think it was this page
[https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/136774](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/136774)

I did some searching on this, but it seems it crashes on resume, not on suspend.  Once launchpad comes back up I'll take a look.

---

### Post by Amorget on 2008-06-19
> **Fixman said:**
> Enable the drivers, login, then open a terminal and write
```
 sudo dpkg-reconfigure xserver-xorg 
```


Hum, bad news, it seems to disable my nVidia drivers... I didn't realize it until I tried to turn on the Visual Effects.

---

### Post by james_vanb on 2008-06-19
Have you tried enabling nVidia drivers again and editing xorg.conf per #3 above?

---

### Post by Delever on 2008-06-19
You may try your luck installing drivers with envyng. Those are proprietary drivers, though (not open source).

To install envyng, type

sudo apt-get install envyng-gtk

You will find it in Applications->SystemTools

---

### Post by Amorget on 2008-06-25
> **james_vanb said:**
> Have you tried enabling nVidia drivers again and editing xorg.conf per #3 above?

I don't have a "Modes" subsection... can someone tell me what it should look like?

---

### Post by james_vanb on 2008-06-25
It might look something like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
```

In this case, login screen resolution would be "800x600@72" - To change, cut and paste desired resolution to the beginning of the line.

If you haven't already, see the following:

[http://ubuntuforums.org/showthread.php?t=833876](http://ubuntuforums.org/showthread.php?t=833876)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

