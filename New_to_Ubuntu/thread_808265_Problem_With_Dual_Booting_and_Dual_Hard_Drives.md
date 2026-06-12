---
title: "Problem With Dual Booting and Dual Hard Drives"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by hitenshi on 2008-05-26
Hi, I recently tried to dual boot my computer to have Ubuntu and Windows XP, but for some reason, the GRUB boot loader never appears. All it ever does is boot directly into Windows. I've tried partitioning with the "Use Largest Continuous Free Space" as well as Manual partitioning, bot to no avail. 

As far as I can tell, nothing has changed save for a SATA hard drive I installed for extra storage. Is that what's causing the problem? 

The BIOS seems to be detecting my new hard drive, otherwise, the LiveCD wouldn't detect it. But I only see my 80GB IDE hard drive as Master in the BIOS. Also, in Windows XP, the only hard drive I can see is the 80GB IDE. I think that I might have to put a jumper into one of the hard drives, but I'm not entirely sure what that will do.

I'm really quite confused by this whole thing since it's the first time I've dealt with having two hard drives so any input will be quite helpful.

Your help is much appreciated. ^.^

---

### Post by bumanie on 2008-05-26
I have read of there being problems with mixed ide/sata drives, however some people do have them working together. The problem, from what you are saying seems to be with recognition of the sata drive as neither xp nor bios 'see' it. Have you formatted the drive and got a filesystem on it yet? A 'raw' drive will not show up in an OS, it needs to be formatted with a filesystem first. You can use xp to put ntfs on it or use gparted to put any of the filesystems it handles (which is most of them).
PS: Gparted will see the drive as 'unallocated.'

---

### Post by cdtech on 2008-05-26
Let's see what you get with:
sudo fdisk -l

You maybe need to install the GRUB bootloader onto the MBR of the primary drive:

sudo grub
grub>find /boot/grub/stage1
grub>root (hd0,whateverpartition)
grub>setup (hd0)
grub>exit

reboot...

---

### Post by hitenshi on 2008-05-26
I formatted the SATA hard drive as FAT32 using GParted so I know I definitely formatted it. And Ubuntu and the BIOS are able to detect it since I was able to format. But otherwise, I can't designate it as Master or Slave or anything.

@cdtech: Sorry to ask, but is that all through the Live CD?

Thanks. ^(^.^)^

---

### Post by cdtech on 2008-05-26
I did a double post, LOL!

sorry..

---

### Post by cdtech on 2008-05-26
WOW! you lost me. What exactly are you trying to redo now?

You say you've uninstalled Ubuntu?## never mind I see what you said now ##

If you've reformated the drive without a boot sector then BIOS will not see the drive as bootable, its just a storage drive. You would need to put an OS on the drive to make it bootable.

Hope this helps....

---

### Post by cdtech on 2008-05-26
> **hitenshi said:**
> I formatted the SATA hard drive as FAT32 using GParted so I know I definitely formatted it. And Ubuntu and the BIOS are able to detect it since I was able to format. But otherwise, I can't designate it as Master or Slave or anything.

@cdtech: Sorry to ask, but is that all through the Live CD?

Thanks. ^(^.^)^


Yes....

---

### Post by hitenshi on 2008-05-26
I think I'm starting to lose myself. >.<

To clarify I guess, I was running Ubuntu as my sole operating system before and I was able to format the SATA hard drive to use as storage. However, afterwards, when I installed Windows XP (wiping Ubuntu off my main IDE hard drive), I found that it could not detect the SATA hard drive. Also, when I attempted to install Ubuntu, the installation went through, but the GRUB boot loader was not installed so every time I turned the computer on, it would load directly into Windows. And that is where I'm stuck now.

Sorry, if I wasn't too clear.

---

### Post by cdtech on 2008-05-26
Thats ok, now we can install the bootloader if you would like?

let me see (from the live cd) what you get with sudo fdisk -l

and we can install it for you...

---

### Post by hitenshi on 2008-05-26
I got this from "sudo fdisk -l":

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071eb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001    b  W95 FAT32

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003990d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5005    40202631    7  HPFS/NTFS
/dev/sdb2            5006       10011    40210695    5  Extended
/dev/sdb5            5006        9800    38515806   83  Linux
/dev/sdb6            9801       10011     1694826   82  Linux swap / Solaris

