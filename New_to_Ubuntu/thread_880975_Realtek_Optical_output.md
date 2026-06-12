---
title: "Realtek Optical output"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by th00ht on 2008-08-05
My Fujitsu Siemens Q5000 has a realtek audio system. Microsoft Windows Vista lets me select the type of audio (optical) when I plug in the optical cable. In Ubuntu I get no such option and I have no sound on the optical output.

How do I enable optical sound output on the the Realtek audio device?

---

### Post by Qchan on 2008-08-05
> **th00ht said:**
> My Fujitsu Siemens Q5000 has a realtek audio system. Microsoft Windows Vista lets me select the type of audio (optical) when I plug in the optical cable. In Ubuntu I get no such option and I have no sound on the optical output.

How do I enable optical sound output on the the Realtek audio device?

[b][color=darkred]
You want to click on Preferences --> Sound (if not Preferences, then Administration. Can't remember since I'm on Windows right now :-( [work pc] ).

You will see for the different sound options a drop down menu. Simply choose the optical selection in each of those drop down menus and you should be fine.
[/b][/color]

---

### Post by th00ht on 2008-08-06
Thanks Qchan, I tried that  none of the settings work
I have:
Autodetect
ALC880 Digital
ALC880 Analog
ALSA - Advanced Lunix Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server


I do not have "Optical" or something like it. 


Actually I have no idea what these all mean. If I click the Help button I get something about a "GNOME sound server". Do I need to install a "GNOME sound server" in order to enjoy sound?

Btw lspci claims I have an Intel sound card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by th00ht on 2008-08-08
so for the time being the Ubuntu team has no solution to play sound on the optical output right? So no Ubuntu as a multi media system as per yet.

I will have to stick to my licenced copy of Microsoft Vista business.

How can I uninstall Ubuntu from my system?

---

### Post by crjackson on 2008-08-08
> **th00ht said:**
> Thanks Qchan, I tried that  none of the settings work
I have:
Autodetect
ALC880 Digital
ALC880 Analog
ALSA - Advanced Lunix Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server


I do not have "Optical" or something like it. 


Actually I have no idea what these all mean. If I click the Help button I get something about a "GNOME sound server". Do I need to install a "GNOME sound server" in order to enjoy sound?

Btw lspci claims I have an Intel sound card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

**_ALC880 Digital_**

---

### Post by x-tian on 2009-05-11
I have tried alc883 digital, and it didn't work, all the other options are analog

---

### Post by x-tian on 2009-05-11
[http://ubuntuforums.org/showthread.php?t=996990](http://ubuntuforums.org/showthread.php?t=996990)

---

