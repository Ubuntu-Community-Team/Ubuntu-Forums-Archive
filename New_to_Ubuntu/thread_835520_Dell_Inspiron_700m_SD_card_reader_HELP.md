---
title: "Dell Inspiron 700m SD card reader HELP"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by resiak on 2008-06-20
Okay, so, I have browsed several forums without much success.
The SD card would mount, and after a few moments, it would be read. I had to right click and click "browse" to actually look at the contents, however, if i tried to open another window, it would freeze very easily, and if I simply double-clicked the icon, it would also freeze. I tried getting access too the setpci file, and without success tried modifying it via a recommendation on a forum. Now the card won't mount at all... help?
This is on 8.04, btw.

---

### Post by cariboo on 2008-06-20
What is the output of Applications-->Accessories-->Terminal **dmesg**, when you plug your sd card in.

Jim

---

### Post by resiak on 2008-06-20
[  173.381709] tifm_core: MMC/SD card detected in socket 0:0
[  173.797171] mmc0: new SD card at address b368
[  173.797706] mmcblk0: mmc0:b368 Lexar 1934848KiB 
[  173.797773]  mmcblk0: p1
[  174.105198] tifm_sd0:0 : card failed to respond for a long period of time (12, 1)
[  174.105436] tifm0 : demand removing card from socket 0:0
[  174.105481] mmc0: card b368 removed
[  174.105805] mmcblk0: error -123 sending read/write command

This is followed by a bunch of errors in varying sectors, such as:
[  174.106190] end_request: I/O error, dev mmcblk0, sector 448

---

### Post by Moistdef on 2008-06-22
I also have a 700m. I recently installed Ubuntu so I am completely new to it. 

When I insert a regular SD card, my computer completely freezes. I tried it twice and had to disconnect my AC and battery for it to turn off. 

Any help would be greatly appreciated.

EDIT: Never mind, I found the answers I needed in this thread: [http://ubuntuforums.org/showthread.php?t=165336&highlight=dell+700m+SD+card+reader](http://ubuntuforums.org/showthread.php?t=165336&highlight=dell+700m+SD+card+reader)

---

