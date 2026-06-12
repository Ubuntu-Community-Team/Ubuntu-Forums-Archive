---
title: "SKYPE probem in ubuntu"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by wariskampar on 2008-09-16
I can not make any call in my Ubuntu box through SKYPE. I will message this message if I try. 
"Problem with Audio Playback"

Looking at my Sound Setting; I select 'AutoDetect' for all options. Can anyone tells me what should I do. Thanks in advance

---

### Post by frolle on 2008-09-16
Try typing lspci in a terminal and post output.

You could just try selecting all the devices in skype configuration and see which one works.

---

### Post by Crafty Kisses on 2008-09-16
I've found the solution to this is, close all programs and re-open Skype, it's a weird fix, but it works for me.

---

### Post by YldGuy on 2008-09-16
> **wariskampar said:**
> I can not make any call in my Ubuntu box through SKYPE. I will message this message if I try. 
"Problem with Audio Playback"

Looking at my Sound Setting; I select 'AutoDetect' for all options. Can anyone tells me what should I do. Thanks in advance

try putting all to ALSA instead of autodetect. Did you test the sound there? Does everything work over there in the settings?

---

### Post by wariskampar on 2008-09-16
Problem solved! frolle is right. I just need to change devices option in Skype config. Before that I went through editing /etc/pulse/default.pa, ~/.asoundrc and /etc/esound/esd.conf, which only make thing worse (can not hear any sound from my system. Once revert all the setting and restart alsa, everything goes back to normal and Skype is now fully functional:)

How do I send message to handphone using Skype (in Ubuntu)? I fail to find the option.

---

