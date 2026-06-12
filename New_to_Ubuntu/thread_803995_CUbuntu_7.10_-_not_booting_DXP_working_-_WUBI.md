---
title: "C:\Ubuntu 7.10 - not booting D:\XP working - WUBI?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by gmilne on 2008-05-22
So far as I'm aware I installed Ubuntu outside windows. I go to GRUB and then it hangs at **inittramfs**. XP works fine.

I want C:: and D: to be dedicated platform drives. E and F I use for Data


Here is the data I've been asked to collect so far:
My last information was that the first para underneath is a WUBI problem. I’ve never heard of WUBI can anyone help?

On pressing e during boot I get:

find-set-root-ignore-floppies /ubuntu/install/boot/vmlinuz
kernel/ubuntu/install/boot/vmlinuz Debian - installer/custom - installation=
initrd/ubuntu/install/boo witrd.gz boot
================================
My computer has 
E:\ partitioned drive on which only Ubuntu 7.01 is installed. 
F:\ Boot drive completely dedicated to XP
C:\ data storage + XP Programs
D:\data storage only.

(I've no idea why the letters are like this)

XP boots fine from Boot Manager.

On booting to Ubuntu computer hangs with message initramfs message.

Can anyone tell me what the next step is to solve this problem?

Mainboard : Asus A8N-SLI Premium
Chipset : nVidia nForce4
Processor : AMD Athlon 64 X2 3800+ @ 2000 MHz
Physical Memory : 4096 MB (4 x 1024 DDR-SDRAM )
Video Card : Nvidia Corp GeForce 7300 GS
Hard Disk : ST3400832AS (400 GB)
Hard Disk : ST3400832AS (400 GB)
Hard Disk : ST380815AS (80 GB)
Hard Disk : ST380815AS (80 GB)
Hard Disk : SEAGATE (250 GB) (external Lacie drive)
DVD-Rom Drive : HL-DT-ST DVD-RAM GSA-H55L
DVD-Rom Drive : HL-DT-ST DVDRAM GSA-4167B
Monitor Type : BenQ BenQ FP937s - 19 inches
Network Card : Marvell Semiconductor (Was: Galileo Technology Ltd) Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller (Copper)
Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 3
======================================================
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x1cf055b4 
Device Boot Start End Blocks Id System 
/dev/sda1 * 1 1824 14651248+ 83 Linux 
/dev/sda2 1825 3040 9767520 82 Linux swap / Solaris 
/dev/sda3 3041 9729 53729392+ 83 Linux 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdce1dce1 

Device Boot Start End Blocks Id System 
/dev/sdb1 1 9728 78140128+ 7 HPFS/NTFS 

Disk /dev/sdc: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8a618a61 
========================
Device Boot Start End Blocks Id System 
/dev/sdc1 * 1 48641 390708801 7 HPFS/NTFS 

Disk /dev/sdd: 400.0 GB, 400088457216 bytes 
255 heads, 63 sectors/track, 48641 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x93e093e0 

Device Boot Start End Blocks Id System 
/dev/sdd1 1 48641 390708801 7 HPFS/NTFS 

Disk /dev/sdf: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xcd8a96ce 

Device Boot Start End Blocks Id System 
/dev/sdf1 * 1 30401 244196001 c W95 FAT32 (LBA) 
ubuntu@ubuntu:~$

---

### Post by shifty_powers on 2008-05-22
in windows, do me a favour, go to control panel>administrative tools>disk management and provide a screen shot showing your disks and partitions?

---

### Post by gmilne on 2008-05-23
Thanks I've got the screenshot in TIFF format but don't know how to send it.
working on it
/g

---

### Post by gmilne on 2008-05-23
Here it is as BMP
Hope it helps

---

### Post by gmilne on 2008-05-23
here it is a jpeg

---

### Post by doctored on 2008-05-23
I had a similar problem. Mine was due to not having shut Windows down properly before rebooting into Ubuntu. Or you may have a 'device' still attached in Windows. So try re-starting windows, 'safely remove hardware' (if there is any) and then shut down Windows using the shut-down command. Then re-boot into Ubuntu and see what happens.

---

### Post by Living2007 on 2008-05-23
It seems that GRUB needs to be edited

When you are at GRUB, press 'E' when "ubuntu" is highlighted and then edit (hd) to (hd3,0)

This should work.

---

### Post by gmilne on 2008-05-23
e doesn't work at highlighted Ubuntu.

On entering the menu neither e, b, nor c work -so I can't even get a command line.

---

### Post by shifty_powers on 2008-05-23
well, you definitely do not have wubi installed, thats for sure...

---

### Post by gmilne on 2008-05-23
I still can't figure out what WUBI is? Can anyone tell me?
I have it but when I go to install it I get the message 'This will install Ubuntu 7.4'
I already have 7.1 installed should I remove it first?
thanks

---

### Post by shifty_powers on 2008-05-23
nope.

wubi is a little program, which is very handy, which will install ubuntu in such a way that the "partition" it creates for it is actually a file on your windows partiton.

this is all handled transparenty when you boot up into ubuntu, (you get a grub menu... it's like an easier veriosn of dual booting), so you just see the normal drive in ubuntu.

i asked for the disk management screenie, as it tells me that you have 3 partittions with file sysytems not recognised by windows. Windows cannot natively read/write to the xt3 filesystme that ubuntu uses by default.

so you have installed ubuntu as an actual dual boot...

---

### Post by Paqman on 2008-05-23
When you get to the boot list, what does it say at the top?

"Please select the operating systm to start"
Or:
"Grub Version xyz"

---

### Post by gmilne on 2008-05-23
It simpley says 
Windows XP (which is highlighted)
Ubuntu

---

### Post by Paqman on 2008-05-23
Are you sure that's the very top line? Neither Grub nor the Windows bootloader used by Wubi would have that as the very first line, IIRC.

---

### Post by gmilne on 2008-05-23
It says
Please select the operating system to start

Microsoft Windows XP Home Edition
Ubuntu

---

### Post by Paqman on 2008-05-23
Aha! If that's the case then you're looking at the Windows bootloader. You'd normally get that if you installed with Wubi.

Do you remember seeing a screen like this during installation:

[img]http://thedarkmaster.files.wordpress.com/2007/08/wubi-02.png[/img]

---

### Post by shifty_powers on 2008-05-23
if he used wubi, i'm intrigued what those three partitions in windows disk management are that have an unknown file system are...

---

### Post by Paqman on 2008-05-23
> **shifty_powers said:**
> if he used wubi, i'm intrigued what those three partitions in windows disk management are that have an unknown file system are...

It looks like they're a pretty standard root/swap/home setup, but why is the swap partition *9GB*? And why is he seeing the Windows bootloader instead of Grub? Some funny stuff going on...

---

### Post by gmilne on 2008-05-23
I partitioned that drive - allocated partition size off the top of my head.

I definitely didn't see the last screeen shot when I was installing Ubuntu. I saw it today though when I was thinking of installing WUBIsaw the last s

---

### Post by Living2007 on 2008-05-25
> **gmilne said:**
> e doesn't work at highlighted Ubuntu.

On entering the menu neither e, b, nor c work -so I can't even get a command line.
Try a WIRED Keyboard, you might be using a wireless keyboard

---

### Post by gmilne on 2008-05-25
Thanks to everyone who replied. I've decided to buy a new drive and do a fresh install.
gm

---

### Post by Living2007 on 2008-05-26
> **gmilne said:**
> Thanks to everyone who replied. I've decided to buy a new drive and do a fresh install.
gm
[QUOTE=Living2007]If all else fails, spend wisely[/QUOTE]
Good Choice

---

