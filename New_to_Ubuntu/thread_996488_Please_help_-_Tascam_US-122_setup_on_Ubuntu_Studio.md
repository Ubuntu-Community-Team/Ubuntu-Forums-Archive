---
title: "Please help - Tascam US-122 setup on Ubuntu Studio"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by jstaples on 2008-11-28
I am desperate for help getting my system to recognise my Tascam US-122. I am brand new to linux of any flavor. I installed Ubuntu Intrepid Ibex as a dual boot on an Acer TravelMate C310. Install went great. Then I discovered Ubuntu studio which I was able to install with a little more trouble. I then tried to hook up my Tascam US-122 which I was previously using on this same machine with Cubase LE in windows XP. I have read all the threads I can find on the subject.  I have read the fine manual for Jack, Alsa,Ardour,   I just can't seem to get this thing working. I'm sure I just have something in the wrong place.

I moved the usx2yloader folder to root/lib/firmware/

typing lsusb at the command prompt shows
Bus 003 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw).
So I know the system sees it, It's just that the green light won't come on and Jack Doesn't seem to know it exists.

john@john-laptop:~$ usx2yloader
usx2yloader: no US-X2Y-compatible cards found

Alas, the coveted green light still eludes me

---

### Post by jstaples on 2008-11-28
Duh.   Fixed.  I read and tried everything one more time an got it fixed.
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

---

