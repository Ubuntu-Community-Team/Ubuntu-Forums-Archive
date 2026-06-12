---
title: "sound stopped working"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by bergeo on 2012-09-10
The sound on my desktop box stopped working a couple days ago.  Now all I get is a little crackly static from my speakers when a sound plays.  It's sometimes just barely recognizable -- like when skype starts up, I can recognize the familiar startup sound from the crackles.

I'm running 12.04 with all the latest updates installed, and with gnome session fallback.

I first noticed the problem shortly after installing vlc media player.  I've since uninstalled it but the problem persists.  I'm not sure if that's what caused it though.  I also installed a bunch of ubuntu automatic updates around that time as well.

If I reboot into Windows the sound works fine, so I know the hardware is okay.

Any suggestions?

---

### Post by bergeo on 2012-09-10
I fumbled around and found a fix.  I ran alsamixer from the command line and noticed that the PCM level was at zero.  No idea what PCM is, but I bumped it up to 100% and sound started working.

---

### Post by Hadaka on 2012-09-10
Hi,

PCM =  pulse code modulation

if you are satisfied with your sound fix, please mark this thread as SOLVED

---

### Post by bergeo on 2012-09-10
Done.  Thanks for the tip.  (Still no idea what PCM is though. :)

---

### Post by Hadaka on 2012-09-10
Hi...PCM = Pulse Code Modulation

in short....it takes an analog signal....kinda looks like this ->    ~~~~~~~~~~
and turns it into a digital signal-------------------------------------->    110110101100110

A to D conversion.....google it.

---

