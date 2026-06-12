---
title: "Fresh install; restart later and don't get a display."
date: 2012-08-11
forum: New to Ubuntu
---

### Post by captainbrad on 2012-08-11
Hey yall. I'm absolutely completely new to Ubuntu. The last time I used Linux was in the mid-80s when I played kid's games on my dad's old Unix system, just to give a perspective of how little I know what I'm doing :P

Okay, so, I installed Ubuntu using the Windows installer and it has me restart the computer and boot into Ubuntu and so I do, and I get to the log in screen and everything goes great! Except that while I'm piddling around in Ubuntu and it downloads those updates in the background, the little system icon turns red and says to restart to apply updates. Alright, well I do that but when it restarts, it comes back to a red screen. I hear the little 'bump' sound that plays at the log in screen, so I know it's there, I just.. can't see it. Instead I get a very bright red color and have to hard-reset the computer to get off the screen.

Okay, so (no offense) I decided to install Mint instead, and that went fine, the first boot was great, I was clicking around seeing what everything was like but after installing updates and restarting - I again can't log in (and for Mint I got a very bright image that flickered and could probably induce a seizure in some people!) So alright, I thought, maybe it was drivers? So I deleted that and tried Ubuntu again, got to the log in screen on the initial boot and decided to try it in 2D mode from that little button before logging in. Things went very well then and it was much faster and much more responsive than the first time I had tried Ubuntu and so I thought that fixed it. I went ahead and installed all the updates (took like an hour) and restarted so it could configure them -- but again! When it booted back up all I got was that red screen.

So what can I do? What am I doing wrong? Here are system specs from Speccy:

CPU
AMD Athlon II X3 455	31 °C
Rana 45nm Technology
RAM
5.00 GB Single-Channel DDR3 @ 665MHz (9-12-12-30)
Motherboard
ASRock M3A770DE (CPUSocket)	39 °C
Graphics
SyncMaster (1440x900@60Hz)
AMD Radeon HD 6800 Series (Sapphire/PCPartner)	47 °C
Hard Drives
466GB Seagate ST500DM002-1BD142 ATA Device (SATA)	41 °C
Optical Drives
SAMSUNG DVD-ROM SD-616T ATA Device
Audio
VIA High Definition Audio

---

### Post by Paqman on 2012-08-11
> **captainbrad said:**
> What am I doing wrong?

Nothing, it's not you. Sounds like you've hit a bug.

From what you describe it sounds like you're having graphics problems. Have you installed the driver for your graphics card?

---

### Post by captainbrad on 2012-08-11
I tried that on the second go-around before restarting and it went through the whole process (roughly 10 minutes) and at the very end said that it failed, so I tried the other one (called post something-or-other) and that failed as well. :confused:

---

### Post by Paqman on 2012-08-11
How did you install the driver? Using the Hardware Drivers tool? What was the error it spat out?

---

### Post by captainbrad on 2012-08-11
From the hardware driver tool, yes sir. It had an alert-type thing next to the mail icon up by the clock saying that I had to pick one out of two options, the ATI driver or the ATI driver that mentioned post-something. I don't remember the exact error but it was something along the lines of failing to install. To re-create it I'll have to reinstall Ubuntu since I can only use it on a fresh, un-updated install; should I go ahead and do that for you? I'm worried that all these re-installs are going to hurt my hard drive (I have the worst luck in the world with hard drives and go through one a year at least).

---

### Post by NikTh on 2012-08-12
> **captainbrad said:**
> I tried that on the second go-around before restarting and it went through the whole process (roughly 10 minutes) and at the very end said that it failed, so I tried the other one (called post something-or-other) and that failed as well. :confused:

Hi , 
Question: Why you try to install additional drivers ? Do you have any problem (like tearing or lag ) with open source driver ?(radeon) 
Thanks

---

### Post by captainbrad on 2012-08-12
Well the first time I didn't install them; Ubuntu was doing automatic updates in the background and when it was done it asked me to restart the computer so it can apply them and it's after restarting that I don't get a display anymore (other than the bright red screen).

So the second time when I uninstall/reinstalled Ubuntu I manually installed them but the same thing happened.

The automatic updates it installed was well over 300 updates so I don't know if I could pinpoint the one causing this (besides the fact that I'm a complete noob D: )

---

### Post by NikTh on 2012-08-12
Hi ,
so the problem occurs either with radeon or fglrx. So might not be a graphics driver problem.
Try to boot from another kernel. Can you ? Do you have grub menu? If not then keep press the "Shift" during PC boot. Choose an older kernel to boot.
Thanks

---

### Post by captainbrad on 2012-08-21
I'm not entirely sure what grub menu is. Like I said, I am absolutely new to this and don't know a thing -_- I will try though, it'll mean having to install Ubuntu again (since I can only use it once-per-install before this problem occurs again).

---