```

What does it all mean? o.o

---

### Post by cdtech on 2008-05-26
OK

With the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd1,5) then you would enter root (hd1,5)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

P.S. It looks to me that you are booting into the secondary hard drive rather than the primary. Thats no big deal, but if your using sda as your storage device, I would change the pinout and use the other drive as your primary, we'll see once you get this working.

---

### Post by hitenshi on 2008-05-26
Hmm, what do you mean by change the pinout? The jumpers on the back of the hard drive?

Also, I tried following the commands, but it didn't work. :(
I might have messed up somewhere though...
1)sudo grub
2)find /boot/grub/stage1  -returned-> (hd1,4)
3)root (hd1,4)
4)setup (hd0) -returned-> a bunch of installation things and then "Done"
5)quit

That's what I input into the GRUB terminal. But was I supposed to do "setup (hd0)" in step 4? Or should it have been "(hd1,4)".

Sorry for all the trouble. T.T

---

### Post by cdtech on 2008-05-26
I thought that would happen with your setup, yes just use setup (hd1) instead... (not (hd1,4) just (hd1)

Sorry......

P.S. It's no trouble to help.

---

### Post by hitenshi on 2008-05-26
GRUB finally loaded! xD

But it's loaded to the GRUB terminal... so do I have to set up the boot table manually?

---

### Post by cdtech on 2008-05-26
What do you mean? Do you see the selections (ie. window, Ubuntu)?

Maybe we need to see the:
cat /boot/grub/menu.lst

I'm not sure what you see on boot.

---

### Post by hitenshi on 2008-05-26
I just see this:

```
grub> _
```

o.o Am I supposed to see the list?

---

### Post by cdtech on 2008-05-26
try typing "boot" at the prompt.

---

### Post by hitenshi on 2008-05-26
I received this error from typing in boot:

```
grub> boot
Starting up...

Error 8: Kernel must be loaded before booting
```

---

### Post by cdtech on 2008-05-26
> **hitenshi said:**
> I received this error from typing in boot:

```
grub> boot
Starting up...

Error 8: Kernel must be loaded before booting
```


No problem, you have the bootloader right, you just need to edit the /boot/grub/menu.lst to point to the kernel.

Can you show me the /boot/grub/menu.lst?

---

### Post by hitenshi on 2008-05-26
Hmm... I tried typing 

```
cat /boot/grub/menu.lst
```

in the prompt, but it said the file doesn't exist. -.-

---

### Post by cdtech on 2008-05-26
WOW!

Try this at the command prompt:
grub --config-file \(hd1,4\)/boot/grub/menu.lst

Wait, you need to be in a terminal and then type:
cat /boot/grub/menu.lst

---

### Post by hitenshi on 2008-05-26
I typed in what you said exactly:
```
grub --config-file \(hd1,4\)/boot/grub/menu.lst
```

It gave me:
```
Error 27: Unrecognized command
```

I also tried typing 
```
cat /boot/grub/menu.lst
``` in the terminal application on the LiveCD.

Also didn't work. T.T

---

### Post by cdtech on 2008-05-26
Do you see anything at bootup before the GRUB prompt?

If you do press the "esc key" quickly to edit the selection.

Highlite the Ubuntu selection and press the "e" key to edit, just put the /dev/sdb4 and change the "root=dev/hdb4" the root line to "root (hd1,4)
after you edit just hit the b key to boot.

---

### Post by hitenshi on 2008-05-26
Nothing appears. :(

It's just:
Loading GRUB 1.5 or something and then straight to:
```
grub> _
```

---

### Post by cdtech on 2008-05-26
Personaly, I would fix the disk order issue by swapping the plugs to give the storage drive as your secondary drive. This should be done anyway to save you the headaches later.

Then I would start with the GRUB again to reinstall to the primary drive. Did you ever have Ubuntu up and running at one time?

Once you have the drives straight (if you have nothing you need to save in the Ubuntu partition) I would reinstall Ubuntu and let the install disk create the bootloader for you.

It looks to me that during install you told GRUB to install to the primary drive which is your storage device (I see by the boot flag). You should have, at install, told it to install to the MBR of hd1 instead.

If you fix the order, you should be ok.

---

### Post by hitenshi on 2008-05-26
How would I swap the plugs? My IDE hard drive already has two plugs in the back of it, and I don't have any spares. -.-
Unless I can take out one of them?

My IDE hard drive has 9 pins in back and looks like this:

P: pin
L: plug (takes up two pins)
-: nothing

PLPPL
-LPPL

While my SATA hard drive has 4 pins and looks like this:

PP
PP

EDIT: I just realized that different companies have different jumper settings, so I'll try to figure it our on my own. Thanks for all the help you've given me cdtech. ^.^

---

### Post by cariboo on 2008-05-26
If you want to edit grub in a live install you'll have to use chroot eg:

```
chroot /mnt
```

The first step is to mount your hard drive:

```
mount /dev/hda /mnt
```

Then mount your drive using the first command:

This will put you in the chroot shell now you can edit things like you have bee trying to do.

I just went through this myself and it took an hour or two of reading before I discovered this, another thing to watch is to make sure you use the live CD that you installed with. I have have several CDs with different 32 and 64 bit distributions and a 32 bit live CD will not work on a 64 bit installation and vice versa.

Good Luck

Jim

---

### Post by jpkotta on 2008-05-26
Please have a look at [https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668](https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668)

---

