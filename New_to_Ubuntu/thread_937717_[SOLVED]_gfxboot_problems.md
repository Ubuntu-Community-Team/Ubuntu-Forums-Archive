---
title: "[SOLVED] gfxboot problems"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by xreaper on 2008-10-04
Hey guys, me again. I was trying to follow a tutorial on how to setup gfxboot about 5 minutes ago.. only to find that when i reboot, all that is there for me is a grub terminal? (if that makes any sense at all) any help will be very much appreciated. 

If it helps, I'm using ubuntu 8.04, dual booted with windows XP, 2ghz processor, 1gb ram, and ati radeon x300 128mb graphics card.

And, one last thing. feel free to talk me through anything like a 5 year old, because I'm only just getting into this whole graphical boot thing.

---

### Post by xreaper on 2008-10-04
oh, and also, I have tried:

root (hd0,0)
setup (hd0)

but no avail, if that makes any sense.

---

### Post by Orange_and_Green on 2008-10-04
If what you are getting really is a GRUB prompt, the correct command sequence to boot into Windows is this: (spaces are important, type them exactly as they are: )

```
root (hd0,0)
makeactive
savedefault
chainloader +1
boot

```
(assuming Windows is on the first boot disk)

Anyway, I suggest you just reinstall GRUB by booting into an Ubuntu live CD. First thing to do when the live CD has booted up is to run ```
sudo fdisk -l
``` and post the results back here :) good luck:KS

---

### Post by xreaper on 2008-10-04
okay, I'm in the live cd now, so I'll just type that in now..

---

### Post by xreaper on 2008-10-04
uhh, i typed "fdisk -l" and all i got was

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$

---

### Post by Orange_and_Green on 2008-10-04
Sorry, my mistake. Make that ```
sudo fdisk -l
``` please.

---

### Post by xreaper on 2008-10-04
ahh, i should have known anyway. uhh, here are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3dd93047

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   83  Linux
/dev/sda2   *         132         262     1052257+   7  HPFS/NTFS
/dev/sda3             263        1655    11189272+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+  83  Linux
/dev/sdb2           13055       18471    43512052+   7  HPFS/NTFS
/dev/sdb3           18472       19457     7920045   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 




did I pass?

---

### Post by Orange_and_Green on 2008-10-04
Interesting setup you have there. Basically, you have one 13 GB disk with Linux and a bootable windows installation, and a second, 160GB disk with yet another Linux partition and a non-bootable windows partition.

Let's see what is in those partitions now shall we? Please post the outputs of:
```
mkdir first_disk
sudo mount /dev/sda1 first_disk
ls first_disk/
```
and
```
mkdir second_disk
sudo mount /dev/sdb1 second_disk
ls second_disk/
```

---

### Post by xreaper on 2008-10-04
lol yeah, long story.. I bought a faulty hard drive that wouldn't boot ubuntu, so then I had to get a smaller one that I could put the boot files onto (friend helped alot with that) and then i just randomly decided to chuck XP on the second hard drive for uhh *cough* gaming purposes.. but enough about that, heres the info:

ubuntu@ubuntu:~$ ls first_disk/
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic             lost+found
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.24-16-generic
grub                              System.map-2.6.24-19-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic


ubuntu@ubuntu:~$ ls second_disk/
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
ubuntu@ubuntu:~$

---

### Post by Orange_and_Green on 2008-10-04
I see. Well, I guess that will require a little "different-from-standard" approach if you wish to boot from the 13 GB drive.

Before we start, could I ask you once more to paste the output of ```
cat second_disk/boot/grub/menu.lst
```
and
```
cat second_disk/boot/grub/device.map
```

please? Once we have that, we should be ready to go ;)

---

### Post by xreaper on 2008-10-04
ofcourse you can, not a problem. but I don't think you're going to like the output.. =S

ubuntu@ubuntu:~$ cat second_disk/boot/grub/menu.lst
cat: second_disk/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat second_disk/boot/grub/device.map
cat: second_disk/boot/grub/device.map: No such file or directory

---

