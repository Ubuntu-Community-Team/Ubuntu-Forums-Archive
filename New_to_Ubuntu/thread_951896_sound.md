---
title: "sound"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-18
Cannot get sound when playing dvd movies, have picture, using totem

---

### Post by kansasnoob on 2008-10-18
Is this Hardy? What version of Ubuntu?

---

### Post by johntravis on 2008-10-18
Ubuntu 8.0.4 using totem  prefer to use vlc which I have downloaded but can't seem to use because totem pops up., no biggie just want sound, fix players after.

---

### Post by beno1990 on 2008-10-18
Does sound work at all or just not on Totem? If you want to open VLC instead of Totem you can right-click on the file and select VLC from "open with", too.

---

### Post by kansasnoob on 2008-10-18
Well read all of this before jumping into something:

(1)> Totem movie player and PulseAudio sound server:

      Some users report problems with video playback in the GNOME movie player, and audio playback in other applications, due to an error when connecting to the PulseAudio sound server. Investigation of this possibly hardware-specific issue is ongoing. A workaround is to enter the System -> Preferences -> Sound dialog and change the Music and Movies sound playback option from 'Autodetect' to 'ALSA'.


That's from [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

(2) If you want to change to VLC just go to Synaptic and remove the unwanted Totem Packages and install VLC (also mozilla-plugin-vlc). It's easy using the search feature in synaptic, just break out a tablet and keep track of what you're doing so you can easily revert.

(3) Best overall fix I've found for pulse-audio problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

But I've not needed to use it on my last two fresh installs.

---

### Post by kansasnoob on 2008-10-18
> **johntravis said:**
> Ubuntu 8.0.4 using totem  prefer to use vlc which I have downloaded but can't seem to use because totem pops up., no biggie just want sound, fix players after.

When you say "downloaded" I hope you mean thru synaptic.

---

### Post by johntravis on 2008-10-18
sound works but not in totem--no sound when playing dvd movies

---

