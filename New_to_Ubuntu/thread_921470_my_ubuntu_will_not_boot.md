---
title: "my ubuntu will not boot"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by seyiisq on 2008-09-16
I dual booted my hard drive using wwindow xp and ubuntu. on saturday i adjusted my partitioning but not where ubuntu resides. 
Now, my i wouldn't even have dual boot option page talkless of booting ubuntu.

pls can someone help

---

### Post by knattlhuber on 2008-09-16
So what do you get when you start your computer? Does it boot into Windows or does it not boot at all?

---

### Post by seyiisq on 2008-09-16
it boot straight into windows

---

### Post by tangibleorange on 2008-09-16
> **seyiisq said:**
> it boot straight into windows

looks like Windows has stolen the MBR! you need GRUB there if you want a dual-boot. follow the instructions here to re-install GRUB to the MBR:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

good luck!

---

### Post by phidia on 2008-09-16
I think you need to setup grub again. Maybe the [super grub disk]("http://www.supergrubdisk.org/") will help.

---

### Post by knattlhuber on 2008-09-16
**EDIT: Please ignore this post and follow the instructions from the other two posters. (No point in looking at menu.lst if GRUB is gone...)**

OK, that's good. I was worried that your whole disk is messed up.

Can you start Ubuntu from the Live CD and do

```
sudo fdisk -l

```
There should be a partition that has Linux on it (hopefully). Take a note of the first couple of characters in that line (should read /dev/sd..)
If you don't see a Linux partition in the output of above command, please stop here and post the output of the fdisk command.

If you see your Linux partition in above list, please create a mountpoint for your Ubuntu/Linux partition and mount it

```
sudo mkdir /media/ubuntu
sudo mount /dev/sd.. /media/ubuntu
```

where /dev/sd.. is the device name of the Linux partition that you got from the fdisk command.

Now run

```
cat /media/ubuntu/boot/grub/menu.lst
```

and post the output here.

---

### Post by seyiisq on 2008-09-16
After following the above setup i had the following error

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

---

### Post by caljohnsmith on 2008-09-16
> **seyiisq said:**
> After following the above setup i had the following error

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested
When you get that Grub after trying to install Grub to the MBR, it is often because your HDD's partition table is corrupted; that would be a strong possibility considering that you repartitioned your HDD. If you have internet access from your Ubuntu Live CD, I would recommend checking your partition table with testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by seyiisq on 2008-09-16
below is the error i found

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$

---

### Post by seyiisq on 2008-09-16
sorry i was able to get the installation done eventually the result is as bellow

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 159 GB / 149 GiB - CHS 19452 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Dell Utility             0   1  1     5 254 63      96327
 2 * HPFS - NTFS              6   0  1 14080 254 63  226114875
 3 E extended             14081   0  1 19059 254 63   79987635
 4 P CP/M                 19060   0  1 19451 254 63    6297480
   X extended             14081   0  2 18849 254 63   76613984
 5 L Linux                14081   2  1 18849 254 63   76613859
   X extended             18850   0  1 19059 254 63    3373650
test_FAT : Boot sector doesn't have the endmark 0xAA55
 6 L FAT16 LBA            18850   1  1 19059 254 63    3373587
 6 L FAT16 LBA            18850   1  1 19059 254 63    3373587




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

---

### Post by seyiisq on 2008-09-16
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 159 GB / 149 GiB - CHS 19452 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     5 254 63      96327 [DellUtility]
P HPFS - NTFS              6   0  1 14080 254 63  226114875
L Linux                14081   1  1 18849 254 63   76613922
L Linux Swap           18850   1  1 19059 254 63    3373587
P FAT32 LBA            19060   0  1 19451 254 63    6297480 [DellRestore]








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 49 MB / 47 MiB

---

### Post by caljohnsmith on 2008-09-16
OK, please also post the following:
```
sudo fdisk -l

```
And also do:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt/boot/grub
cat /mnt/boot/grub/menu.lst

```
And please post the results.

---

### Post by seyiisq on 2008-09-16
pls can someone help

---

### Post by seyiisq on 2008-09-16
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14081   113057437+   7  HPFS/NTFS
/dev/sda3           14082       19060    39993817+   5  Extended
/dev/sda4           19061       19452     3148740   db  CP/M / CTOS / ...
/dev/sda5           14082       18850    38306929+  83  Linux
/dev/sda6           18851       19060     1686793+   e  W95 FAT16 (LBA)

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/ubuntu
ubuntu@ubuntu:~$ cat /media/ubuntu/boot/grub/menu.lst
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef63a212-c00b-4300-877e-3b2f4d40e891 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-16
OK, it looks like your partition table might be just fine. Please do the following from the Live CD:
```
sudo blkid
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands, then reboot, and tell us exactly what happens on start up (including any errors).

---

### Post by seyiisq on 2008-09-16
Below is the result of the above

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0214" TYPE="vfat" 
/dev/sda2: UUID="B6A4508FA45053C9" TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="ef63a212-c00b-4300-877e-3b2f4d40e891" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="23144f04-2ed6-40b5-b2ea-285e36947d17" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

