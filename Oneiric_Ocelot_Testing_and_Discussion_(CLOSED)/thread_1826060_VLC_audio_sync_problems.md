---
title: "VLC audio sync problems"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pressureman on 2011-08-16
Is anybody noticing that VLC has had audio sync problems since Natty? With nearly every video, I have to delay the audio by about 300ms so that it's in sync with the video. I did a fresh install of Oneiric yesterday, hoping that the updated VLC/kernel/Pulseaudio/everything might fix it, but the problem is still there.

My notebook is no slouch (Core 2 Duo 2.6 GHz, 4GB RAM, 7200 RPM HDD), so I don't think hardware is to blame. Also, I don't remember this ever being a problem before Natty.

---

### Post by TopEnder on 2011-08-16
Have a look at this post I solved my sync problem better that what I use to do to solve it, works in 10.04, 10.10 & 11.04, not sure about 11.10 (Oneiric)

[http://ubuntuforums.org/showthread.php?t=1769271&page=](http://ubuntuforums.org/showthread.php?t=1769271&page=)

---

### Post by mc4man on 2011-08-16
A known and continuing issue with recent vlc releases and pulse audio
You could try a couple of different things - shown here (what I do - switch vlc to alsa) and a link to a thread showing a global pulseaudo edit

Overall here in both 11.04 and 11.10 use the 1.2+ version of vlc which has some advantages but either method should provide some relief w/ vlc 1.1X

[http://ubuntuforums.org/showthread.php?p=11126930#post11126930](http://ubuntuforums.org/showthread.php?p=11126930#post11126930)

---

### Post by P-I H on 2011-08-16
I have also this problem. So far I have used the function Tools/Tracksynchronisation i VLC to get a better lip-sync.

However post #18 in thread TopEnder referred to fixed the problem.

Change the line
load-module module-udev-detect
to
load-module module-udev-detect tsched=0
in /etc/pulse/default.pa

---

### Post by mc4man on 2011-08-16
what's a little interesting w. vlc 1.2 is that there is the begining of some sound menu sopport - open vlc, play, pause, album art, osd.

The indicator is still a hair more useful, vlc can't as yet be minised to the sound menu like the it can with the indicator

---

### Post by pressureman on 2011-08-21
This appears to be a problem unique to VLC though, because Totem (which is actually starting to look quite nice) is in sync, without having to make any changes to Pulseaudio config.

So.... whose fault is it? PA's, or VLC's?

---

### Post by mc4man on 2011-08-21
> **pressureman said:**
> This appears to be a problem unique to VLC though, because Totem (which is actually starting to look quite nice) is in sync, without having to make any changes to Pulseaudio config.

So.... whose fault is it? PA's, or VLC's?
It's not really a matter of 'fault', more a matter of available resources in videolan to correct this

---

### Post by pressureman on 2011-08-21
> **mc4man said:**
> It's not really a matter of 'fault', more a matter of available resources in videolan to correct this

Sorry, that was poorly phrased, and I didn't mean to start a witch hunt or anything like that. VLC is definitely a great app with a lot of features not found in other media players. I was just trying to ascertain whether it's an issue with PA (and thus should theoretically affect other apps), or whether it's specific to VLC.

---

