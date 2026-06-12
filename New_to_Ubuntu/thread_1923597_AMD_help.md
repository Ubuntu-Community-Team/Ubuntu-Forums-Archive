---
title: "AMD help?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by doomsday440 on 2012-02-11
Thought i'd ask a few questions in one post. starting with my specs..

AMD Phenom II x4 955 Black Edition 3.2ghz, OC'ed 8%
MSI R5850 1Gb GDDR5 Twin Frozr II
    Connected Via HDMI to Vizio RazorLCD 22" HDTV, 1920x1080 32 bit res.
4GB (2x2gb) Corsair XMS3 Dominator w/DHX
Maxtor 40gb HDD (Ubuntu 11.10 Oneiric Ocelot x64 installed)
Hitachi 1TB HDD (Windows 7 64 bit Home Premium installed)
ASUS M4A77TD Motherboard
VIA Vinyl Internal HD Audio
(Internet connection via either Samsung Solstice or Samsung Strive through USB under AT&T Mobile 3G GSM Connection)

Quick note beforehand; this is the straight up disk install on a separate hard drive, I was running Wubi before and it was having the same problems. I'm considering downgrading to 11.04 or 10.10, I already have 10.04LTS x64 on a CDR floating around here somewhere but I'm not sure I want to go back to it. If it helps I could also go to an x86 version of Ubuntu but I'll probably lose half my ram's functionality while running it.

Okay so First thing I want to bring up is i've had the issue of the proprietary AMD Post release updates in the extra drivers window gives me a failure message and says to look at the jockey log file. If I download the AMD Catalyst Proprietary drivers, version 11.11 rev 12.1 and install the .run file it gives me, it doesn't seem to really do anything except manage my resolution and whatnot through the HDMI connection with the CCC, as when i boot up after installing it puts a border around my screen (scales it down, i have to reset it to 0% scaling) and when i try to open second life it gives me a message saying "failure to create window" which means the FGLRX drivers either aren't activated or not working properly. The second proprietary driver option not labeled as post release installs fine though.

Second thing; when using the audio through the Cypress HDMI audio (as listed in the sound options for output) certain programs sound just ghastly. if i'm listening to music through banshee and i get a blip from Skype, the sound quality of that blip is insanely bad, and distorts the music for a moment or two afterwards. I have a Cyber Acoustics USB headset and if i use that as my primary sound output source it gets no distortions, no issues at all. 

Finally, I know this isn't really the fastest OS for 3d processing, games, etc.. but on Windows 7, Second Life (referring primarily to the Phoenix, Firestorm and Singularity viewers) runs mostly at a very smooth 30 - 70 FPS on all high or ultra settings. Under the version of Ubuntu I'm running it gets rather noticeable stuttering and i only get around 22FPS in most areas.

Any solutions, fixes, workarounds, etc are welcomed. Thanks in advance.

---

### Post by sadaruwan12 on 2012-02-11
First of all welcome to the forum !

Now about your graphic issues well with the ATI or now AMD the linux support is very very bad I'd a ATI once I only used it with the default open driver never went for the vendor release 'cos it breaks things. But I switched to NVIDIA they are gr8 for linux good driver support and never breaks your system after upgrade.

the sound part well use VLC not banshee but that I cant help you with never had an issue there ever.

P.S: I my self is a die hard AMD fan never liked intel too slow.

---

### Post by doomsday440 on 2012-02-11
well, banshee works fine, audio quality is good. but when other applications make noises while i'm using the Cypress HDMI Audio, it sounds horrible for the duration of the noise.. I dunno. might have a problem with multichannel audio under the AMD drivers, because the USB headphones/microphone I've got work fine, no horrible quality ever.

I'm probably going to stick to AMD setups, they're generally more stable than Nvidia/Intel. Drivers aren't anything special but the cards are cheaper and they tend to last longer than Nvidia cards of equivalent power.

Hmm.. Does anyone know of a possible 3rd party driver for AMD/ATI users on linux? I'd once heard of a hybrid Nvidia/ATI driver on Windows that allowed for PhysX processing through Nvidia and output with ATI..

---

