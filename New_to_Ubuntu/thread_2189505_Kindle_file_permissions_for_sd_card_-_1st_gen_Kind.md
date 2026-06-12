---
title: "Kindle file permissions for sd card - 1st gen Kindle"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-11-22
I have a first generation Kindle given to me a week ago. It has a slot for an SD card. I've installed a 1 gig sd card in that slot. The write-protect tab or switch is open or not-protected. The first day I had the Kindle and plugged it into the computer, the device acted like an ordinary memory card/usb flash "drive". Then I tried listening to some music. It played through the Kindle without problem. When I next plugged the Kindle back into the computer, the kindle did not mount and lsusb did not show it.

The next day, sometimes, plugging in a usb cable between the kindle and the computer works. But the kindle often says that I need to re-format the card. I tried that with Disk Utility, formatting as Master Boot Record and Win95 FAT32 (LBA) (0x0c).  After that, plugging in the kindle shows only the internal kindle memory, not the sd card. In the Kindle Settings and Device Info screen, the sd card shows: "0 MB available". And it's empty, because it was formatted just before I wrote this post.

I tried installing mpt and gMTP. gMTP doesn't find the first generation Kindle. Calibre find the Kindle.

Looking in /media, while the device is mounted shows: 

Kindle and Kindle-1gig. Kindle-1gig is the name I gave the SD card.

Files and be cut, copy and pasted between the Kindle and Kindle-1gig.

Terminal output of lsusb:

Bus 001 Device 014: ID 1949:0001 Lab126 

Following a post I made a file:

mark@Lexington:/etc/udev/rules.d$ cat 51-android.rules

with this one line:

SUBSYSTEM=="usb", ATTR{idVendor}=="1949", ATTR{idProduct}=="0001", MODE="0666"

So, after all this, plugging in the usb cable, brings up the Kindle (internal storage) but the sd card isn't recognized. How does one change permission or convince the Kindle that the sd card is NOT write protected?

---

### Post by DuckHook on 2013-11-22
Mark,

Is it an old card? Cards with enough blocks dead from write fatigue will drop to permanent read-only, which shows up as write-protected. A burned-out partition or file-structure will do the same thing and is the usual culprit, as these blocks get written to more often than the general file/data-system itself. Linux may see the backup block, whereas Kindle might not. This is pure conjecture on my part and I'm not knowledgeable enough to tell you how to test it.

What does it do with another SD card?

---

