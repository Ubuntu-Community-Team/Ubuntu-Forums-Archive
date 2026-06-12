---
title: "On boot Bad Taint for sound codec and module"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by Punk_A_Cat on 2014-06-30
I updated from 12.4 to 14.4 Trusty Tahr, and since the update my soundcard doesn't work - it doesn't even exist as far as alsamixer is concerned - it only shows the beep and nothing else, but when a hardware search is done the card shows up as Realtek ALC880 Intel corp 8280IFB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio controller (rev3).
[FONT=arial]In sounds settings it's just Dummy output, and testing sound gets nothing.[/FONT]
[FONT=arial]On boot it goes to a black screen and shows 
snd_hda_codec: module has bad taint, not creating trace events
snd_hda_controller: module has bad taint, not creating trace events
and it goes on to ignore both - which I assume is why I have no sound?
I have installed oem-audio-hda-daily-dkms, but that doesn't seem to have helped at all.
I'd really like to get sound working again, I do remember having some issies getting it to work under 12.4 but I don't remember how I fixed it, and can't find anything helpful for 14.4.[/FONT]

---

### Post by jay43 on 2014-08-05
I'm having the same issue, although I'm still getting sound.  I just get the errors on boot up.  Have you figured out what is causing the notifications?

Thanks,
Jay

---

### Post by spider4d1c on 2014-08-15
I have the same error messages as I have installed [FONT=arial]oem-audio-hda-daily-dkms (according to this guide [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS))[/FONT] but I have sound, not the one similar to DOLBY ADVANCED AUDIO though as I have it in windows 7.
What to do to fix the errors and to have the desired sound ?

---

