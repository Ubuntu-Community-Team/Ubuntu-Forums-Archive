---
title: "Potential black screen fix (not solved, but some progress)"
date: 2019-11-24
forum: New to Ubuntu
---

### Post by Durandall on 2019-11-24
I had 19.10 UbStu installed, and did the nomodeset workaround to install and mess around with it.

I'm not sure WHY I'm getting the black screen... but... what worked for me is installing linux kernel 4.14.156 - I tried both the generic and low latency versions (for UbStu)

Both worked, no nomodeset fix necessary for a standard boot.  

I say not solved, but close - because I still had no audio.  In the sound mixer I was sure to select HDMI output.  What's kind of strange is when I had an audio source play (tried rhythmbox and a youtube video) the sound mixer would SHOW that it had something playing - I mean the VU was actively tracking the signal.

Yes, I was sure the volume was up on my TV and Desktop.

Just thought I would put this out in case anyone else wanted to try.

Hardware:
AMD FX-8370
Asus 970 Aura MB
Corsair Vengeance 16gb
Asus RX480 Strix
2 separate 250GB SSD's (Not in RAID) - purchased with intent of dual-booting
Storage HDD
BD-Rom Drive

---

