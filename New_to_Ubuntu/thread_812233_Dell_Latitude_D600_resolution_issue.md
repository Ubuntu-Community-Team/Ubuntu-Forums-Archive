---
title: "Dell Latitude D600 resolution issue"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by another_one on 2008-05-29
I have a fresh install of Ubuntu 8.04 on a Dell Latitude D600 with an ATI Mobility 9000 video card.  I have not been able to set my screen resolution to the laptop monitor's maximum resolution, 1400x1050.  It does not show up in System > Preferences > Screen Resolution.

I have read many threads relating to this kind of problem, but I have noticed that most of them include postings of xorg.conf files that include lines specifying the "ati" driver and have a Modules section... my xorg.conf file is virtually empty.

Here are some relevant lines:

```
Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

As you can see, there is no line specifying the "ati" driver.  I have copied the video-related sections of other peoples' xorg.conf files but none of them have given me new resolutions in the Screen Resolution tool.  Also, there are no Module or Extension sections, which I have seen in other folks' xorg.conf files.  I have tried to dpkg-reconfigure xorg-server but that doesn't seem to help.

Thanks in advance for any assistance you can provide!

---

### Post by overdrank on 2008-05-29
HI and welcome, you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by another_one on 2008-05-30
Hi, and thanks for the reply.  I have already read through that thread while searching the forums for a solution, but I'm not sure I understand the relevance.  Do I need to use Compiz Fusion to be able to set my resolution to 1440x1050?  Will Compiz Fusion generate an xorg.conf file that isn't so "vanilla" as the one on my system and which will use my hardware to the fullest?

---

### Post by amitai on 2008-10-05
> **another_one said:**
> Hi, and thanks for the reply.  I have already read through that thread while searching the forums for a solution, but I'm not sure I understand the relevance.  Do I need to use Compiz Fusion to be able to set my resolution to 1440x1050?  Will Compiz Fusion generate an xorg.conf file that isn't so "vanilla" as the one on my system and which will use my hardware to the fullest?

I'm having the same issue...  I'm maxing out at 1024x768 on the Dell D600.

p.s. very new user here -- second day on Ubuntu, came from Windows.

---

