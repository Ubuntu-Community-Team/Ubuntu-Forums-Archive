---
title: "USB drives won't show up"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by DouglasL on 2008-08-16
*(First off, I've searched the forum for similar threads, none of them helped)*

Okay, so I have a Sony Ericson k810i, which I'm plugging into my computer as an usb drive to transfer photos/music/etc. from and to it. This has always worked without any problems whatsoever, but today when I connected it it simply didn't show up.

Maybe this has something to do with what happened when I recently started my computer. It said something along the lines of "Routine drive check ..." and the startup took longer than usual.

Anyways, any help?
Thanks

---

### Post by nothingspecial on 2008-08-16
Do you mean there is no icon on your desktop?
Does it show up in places?
Does it show up in media?

---

### Post by MattBD on 2008-08-16
Can you run the following command in the terminal:
```
sudo fdisk -l
```
That should show what hard drives & USB devices are connected to your computer.

---

### Post by DouglasL on 2008-08-16
Well, now it worked lol.
I guess I'll use this thread i I get this problem again.

---

### Post by Hoyland84 on 2008-10-29
I have the exact same phone and the exact same problem. I have plugged my phone into other Ubuntu-systems and the phone and its card were then auto detected. This Ubuntu-machine runs hardy x64. Other plug-and-play products like my Samsung MP3 player are auto deteced and works smooth. When I plug the cable in the the computer and over to the phone i get the dialog box for file transfer on the phone display, so there's definitely some sort of connection, but still no sign of this in Ubuntu. I have no bluetooth on the computer.

sudo fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a24c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120896   971097088+  83  Linux
/dev/sda2          120897      121601     5662912+   5  Extended
/dev/sda5          120897      121601     5662881   82  Linux swap / Solaris

---

### Post by pianistinthedark on 2009-04-05
I have the same problem. I have a Sony C905 and it does not show up when I plug the USB pen drive adaptor into my computer.
If I use the wire adaptor, my phone gives me the option of Media Transfer, Phone transfer etc, so it is recognising some sort of connection, but still, nothing appears on the screen. It reads other USB external hard drives and the USB mouse and printer. 
What is causing this??

---

