---
title: "Sound Blaster SB0570 Not giving sound on Ubuntu"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by SaintRatho on 2008-11-28
OK, so I just got this Sound Blaster SB0570 and got it to install on XP and works fine (have dual boot on my PC) then I came to Unbuntu and can not get any sound out of this thing. 

I already tried looking under system>admin>hardware drivers. Only shows my Nvidia there. 

Also double clicked on my sound icon to bring up options and tried all the different devices, but still no sound. 

I am about Med on my Ubunut experience. I will tell you I get a little lost when a terminal is involved, but if you tell me the commands I can get that much done. 

Let me know if there is more stuff you need to know to help.

Thank you

---

### Post by bodhi.zazen on 2008-11-28
see if this helps :

[https://wiki.kubuntu.org/DebuggingSoundProblems](https://wiki.kubuntu.org/DebuggingSoundProblems)

I do not know your exact card, you may need to use alsa rather then pulse audio.

---

### Post by SaintRatho on 2008-11-29
OK, I followed all those steps, except the ones with terminal stuff. Whatever I entered was like bad commands and such or not found. Everything, even my BIOS seems to have the card in place. 

The interesting thing I DID think to try while I was checking that stuff was to put in a live 8.10 disc. The strange part was that the login drums made sound, but when it got into the actual desktop all the sound stopped again. So even on a fresh live CD it is not playing my sound. The device it chose and I have is "CA0106 (Alsa mixer)" I assume this is the right device.

---

