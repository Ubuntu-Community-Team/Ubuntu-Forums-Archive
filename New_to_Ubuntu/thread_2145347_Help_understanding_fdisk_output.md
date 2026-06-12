---
title: "Help understanding fdisk output"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by PoddyOne on 2013-05-15
Hi there,

I'm having trouble whats going on with my partitions. Here is the output from 'sudo fdisk -lu':

```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00071a75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953127047   976562500   83  Linux
/dev/sda2      1953128446  3907028991   976950273    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3890352128  3907028991     8338432   82  Linux swap / Solaris
/dev/sda6      1953128448  3873673215   960272384   83  Linux
/dev/sda7      3873675264  3890348031     8336384   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 8536 MB, 8536457216 bytes
255 heads, 63 sectors/track, 1037 cylinders, total 16672768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x35bed1dd

```


It seems to be that /dev/sda1 is not actually being used at all, and gparted claims is not even mounted. I'm hoping to create a separate home partition there, is that possible?

Here is a 'df' output if it helps

```
Filesystem            1K-blocks     Used Available Use% Mounted on
/dev/sda6             945203588 38050440 859139532   5% /
udev                    4102024        4   4102020   1% /dev
tmpfs                   1644796      932   1643864   1% /run
none                       5120        0      5120   0% /run/lock
none                    4111980      328   4111652   1% /run/shm
/home/MYNAME/.Private 945203588 38050440 859139532   5% /home/MYNAME
/dev/sr0                3107832  3107832         0 100% /media/UDF Volume

```

---

### Post by prodigy_ on 2013-05-15
> **PoddyOne said:**
> It seems to be that /dev/sda1 is not actually being used at all, and gparted claims is not even mounted. I'm hoping to create a separate home partition there, is that possible?
Sure. Check these HOWTOs:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by PoddyOne on 2013-05-15
Thanks for that. I guess I'll have a read through the tutorials. I was just a bit worried about completely ******* things up.

---

### Post by PoddyOne on 2013-05-15
Actually, can I just ask one specific question:

I currently have 32-bit Ubuntu installed. I want to install 64-bit while retaining the separate home. It is a problem that the split of my filesystem is 'non-physical'?

---

### Post by Bashing-om on 2013-05-15
PoddyOne;

Keep in mind, any time you do not understand something, and you have done your homework, and continue to be confused; all you have to do is ask. Confirmation and guidance is but a keyboard away.

Also to see what is mounted and in-use; Terminal commands:
```
cat /etc/fstab
mount
```[INDENT=2]
best regards
[/INDENT]

---

### Post by PoddyOne on 2013-05-15
Hi Bashing-om,

Thanks. Sorry for being a little rushed/rude, I was feeling a bit frustrated. I understand your point.

---

### Post by Bashing-om on 2013-05-15
PoddyOne;

Coping with a computer system can be a frustrating experience, but sure makes you get your ducks all in a row !
Will do what I can to lessen the impact.
As to 32/64 bit operating systems relations, can be done but it is very complex and involves adding the required 32 bit libraries on the 64 bit system - the package manager may get confused and scream and holler -, the reverse can not be done as the addressing is not possible.

However, the "files" can be read from either operating system, after all they are just files. Just requires mounting the partition to access those "files". Is this what you have in mind ?[INDENT=2]
hope this helps

[/INDENT]

---

### Post by PoddyOne on 2013-05-16
Cheers,

>However, the "files" can be read from either operating system, after all  they are just files. Just requires mounting the partition to access  those "files". Is this what you have in mind ?

No nothing that complicated. I really just wanted to get my /home directory mounted on a separate partition, so that I could wipe my 32bit operating system and start again with 64bit. I basically just wanted a way of saving all my data. 

EDIT: Just re-read your post, yes I think that is exactly what I want to do. 

So I reformatted the /dev/sda1 parition, copied my home files there, and then tried to set up an automatic mount into /home. However I couldn't even boot once I did this.

I'm instead going to install the 64-bit ubuntu onto /dev/sda1, and then copy what home directory material I need over afterwards.

---

### Post by Bashing-om on 2013-05-16
PoddyOne;

I am trying to keep up with you // I do not think (re-)installing is needed.
> Panic not. Just proceed in a calm and orderly fashion.
If you have not done the (re-)install, should be able to install grub, to boot back up; easily mount "sda1" from the install and copy the wanted files back to the installed system ( even easier if ya want to do it from the GUI file manager).

When all done, iffen ya want ...make the old /home partition into a "data" partition. (??)[INDENT=2]
it is all a learning experience

[/INDENT]

---

