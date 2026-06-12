---
title: "[SOLVED] Update Ubuntu8.04 to 8.10"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by bj218 on 2008-11-17
I have a dual boot sys. With Ubuntu on 1HD and WinXP on another HD. I booted to Ubuntu 8.04 and went to Administration then to Software Sources then to updates tab and selected Normal 
Releases closed this window. Then I went to Aministration and I clked on UpdateMgr. and followed instructions for updating 8.04 to 8.10. this operation took about 2 hours. When I rebooted
the boot menu still shows  WinXP and Ubuntu 8.04 as the installed operating sys. How can I tell what version of Ubuntu is now inst.? Also I now get a message on bootup that says I am connected to a network?

---

### Post by cwsnyder on 2008-11-17
The message seems to indicate you are on Intrepid Ibex (8.10).

Grub will show whatever is on your /boot/grub/menu.lst file.  You will need to ```
sudo gedit /boot/grub/menu.lst
``` to edit the file (you can use nano or whatever your favorite text editor is).

---

### Post by markjensen on 2008-11-17
Well, it may just be a terminology issue in your grub's munu.lst file.   I don't think that any of the old kernels and packages are still around after an upgrade.

Open a terminal and post the results of this following command:
**uname -a**

If you are running the newer 8.10, and just need the text changed to say "8.10", or just "Ubuntu", you can edit the menu.lst file to make it say whatever you please:
**sudo gedit /boot/grub/menu.lst**

If you want to play it safe, make a backup of that currently working file by doing this beforehand:
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**

---

### Post by caljohnsmith on 2008-11-17
The only thing you might need to edit in your Grub menu is if you don't all ready have an entry for the new 2.6.27-7-generic kernel. If you don't, then first do:
```
gksudo gedit /boot/grub/menu.lst
```
And just copy one of your existing Ubuntu kernel entries, but change it to use the new kernel, similar to:
```
title		Ubuntu 8.10, kernel [COLOR="Blue"]2.6.27-7-generic[/COLOR]
(hd0,1)
kernel		/boot/[COLOR="Blue"]vmlinuz-2.6.27-7-generic[/COLOR] root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/[COLOR="Blue"]initrd.img-2.6.27-7-generic[/COLOR]
quiet

```
Of course use your (hdX,Y) and not the (hd0,1) above, and also keep your own UUID. Let me know how it goes. :)

---

### Post by markjensen on 2008-11-17
^^^  You also have a UUID entry in that code snippet.    That will not transfer over, either, and that entry will be non-bootable, if the Thread Starter puts that in his menu.lst

---

### Post by bj218 on 2008-11-18
Ubuntu 8.04 to 8.10  (11/17/08)
I think I made a big BOO  BOO in not telling all about my comp. Setup!! I have Ubuntu and Linux Mint on 1HD and WinXP on a second HD. The Linux Mint was formated as ROOT and is also a part
of the WinXP MBR. I really do not fully understand all this but it looks to me like I do have 
Ubuntu 8.10 installed!! Is there some way I can update the Mint grub to indicate the changes I have made to Ubuntu?  I think this would make the Boot Options Screen more meaning full? Also both 
hard drives are serial and Mint shows HD'S as /dev/sd and /dev/hd does this really mater.


The following is a copy of the lower part of the Ubuntu grub lst.
 
# End Default Options ## 
title		Ubuntu 8.10, kernel 2.6.27-7-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.24-19-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.24-19-generic 

title		Ubuntu 8.10, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 

# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title	Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 

title   Linux Mint, kernel 2.6.22-14-generic 
root  (hd2,0) 
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quit splash 
initrd /boot/initrd.img-2.6.22-14-generic 
boot 

title   Linux Mint, kernel 2.6.22-14-generic (recovery mode) 
root  (hd2,0) 
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single 
initrd /boot/initrd.img-2.6.22-14-generic 
boot 

title   Linux Mint, kernel memtest86+ 
root  (hd2,0) 
kernel /boot/memtest86+.bin 
boot

This is a copy of the lower part of the Mint GRUB lst.

 ## ## End Default Options ## 

title		Linux Mint, kernel 2.6.24-16-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5    This is where my data  is stored.
#title		Windows NT/2000/XP 
#root		(hd0,4) 
#savedefault 
#makeactive 
#chainloader	+1 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-19-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 
 

# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5   **This is where the backup of my data is stored**
# title		Windows NT/2000/XP 
# root		(hd1,4) 
# savedefault 
# makeactive 
# map		(hd0) (hd1) 
# map		(hd1) (hd0) 
# chainloader	+1

