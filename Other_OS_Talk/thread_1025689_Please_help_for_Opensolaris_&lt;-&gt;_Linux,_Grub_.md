---
title: "Please help for Opensolaris &lt;-&gt; Linux, Grub Error 13"
date: 2008-12-30
forum: Other OS Talk
---

### Post by cdiem on 2008-12-30
-------------------------------
Problem: Debian doesn't boot; the system is dual-bootable with Opensolaris.
-------------------------------
-------------------------------
Problem Description:
-------------------------------
Before installing Opensolaris 2008.11, the system looks this way:
/dev/sda1   /home   66GB
/dev/sda2   linux-swap  1GB
/dev/sda3   /    15 GB
/dev/sda4   ?    30 GB

/dev/sda1, /dev/sda2 and /dev/sda3 are Debian, on /dev/sda4 there is Fedora. The Fedora is deleted, and Opensolaris is installed instead. There are problems with Opensolaris if as a primary slice on the disk there is linux-swap, so following some advices over the internet, /dev/sda2 is turned into NTFS during the installation and is turned back to linux-swap after the installation completes. After the installation Opensolaris boots without problems - but Debian doesn't. The installer of Opensolaris somehow changes the slices, and instead of /dev/sda2 puts /dev/sda3 etc., - down here follows 'fdisk -l'.

When trying to load Debian this error comes: Grub Error 13: "Invalid or unsupported executable format"

With the help of a LiveCD of Ubuntu 8.10, I decided to set the 'boot' flag to the slice with Debian. After setting the boot flag on the slice with Debian (the 15 GB one), there was this:
Bad Pbr Sig
and this afterwards:
----------------------------------------
Yukon PXE v. 4.17.8.1
PXE v.2.1
PXE-E61: Media
test failure check
PXE-MOF: Exiting PXE ROM
Operating System not fount
----------------------------------------
I was able to receive the same messages if I put 'makeactive' in the menu.lst of Opensolaris. So i turned back the 'boot' flag to the slice with Opensolaris, who now loads without any problems. But Debian doesn't load at all.

-------------------------------
Some more info
-------------------------------
1. How Linux sees the disk:
fdisk -l from the Ubuntu LiveCD:

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f6f6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8625    69280281   83  Linux
/dev/sda2           12420       14469    16466625   83  Linux
/dev/sda3           14470       14593      996030   82  Linux swap / Solaris
/dev/sda4   *        8626       12419    30475305   bf  Solaris

Partition table entries are not in disk order[/PHP]


2. How Solaris sees the disk:
'format' from the LiveCD of Opensolaris:

[PHP]format> current
Current Disk = c4t0d0
<ATA-WDCWD1200BEVS-0-6M01 cyl 122 alt 2 hd 255 sec 63>
/pci@0,0/pci1734,10c1@1f,2/disk@0,0

format> verify
Warning: Could not read backup labels.

Warning: Check the current partitioning and 'label' the disk or use the
	 'backup' command.

             Total disk size is 14593 cylinders
             Cylinder size is 16065 (512 byte) blocks

                                               Cylinders
      Partition   Status    Type          Start   End   Length    %
      =========   ======    ============  =====   ===   ======   ===
          1                 Linux native      0  8624    8625     59
          2                 Linux native   12419  14468    2050     14
          3                 Solaris        14469  14592     124      1
          4       Active    Solaris2       8625  12418    3794     26
format> quit
[/PHP]

