---
title: "Spdif, 5.1 surround pulse audio (for the love of god please help)"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Iang123 on 2011-10-17
Hi,

I'm actually losing my marbles trying get this to work now. I'm very new to Linux (yesterday) but I think I've got a pretty decent handle on some things. 

I have a sound card with spdif out. now when I plug my headphones in to the sound card I get sound through, so at least I know the thing is working. I have been searching round for hours, and it looks like digital passthrough is not possible with pulse audio? 

However, I stumbled across another post that said that in the latest version that this is possible! If it is, I'll be a very happy man. Could any of you tell me how to upgrade to the latest version? I have been on the website but can't really make head nor take of it?

I can get sound when I completely disable pulse audio and just use alsa mixer, but then I can't get 5.1 surround? 

Oh, I'm using Ubuntu 11.10 by the way

Cheers
Ian

---

### Post by wesleybishop on 2011-10-17
Not sure what the last version of what you are looking for is. Pulse? Ubuntu? Alsa?

---

### Post by Iang123 on 2011-10-18
It was for pulse audio, turns out it looks like 1.0 is already installed on Ubuntu 11.10.

Basically this is what's happening. On a fresh install I get no sound. So I tried ALSA mixer, after a few recommendations. So I try to open ALSA mixer, but no GUI shows up,I try open it in terminal with gnome-alsamixer, and it just throws up a bunch of errors. I tried running alsa mixer from within the terminal and no matter what I pressed or configured still no sound.

 So I installed Alsa mixer GUI, that opens, but it only shows 2 channels, and it shows the chip set as Pulse audio. So anyway, I uninstalled pulse audio and rebooted..

When it started back up again, I opened the alsa mixer gui program again, and now I had much more levels and it was showing the chipset as C-media, which is my sound card. So there was an option for spdif out, pressed it on and success! I had sound. However it was a short lived victory as I found that I could not get surround to work.

So basically that's my main issue, and I just can't figure it out?

---