---

### Post by bj218 on 2008-11-19
> **markjensen said:**
> Well, it may just be a terminology issue in your grub's munu.lst file.   I don't think that any of the old kernels and packages are still around after an upgrade.

Open a terminal and post the results of this following command:
**uname -a**

If you are running the newer 8.10, and just need the text changed to say "8.10", or just "Ubuntu", you can edit the menu.lst file to make it say whatever you please:
**sudo gedit /boot/grub/menu.lst**

If you want to play it safe, make a backup of that currently working file by doing this beforehand:
**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**

I just ran this command (11/19) and it looks like 2.6.24-19 is Ubuntu 8.04
am I right? 
bill@bill-desktop:~$ uname -a
Linux bill-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
bill@bill-desktop:~$

---

### Post by caljohnsmith on 2008-11-19
OK, how about posting the output of:
```
sudo fdisk -lu
```
And please identify which is your Ubuntu and Mint partitions. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like and reveal whether Ubuntu or Mint is in charge of the booting process.

---

### Post by markjensen on 2008-11-20
> **bj218 said:**
> I just ran this command (11/19) and it looks like 2.6.24-19 is Ubuntu 8.04
am I right? 
bill@bill-desktop:~$ uname -a
Linux bill-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
bill@bill-desktop:~$

I agree.  I think you are on 8.04 still.   It looks like you didn't upgrade your Ubuntu.

---

### Post by caljohnsmith on 2008-11-20
> **markjensen said:**
> I agree.  I think you are on 8.04 still.   It looks like you didn't upgrade your Ubuntu.
Just because he booted into the older 2.6.24-19-generic kernel doesn't necessarily mean he's still using 8.04 I think, because that's all that "uname -a" tells you. It would be more accurate to run:
```
lsb_release -a
```
To find out his current Ubuntu version.

---

### Post by markjensen on 2008-11-20
I didn't know about the lsb release info.   But I am pretty sure that 8.10 never came with a 2.6.24 series kernel ;)

---

### Post by caljohnsmith on 2008-11-20
> **markjensen said:**
> I didn't know about the lsb release info.   But I am pretty sure that 8.10 never came with a 2.6.24 series kernel ;)
I agree, but I don't think the older kernel is uninstalled when you upgrade, so it would still be an option in his Grub menu; but I could be wrong since I never upgraded from Hardy to Intrepid--I decided to do a clean install of Intrepid. :)

---

### Post by bj218 on 2008-11-21
11/20/08

Re Ubuntu grub.lst in my response of 11/17/08 I note the following:
Ubuntu is (hd1,0)
Mint is     (hd2,0)     /dev/hda1
WinXP     (hd0,0)    /dev/sdb1

Re Mint grub.lst   (11/17/08)
Ubuntu is (hd1,0)    /dev/sdb1
Mint is     (hd1,3)    /dev/sdb4
WinXP is (hd0,0)   /dev/sda1

WinXP has been on 1 HD for several years.
Ubuntu 8.04 has been on the second HD for about 6months.
Mint has been on the second HD for about 2months.
When I installed and formated  Mint I made it root.


bill@bill-desktop:~$ sudo fdisk -lu

[sudo] password for bill: 



Disk /dev/sda: 100.0 GB, 100030242816 bytes

255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x0d4057a2



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   144167309    72083623+   7  HPFS/NTFS

/dev/sda3       144167310   195366464    25599577+   f  W95 Ext'd (LBA)

/dev/sda5       144167373   195366464    25599546    7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x761c12f3



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *          63    51199154    25599546    7  HPFS/NTFS

/dev/sdb2        51199155   312576704   130688775    f  W95 Ext'd (LBA)



Disk /dev/sdc: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x95dc719e



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *          63    48837599    24418768+  83  Linux

/dev/sdc2       102109140   153308294    25599577+   f  W95 Ext'd (LBA)

/dev/sdc3       100052820   102109139     1028160   82  Linux swap / Solaris

/dev/sdc4        48837600   100052819    25607610   83  Linux

/dev/sdc5       102109203   153308294    25599546    7  HPFS/NTFS



Partition table entries are not in disk order



bill@bill-desktop:~$ sudo dd if=/dev/sdb2 count=1 2>/dev/null | strings |grep -ie grub -ie

grep: option requires an argument -- 'e'

Usage: grep [OPTION]... PATTERN [FILE]...

