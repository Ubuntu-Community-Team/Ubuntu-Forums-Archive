---
title: "Cannot Boot LiveCD w/compact flash installed"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by m00njal on 2008-08-19
Hi there everyone. For the past week or so, I have been trying to build sort of a "net-top" system with the new Intel Atom hardware I picked up at my local Fry's. (Frys.com) 

I bought this enclosure from mini-box.com to house all the hardware, [http://www.mini-box.com/M200-Enclosure_2?sc=8&category=87](http://www.mini-box.com/M200-Enclosure_2?sc=8&category=87) , which by chance also has a built in Compact Flash-to-IDE adapter. Now for those who don't know, these adapters are straightforward board-to-pin adapters with no conversion done on the signal side, the CF card shows up as an HDD in the bios/most operating systems. 

So, I went along with initially an older 256mb CF card plugged in and booted a liveCD of gOS 3 ([www.thinkgos.com](www.thinkgos.com)) and it booted fine, and I saw the CF card as a drive on the desktop, and could write to it (again, a smaller 256mb no-name card). 

So with the intention of installing to a larger CF, and I went out and bought an 8GB RiData CF card, and attempted again to boot the liveCD.


However, Somewhere half way along booting, instead of getting the desktop, I get the BusyBox (Debian bootloader) prompt and a  prompt that starts with "initramfs" and "type help for more options" 

This had my very puzzled, I didn't know what to make of it. So I downloaded and burned Xubuntu, and it had the same exact problem, along with a regular Ubuntu 7.10 disc. I thought the card might be bad, so I checked/formatted it in another computer via USB reader, but still the same problems. So I returned that 8GB and came home today with a kingston 4gb drive. I have the exact same problem. 

So, I have googled around, but have yet to find a similar issue to mine. Also, I have tried "ide=nodma" on booting up any distro, but same problem still. My question is, what do I need to do to get a LiveCD to boot, then install to it? I know its been done before? And why is it that my smaller CF cards recognize and are problem free, versus large (4GB and 8GB) cards?

Infact, I have installed FreeNAS on several computers using a CF to IDE adapter with no problems at all, just comes up as an HDD.


Everyone's feedback is greatly appreciated.

---

### Post by cwsnyder on 2008-08-24
OK, this is what I have learned on-line about flash cards:  When you use a flash drive larger than 2G, the flash drive is physically formatted differently.  Older cameras cannot even use cards larger than 2G.  Try using a 2G or smaller, new card as your main storage and use the 4G or larger card through USB connection.

cwsnyder

---