3. What is in the /boot/grub/menu.lst of Debian (which was mounted with the Ubuntu's LiveCD):
[PHP]
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.25-2-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25-2-686 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.25-2-686

title		Debian GNU/Linux, kernel 2.6.25-2-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25-2-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.25-2-686

title		Debian GNU/Linux, kernel 2.6.24-1-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-1-686 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.24-1-686

title		Debian GNU/Linux, kernel 2.6.24-1-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-1-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.24-1-686

title		Debian GNU/Linux, kernel 2.6.18-6-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.18-6-686

title		Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.18-6-686

### END DEBIAN AUTOMAGIC KERNELS LIST[/PHP]


4. What is in /rpool/boot/grub/menu.lst of Opensolaris:

[PHP]splashimage /boot/grub/splash.xpm.gz
background 215ECA
timeout 30
default 0
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title OpenSolaris 2008.11 snv_101b_rc2 X86
findroot (pool_rpool,3,a)
splashimage /boot/solaris.xpm
foreground d25f00
background 115d93
bootfs rpool/ROOT/opensolaris
kernel$ /platform/i86pc/kernel/$ISADIR/unix -B $ZFS-BOOTFS,console=graphics
module$ /platform/i86pc/$ISADIR/boot_archive
#---------------------END BOOTADM--------------------

# Unknown partition of type 131 found on /dev/rdsk/c4t0d0p0 partition: 1
# It maps to the GRUB device: (hd0,0) .

# Unknown partition of type 131 found on /dev/rdsk/c4t0d0p0 partition: 2
# It maps to the GRUB device: (hd0,1) .

title Debian01
rootnoverify (hd0,1)
chainloader +1

title Debian00
rootnoverify (hd0,0)
chainloader +1

title Debian02
rootnoverify (hd0,2)
chainloader +1

title OpenSolaris 2008.11 snv_101b_rc2 X86 text boot
findroot (pool_rpool,3,a)
bootfs rpool/ROOT/opensolaris
kernel$ /platform/i86pc/kernel/$ISADIR/unix -B $ZFS-BOOTFS
module$ /platform/i86pc/$ISADIR/boot_archive
[/PHP]

-------------------------------
What else was done in regards to the problem
-------------------------------

The change of rootnoverify (hd0,1) with all other variants: hd(0,1), hd0(0,1), etc. did not help. Putting 'makeactive' did not help. Opensolaris boots, Debian doesn't. I'm not quite sure where the installer of Opensolaris installs grub - whether in the slice for Opensolaris, or in MBR. PLease, help me, cause my ideas are over.

---

### Post by caljohnsmith on 2008-12-30
How about in your Solaris menu.lst try:
```
title Debian
root (hd0,2)
configfile /boot/grub/menu.lst
```
How about giving that a shot and let me know if it works.

---

### Post by cdiem on 2008-12-30
Many thanks. Using
[PHP]
title Debian
root (hd0,1)
configfile /boot/grub/menu.lst[/PHP]

and changing the /menu.lst of Debian to

[PHP]title        Debian GNU/Linux, kernel 2.6.26-1-686
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro 
initrd        /boot/initrd.img-2.6.26-1-686

title        Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro single
initrd        /boot/initrd.img-2.6.26-1-686[/PHP]

booted the Debian. I guess it picked the first kernel in the menu.lst.

Now the problem is, how can I chainload from the Opensolaris Grub to the Debian one? I would like to pick up a kernel (without having to comment out the other kernels first in order to pick the one I want to use).

---

### Post by caljohnsmith on 2008-12-30
> **cdiem said:**
> 
Now the problem is, how can I chainload from the Opensolaris Grub to the Debian one? I would like to pick up a kernel (without having to comment out the other kernels first in order to pick the one I want to use).
OK, if you want to chainload Debian instead of reading its menu.lst directly, you could do the following as root user:
```
grub
grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit
```
That will install Grub to the boot sector of your sda2 Debian partition so you should be able to chainload it with what you originally tried:
```
title Debian
rootnoverify (hd0,1)
chainloader +1 

```
Let me know if that works, or if not, let me know what problems you run into.

---

### Post by cdiem on 2008-12-30
It worked like a charm, thank you a lot. You saved me reinstalling the debian. Thanks.

---

### Post by caljohnsmith on 2008-12-30
Glad to hear that worked OK; cheers and have fun with all your OSes. :)

