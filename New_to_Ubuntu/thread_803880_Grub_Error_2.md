---
title: "Grub Error 2"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by cotrean on 2008-05-22
I installed ubuntu 7.04 on a Dell 8200 Dimension running XP for a dual boot setup on one existing 160 GB IDE hard drive. I used "manual partition" in ubuntu install using the last 21 GB unformatted section of hard drive - approx 20 GB for /root on primary and 1 GB for swap

After install at first reboot I get this message:

Grub Loading stage1.5. 
GRUB loading, please wait 
Error 2

I have read similiar responses on this forum and did the following :
I booted into the live Ubuntu 7.04 install cd and from terminal ran these commands:

ubuntu@ubuntu:~$ sudo fdisk -l

## This is the output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3909    31399011    7  HPFS/NTFS
/dev/sda2            3910       16704   102775837+   f  W95 Ext'd (LBA)
/dev/sda3           16705       19332    21109410   83  Linux
/dev/sda4           19333       19457     1004062+  82  Linux swap / Solaris
/dev/sda5            3910        5214    10482381    7  HPFS/NTFS
/dev/sda6            5215        6519    10482381    7  HPFS/NTFS
/dev/sda7            6520        7824    10482381    7  HPFS/NTFS
/dev/sda8            7825       11740    31455238+   7  HPFS/NTFS
/dev/sda9           11741       15656    31455238+   7  HPFS/NTFS
/dev/sda10          15657       16704     8418028+   b  W95 FAT32

### I am puzzeled about the sda which I thought meant a scsi hard drive - my hd is ide
### Also in other posts I have seen there is an "*" in the boot column - I have none

ubuntu@ubuntu:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory

## menu.lst does exist and I can see it from live ubuntu cd using natalus and located file on sda3 and can open it with text editor but can not write to it. Below is the output: 


##################### partial menu.lst ########################
default		0
timeout		10

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8e940a6-339e-4e06-a54c-c71d2e1575a1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e8e940a6-339e-4e06-a54c-c71d2e1575a1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
##################### end menu.lst ########################

## ran these commands per another thread I read 

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,2)

grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

I can not figure out how to access that root partition from live cd in terminal to edit file. Tried this code:
gksudo gedit /boot/grub/menu.lst 
but it doesn't open existing file but opens new (blank) file.


I am not sure where to go from here. It seems like grub is installed but maybe the location of partitions is mixed up. Anyone have an idea what I can do to get grub to work? 

Thank you,

---

### Post by shifty_powers on 2008-05-22
try gksudo nautilus in a terminal of the live cd to navigate and be able to alter the grub menu on the root partition...

---

### Post by Baelus on 2008-05-22
I've used Super Grub Disk to muck about with the boot process (restore grub, break grub, wipe out mbr, fix mbr, etc.) It's dangerous, but with careful handling it can work magic.

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

The download links are on the right sidebar near the top.

It's been useful to me more than once.

- B

---

### Post by shifty_powers on 2008-05-22
yup, a very useful, but veyr powerful and dangerous tool ;)

---

### Post by cotrean on 2008-05-22
From terminal I ran this command:

gksudo nautilus
Initializing gnome-mount extension

## new window opened titled " / - File Browser" 
It appears to be the live cd contents - not the contents of sd3/boot that I can open in Places > Computer > 20.1 GB Volume > Boot  (which has grub)

Thanks,

---

### Post by shifty_powers on 2008-05-22
heh keep going up to the root folder, with everything in it, go to media and then the disk that you need, assuming it is mounted.

(this is iirc, as it is a while since i had to anything like this, guess I've been lucky ;)).

---

### Post by cotrean on 2008-05-22
Yes that worked - Now I have menu.lst open in gedit 

tile in window: menu.lst (/media/disk/boot/grub) - gedit

Now any ideas about what I might change?

Thanks,

---

### Post by meierfra. on 2008-05-22
Your menu.lst looks fine. So you don't need to edit it. Check out this thread (start at post 6)

[URL="http://ubuntuforums.org/showthread.php?t=151682"]http://ubuntuforums.org/showthread.php?t=151682
[/URL]

---

### Post by cotrean on 2008-05-22
Thank you Meierfra and Shifty_powers my problem is solved:

Followed link suggested and did what it suggested and all is working great:

Solution:
Went into your BIOS (F2) > Intetrated Devices > IDE Drive UDMA set to Off

Thanks so much... Bye
Cotrean

---

### Post by cotrean on 2008-05-22
Thank you Meierfra and Shifty_powers my problem is solved:

Followed link suggested and did what it suggested and all is working great:

Solution:
Went into your BIOS (F2) > Intetrated Devices > IDE Drive UDMA set to Off

Thanks so much... Bye
Cotrean

---

