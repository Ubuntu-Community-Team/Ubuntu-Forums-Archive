---
title: "[SOLVED] Set up SWAP partition after installation"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by reg4c on 2008-10-31
Hello, 

I installed Ibex a while back and I did not set up a SWAP partition thinking that it would not be necessary but now I want to try and see whether there would be any preformance improvement.

So, I want to know whether there is a way to make a swap partition now? Perhaps Gparted?

Cheers

---

### Post by Sealbhach on 2008-10-31
Hi, put this in the terminal and paste the result here.
```

sudo fdisk -l
```


.

---

### Post by reg4c on 2008-11-01
Here you go:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0454f7b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       19034    69492736+   f  W95 Ext'd (LBA)
/dev/sda4           19034       19458     3398656   17  Hidden HPFS/NTFS
/dev/sda5           10383       19034    69492736   83  Linux

```

---

### Post by Nepherte on 2008-11-01
Create a swap partition in gparted and add a line in /etc/fstab:
```
# Entry for swap partition (sda3)
UUID=d25b9438-0c78-4159-9b74-aa8d441e7fab swap swap defaults 0 0
```
replace the uuid value with the one corresponding to your swap partition.

---

### Post by Sealbhach on 2008-11-01
So all your Ibex is on sda5?

I don't think you'll be able to change an active partition. You will probably have to use the Live CD or use Windows to resize the partition. There's a danger of losing all your data though so back up everything you want to keep.

You can probably resize sda5 and use the freed space as swap.

If it were me though, I would go for a complete re-install and set up three partitions, one for root (/), one for /home and a small swap partition. This scheme will make things much easier if you want to upgrade or if you have to reinstall.


.

---

### Post by reg4c on 2008-11-01
Yes, for now everything is on one disk. I am reluctant to format the Win partiton since I don't want to lose it and I may mess up the thing for recovery: thats the Compaq thing I think.

If I do go for a complete reinstall then how big should I make the root, home and swap? The swap is 2xRAM right? And as for the other two?

Ow, and is there a script perhaps that would list out all the currently installed packages so that when I reinstall I can download all the packages again?

Cheers

---

### Post by Sealbhach on 2008-11-01
Hi,

Typically, root should be about 12GB, defintely no less than 8GB.

Swap, well I use 2GB, some people only use 1GB or even less. The /home partition can be as big as you wish, the bigger the better really as that is where you store all you documents, music, videos, pictures etc.

If you run 

sudo dpkg -l

and copy it into a text file, you can use it to remind yourself of what you had installed.

.

---

### Post by reg4c on 2008-11-01
12GB, 2GB, the rest, alright I got it.

I will reinstall as soon as I find a way to get a list of all the apps that I've installed.

sudo dpkg -l | grep i -c

showed that there are 1885 packages, so thanks but I dont think that that could work.
Thanks to all.

[SOLVED]

---

### Post by Sealbhach on 2008-11-01
There is a way to look at differences, I just tried an example for myself.

First I did this:

```
sudo dpkg -l > list1
```

Then removed the application Cheese.

Then did:

```
sudo dpkg -l > list2
```

Then to compare them:

```
diff list1 list2 > ~/Desktop/diff
```

Gave me the difference (see attached).



.

---

### Post by reg4c on 2008-11-01
Ahuh
So, what you mean is that I should list the packages before and after, and then compare the two and the difference would be the things that were installed but are not installed now.

Ahhh
Alright, lemme try
Cheers

---

### Post by reg4c on 2008-11-01
Ahuh
So, what you mean is that I should list the packages before and after, and then compare the two and the difference would be the things that were installed but are not installed now.

Ahhh
Alright, lemme try
Cheers

---

### Post by reg4c on 2008-11-01
Hey, Sealbhach

is there are way to echo different things in a single line...
Because every time that I call "echo BLABLA >> " things are written in a new line...

Cheers

EDIT: Nevermind: ```
man echo
```

---

