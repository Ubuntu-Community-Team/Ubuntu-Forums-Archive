---
title: "Gnome ALSA mixer Ubuntu 11.10"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Iang123 on 2011-10-17
Hi,

Could any of you tell me why ALSA mixer would not be opening in Ubuntu 11.10? I click on the icon for it to stat but nothing opens?

Cheers
Ian

---

### Post by roger_1960 on 2011-10-17
Hi

normally it runs by typing
> 
alsamixer

in a terminal

I agree, the Gnome alsamixer GUI package doesn't seem to run - no idea why.

---

### Post by Iang123 on 2011-10-18
Basically this is what's happening. On a fresh install I get no sound. So I tried ALSA mixer, after a few recommendations. So I try to open ALSA mixer, but no GUI shows up,I try open it in terminal with gnome-alsamixer, and it just throws up a bunch of errors. I tried running alsa mixer from within the terminal and no matter what I pressed or configured still no sound.

 So I installed Alsa mixer GUI, that opens, but it only shows 2 channels, and it shows the chip set as Pulse audio. So anyway, I uninstalled pulse audio and rebooted..

When it started back up again, I opened the alsa mixer gui program again, and now I had much more levels and it was showing the chipset as C-media, which is my sound card. So there was an option for spdif out, pressed it on and success! I had sound. However it was a short lived victory as I found that I could not get surround to work.

---

### Post by MartinusEx on 2011-10-20
Hi Folks,

same issue with me and I KNOW that it was different with 10.10

Not amusing though.


I tried the alsamixer in terminal and this starts..
did not play with all options by now

Martin

---

### Post by ThePinion on 2011-10-20
GUI is also not starting here. The terminal mode does work, but it doesn't give me the option I need.

The laptop in question is my girlfriend's old Macbook 2,1. It has this ridiculous bug/issue where you have to enable a certain bar on the Gnome AlsaMixer in order to get the sound to not sound like crap. She has to disable it any time she wants to plug her laptop into external speakers. So this is a pretty important issue. Unfortunately that option isn't available in the terminal mode. It worked just fine with Ubuntu 11.04.

Hopefully someone knows what to do. Here's full pastebin of trying to open gnome-alsamixer: [http://pastie.org/2728147](http://pastie.org/2728147)

---

### Post by chrisgerow on 2011-11-10
Same problem as everyone else.  Except I was trying to pass audio from a blue-ray player through my sound card to avoid using a switch or plugging and unplugging.  
I used gnome alsa mixer in ubuntu 10.10 and the changes carried through to my 11.10 update. However I did a fresh install recently and didnt make my changes to the sound before the upgrade this time. So i was outta luck gnome alsa does not work nor does terminal alsa mixer.

ANYWAYS, the solution is:

GMERLIN MIXER

this still works, not sure how, I pressed a few button and BAM sound from my blue ray blasting outta my PC speakers.

Cheers Folks

---

### Post by whoey on 2011-11-11
> **chrisgerow said:**
> Same problem as everyone else.  Except I was trying to pass audio from a blue-ray player through my sound card to avoid using a switch or plugging and unplugging.  
I used gnome alsa mixer in ubuntu 10.10 and the changes carried through to my 11.10 update. However I did a fresh install recently and didnt make my changes to the sound before the upgrade this time. So i was outta luck gnome alsa does not work nor does terminal alsa mixer.

ANYWAYS, the solution is:

GMERLIN MIXER

this still works, not sure how, I pressed a few button and BAM sound from my blue ray blasting outta my PC speakers.

Cheers Folks

great, gmerlin works for me too! Needed my line in control.

---