### Post by xreaper on 2008-10-04
oh, by the way.. I've just checked the boot file on my second hard drive and it is completely blank. So thats probably why i can't find it

---

### Post by xreaper on 2008-10-04
Oh, sorry, I should have remembered. ALL off the boot files are on the first hdd.

ubuntu@ubuntu:~$  cat first_disk/grub/menu.lst
gfxmenu /boot/grub/message.suse
ubuntu@ubuntu:~$ cat first_disk/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Orange_and_Green on 2008-10-04
> **xreaper said:**
> ofcourse you can, not a problem. but I don't think you're going to like the output..

LOL well yes and no actually. At least now I know it makes sense for GRUB to drop you to a prompt since it has no config files to work with.

If I were you at this point, I would:
1) reinstall grub to sda letting it know it should get its config files from sdb1, and
2) supply the said config files.

This is step 1.
```
cd second_disk
sudo grub_install --root-directory=/ /dev/sda
```

This command should create a device.map that reads "hd0 /dev/sda" and "hd1 /dev/sdb"

You can start doing this, but please do NOT restart before I post again. I will try and put together a workable menu.lst and post again.
good luck:KS

---

### Post by xreaper on 2008-10-04
hey, I tried what you said, and it didn't work. also tried a couple of other little adjustments 8) but still nothing :

ubuntu@ubuntu:~/second_disk$ sudo grub_install --root-directory=/ /dev/sda
sudo: grub_install: command not found
ubuntu@ubuntu:~/second_disk$ grub_install --root-directory=/ /dev/sda
bash: grub_install: command not found
ubuntu@ubuntu:~/second_disk$ sudo grub_install --root-directory=/ /dev/sda
sudo: grub_install: command not found
ubuntu@ubuntu:~/second_disk$ sudo grub install --root-directory=/ /dev/sda
grub: unrecognized option `--root-directory=/'

---

### Post by xreaper on 2008-10-04
I have a menu.lst backup. tried to copy and paste, but I don't have the permissions. is there anyway I can bypass the permissions thing? 

menu.lst backup looks pretty...yeah, I hope you get the sarcasm =P


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
# kopt=root=UUID=634c96ed-7b53-4d9d-96da-0724e4e1ccbd ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=634c96ed-7b53-4d9d-96da-0724e4e1ccbd ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=634c96ed-7b53-4d9d-96da-0724e4e1ccbd ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Orange_and_Green on 2008-10-04
To "bypass the protection" is easy.

Type "gksu gedit" in a shell, open the backup (or copy-paste my suggestion if that one won't work) then save it where you want.

If you follow my advice (also with the grub-install bit), you need to save the file as second_disk/boot/grub/menu.lst.

And this is my try:
```
default		0

timeout		10

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		vmlinuz-2.6.24-19-generic root=/dev/sdb1 ro quiet splash
initrd		initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04 recovery mode, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		vmlinuz-2.6.24-19-generic root=/dev/sdb1 ro single
initrd		initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		vmlinuz-2.6.24-16-generic root=/dev/sdb1 ro quiet splash
initrd		initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04 recovery mode, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		vmlinuz-2.6.24-16-generic root=/dev/sdb1 ro single
initrd		initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Good luck:KS

---

### Post by xreaper on 2008-10-04
uhh, It won't show me the place you told me to save it to lol. seems like I'll never be able to trust tutorials ever again... =\ want me to keep looking?

---

### Post by xreaper on 2008-10-04
ok, I used gksu nautilus to copy the menu.lst backup file into the folder and then rename it menu.lst. its the only file in there though, is that normal?

---

### Post by xreaper on 2008-10-04
ahh.. RIGHT! What I did was taken the menu.lst backup file (renamed menu.lst) and chucked into my first ubuntu partition. then, after being able to get the grub menu, I restored all my backup files ^^ I now have both ubuntu back. going to try windows in a sec. now, one last question.. do you know how to get gfxboot working? it looks really cool, and I might even be able to impress my friend with it. =D

---

### Post by xreaper on 2008-10-04
Yeah, windows works aswell ^^ thanks heaps. worked like a charm=D hope this can help someone in the future. thanks again! =D

---

