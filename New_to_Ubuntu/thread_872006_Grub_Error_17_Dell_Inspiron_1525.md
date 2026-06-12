---
title: "Grub Error 17 Dell Inspiron 1525"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by nintendorulz55 on 2008-07-27
I pushed the wrong button this morning when i was all groggy, and accidentally opened Dell Media Direct. I exited and when i tried to boot, i got error 17... i've tried everything on the forums. I'm very n00b-ish when it comes to partitions and such, so please go step by step to get me through this! I don't want to reinstall... mainly because I was playing Mother 1 on an NES emu and i got really far and i DONT want to do it all again.. but if there is a way to back that up and my music and documents and whatnot, i guess i would consider it.

---

### Post by Vakman on 2008-07-27
Have you tried using a disk called Super GRUB? You can download it and burn it to a CD. 
**[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)**
There is the site. Try it out, I used it to restore my Ubuntu a few times already as well as others.

---

### Post by nintendorulz55 on 2008-07-27
im going to try this.. i'll report back later.

---

### Post by stevoo on 2008-07-27
Or post us the below

sudo  gedit /boot/grub/menu.lst
sudo fdisk -l

and give us results

---

### Post by nintendorulz55 on 2008-07-27
nope. SGD did not work. here's the output, stevoo.
the first one... nothing. menu.lst pops up, but theres nothing in it. i know thats a big problem.
second..
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        9403        9730     2620416    c  W95 FAT32 (LBA)
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

---

### Post by Vakman on 2008-07-27
All right. Try this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and do as it says basically and then see what happens :)

---

### Post by panther_sn on 2008-07-27
I did exactly the same thing with my wifes inspiron, the quick easy solution to this (dont ask me why it works it just does), do the same thing press the dell media button, have it start loading then hard power the machine off and restart and all shoud be fine.  Hope that works for you as well as it does for me
Stuart

---

### Post by nintendorulz55 on 2008-07-28
> **panther_sn said:**
> I did exactly the same thing with my wifes inspiron, the quick easy solution to this (dont ask me why it works it just does), do the same thing press the dell media button, have it start loading then hard power the machine off and restart and all shoud be fine.  Hope that works for you as well as it does for me
Stuart

Oh my God!!! that worked! to think it could be that simple! thank you 20 times over!

---

