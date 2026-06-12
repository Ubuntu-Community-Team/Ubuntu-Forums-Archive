---
title: "[SOLVED] How to mount digital camera?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by ingeva on 2008-09-03
When I connect my digital camera (Nikon D80) to the USB I find two new devices, /dev/sdc and /dev/sdc1.

When I try to mount the latter as -t vfat I get the message:

can't read superblock (/dev/sdc).

Advice please?

---

### Post by falcon61102 on 2008-09-03
Have you tried mounting sdc1?  It seems that /dev/sdc is the entire disk while /dev/sdc1 may be the actual partition.  To get more info, run:
```
sudo fdisk -l
```
-l being a lower case L

That will list a little more of the specifics about the partitions.

---

### Post by clive littlewood on 2008-09-03
Hi

Have you got Digicam loaded on you box ?  (download from synaptic)

I use this for my cameras (including a nikon coolpix) and it auto detecs just fine.

hope this helps

cl

---

### Post by Vivaldi Gloria on 2008-09-03
On a side note, you can buy a cheap memory card reader for 10-15$. It'll automount and it'll copy faster.

---

### Post by timcredible on 2008-09-03
install digikam and kipi-plugins from synaptic (digikam is great).  it has recognized every camera i've thrown at it so far.  and if it doesn't understand the d80, just pick 'mass storage camera' or whatever.  also, if you're using raw files, you can read them in digikam because it installs dcraw by default.  you can also install rawtherapee if you don't like dcraw.

---

### Post by ingeva on 2008-09-03
> **timcredible said:**
> install digikam and kipi-plugins

Thanks for these tips!
Busy now but I'll check them out and respond ASAP!

---

### Post by ingeva on 2008-09-04
> **clive littlewood said:**
> Hi

Have you got Digicam loaded on you box ?  (download from synaptic)

I use this for my cameras (including a nikon coolpix) and it auto detecs just fine.

hope this helps

cl

Downloading digikam right now. It's for KDE, but I guess it's OK?
OK. Downloaded.
```
sudo -fdisk -l
```

shows no changes.

Well digikam started ok when I tried. Guess I'll find out more. If not I'll ask you experts here! :)

I would have preferred just to see the camera contents as a regular folder/directory because I like things to be simple, but you must live with what you have. :)

---

### Post by ingeva on 2008-09-04
No dice.

I used the help system on line and followed the tips there.
The program reports that no camera is connected.

I tried F-spot and it reports the same.

It IS turned on, and the LCD display shows "PC".

Next step please? :)

---

### Post by ingeva on 2008-09-05
No more tips?

It's a fact that the system recognizes /dev/sdc and /dev/sdc1,
but fdisk does not and mount reports that the "disk" can't read the superblock.

I'll experiment a little: Connect it to a Windows computer and reformat the "disk" and see what happens. If I ruin the formatting I can always use the camera to reformat.

---

### Post by ingeva on 2008-09-05
> **ingeva said:**
> 
It's a fact that the system recognizes /dev/sdc and /dev/sdc1,
but fdisk does not and mount reports that the "disk" can't read the superblock.


I had some trouble removing the existing partition on the SD card, but using a Knoppix live CD I could do it and then I could create a new FAT32 partition using the old laptop with W2000. However, the camera then wouldn't see the pictures on the card (I had copied a few pictures to it after formatting).

After a little more studying I found that the USB setting on the camera (which is quite new so I haven't studied it in full yet) was set to "mass storage". This allowed me to access the pictures from W2000, but not from Linux.

Setting the mode to PTP made the whole difference. F-spot started immediately and the only complaint was a missing directory (~/Photos) which I created immediately, and I could copy pictures quickly and efficiently.

I had a similar experience with my Sandisk MP3 player, which requires special software and Windows XP to be used with the standard format setting. Setting it to "disk" solved that problem.

---

### Post by richardh9936 on 2008-09-09
Many thanks.  Using pictbridge wasn't obvious to me, so I'm very grateful to you for working that out.  P2p (pictbridge) worked perfectly.

---

