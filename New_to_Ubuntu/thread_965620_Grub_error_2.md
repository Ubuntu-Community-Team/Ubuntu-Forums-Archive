---
title: "Grub error 2"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by phoenix23 on 2008-10-31
I installed Intrepid on my 1st hard drive, and Vista is on my second. I am getting grub error 2 on startup.

Here is sources.lst

```

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
# kopt=root=UUID=7a4be2ad-ffc6-4021-a63c-86f9f04e84c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a4be2ad-ffc6-4021-a63c-86f9f04e84c5

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
uuid		7a4be2ad-ffc6-4021-a63c-86f9f04e84c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a4be2ad-ffc6-4021-a63c-86f9f04e84c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7a4be2ad-ffc6-4021-a63c-86f9f04e84c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a4be2ad-ffc6-4021-a63c-86f9f04e84c5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7a4be2ad-ffc6-4021-a63c-86f9f04e84c5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

and sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60425   485363781   83  Linux
/dev/sda2           60426       60801     3020220    5  Extended
/dev/sda5           60426       60801     3020188+  82  Linux swap / Solaris
```

Any help? Thanks.

---

### Post by Berean on 2008-10-31
As I understand it - and of course, I may be wrong - but Windows prefers to be the on the first partition.  When I tried to boot from Windows on a secondary partition it failed until I reversed the priority (ie Windows first, Ubuntu second).

Edit: Sorry, I misread your post!  Unfortunately, I have no experience of booting from two internal disk drives.  Have you attempted looking at your bios?  Once again, my apologies.

---

### Post by caljohnsmith on 2008-10-31
So are you getting the Grub error 2 before seeing a Grub menu or after you get the Grub menu and select Ubuntu or Vista? Also please post:
```
sudo blkid
```

---

### Post by phoenix23 on 2008-10-31
> **caljohnsmith said:**
> So are you getting the Grub error 2 before seeing a Grub menu or after you get the Grub menu and select Ubuntu or Vista? Also please post:
```
sudo blkid
```
I get the grub error immediately after I turn my computer on. There is no menu, or choices.

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="7a4be2ad-ffc6-4021-a63c-86f9f04e84c5" TYPE="ext3" 
/dev/sda5: UUID="1080ead8-4e5f-4fd3-b841-bb5dd40d70db" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

```

---

### Post by caljohnsmith on 2008-10-31
Your menu entry for Vista uses (hd1), so do you have more than one HDD? If so, please post the full output of:
```
sudo fdisk -lu
```
Also post:
```
sudo dumpe2fs /dev/sda1 | grep -i "inode size"
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo mount /dev/sda1 /mnt
sudo chroot /mnt /bin/bash
apt-cache policy grub
exit
```
Are you booting from your sda drive on start up?

---

### Post by phoenix23 on 2008-10-31
Yes, ubuntu is on my first hard drive and vista is on my second.
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00012741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   970727624   485363781   83  Linux
/dev/sda2       970727625   976768064     3020220    5  Extended
/dev/sda5       970727688   976768064     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       64259       32098+  de  Dell Utility
/dev/sdb2   *       65536   234371071   117152768    7  HPFS/NTFS

```

and when I copy and paste the second command

```
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i "inode size"
dumpe2fs 1.41.3 (12-Oct-2008)
Inode size:	          256
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# apt-cache policy grub
grub:
  Installed: 0.97-29ubuntu45
  Candidate: 0.97-29ubuntu45
  Version table:
 *** 0.97-29ubuntu45 0
        500 http://us.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
root@ubuntu:/# exit
```

---

### Post by meierfra. on 2008-10-31
> I installed Intrepid on my 1st hard drive

Is this a fresh install or did you upgrade from an earlier version of Ubuntu?

---

### Post by phoenix23 on 2008-10-31
> **meierfra. said:**
> Is this a fresh install or did you upgrade from an earlier version of Ubuntu?
it is a fresh install

---

