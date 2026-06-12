---
title: "9800se softmod in Ubuntu?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by vapd on 2008-05-03
Hi,
just DL'd the latest Ubuntu and just removing the last of my data from my old Athlon rig before I try my first install of Ubuntu, or linux of any kind for that matter. My aim is to use Myth TV and create a media centre type thing. But first things first.

My old rig is based on an Abit An7 with an old 256 bit ATI 9800se agp card. When using it with windows it was possible to use a driver that unlocked the 9800se's disabled pipelines, effectively making it an 9800pro. Is such an option available in Ubuntu?

I mention the mobo type in case anyone has had problems with it under Ubuntu. I want to install to a drive on the SATA controller and use the integrated networking and sound.

Thanks!

---

### Post by frup on 2008-05-03
I dunno so much if that is possible or even necessary in linux but you could probably try editing xorg and see if you can trick xorg in to thinking it is a 9800pro instead of se but really I think they all use exactly the same driver in linux (fglrx or the open source ati)

---

### Post by vapd on 2008-05-03
Okay, thanks. I guess that it isnt really important. I might try something like that in the future.

---

### Post by arpanaut on 2008-05-03
Correct me If I am Wrong, 
I thought the se-> pro mod was a firmware hack.
If that is so then the OS should not make a difference...
The mod should still be in force. No?

---

### Post by vapd on 2008-05-03
I think there was a firmware mod for a different card that unlocked the disabled pipelines, for the 9800se to pro it is just a driver mod.

Am ready to install, just checking my BIOS settings, come across:

APIC mode, enabled or disabled and below it:

mps version control for os 1.1 or 1.4

am having a look for what it should be but if anyone can tell me if it matters under Ubuntu I would be greatfull!

---

