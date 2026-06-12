---
title: "did i just dodge a bullet?"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by lolful64 on 2013-01-28
i was using a wbfs manager and getting mad because i can't find one that works (for those who don't know what wbfs manager is, it is a formatting tool used to make a flash drive have a wbfs partition)

so i clicked device: /dev/sda1 and clicked format. the computer didn't seem to change but im pretty sure my 8gb usb can't turn into 16.00GB in a simple flash. along side /dev/sda1 i saw /dev/sr0 as well, but i DID NOT format that one.

i know for a fact that my computer has only 3 partitions, main hard drive 1 (contains what is left of my probably corrupt copy of windows vista+files), main hard drive 2 (contains all my needed files [i didn't allocate enough space D: so i had to relocate my files]) and finally one mystery partition. it has no format, its small (i forgot how small but im sure it's between 4-18GB)

so my question is simple. did i **** up my version of ubuntu and if i did how can i fix it

im too scared to turn off my computer incase its in a unstable state :(

---

### Post by ghost1227 on 2013-01-28
If it showed up as unknown partition type, my guess would be that it is the Windows bootloader partition. Windows creates a small 'system' partition on installation (Vista and later) that contains the files necessary to boot the OS, similar to the Linux /boot dir. If your Windows install is hosed already, you're probably safe.

---

### Post by MG&amp;TL on 2013-01-28
Uhh...normally, your main hard drive ubuntu runs off is labelled '/dev/sda[digit]', with successive partition numbers filling in ['digit'].

So I'd start worrying if you formatted that one. 

Can you bootup 'disks' or whatever it's called these days (Just search for 'disks' in the unity dash) and post a screenshot?

---

### Post by deadflowr on 2013-01-28
So where is Ubuntu installed?

I see one partition for vista, and one for files, and the third which is blank.

But it seems you were running your program on Ubuntu.
If that's the case, Ubuntu is still there, as partitioning and formatting tools typically don't work on mounted drives/partitions.
Most likely, if formatting /dev/sda1 actually worked, from the sound of it you probably wiped the vista drive.

Of course this is all speculation.

---

### Post by Bashing-om on 2013-01-28
lolful64; Hi !

The terminal command:
```
sudo fdisk -l
``` lower case "ell" ->
will tell the tale.
```
man fdisk
``` for full usage/syntax.
[INDENT]best regards

[/INDENT]

---

