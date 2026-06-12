---
title: "Boot CD read error"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Ahmed28 on 2008-11-03
Hi, it's my first time trying Linux, I downloaded Ubuntu ver 8.10, I burned it to a cdrw, the burning process and verify went succesfull, I used Ultra ISO for burning the image

When I booted the CD, there is a menu with several option, I choosed the first "Run Ubuntu without changes in system"
The result is always "Boot CD read error"

Here is my specs

> CPU Type                                          DualCore AMD Athlon 64 X2, 2600 MHz (13 x 200) 5000+
Motherboard Name                                  Zotac GeForce 8200/8300
Motherboard Chipset                               nVIDIA MCP72/77/78, AMD Hammer
System Memory                                     2048 MB  (DDR2-800 DDR2 SDRAM)
  
Video Adapter                                     ATI Radeon X1300/X1550 Series Secondary  (512 MB)
Monitor                                           Dell M991  [19" CRT]  (5C5441CJH07J)
Audio Adapter                                     Realtek ALC662 @ nVIDIA MCP77/78 - High Definition Audio    Disk Drive                                        WDC 160gb Sata II

Can someone help me ?




Thanks

---

### Post by kellemes on 2008-11-03
Last post of following thread may be helpful..
[https://answers.launchpad.net/ubuntu/+question/12949]("https://answers.launchpad.net/ubuntu/+question/12949")

First I'd try burning slow (4x) at another drive, if you have one available.

---

### Post by Ahmed28 on 2008-11-04
Burned at 4x, still the same error msg "IO read error boot cd", I doubt that my download is corrupt, since I use download manager to download it


It is possible the culprit is my sata DVDRW which I used to boot it ?

---

### Post by Ryadt on 2008-11-04
Check the md5sum of the downloaded iso.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ahmed28 on 2008-11-05
@Ryadt, thanks, I checked the checksum, it's different, so I redownloaded it from another server, now it works, what a magnificent OS, wow

---