Try `grep --help' for more information.

[sudo] password for bill: 

bill@bill-desktop:~$ sudo dd if=/dev/sdb2 bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk


bill@bill-desktop:~$ lsb_release -a

No LSB modules are available.

Distributor ID:	Ubuntu

Description:	Ubuntu 8.10

Release:	8.10

Codename:	intrepid

bill@bill-desktop:~$ 


I hope all this has some meaning to you!!

---

### Post by caljohnsmith on 2008-11-21
You didn't quite copy/paste the full commands, which is why you got those errors; please try again with these commands:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

---

### Post by bj218 on 2008-11-22
11/22/08

I know I don't know what I am doing. I think one of my problems is  I am unable to tell  what the ubuntu/mint drives are ie /dev/sd?

bill@bill-desktop:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

[sudo] password for bill: 

Missing operating system

bill@bill-desktop:~$ 

bill@bill-desktop:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

8103



bill@bill-desktop:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

Missing operating system

bill@bill-desktop:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

ff00



bill@bill-desktop:~$ sudo fdisk -l



Disk /dev/sda: 100.0 GB, 100030242816 bytes

255 heads, 63 sectors/track, 12161 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x0d4057a2



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        8974    72083623+   7  HPFS/NTFS

/dev/sda3            8975       12161    25599577+   f  W95 Ext'd (LBA)

/dev/sda5            8975       12161    25599546    7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x761c12f3



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS

/dev/sdb2            3188       19457   130688775    f  W95 Ext'd (LBA)



Disk /dev/sdc: 250.0 GB, 250059350016 bytes
 _THIS is THE HD WHERE UBUNTU/MINT RESIDE_.
255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x95dc719e



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *           1        3040    24418768+  83  Linux

/dev/sdc2            6357        9543    25599577+   f  W95 Ext'd (LBA)

/dev/sdc3            6229        6356     1028160   82  Linux swap / Solaris

/dev/sdc4            3041        6228    25607610   83  Linux

/dev/sdc5            6357        9543    25599546    7  HPFS/NTFS



Partition table entries are not in disk order

bill@bill-desktop:~$ sudo dd if=/dev/sdc4 count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

bill@bill-desktop:~$ sudo dd if=/dev/sdc4 bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

0000



bill@bill-desktop:~$ sudo dd if=/dev/sdc1 count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

bill@bill-desktop:~$ sudo dd if=/dev/sdc1 bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

0000



bill@bill-desktop:~$

---

### Post by caljohnsmith on 2008-11-22
Do you know which drive you are booting on start up? According to the "dd" commands you ran, you don't have Grub in the MBR (Master Boot Record) of either your sda drive or sdc drive. Also, it doesn't look like you have Grub installed to the boot sector of sdc1, so that would mean you can't be booting the sdc drive on start up the way you have it configured. Do you get a Grub menu on start up, or do you get a Windows XP boot menu that allows you to select Ubuntu? I assume it's the former, but I don't know which drive you are booting from; can you go into your BIOS and check your boot order to see which drive is being booted? 

How about when you get the Grub menu on start up, press "c" to get the grub command line, and then do:
```
grub> geometry (hd0)
```
How many partitions does that show, and what does it say the number of sectors are for the HDD? Next do:
```
grub> find /boot/grub/stage1
```
And let me know what that returns. We can work from there. :)

---

### Post by bj218 on 2008-11-23
11/23/08

The BIOS boot order is 1st Boot Device is 160GB(WinXP) the 2ndBD is 250GB(Ubuntu/Mint)
the 3rdBD is 100GB  (BU of Win and my Data)

I was told to do the following to put grub on Win MBR:

sudo grub
root (hd0,0)
setup (hda)

NOTE:Today I think setup probably should have been (sda) as it is a serial HD the only PATA HD on my sys. is the 100GB HD


This is fdisk on Mint

bill@bill-desktop ~ $ sudo fdisk -l 
[sudo] password for bill: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x761c12f3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS 
/dev/sda2            3188       19457   130688775    f  W95 Ext'd (LBA) 

Disk /dev/sdb: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x95dc719e 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        3040    24418768+  83  Linux 
/dev/sdb2            6357        9543    25599577+   f  W95 Ext'd (LBA) 
/dev/sdb3            6229        6356     1028160   82  Linux swap / Solaris 
/dev/sdb4            3041        6228    25607610   83  Linux 
/dev/sdb5            6357        9543    25599546    7  HPFS/NTFS 

Partition table entries are not in disk order 

Disk /dev/sdc: 100.0 GB, 100030242816 bytes 
255 heads, 63 sectors/track, 12161 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0d4057a2 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1        8974    72083623+   7  HPFS/NTFS 
/dev/sdc3            8975       12161    25599577+   f  W95 Ext'd (LBA) 
/dev/sdc5            8975       12161    25599546    7  HPFS/NTFS 
bill@bill-desktop ~ $ 


This is fdisk on Ubuntu

bill@bill-desktop:~$ sudo fdisk -l 
[sudo] password for bill: 
 
Disk /dev/sda: 100.0 GB, 100030242816 bytes 
255 heads, 63 sectors/track, 12161 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x0d4057a2 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        8974    72083623+   7  HPFS/NTFS 
/dev/sda3            8975       12161    25599577+   f  W95 Ext'd (LBA) 
/dev/sda5            8975       12161    25599546    7  HPFS/NTFS 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x761c12f3 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS 
/dev/sdb2            3188       19457   130688775    f  W95 Ext'd (LBA) 

Disk /dev/sdc: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x95dc719e 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1        3040    24418768+  83  Linux 
/dev/sdc2            6357        9543    25599577+   f  W95 Ext'd (LBA) 
/dev/sdc3            6229        6356     1028160   82  Linux swap / Solaris 
/dev/sdc4            3041        6228    25607610   83  Linux 
/dev/sdc5            6357        9543    25599546    7  HPFS/NTFS 

Partition table entries are not in disk order 
bill@bill-desktop:~$ 

NOTE: Mint says 100GB drive is sdc the 160GB drive is sda and the 250GB drive is sdb
        Ubuntu says 100GB drive is sda the 160 GB drive is sdb and the 250GB drive is sdc 
Does this mater?  Is there some way to make them same?

I think the bootup screen is grub.
I noticed the following at the bottom of the bootup screen &#8220;Boot Options root=/dev/sdb4 ro  quite splash&#8221;.

On startup I got nothing when I pressed &#8220;c&#8221;.
I ran the 2 commands in Mint and got the following:
bill@bill-desktop ~ $ grub geometry (hd0) 
bash: syntax error near unexpected token `('
 
bill@bill-desktop ~ $ grub find /boot/grub/stage1
GNU GRUB  version 0.97  (640K lower / 3072K upper memory) 

 [ Minimal BASH-like line editing is supported.  For the first word, TAB 
   lists possible command completions.  Anywhere else TAB lists the possible 
   completions of a device/filename. ]

I sure hope the above helps and that I have answered all your questions.

---

### Post by caljohnsmith on 2008-11-23
OK, it's more clear now. While you are in Mint (not Ubuntu), how about posting:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

```
If the first command returns "GRUB", then you have Grub installed to the MBR of your 160 GB Windows drive, and the second command should return either "8100" or "8103". I'm guessing it will return "8103" since it looks like Mint might be in charge of your booting process. Also, please post your Mint menu.lst.
[QUOTE=bj218]
NOTE: Mint says 100GB drive is sdc the 160GB drive is sda and the 250GB drive is sdb
Ubuntu says 100GB drive is sda the 160 GB drive is sdb and the 250GB drive is sdc
Does this mater? Is there some way to make them same?[/QUOTE]
I'm not sure why Mint and Ubuntu would see the order of your drives differently, but I don't think it should be a problem; there is no way of reordering them in /dev that I'm aware of--you have to go with what it gives you. :)

---

### Post by bj218 on 2008-11-23
11/23/08
I sure hope this helps. I think I did all the things asked for!!

bill@bill-desktop ~ $ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
[sudo] password for bill: 
GRUB 
bill@bill-desktop ~ $ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8103
bill@bill-desktop ~ $ 



## ## End Default Options ## 

title		Linux Mint, kernel 2.6.24-16-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda5 
#title		Windows NT/2000/XP 
#root		(hd0,4) 
#savedefault 
#makeactive 
#chainloader	+1 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-19-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-18-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 

 
# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-17-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb5 
# title		Windows NT/2000/XP 
# root		(hd1,4) 
# savedefault 
# makeactive 
# map		(hd0) (hd1) 
# map		(hd1) (hd0) 
# chainloader	+1 


This is the boot menu.

Linux Mint,kernel 2.6.24-16-generic
Linux Mint,kernel 2.6.24-16-generic (recovery mode)
Linux Mint,kernel memtest86+
Other operating systems
Microsoft Windows XP Professional
Ubuntu 8.04.1,kernel 2.6.24-19-generic (on /dev/sdb1)
Ubuntu 8.04.1,kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
Ubuntu 8.04.1,kernel 2.6.24-18-generic (on /dev/sdb1)

---

### Post by caljohnsmith on 2008-11-23
Great, that clears it up; your Mint is indeed in charge of Grub on start up. You could simply add a new entry in your Mint menu.lst for the new Intrepid kernel, but I think I would recommend recreating your Ubuntu's menu.lst to clean it up, and then linking to it in your Mint menu.lst. That way when you get new kernel updates, you will see the new kernel options on start up in the Grub menu without having to manually copy them over each time. So first boot into Ubuntu and post the output of the following comands:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub
```
When "update-grub" asks if you want to create a new menu.lst, say yes, and after it is done do:
```
gksudo gedit /boot/grub/menu.lst
```
And make sure the "groot" line is:
```
# groot=(hd1,0)
```
If groot does not use (hd1,0) and you have to change it, then run the "update-grub" command after you change it and save the menu.lst. Next boot into Mint and do:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
And then delete all your Ubuntu entries that come after your Windows XP entry, and replace them with:
```
title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
Reboot, and you should see the new "Ubuntu Grub Menu" choice in your Mint's Grub menu, and when you select it, you should see the new kernel 2.6.27-7-generic for Intrepid listed. Let me know how it goes or if you run into problems. :)

---

### Post by bj218 on 2008-11-26
11/26/08


bill@bill-desktop:~$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup 
[sudo] password for bill: 

bill@bill-desktop:~$ sudo update-grub 
Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.27-7-generic 
Found kernel: /boot/vmlinuz-2.6.24-19-generic 
Found kernel: /boot/memtest86+.bin 
Updating /boot/grub/menu.lst ... done 

bill@bill-desktop:~$ gksudo gedit /boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not use 'savedefault' or your 
# array will desync and will not let you boot your system. 
default		0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		5 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 

# Pretty colours 
#color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 

# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 

### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 

## DO NOT UNCOMMENT THEM, Just edit them to your needs 

## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro 

## default grub root device 
## e.g. groot=(hd1,0)                             WAS (hd0,0) 
# groot=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 

## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 

## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 

## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 

## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 

## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery) single 
# altoptions=(recovery mode) single 

## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=all 

## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 

## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 

## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 

## ## End Default Options ## 

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
uuid		4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
uuid		4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, kernel 2.6.24-19-generic 
uuid		4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode) 
uuid		4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro  single 
initrd		/boot/initrd.img-2.6.24-19-generic 

title		Ubuntu 8.10, memtest86+ 
uuid		4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST


bill@bill-desktop:~$ sudo update-grub 
[sudo] password for bill: 
Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.27-7-generic 
Found kernel: /boot/vmlinuz-2.6.24-19-generic 
Found kernel: /boot/memtest86+.bin 
Updating /boot/grub/menu.lst ... done 

bill@bill-desktop:~$ 

ALL OF THE ABOVE WAS DONE IN UBUNTU


ALL OF THE FOLLOWING WERE DONE in Mint

# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-legacy-doc/. 

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default		0 

gfxmenu=/etc/grub/message.elyssa 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout		15 

# Pretty colours 
color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
# control (menu entry editor and command-line)  and entries protected by the 
# command 'lock' 
# e.g. password topsecret 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
# password topsecret 

# 
# examples 
# 
# title		Windows 95/98/NT/2000 
# root		(hd0,0) 
# makeactive 
# chainloader	+1 
# 
# title		Linux 
# root		(hd0,1) 
# kernel	/vmlinuz root=/dev/hda2 ro 
# 

# 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 

### BEGIN AUTOMAGIC KERNELS LIST 
## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
## by the debian update-grub script except for the default options below 

## DO NOT UNCOMMENT THEM, Just edit them to your needs 

## ## Start Default Options ## 
## default kernel options 
## default kernel options for automagic boot options 
## If you want special options for specific kernels use kopt_x_y_z 
## where x.y.z is kernel version. Minor versions can be omitted. 
## e.g. kopt=root=/dev/hda1 ro 
##      kopt_2_6_8=root=/dev/hdc1 ro 
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=/dev/sdb4 ro 

## default grub root device 
## e.g. groot=(hd0,0)            IS THIS CORRECT?
# groot=(hd1,3) 

## should update-grub create alternative automagic boot options 
## e.g. alternative=true 
##      alternative=false 
# alternative=true 

## should update-grub lock alternative automagic boot options 
## e.g. lockalternative=true 
##      lockalternative=false 
# lockalternative=false 

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash 

## should update-grub lock old automagic boot options 
## e.g. lockold=false 
##      lockold=true 
# lockold=false 

## Xen hypervisor options to use with the default Xen boot option 
# xenhopt= 

## Xen Linux kernel options to use with the default Xen boot option 
# xenkopt=console=tty0 

## altoption boot targets option 
## multiple altoptions lines are allowed 
## e.g. altoptions=(extra menu suffix) extra boot options 
##      altoptions=(recovery mode) single 
# altoptions=(recovery mode) single 

## controls how many kernels should be put into the menu.lst 
## only counts the first occurence of a kernel, not the 
## alternative kernel options 
## e.g. howmany=all 
##      howmany=7 
# howmany=all 

## should update-grub create memtest86 boot option 
## e.g. memtest86=true 
##      memtest86=false 
# memtest86=true 

## should update-grub adjust the value of the default booted system 
## can be true or false 
# updatedefaultentry=false 

## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 

## ## End Default Options ## 

title		Linux Mint, kernel 2.6.24-16-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Microsoft Windows XP Professional 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 



# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sdb1. 
title		Linux Mint, kernel memtest86+ (on /dev/sdb1) 
root		(hd1,0) 
kernel		/boot/memtest86+.bin  
savedefault 
boot 

bill@bill-desktop ~ $ title Ubuntu Grub Menu 
bash: title: command not found 
bill@bill-desktop ~ $ configfile (hd1,0)/boot/grub/menu.lst 
bash: syntax error near unexpected token `hd1,0' 
bill@bill-desktop ~ $

Some Mints commands I think are different for Mint?

---

### Post by caljohnsmith on 2008-11-26
When you are in Mint, first open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then in the gedit application that pops up, add the following at the very end of the file:
```
title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
Then reboot, and let me know if you can boot into Ubuntu. It may be that since your Ubuntu entries use "uuid" rather than (hdX,Y) notation in Ubuntu's menu.lst, that might be a problem for Mint's Grub. But let me know how far you get and we'll work from there.

---

### Post by bj218 on 2008-11-26
11/26/08
The following is the result of the Mint command                                  &#8220;gksudo gedit /boot/grub/menu.lst&#8221;


# menu.lst - See: grub(8), info grub, update-grub(8)

#            grub-install(8), grub-floppy(8),

#            grub-md5-crypt, /usr/share/doc/grub

#            and /usr/share/doc/grub-legacy-doc/.



## default num

# Set the default entry to the entry number NUM. Numbering starts from 0, and

# the entry number 0 is the default if the command is not used.

#

# You can specify 'saved' instead of a number. In this case, the default entry

# is the entry saved with the command 'savedefault'.

# WARNING: If you are using dmraid do not change this entry to 'saved' or your

# array will desync and will not let you boot your system.

default		0



gfxmenu=/etc/grub/message.elyssa



## timeout sec

# Set a timeout, in SEC seconds, before automatically booting the default entry

# (normally the first entry defined).

timeout		15



# Pretty colours

color cyan/blue white/blue



## password ['--md5'] passwd

# If used in the first section of a menu file, disable all interactive editing

# control (menu entry editor and command-line)  and entries protected by the

# command 'lock'

# e.g. password topsecret

#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/

# password topsecret



#

# examples

#

# title		Windows 95/98/NT/2000

# root		(hd0,0)

# makeactive

# chainloader	+1

#

# title		Linux

# root		(hd0,1)

# kernel	/vmlinuz root=/dev/hda2 ro

#



#

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST



### BEGIN AUTOMAGIC KERNELS LIST

## lines between the AUTOMAGIC KERNELS LIST markers will be modified

## by the debian update-grub script except for the default options below



## DO NOT UNCOMMENT THEM, Just edit them to your needs



## ## Start Default Options ##

## default kernel options

## default kernel options for automagic boot options

## If you want special options for specific kernels use kopt_x_y_z

## where x.y.z is kernel version. Minor versions can be omitted.

## e.g. kopt=root=/dev/hda1 ro

##      kopt_2_6_8=root=/dev/hdc1 ro

##      kopt_2_6_8_2_686=root=/dev/hdc2 ro

# kopt=root=/dev/sdb4 ro



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd1,3)



## should update-grub create alternative automagic boot options

## e.g. alternative=true

##      alternative=false

# alternative=true



## should update-grub lock alternative automagic boot options

## e.g. lockalternative=true

##      lockalternative=false

# lockalternative=false



## additional options to use with the default boot option, but not with the

## alternatives

## e.g. defoptions=vga=791 resume=/dev/hda5

# defoptions=quiet splash



## should update-grub lock old automagic boot options

## e.g. lockold=false

##      lockold=true

# lockold=false



## Xen hypervisor options to use with the default Xen boot option

# xenhopt=



## Xen Linux kernel options to use with the default Xen boot option

# xenkopt=console=tty0



## altoption boot targets option

## multiple altoptions lines are allowed

## e.g. altoptions=(extra menu suffix) extra boot options

##      altoptions=(recovery mode) single

# altoptions=(recovery mode) single



## controls how many kernels should be put into the menu.lst

## only counts the first occurence of a kernel, not the

## alternative kernel options

## e.g. howmany=all

##      howmany=7

# howmany=all



## should update-grub create memtest86 boot option

## e.g. memtest86=true

##      memtest86=false

# memtest86=true



## should update-grub adjust the value of the default booted system

## can be true or false

# updatedefaultentry=false



## should update-grub add savedefault to the default options

## can be true or false

# savedefault=false



## ## End Default Options ##



title		Linux Mint, kernel 2.6.24-16-generic

root		(hd1,3)

kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash

initrd		/boot/initrd.img-2.6.24-16-generic



title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)

root		(hd1,3)

kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single

initrd		/boot/initrd.img-2.6.24-16-generic



title		Linux Mint, kernel memtest86+

root		(hd1,3)

kernel		/boot/memtest86+.bin



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Microsoft Windows XP Professional

root		(hd0,0)

savedefault

makeactive

chainloader	+1







# This entry automatically added by the Debian installer for an existing

# linux installation on /dev/sdb1.

title		Linux Mint, kernel memtest86+ (on /dev/sdb1)

root		(hd1,0)

kernel		/boot/memtest86+.bin  

savedefault

boot



title Ubuntu Grub Menu

configfile (hd1,0)/boot/grub/menu.lst


When I reboot I get the following.

The boot screen has 3 Mint and 1 WinXP entries + the following &#8220;Ubuntu Grub Menu&#8221; press any
key to continue. When I press a key I get a blue screen that shows the following:
Ubuntu 8.10,kernel 2.6.27-7 generic

Ubuntu 8.10,kernel 2.6.27-7 generic+ (recovery mode)
Ubuntu 8.10,kernel 2.6.27-7 memtest
IF I highlite and press enter on any of these I get &#8220;error 15&#8221;

---

### Post by caljohnsmith on 2008-11-26
OK, when you select "Ubuntu Grub Menu" on start up, after that select "Ubuntu 8.10,kernel 2.6.27-7 generic", press "e" to edit it, select the line that says "uuid 4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac", press "e" to edit it, change it to "root (hd1,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac" to instead be:
```
# groot=(hd1,0)
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by bj218 on 2008-11-27
> **caljohnsmith said:**
> OK, when you select "Ubuntu Grub Menu" on start up, after that select "Ubuntu 8.10,kernel 2.6.27-7 generic", press "e" to edit it, select the line that says "uuid 4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac", press "e" to edit it, change it to "root (hd1,0)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac" to instead be:
```
# groot=(hd1,0)
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

I did all of the above but when I pressed “b” I got the following:
Booting command-list
kernel  /boot/vmlinuz-2.6.27-7 generic root=(hd1,0)
Error 15:file not found
Press any to continue

I did all of the above twice once as “root (hd1,0) the second time as root=(hd1,0)” and each time I got the same result.
Is there any way I can look at the Ubuntu grub list now?
Can I use the Ubuntu 8.10 CD or something else.

---

### Post by caljohnsmith on 2008-11-27
OK, while you are in Mint try the following:
```
sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all the Ubuntu entries to use "root (hd1,0)" similar to:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]root (hd1,0)[/COLOR]
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=4772fcc0-4a9d-4634-a65f-d7ba9a3d88ac ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet 
```
So don't change the uuid in the kernel line. Reboot and let me know how far you get.

---

### Post by bj218 on 2008-11-28
This morning (11/28/08)  I installed some updates which changed Ubuntu to 2.6.27-9!
I made the changes you suggested yesterday. Will the change I made today cause any  prob.?
When I boot up (yesterday or today) the bootup screen shows 3 Mint+1 WinXP and Ubuntu  Grub Menu. When I press ENTER on the &#8220;Ubuntu GRUB Menu&#8221;I get a screen with some text then it boots into Ubuntu. Is there some way to get the 3 Ubuntu choices to show on the first boot screen? Another question there is and update for Mint if install it will this create a problem? One more ?
how can I put the Mint grub in the WinXP MBR?

---

### Post by caljohnsmith on 2008-12-11
> **bj218 said:**
> This morning (11/28/08)  I installed some updates which changed Ubuntu to 2.6.27-9!
I made the changes you suggested yesterday. Will the change I made today cause any  prob.?
When I boot up (yesterday or today) the bootup screen shows 3 Mint+1 WinXP and Ubuntu  Grub Menu. When I press ENTER on the “Ubuntu GRUB Menu”I get a screen with some text then it boots into Ubuntu. Is there some way to get the 3 Ubuntu choices to show on the first boot screen? Another question there is and update for Mint if install it will this create a problem? One more ?
Having the new kernel installed won't cause any problems the way you have it right now, because the Ubuntu menu.lst gets automatically updated after you install a new kernel (as long as you let it do so). But if want your Ubuntu entries to show up in the first Grub menu, you would have to copy over the Ubuntu Grub entries by hand from Ubuntu's menu.lst into your Mint's menu.lst. The disadvantage of that is when you get a new kernel update again, you will have to manually add it to your Mint menu.lst. 
> **bj218 said:**
> how can I put the Mint grub in the WinXP MBR?
Windows does not currently have its boot code in your MBR, so I don't think I understand your question. What are you trying to do?

---

### Post by bj218 on 2008-12-11
Having the new kernel installed won't cause any problems the way you have it right now, because the Ubuntu menu.lst gets automatically updated after you install a new kernel (as long as you let it do so). But if want your Ubuntu entries to show up in the first Grub menu, you would have to copy over the Ubuntu Grub entries by hand from Ubuntu's menu.lst into your Mint's menu.lst. The disadvantage of that is when you get a new kernel update again, you will have to manually add it to your Mint menu.lst. 
Quote:
Originally Posted by bj218 
how can I put the Mint grub in the WinXP MBR?
Windows does not currently have its boot code in your MBR, so I don't think I understand your question. What are you trying to do?

At one time I was told if I put the boot grub.lst in the Win MBR then if I updated the Linux OS it would  be updated in the MBR. I gather this is not the so?

Below is the last part of the Mint grub.lst that I ran a few minutes ago. What do the last two lines mean 

title		Linux Mint, kernel 2.6.24-16-generic 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode) 
root		(hd1,3) 
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb4 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic 

title		Linux Mint, kernel memtest86+ 
root		(hd1,3) 
kernel		/boot/memtest86+.bin 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Microsoft Windows XP Professional

root		(hd0,0)

savedefault

makeactive

chainloader	+1







# This entry automatically added by the Debian installer for an existing

# linux installation on /dev/sdb1.

title		Linux Mint, kernel memtest86+ (on /dev/sdb1)

root		(hd1,0)

kernel		/boot/memtest86+.bin  

savedefault

boot



title Ubuntu Grub Menu

configfile (hd1,0)/boot/grub/menu.lst
The words&#8221;Ubuntu Grub Menu&#8221; show up on the first boot screen!

---

### Post by caljohnsmith on 2008-12-11
The "Ubuntu Grub Menu" entry that shows up on your Grub menu on start up is because the Ubuntu menu.lst is linked to your Mint menu.lst with the last two lines in your Mint menu.lst:
```
title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
So when you select "Ubuntu Grub Menu" from the Grub menu on start up, it simply loads the Ubuntu menu.lst. Like I all ready mentioned, if you don't like that, you would have to manually copy over the Ubuntu entries in the Ubuntu menu.lst over to your Mint menu.lst.

---

### Post by bj218 on 2008-12-12
Thanks for all the help. I think I will stay with what I have now. If I ever have to use the Ubuntu Rescue mode How doI get to it?

---

### Post by caljohnsmith on 2008-12-12
> **bj218 said:**
> Thanks for all the help. I think I will stay with what I have now. If I ever have to use the Ubuntu Rescue mode How doI get to it?
If you mean "recovery mode", then you can just select it from the Grub menu you all ready have; in the Ubuntu menu.lst you showed in your first post, one of the selections is "Ubuntu 8.10, kernel 2.6.27-7-generic [COLOR="Blue"](recovery mode)[/COLOR]". Selecting that from the Grub menu would take you to the recovery mode.

---

### Post by bj218 on 2008-12-13
After  reading your last response  I rebooted and on the first boot screen I highlited
&#8221;Ubuntu Grub Menu&#8221; & pressed Enter on the next screen  one of the items there said
 to press &#8220;ESC&#8221; to access the Grub Menu after pressing ESC I got a new window that 
showed the three grub choices. Thanks again  every thing is working great.

---

