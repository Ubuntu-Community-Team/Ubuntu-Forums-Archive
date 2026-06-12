---
title: "[SOLVED] thought i had it fixed,hmmm error21?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-03
i have a usb hd w/kubuntu on it and my laptop has ubuntu studio,
right now as it is wit the usb drive plugged in every thing boots
fine except on a restart i get error 21,with the usb hd unplugged
i get error 21,i really thought i had this set up right!
i reinstalled everything,ubuntu studio on my 1st hd,then the usb hd
and i saved the boot to (hdo,1)on the usb hd,isthis wrong?
/dev/hda wouldbe my 1st hd
/dev/sdb woulbe the usb drive.
i have a super grub disk, i really dont know how to use it,other than
using the auto function.i also dont know how to use the install disk
to change the grub settings,ive tried but just messed things up
when it comes to boot stuff i really suck!so i could use some help!
rick:confused:

---

### Post by steveneddy on 2008-08-03
So, let me get this right.

You have Ubuntu Studio installed permanently on a hard drive of the PC and then another OS on a thumb drive and Grub looks for it when it boots?

And it won't boot without the thumb drive installed?

Sorry, another question...

Why?

---

### Post by rixtr66 on 2008-08-03
yes. as to why idont know what you mean?i dont know why,thats why im asking.

rick

---

### Post by muted1987 on 2008-08-03
what he means is why have a second OS on a usb drive when you could just have the one filesystem (even then you can still have gnome and kde sessions if you want to) with the usb drive as a data drive

---

### Post by Elfy on 2008-08-03
I'd be inclined to set grub up on the ubuntustudio then edit the menu list to add the usb kubuntu.

Supergrub is quite easy to use - boot with it navigate to the fix grub options and then once it's checked it should find your harddrive and just tell it to fix grub - perhaps do it with the usb unplugged.

---

### Post by rixtr66 on 2008-08-03
i used super grub to fix my 1st hd,now icant access my usb drive.
i get error15(here we go again.
rick:confused:

---

### Post by Elfy on 2008-08-03
Boot your ubuntu studio and check the menu.lst to make sure that the usb install is there and that the correct .

When you're usb is plugged in it should always have the same UUID afaik - unless you change the partitions make sure that the UUID in the menu list matches. Plug it in and run

```
sudo blkid
``` to get UUID for the usb drive

---

### Post by rixtr66 on 2008-08-03
the list matches,i got it back to where i can boot both,but
istill get error 21 when restarting.and when the usb hd is unplugged.
now what??
rick

---

### Post by Elfy on 2008-08-03
Error 21 is disk not recognised - can you post the menu list```
cat /boot/grub/menu.lst
``` - all of it and also ```
sudo fdisk -l
```

---

### Post by rixtr66 on 2008-08-03
ok here's the first one:
root@ubuntu-studio:/home/rick# cat /boot/grub/menu.lst
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
# kopt=root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro single 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

root@ubuntu-studio:/home/rick# 

and here's the second one:
root@ubuntu-studio:/home/rick# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29648   238147528+  83  Linux
/dev/sdb2           29649       30401     6048472+   5  Extended
/dev/sdb5           29649       30401     6048441   82  Linux swap / Solaris
root@ubuntu-studio:/home/rick# 
hope this helps!
rick

---

### Post by Elfy on 2008-08-03
can you mount the usb and check that the kernel in /boot of the kubuntu installation is 2.6.24-19-rt ,ie the same as the ubuntu studio one please.

It all looks ok as it is to me, but that doesn't mean a great deal..

---

### Post by rixtr66 on 2008-08-03
i have both 2.6.24-19 and 2.6.24-20?
rick

---

### Post by cariboo on 2008-08-03
It looks like you have both the rt and generic kernels installed and it looks like you are trying to us the generic kerenel on you usb device. In other words you are duplicating installations why not just choose the generic kernel when you don't want to use the rt kernel.

Jim

---

### Post by Elfy on 2008-08-03
> **rixtr66 said:**
> i have both 2.6.24-19 and 2.6.24-20?
rick the important question is whether the kernel in your kubuntu installation is -generic or -rt - because at the moment the menu list is telling it to look for an -rt

---

### Post by rixtr66 on 2008-08-03
myfirst hardrive is 2.6.24-19-rt
the usb hardrive is 2.6.24-20 (generic)
hope this helps!!
rick

---

### Post by Elfy on 2008-08-04
It certainly could - I assume that the kernel doesn't have brackets but has -generic - open the menu list in ubuntu studio - which has kubuntu added at the bottom

Where the menu is looking for 

> title Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sdb1)
root (hd1,0)
kernel /boot/[COLOR="Red"]vmlinuz-2.6.24-19-rt[/COLOR] root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro quiet splash 
initrd /boot/initrd.img-2.6.24-19-rt
savedefault
boot