---

### Post by caljohnsmith on 2008-09-16
> **seyiisq said:**
> 
grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition
Are you sure you used "sudo grub" and not just "grub"? If so, then please do:
```
sudo fsck /dev/sda5

```
If it asks to correct errors, say "y". Let me know the output.

---

### Post by seyiisq on 2008-09-16
yes i uesd sudo grub, below is the output of the command above

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda5: clean, 158964/2400256 files, 2412680/9576732 blocks (check in 5 mounts)
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-16
I think the problem might be that your Ubuntu partition starts at about 115 GB and goes to about 155 GB; some older BIOSes have a limitation where they can't see anything beyond 137 GB. Can you shrink down your first Dell Utility partition (sda1) at its end by only about 10-20 MB, and create a ~10 MB primary partition after it? If you can do that, you could have a dedicated Grub partition, and then you definitely wouldn't have to worry about BIOS limitations; I can't be sure a BIOS limitation is your problem, but if you do the dedicated Grub partition correctly it shouldn't hurt anything, only help.

---

### Post by seyiisq on 2008-09-16
it was working fine before, this problem started recently

---

### Post by caljohnsmith on 2008-09-16
I'm surprised that the Grub commands you did before returned that error 17. Something seems really screwy with your system if it was working before. Try the following and let me know what the result is:
```
sudo grub
grub> cat (hd0,4)/boot/grub/menu.lst
```
Does that show your menu.lst?

---

### Post by meierfra. on 2008-09-16
caljohnsmith:  you seemed to have overlooked this in post 14:

> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)


So the partition table needs to be rewritten with testdisk.

---

### Post by seyiisq on 2008-09-16
I am a bit confuse here. i am new to all this. This is still returning error


grub>  cat (hd0,4)/boot/grub/menu.lst

Error 17: Cannot mount selected partition

---

### Post by seyiisq on 2008-09-16
> **meierfra. said:**
> caljohnsmith:  you seemed to have overlooked this in post 14:



So the partition table needs to be rewritten with testdisk.

pls how do i get this done

---

### Post by meierfra. on 2008-09-16
Use testdisk as before until you get to the screen from post 11. Press enter  to "continue". Then select "write" and press enter.

You also need to edit "menu.lst":

Assuming that /dev/sda5 is still mounted:

```
gksudo gedit /mnt/boot/grub/menu.lst
```

Change all "root (hd0,5)" to "root (hd0,4)"

also change "#groot (hd0,5)" to "#groot (hd0,4)".

Save the file.

Finally

```

sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```

If the last step fails, reboot the LiveCD and try  the last step again.

---

### Post by caljohnsmith on 2008-09-16
> **meierfra. said:**
> caljohnsmith:  you seemed to have overlooked this in post 14:
> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5) 

So the partition table needs to be rewritten with testdisk.
Thanks for pointing that out; I knew I must have been missing something, because all the signs seemed to point to a problem with his partition table. But why didn't testdisk report any errors?

---

### Post by seyiisq on 2008-09-17
i tried mounting but i had the error below, pls i need help

ubuntu@ubuntu:~$  sudo mount /dev/sda5 /media/ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by caljohnsmith on 2008-09-17
Have you first done this:
[QUOTE=meierfra.]Use testdisk as before until you get to the screen from post 11. Press enter to "continue". Then select "write" and press enter.[/QUOTE]

---

### Post by seyiisq on 2008-09-17
yes i have

---

### Post by caljohnsmith on 2008-09-17
First do:
```
sudo dumpe2fs /dev/sda5 | grep -i "block size"
```
And notice what the block size is, most likely 4096 or 4K. Then do:
```
sudo dumpe2fs /dev/sda5 | grep superblock
```
And it will print out a list of your backup superblocks. Try the first one, probably 32768, and use that below:
```
sudo mount -o sb=$[[COLOR="Blue"]4*32768[/COLOR]] /dev/sda5 /mnt
```
So the 4 is your block size in kilobytes, and the 32768 is the superblock location. Try different superblock locations until you find one where the above mount command does not return an error.

Once you know which superblock works, just do:
```

sudo umount /dev/sda5
sudo e2fsck -b [COLOR="Blue"]32768[/COLOR] /dev/sda5
```
Replace 32768 with the good superblock you found previously. Now you should be able to remount your sda5 partition with simply:
```
sudo mount /dev/sda5 /mnt
```

---

### Post by meierfra. on 2008-09-17
I suggest rebooting  before following caljohnsmith's advice.  (Changing the partition table only becomes effective after a reboot)

---

