---
title: "Sound Coming Out of Internal Speaker in Some Applications"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Giganteface on 2008-05-09
Synopsis: Sound works properly (meaning uses my PCI sound card to export sound to my external speakers) in all Gnome applications.  Sound comes out my internal speaker in other applications though (such as Flash videos and the game Quake 3: Arena).

Hello,

I'm pretty new to Ubuntu, but I decided to install it and give it a try a little over a month ago, bought a book on it, and I've learned a bunch in a short span of time (or at least I feel like I have).  However, this is one problem I've been unable to figure out (and I'm thinking/hoping it's probably an easy-to-fix type deal that I'm just too dumb to figure out on my own):

It seems as if, within all Gnome applications, sound operates properly (meaning it uses my Santa Cruz PCI sound card to send the sound to my external speakers).  However, with all Flash videos, the sound has always come out of my internal speaker instead of using my sound card for some reason (this is using the flashplugin-nonfree package).  In addition, I recently put the game Quake 3: Arena on this PC as well, and I get the same thing from within it: the sound comes out of the PC's internal speaker, rather than using my sound card to send it to my external speakers.

Within System - Preferences - Sound, I have all of my sound options set to the CS46xx option (which is indeed my sound card chipset), and as I mentioned, this has allowed sound to operate properly using my PCI sound card for all Gnome applications (like Totem, Rhythmbox, etc.)  However, if I set these options to ALSA, or Autodetect (as well as many of the other available options), it will instead come out of my PC's internal speaker (if that helps at all).  This is a fairly new install as well (8.04/Hardy), so any settings that might interfere with the sound should probably still be the same as a fresh install, or at least pretty close.

Anybody know what I might need to do to fix this?  Any help would be greatly appreciated!  Thank you!

---

### Post by oliviacond on 2008-05-09
try select PulseAudio in Sound preferences and all the programs.

---

### Post by billgoldberg on 2008-05-09
Try installing "libflashsupport".

It could help with the flash issue, but I'm not sure.

```
sudo apt-get install libflashsupport
```

---

### Post by Giganteface on 2008-05-09
Thank you both very much for your replies!  Unfortunately, it doesn't seem as if either of these suggestions has helped fix this issue :(  PulseAudio is one of the options that outputs to my PC's internal speaker, and the libflashsupport package is already installed.  I have tried removing/purging and re-installing both the flashplugin-nonfree and libflashsupport packages, as well as some of the sound package stuff mentioned in the two "Comprehensive" stickied threads in the Multimedia & Video section of the forum, but to no avail.  If it helps, within Quake 3: Arena the snddevice parameter is "/dev/dsp" (which I assume it ought to be but I thought I'd mention it).  In addition, whenever I first boot my PC into Ubuntu the sound made when you first make it to the login screen (but before actually logging in) comes out my internal speaker too, which I've always thought was kind of odd.  Thanks again for any help anyone can provide!

---