change it to suit exactly what is actually available in the boot directory of kubuntu, don't change any above the ### END DEBIAN AUTOMAGIC KERNELS LIST line, save the file and reboot

---

### Post by rixtr66 on 2008-08-04
ok i rewrote the menu list and saved it.when i reebooted things where the 
same as before error 21.hmmmm!any ideas?im stumped.
rick:confused:

---

### Post by unutbu on 2008-08-04
Please plug in the USB HD. Boot to Ubuntu Studio. Open a terminal, and post the output to:

```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
sudo dd if=/dev/sdb1 bs=512 count=1 | hexdump -C
```

---

### Post by rixtr66 on 2008-08-04
rick@ubuntu-studio:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
[sudo] password for rick: 
2+0 records in
2+0 records out
2 bytes (2 B) copied, 3.7081e-05 s, 53.9 kB/s
0000000 8100                                   
0000002
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump

2+0 records in
2+0 records out
2 bytes (2 B) copied, 3.78514 s, 0.0 kB/s
0000000 ff00                                   
0000002
rick@ubuntu-studio:~$ 
rick@ubuntu-studio:~$ sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000128629 s, 4.0 MB/s
00000000  eb 48 90 01 b4 01 4c 49  4c 4f 16 08 6c 5c 8e 48  |.H....LILO..l\.H|
00000010  00 00 00 00 6d 5c 8e 48  1f 8a 0d 00 00 00 80 60  |....m\.H.......`|
00000020  56 80 9e 08 b8 c0 07 8e  d0 bc 00 08 fb 52 53 06  |V............RS.|
00000030  56 fc 8e d8 31 ed 60 b8  00 12 b3 36 cd 10 03 02  |V...1.`....6....|
00000040  80 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  1f 8a 0d 00 00 00 80 01  |................|
000001c0  01 00 83 fe ff ff 3f 00  00 00 70 59 ee 08 00 fe  |......?...pY....|
000001d0  ff ff 05 fe ff ff af 59  ee 08 12 8b 62 00 00 00  |.......Y....b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.8631e-05 s, 17.9 MB/s
00000000  eb 48 90 13 00 00 4c 49  4c 4f 16 06 10 00 01 00  |.H....LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 03 02  |....1.....|.....|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  46 c6 6a 5b 00 00 00 01  |........F.j[....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 91 af 63 1c 00 fe  |......?.....c...|
000001d0  ff ff 05 fe ff ff d0 af  63 1c b1 95 b8 00 00 00  |........c.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.296e-05 s, 15.5 MB/s
00000000  eb 48 90 13 00 00 4c 49  4c 4f 16 06 10 00 01 00  |.H....LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 03 02  |....1.....|.....|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  46 c6 6a 5b 00 00 00 01  |........F.j[....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 91 af 63 1c 00 fe  |......?.....c...|
000001d0  ff ff 05 fe ff ff d0 af  63 1c b1 95 b8 00 00 00  |........c.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.6172e-05 s, 14.2 MB/s
00000000  eb 48 90 13 00 00 4c 49  4c 4f 16 06 10 00 01 00  |.H....LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 03 02  |....1.....|.....|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  46 c6 6a 5b 00 00 00 01  |........F.j[....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 91 af 63 1c 00 fe  |......?.....c...|
000001d0  ff ff 05 fe ff ff d0 af  63 1c b1 95 b8 00 00 00  |........c.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.8212e-05 s, 18.1 MB/s
00000000  eb 48 90 13 00 00 4c 49  4c 4f 16 06 10 00 01 00  |.H....LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 03 02  |....1.....|.....|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  46 c6 6a 5b 00 00 00 01  |........F.j[....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 91 af 63 1c 00 fe  |......?.....c...|
000001d0  ff ff 05 fe ff ff d0 af  63 1c b1 95 b8 00 00 00  |........c.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count =1 | hexdump -c
dd: unrecognized operand `count'
Try `dd --help' for more information.
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 3.3869e-05 s, 15.1 MB/s
00000000  eb 48 90 13 00 00 4c 49  4c 4f 16 06 10 00 01 00  |.H....LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 03 02  |....1.....|.....|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  46 c6 6a 5b 00 00 00 01  |........F.j[....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 91 af 63 1c 00 fe  |......?.....c...|
000001d0  ff ff 05 fe ff ff d0 af  63 1c b1 95 b8 00 00 00  |........c.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.9679e-05 s, 17.3 MB/s
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 3f 00 57 02  00 08 fa 90 90 f6 c2 80  |....?.W.........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
rick@ubuntu-studio:~$ sudo dd if=/dev/sdb1 bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.877e-05 s, 17.8 MB/s
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
rick@ubuntu-studio:~$ 

hope this helps
rick:confused:

---

### Post by unutbu on 2008-08-04
rixtr66, thanks for the output.
I think what it is saying is that the BIOS hands control to the MBR on /dev/sdb. The GRUB bootloader  hands off to the stage2 file located on /dev/sda1 and the /boot/grub/menu.lst on /dev/sda1 gets read.
This relies on /dev/sdb being present at boot time.

Try this: Power down. Unplug the USB HD. Boot from the LiveCD. Open a terminal and type

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Reboot (still without the USB HD). Does this work?
If so, then try booting with the USB HD plugged in.

---

### Post by rixtr66 on 2008-08-04
well it worked,sortof,it boots just fine to the 1st hd,and it boots
to the usb hardrive,but kubuntu hangs both in regular mode,and recovery
mode,it just wont start????any ideas for this??
now im really lost!!!s.o.s
rick:confused:

---

### Post by rixtr66 on 2008-08-04
now im getting error 15 file not found,again??????????????
grrrrrrrrr.now what

---

### Post by unutbu on 2008-08-04
Please post your menu.lst again. I think it underwent some changes (post #17) since last you posted it.

Boot into Ubuntu Studio (laptop OS)
Open a terminal and type
```
cat /boot/grub/menu.lst
```

---

### Post by rixtr66 on 2008-08-04
rick@ubuntu-studio:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quietic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

rick@ubuntu-studio:~$ 

hope this helps!
rick

---

### Post by unutbu on 2008-08-04
I believe you are getting the Error 15: File not found error when booting to Kubuntu because

/boot/vmlinuz-2.6.24-19-generic

probably does not exist on the USB HD). I think the menu.lst you posted in #10:
[http://ubuntuforums.org/showpost.php?p=5517352&postcount=10](http://ubuntuforums.org/showpost.php?p=5517352&postcount=10)
probably had it right. On Kubuntu, I'm guessing you have 

/boot/vmlinuz-2.6.24-19-rt

So I think the fix is to boot into Ubuntu Studio,
open a terminal and type

```
cd /boot/grub
mv menu.lst menu.lst-20080804    # just to be safe
gksu gedit /boot/grub/menu.lst
```

Now open up a browser and go to 
[http://ubuntuforums.org/showpost.php?p=5517352&postcount=10](http://ubuntuforums.org/showpost.php?p=5517352&postcount=10)

Copy and paste your old menu.lst into the gedit window. Save and quit.

Then try rebooting, with and without the USB HD.

---

### Post by Elfy on 2008-08-05
> On Kubuntu, I'm guessing you have 

/boot/vmlinuz-2.6.24-19-rtwe've been here :) - post 15

> myfirst hardrive is 2.6.24-19-rt
the usb hardrive is 2.6.24-20 (generic)which is why I had him change the kernel line for kubuntu ;) 

So i guess if he changes the lines to match -20 we might get there


> # linux installation on /dev/sdb.
title Ubuntu 8.04.1, kernel 2.6.24-[COLOR="Red"]19[/COLOR]-generic (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-[COLOR="#ff0000"]19[/COLOR]-generic root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro quiet splash 
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb.
title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro single 
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot


---

### Post by unutbu on 2008-08-05
I could be wrong (perhaps I should put that in my sig...)
However, here's my reasoning:

[list]
[*] rixtr66 begins this thread saying he is able to boot both UbuntuStudio and Kubuntu as long as the USB HD is plugged in. This implies that some menu.lst is getting read, and the menu.lst is correct, otherwise UbuntuStudio and Kubuntu would not both be booting properly. 

(At this point it is an open question whether it is the menu.lst on UbuntuStudio that is controlling the boot process, or if it is the one on Kubuntu)

[*]  rixtr66 posts
```

rick@ubuntu-studio:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump

2+0 records in
2+0 records out
2 bytes (2 B) copied, 3.78514 s, 0.0 kB/s
0000000 ff00
0000002
```

According to [http://ubuntuforums.org/showpost.php?p=5242287&postcount=4](http://ubuntuforums.org/showpost.php?p=5242287&postcount=4) this implies that if/when the boot process reaches the MBR on the USB HD (/dev/sdb), the boot process gets pointed back to (hd0,0) aka /dev/sda1. While this is not completely definitive (I have not proven the boot process ever reaches the MBR on the USB HD), it suggests to me that the menu.lst on UbuntuStudio is the one in control, not the one on Kubuntu.
[/list]
This also provides a possible explanation for his problem: The BIOS was handing control to the MBR on the USB HD, and then getting redirected back to /dev/sda1. Since the daisy chain of bootloaders included the USB HD, it became an integral part of the boot process and without it the laptop failed to boot.

As I said, I could be wrong, but for what its worth, this is why I believe the original menu.lst on UbuntuStudio was correct.

---

### Post by Elfy on 2008-08-05
> I could be wrong (perhaps I should put that in my sig...)+1

I was just working from the fact that the op doesn't actually have an -rt kernel in kubuntu for it to find - in fact if his post is correct he doesn't actually have -19 but -20 (didn't know that had come out of proposed)

But as you say it worked more or less correctly at the beginning, although it failed on a restart.

If the op did in fact run supergrub with the usb unplugged then studio on the hdd should, as you say, be in control.

It must be worth changing it as you say.

TBH the  > sudo dd if=/dev/sdb bs=1 skip=1049 count=2 | hexdump is completely beyond me at the moment.

The only reason I actually posted the last time was because I was aware that the kernel was -20 and not -19-rt - to my knowledge then the boot would have failed as soon as it tried to boot the missing kernel...

---

### Post by rixtr66 on 2008-08-05
i tried using the old menu as you suggested,to no avail i still get
error 21 with the usb unplugged,and on restarts.
this is my plan;to run supergrub to fix the mbr,then reinstall
kubuntu  to the usb drive,now where should i put the boot?(hd0)
wich is where i put it last time,or /dev/sdb???
or is it something different?
rick

---

### Post by unutbu on 2008-08-05
Personally, I'd like to persevere, because I think this problem is solvable and we will learn something valuable. But of course this is your decision to make and you should do what is best for you.

> where should i put the boot?(hd0)
wich is where i put it last time,or /dev/sdb???
or is it something different?

If you choose to reinstall Kubuntu, it will (should?) ask you where you want to install GRUB. If you say (hd0) aka /dev/sda, then the GRUB it writes will direct the boot process to read the menu.lst on the USB drive. You will be back to square 1, being able to boot both OSs only when the USB HD is connected. 

If you instead say not to install GRUB, or just install it on (hd1) aka /dev/sdb, then after installing Kubuntu your laptop will not know how to boot Kubuntu at first, but you can come back here and we can tell you what stanzas to add to your UbuntuStudio menu.lst so it can boot Kubuntu. If you do it this way, I think you will then be able to boot UbuntuStudio and/or Kubuntu with the USB attached, and UbuntuStudio without the USB attached.

At least, this is the way I think things should work. So far, I haven't been able to predict the future very well on this thread, so I could very well be wrong again. 

If you choose to hold off on reinstalling Kubuntu, just say the word; I'd like to ask you a few more questions to get to the bottom of this mystery.

---

### Post by rixtr66 on 2008-08-05
ok ask away!!!im still fooling around with installing,
i dont really mind the time it takes,so far i have installed
kubuntu w/kde 3.5 and installed kubuntu w/kde4,im not sure 
i like 4 it seems touchy.i would like to resolve this issue
myself,so im open to suggestions.
rick

---

### Post by unutbu on 2008-08-05
Questions:
[list=1]
[*] When you boot up, do you change the boot order in the BIOS, or do you keep it the same all the time?
[*] What is the BIOS boot order? Does it go Laptop first, then USB HD, or is it the other way around?
[*] In post 21, after we reinstalled GRUB on (hd0), but before you restored your old menu.lst, you say [http://ubuntuforums.org/showpost.php?p=5523635&postcount=21](http://ubuntuforums.org/showpost.php?p=5523635&postcount=21), > it boots just fine to the 1st hd,... but kubuntu hangs both in regular mode, and recovery mode.
```

                with USB         w/o USB 
UbuntuStudio    Y                Y 
Kubuntu         hangs            N
```

So was this the state of affairs? (I'm clumping regular and recovery mode together because the boot stanzas are sufficently similar that how one behaves so will the other).

[*] After the menu.lst had been restored to its orignal form (post 10), in post 29, you write [http://ubuntuforums.org/showpost.php?p=5530420&postcount=29](http://ubuntuforums.org/showpost.php?p=5530420&postcount=29), > i still get error 21 with the usb unplugged,and on restarts.

```
                with USB         w/o USB 
UbuntuStudio    Y                Y 
Kubuntu         error 21         N
```
Is this correct? 
[*] Finally, I'd like to take a look at both your menu.lsts. With the USB attached, please boot up UbuntuStudio, open a terminal, and type
```

sudo mkdir /K
sudo mount /dev/sdb1 /K  # Your Kubuntu filesystem will be mounted at /K
```

Then post as attachments /boot/grub/menu.lst and /K/boot/grub/menu.lst
[/list]

---

### Post by rixtr66 on 2008-08-05
to answer your questions:
1 the boot structure stays the same all the time,no changes.
2 the bios boot order is,dvd,usbhd,1st hd.
3 yes that was the closest we got it to working!
4 yes i still get error21.
5 :rick@ubuntu-studio:~$ cat /k/boot/grub/menu.lst
cat: /k/boot/grub/menu.lst: No such file or directory
rick@ubuntu-studio:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-rt
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-19-rt
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-19-rt

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=d7b09986-7147-4fc6-b9b4-60cb52e7314d ro single
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot


rick@ubuntu-studio:~$ 

/k/boot/grub/menu.lst

rick@ubuntu-studio:~$ cat /k/boot/grub/menu.lst
cat: /k/boot/grub/menu.lst: No such file or directory
rick@ubuntu-studio:~$
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 8.04.1, kernel 2.6.24-20-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-20-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-20-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-20-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-20-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd          /boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd          /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot

rick@bb-216-195-181-118:~$

---

### Post by unutbu on 2008-08-05
How do you want the system setup?
When the USB is attached, do you want Kubuntu to boot by default, or do you want UStudio to boot by default and have Kubuntu selectable through the GRUB menu?

---

### Post by rixtr66 on 2008-08-05
igot the other part of the menu posted(k)
yes i would like to have u studio to be the main boot
with kubuntu selectable.
rick

---

### Post by unutbu on 2008-08-05
Please post the output of
```

blkid
```

---

### Post by rixtr66 on 2008-08-05
rick@bb-216-195-181-118:~$ sudo blkid
[sudo] password for rick:
/dev/sda1: UUID="f1c57898-5a93-451f-a762-2e6fe5839cdb" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="c5569aea-0692-4238-8e99-1465bed28e62"
/dev/sdb1: UUID="1fdaf9eb-b819-461c-9cde-372c824c538e" TYPE="ext3"
/dev/sdb5: TYPE="swap" UUID="f0608017-8210-40b3-b642-de0a57e27e4f"
rick@bb-216-195-181-118:~$

rick:)

---

### Post by unutbu on 2008-08-05
[list]
[*] First, change the BIOS boot order so that the 1st hd is before the usbhd.
If this succeeds, the boot process will go:
```

BIOS --> MBR on /dev/sda --> menu.lst on /dev/sda --> UStudio by default
                                                  --> Kubuntu selectable
```

[*] Boot into UStudio. Open terminal.
```
cd /boot/grub
sudo mv menu.lst menu.lst-20080805
gksu gedit /boot/grub/menu.lst
```
Cut and paste this into /boot/grub/menu.lst:

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
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-rt
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-19-rt
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-rt root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-19-rt

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f1c57898-5a93-451f-a762-2e6fe5839cdb ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title           Kubuntu 8.04.1, kernel 2.6.24-20-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-20-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-20-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-20-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-20-generic

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Kubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sdb1)
root            (hd1,0)
kernel 		/boot/vmlinuz-2.6.24-19-rt root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro quiet splash
initrd 		/boot/initrd.img-2.6.24-19-generic

title  		Kubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sdb1)
root   		(hd1,0)
kernel 		/boot/vmlinuz-2.6.24-19-rt root=UUID=1fdaf9eb-b819-461c-9cde-372c824c538e ro single
initrd 		/boot/initrd.img-2.6.24-19-generic

title           Kubuntu 8.04.1, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

```
[/list]
Test it out. If it doesn't work, please post the new chart:
```

                with USB         w/o USB 
UbuntuStudio    Y                Y 
Kubuntu         error 21         N

```

---

### Post by rixtr66 on 2008-08-05
with usb i get both ubuntu studio,and kubuntu
without the usb i only get error21,and no access to either.
rick

---

### Post by unutbu on 2008-08-05
When you get to the GRUB menu, do you see options to boot 'Kubuntu' with a 'K', or do all the boot options say 'Ubuntu...'?

---

### Post by rixtr66 on 2008-08-05
all the options say ubuntu.i dont know if this is relavant,but kubuntu is listed before studio.
rick

---

### Post by unutbu on 2008-08-05
Okay, that is a clear sign that the menu.lst on /dev/sdb is still getting read. This might be the case if you reinstalled Kubuntu after post 20.

If so, please repeat the instructions in post #20:
[http://ubuntuforums.org/showpost.php?p=5522884&postcount=20](http://ubuntuforums.org/showpost.php?p=5522884&postcount=20)

If it is not so, then I'm mystified.
Perhaps check again that the laptop 1st HD is listed before the USB external HD in the BIOS boot order, and then do post #20 again too.

When things are working the way I planned, you should see Ubuntu Studio first in the GRUB menu, and then a bunch of Kubuntu boot lines.

---

### Post by rixtr66 on 2008-08-05
success!!!!!!!at last thank you very much!!
how long till i can do stuff like that?
much thanx rick:)

---

### Post by unutbu on 2008-08-05
Yippie! Sweeeet.
> 
how long till i can do stuff like that?
8 months ago I thought a GRUB was something robins ate :) Then I bricked my computer. That provided me with a lot of motivation to learn how to fix GRUB problems.

---

