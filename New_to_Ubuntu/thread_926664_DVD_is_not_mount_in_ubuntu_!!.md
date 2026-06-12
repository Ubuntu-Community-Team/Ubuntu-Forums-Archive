---
title: "DVD is not mount in ubuntu !!"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Me! on 2008-09-22
Hello,

I have a dvd can play in dvd-player but Ubuntu says it's blank dvd !!

could any one told me how to play it in Ubuntu 8.04

 :sad:

This some info about dvd
dvd+rw-mediainfo /dev/dvd
INQUIRY:                [Slimtype][DVD A  DS8A1P   ][CA24]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Current Write Speed:   3.1x1385=4234KB/s
 Write Speed #0:        3.1x1385=4234KB/s
 Write Speed #1:        2.5x1385=3528KB/s
 Write Speed #2:        2.0x1385=2822KB/s
 Write Speed #3:        1.3x1385=1764KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     1.3x1385=1764KB/s@0 -> 3.1x1385=4234KB/s@332999
 Speed Descriptor#0:    00/332999 R@3.1x1385=4234KB/s W@3.1x1385=4234KB/s
:-[ READ DVD STRUCTURE#0 failed with SK=2h/ASC=06h/ACQ=00h]: Input/output error
:-[ READ DISC INFORMATION failed with SK=2h/ASC=06h/ACQ=00h]: Input/output error



[COLOR=Red]What can I do to mount it & play it in Ubuntu ?[/COLOR]

---

### Post by Orange_and_Green on 2008-09-22
Hello,

if you haven't already, you might want to install libdvdcss.

You can find the instructions and the legal notices here:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

If this does not fix it, maybe you could check if your DVD drive is OK (the easiest way to do so is to see if it can read other DVDs, or you could try and find a friend who has got an external USB DVD drive and see if you an read it with that)...

Hope this helps, good luck:)

---

### Post by jemate18 on 2008-09-22
what is the content of the DVD you are trying to open in UBUNTU?

---