### Post by seyiisq on 2008-09-17
As shown below i tried all the option but none seems to work

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda5 | grep superblock
dumpe2fs 1.40.8 (13-Mar-2008)
  Primary superblock at 0, Group descriptors at 1-3
  Backup superblock at 32768, Group descriptors at 32769-32771
  Backup superblock at 98304, Group descriptors at 98305-98307
  Backup superblock at 163840, Group descriptors at 163841-163843
  Backup superblock at 229376, Group descriptors at 229377-229379
  Backup superblock at 294912, Group descriptors at 294913-294915
  Backup superblock at 819200, Group descriptors at 819201-819203
  Backup superblock at 884736, Group descriptors at 884737-884739
  Backup superblock at 1605632, Group descriptors at 1605633-1605635
  Backup superblock at 2654208, Group descriptors at 2654209-2654211
  Backup superblock at 4096000, Group descriptors at 4096001-4096003
  Backup superblock at 7962624, Group descriptors at 7962625-7962627
ubuntu@ubuntu:~$ sudo mount -o sb=$[4*32768] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*98304] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*163840] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*229376] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*294912] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*819200] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*884736] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*1605632] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*2654208] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*4096000] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4*7962624] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -o sb=$[4.096*32768] /dev/sda5 /mnt
bash: 4.096*32768: syntax error: invalid arithmetic operator (error token is ".096*32768")
ubuntu@ubuntu:~$ sudo mount -o sb=$[4*32768] /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by meierfra. on 2008-09-17
Did you reboot?  Post "sudo fdisk -l " again.

---

### Post by seyiisq on 2008-09-17
yes i did reboot. 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14081   113057437+   7  HPFS/NTFS
/dev/sda3           14082       19060    39993817+   f  W95 Ext'd (LBA)
/dev/sda4           19061       19452     3148740    c  W95 FAT32 (LBA)
/dev/sda5           14082       18850    38306961   83  Linux
/dev/sda6           18851       19060     1686793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by meierfra. on 2008-09-17
It seems that testdisk fixed the "empty partition" problem, but introduced new problems. If you compare the two "fdisk" outputs, you will notice two changes:

1)  sda6 used to be a Fat16 partition, but now is a swap partition

2)  the length of sda5 (your ubuntu partition) has changed from
38306929  to 38306961


I assume that 2) is the reason you cannot mount your Ubuntu partition.
I'm not sure how to fix it, but I suggest to try the following:

Use testdisk as before, but instead of selecting  "write" choose "search". testdisk will then  do a thorough search for partitions on your hard drive.(that may take a while). Once the search is done, you can choose which of partition you want to appear in the partition table. (Select a partition and use the left arrrow key to choose between "D" for delete, "L" for logical, "*" for boot and "P" for primary) Choose exactly those which appear on your fdisk output from post #14. (sda1 and sda4 need to be "P",  sda2 needs to be "*" and sda5 and sda6 need to be "L". The extended partition (sda3) will not appear be on the testdisk  list, testdisk will create the extended partition automatically

Use "write" to rewrite the partition table and hope for the best.

---

### Post by seyiisq on 2008-09-18
it is still not working after trying your above instruction. do you advice that i install ubuntu again. I just got another disk should i install ubuntu on this new disk and leave windows on the other or re-install ubuntu on the same partition and leave the new disk as a storage

---

### Post by Keen101 on 2008-09-18
You should not have to re-install ubuntu. (all though you could i guess)

I recommend trying the SUPER GRUB DISK first. I have used it twice in the past to restore the GRUB boot loader. Just download the latest .iso file, and burn to a cd.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If you do decide to re-install ubuntu i recommend the GPARTED LIVE-CD to delete the Linux partitions, and then using your ubuntu to install on "largest free space" option. Otherwise you will have to do that in Ubuntu live-cd, which i find a pain.

---

### Post by meierfra. on 2008-09-18
If you do not have any valuable data on your ubuntu partition, reinstalling ubuntu is probably the fastest solutions at this stage. 
Whether your reinstall ubuntu onto the old or the new disk, should not  really matter. (But it could be that the LiveCD has problems detecting the partitions on you old disk, since the partitions table still seems to be messed up)

Personally, I would keep trying to fix the system. One just learns more that way. Also I never have seen testdisk  cause problem before, so  I would like to figure out what is going on.

Could you post "sudo fdisk -l" again, so that I can see whether anything has changed?

---

### Post by seyiisq on 2008-09-18
Thanks for your comment,

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14081   113057437+   7  HPFS/NTFS
/dev/sda3           14082       19060    39993817+   f  W95 Ext'd (LBA)
/dev/sda4           19061       19452     3148740    c  W95 FAT32 (LBA)
/dev/sda5           17528       18520     7976241   83  Linux
/dev/sda6           18851       19060     1686793+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by meierfra. on 2008-09-18
The "fdisk -l" does not match the one from post #14. So I suggest to try again.  Choose "D" for the swap partition (you can  create a new swap partition once you succeeded to boot into ubuntu again) Also  it seems that testdisk  discovered more than one linux partition. Make sure that you pick the correct one.  (Select the linux partition and press "P" . This should  list the files  on your ubuntu partition. If not, pick a different linux partition)

If you need more help, post  the result of the testdisk "search"

---