---

### Post by nopq631 on 2008-12-31
According to Israeli media reported that 29 Palestinian and Israeli sources said the Hamas militant group affiliated "Qassam Brigades," the chief of general staff of the Israeli air raids killed. But so far, Hamas does not recognize the armed nor deny the news. Palestinian and Israeli sources said the Israel Air Force for two consecutive days on the Gaza Strip more than 280 targets in air strikes, making the Hamas militant group killed a number of senior officials, including the "Qassam Brigades," the chief of general staff of AI Ahmed - Jia Boli. According to sources, the Israeli air raid, Ahmed - Jia Boli he is a regular in the mosque to pray to the Air Force fighter planes dropped a bomb he was killed on the spot. But so far, the militant group Hamas does not recognize nor deny the report, but said they are still to confirm the identity of the deceased. The source said that the Israeli air strikes after the end of Hamas, at least 50% of the underground rocket launchers have been destroyed and at the same time have destroyed more than Hamas's armed arms ammunition depots. In addition, at almost all of the Gaza Strip, Hamas headquarters and camps have been completely destroyed. The Israeli army said in a statement, the Israeli air strike in Gaza in retaliation for Hamas in the past few days to fire rockets, Israeli goal is to crack down on Hamas institutions. Israel will continue to take action against Hamas, the Gaza Strip until the militants to stop attacks against Israel. President Shimon Peres in an interview that Israel will take all necessary measures to put an end to Hamas and other militant groups against Israel's attacks, but Israel does not plan to re-occupation of the Gaza Strip. Palestinian National Authority Chairman Mahmoud Abbas's spokesman Abu - Lu satisfied on behalf of the day in the West Bank city of Ramallah issued a statement saying, "Abbas strongly condemned the Israeli side to the Gaza Strip launched by an act of aggression, he called on the Government of Israel immediately To stop the aggression against the Gaza Strip and called on the international community to intervene. " Residents in the northern Gaza Strip, told reporters that the current Israeli warplanes continued to launch sporadic in the northern Gaza Strip air raid destroyed the northern Gaza refugee camp of the two leading one of the main road. Gaza City residents said that Israeli warplanes have been hearing voices and blur the voice of the helicopter circling, during which there have been explosions heard. Red Cross officials in Gaza Mohammed - Spanier said that Hamas in the Gaza Strip almost all the security agencies have been damaged in air strikes in the dead also included several senior Hamas security agency head. Spanier said the air strikes also caused a large number of innocent Palestinian civilians were killed, which he's ever seen the bloodiest day there were bombs caused the destruction of houses of black smoke, the survivors have been crying out crying. Gaza attack a number of regions of the power failure occurred a long time, rescue personnel used a flashlight around looking for survivors, but they can only carry out those who were injured in the simplest of dressings. 27, 1200, Israeli warplanes to the Gaza Strip, dozens of goals at the same time launched a massive air strike. Up to 28, air strikes have caused nearly 1,000 deaths and injuries. Gaza's first-aid agency said it would be the 1967 Middle East war, Israeli attacks on Palestinians caused by the one-day death toll up to the first. Israel sent more than 100 fighter planes and helicopter gunships in two waves to the Gaza Strip, Hamas training camps, headquarters, arms arsenals, underground missile launching sites, command and control center for the air strike, to the projection of dozens of these goals Pieces of precision-guided bombs. Israel said that they are not close to schools and densely populated areas to launch attacks on the goal of the operation is to stop Palestinian militants in Gaza to the south to launch rockets.___________[ffxi gil](http://www.fast-wowgold.com)[buy warhammer online gold](http://www.just4gold.com/Warhammer-Online-Gold.html)[world of warcraft gold](http://www.fcsgame.com/)[dofus kamas](http://www.dofus-kamas.cc/)[warhammer online gold](http://www.fast-wowgold.com/warhammer-online-gold.htm)

---

