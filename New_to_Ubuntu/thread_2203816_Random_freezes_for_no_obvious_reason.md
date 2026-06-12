---
title: "Random freezes for no obvious reason"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by random4 on 2014-02-05
Good day to everyone!

Just installed Ubuntu on a nettop used as HTPC, and things are working fine except one weird issue.

About once per 1-2 minutes any kind of video content freezes for second with both video and audio stuffering. It happens with video from flash player and VLC playing from hard drive alike; same thing happens with flac and mp3 music.
Machine itself is not that bad: it has 4GB of RAM and i3-processor, so it probably should handle any kind of video playback, and freezes never happened when it was working with Windows.

I tried to disable any kind of visual effects, but situation remains the same.

I'm a novice when it comes to Ubuntu. Maybe anyone knows what i should look for when it comes to such issues?

Thanks in advance.

---

### Post by LukasLeon on 2014-02-05
Well, when you are sure that it worked allright with win, there wont be a problem in your HDD propably, the only thing that comes to my mind are drivers / updates. What kind of GPU are you using? and have you installed drivers for it? also try sudo apt-get update and sudo apt-get dist-upgrade in terminal.

---

### Post by Vladlenin5000 on 2014-02-06
+1 for GPU drivers
It's the usual culptit.

---

### Post by random4 on 2014-02-08
> **LukasLeon said:**
> Well, when you are sure that it worked allright with win, there wont be a problem in your HDD propably, the only thing that comes to my mind are drivers / updates. What kind of GPU are you using? and have you installed drivers for it? also try sudo apt-get update and sudo apt-get dist-upgrade in terminal.
 1) It is built-in Intel HD Graphics.
 2) As far as i know, without them desktop visual effects are unavailable, so yes, they are probably there (although i don't know how to double-check that).
 3) Did exactly that, things remain the same.

 Tried playing stuff directly from usb flash drive, and problem is still there, so it seems that HDD is fine.

---

### Post by random4 on 2014-02-09
> **Vladlenin5000 said:**
> +1 for GPU drivers
 It's the usual culptit.
 So how do i properly check whether they are there or not?

---

### Post by random4 on 2014-02-15
Never mind, after all the trouble just installed Debian 7.4 instead, works like a charm.

---