### Post by caljohnsmith on 2008-10-31
OK, it appears you have Grub correctly installed to the MBR (Master Boot Record) of sda, and that it points correctly to sda1 for its boot files. As expected, your Intrepid partition uses the newer 256 byte inode size, so it is important that your Grub version be the 45 version that you have. I would try reinstalling Grub to the MBR, so from your Intrepid Live CD (don't use an earlier version Live CD):
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda --recheck
```
See if that makes any difference.

---

### Post by phoenix23 on 2008-10-31
Is this alright?

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-10-31
Those messages are just fine. Go ahead and reboot and see if it changed anything.

---

### Post by phoenix23 on 2008-10-31
Nothing has changed :(

still getting grub error 2

---

### Post by caljohnsmith on 2008-10-31
Well, it may not make any difference, but since we know from your other post that your installed Grub in sda1 is version 45, you could try:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
grub-install /dev/sda
exit
```
Reboot, see if anything changed, and if not, maybe you could try downloading a new Grub 0.97-29ubuntu45 version from packages.ubuntu.com, and manually installing it into sda1 from the Live CD. I know from helping a few others that the newer 45 version of Grub should not give a Grub error 2 with the newer 256 byte inode size partitions, because that's exactly what the newer version was modified for. Anyway, try the above and let me know what happens.

---

### Post by phoenix23 on 2008-10-31
I don't think that worked

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ mount --bind /dev /mnt/dev
mount: only root can do that
ubuntu@ubuntu:~$ mount --bind /proc /mnt/proc
mount: only root can do that
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# grub-install /dev/sda
/dev/sda: Not found or not a block device.
root@ubuntu:/# exit

```

According to synaptic, I have that version of grub. What do I do?

---

### Post by caljohnsmith on 2008-10-31
My mistake, I forgot to use "sudo" in front of the mount commands. Try again and let me know if it makes any difference after rebooting.

---

### Post by phoenix23 on 2008-10-31
Alright, here's what I did.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:/# sudo grub-install
sudo: unable to resolve host ubuntu
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
root@ubuntu:/# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
root@ubuntu:/# 

```

rebooting now

---

### Post by phoenix23 on 2008-10-31
did not work. grub error 2.

---

### Post by phoenix23 on 2008-10-31
How do I go about installing Grub 0.97-29ubuntu45? According to synaptic, it is already downloaded.

---

### Post by meierfra. on 2008-10-31
[QUOTE=phoenix23]root@ubuntu:/# sudo grub-install[/QUOTE]

This needs to be

```
root@ubuntu:/#  grub-install /dev/sda
```



[QUOTE=Berean]Have you attempted looking at your bios?[/QUOTE]
+1

---

### Post by bumanie on 2008-10-31
Try [super grub disk]("http://www.supergrubdisk.org/index.php?pid=5"). > Grub error 2 is: "Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO". As quoted from the grub manual.

Try this in terminal and reboot sudo e2fsck -C0 -p -f -v /dev/sda1 This will check the filesystem on sda1 upon rebooting and it fixes 99% of errors.

---

### Post by caljohnsmith on 2008-10-31
Don't worry about trying to reinstall the 0.97-29ubuntu45 package, I'm thinking now that would be a waste of time since your Intrepid install seems by all indications to have the newer package installed all ready. I think meierfra and Berean gave you the best advice about changing your BIOS settings related to your HDD. Try that and let us know how it goes.

---

### Post by meierfra. on 2008-10-31
Check out this thread:
[URL="http://ubuntuforums.org/showthread.php?t=151682"]
http://ubuntuforums.org/showthread.php?t=151682[/URL]

---

### Post by phoenix23 on 2008-10-31
Tried supergrubdisk, ran throuhg "fix linux boot" getting error 15:file not found
booting not lucky

suggestions?

what should I look for in bios? I have the right hd order already.

---

### Post by phoenix23 on 2008-10-31
could this be the problem?

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7a4be2ad-ffc6-4021-a63c-86f9f04e84c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a4be2ad-ffc6-4021-a63c-86f9f04e84c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```

why isn't root (hd0,0)

---

### Post by meierfra. on 2008-10-31
That shouldn't cause a problem. Intrepid uses "uuid some_long_number" instead of  "root (hdX,Y)" 

Also since the grub menu does not appear at boot up, your "error 2" has nothing to do with menu.lst.

---

### Post by meierfra. on 2008-10-31
> what should I look for in bios? 

The link I posted earlier contains some suggestions.

---

### Post by bumanie on 2008-10-31
If I'm not mistaken, grub error 15 indicates that there is a file (or may be two) missing from the kernel image that grub refers to. I have to go out now, but I'll boot my laptop which has intrepid on it when I get back if this is not solved by then. We can compare kernel image files and see if we can work out what is missing and then replace them.

---

### Post by Dual-Boot_PDX on 2009-02-14
I just went through the ordeal of this on my Dell Precision WorkStation 340 Series today.  My Windows XP Pro was fully corrupted (full of viruses and wouldn't boot-up after relatives came and stayed with us over the holidays... wonder what they were looking-at/downloading).  Anyhow, wiped my single 160 Gig hard-drive clean, installed a fresh copy of Windows XP Pro from disk, let Windows partition my drive, then went back and installed a dual-boot with Ubuntu.  When the installation finished and I removed the install disk and restarted the system, I got the "GRUB Error 2".

I searched through tons of threads and got a strong sense the problem was in the BIOS... but what to change?  I tried a bunch of different things and nothing worked, except for one change.  Here it is:

**Changed "IDE Drive UDMA" to "off"** under "Integrated Devices (LegacySelect Options)".  Again, this was on a Dell Precision WorkStation 240 Series using BIOS Version A06.  That was the only change I made, and viola... everything works perfectly for a dual-boot environment... both OS's load and run fast and clean.

Hope this helps someone.

-Lee

---

