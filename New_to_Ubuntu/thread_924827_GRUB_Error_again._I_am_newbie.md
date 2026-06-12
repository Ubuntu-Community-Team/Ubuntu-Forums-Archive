---
title: "GRUB Error again. I am newbie"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by superthin on 2008-09-19
Hello everybody,

After installing Ubuntu into an PC (existing Windows XP SP2), I could not boot successfully. I am very new to Linux / Ubuntu (I've begun Ubuntu for a week).

**Error 17. Cannot mount selected partition**

I am booting my PC with a LiveCD Ubuntu 8.04 and some details:

This is my HDD:

[IMG]http://img520.imageshack.us/img520/7015/error1yl9.png[/IMG]

and **menu.lst**:

> 
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
timeout		3

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
# kopt=root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



Please help me modify to boot with requirements:

- Choose to boot Ubuntu 8.04 LTS or Windows XP SP2 in menu when booting

- Tell me "Which is best item will I choose in menu?" (Ubuntu 8.04.1, kernel 2.6.24-19-generic / Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) / Ubuntu 8.04.1, memtest86+ / Another). I don't know choose which to boot an normal Unbuntu desktop.

- Wait for 15 seconds to choose Windows XP or Ubuntu

- Modify content of menu.lst above for me (so I could copy & paste and save and reboot my PC).

- If I must type some commands at the terminal, please tell me step by step exactly so I could follow. (I have got very little knowledge about structure of HDD, mount, permission,... in Linux).

Thanks very much!

Best regards,

---

### Post by Locutus_of_Borg on 2008-09-20
this *should* work

menu.lst:
```

timeout=15

title Ubuntu 8.04 LTS
root (hd0,8)
kernel /boot/vmlinuz-2.6.24-19-generic  root=/dev/sda9

title Windows XP SP2
root (hd0,0)
makeactive
chainloader +1
```

copy the text in the box there and paste into a text editor, save as menu.lst

open a terminal and enter ```
sudo -i
mkdir /ubuntu/
mount /dev/sda9 /ubuntu/
cp menu.lst /ubuntu/boot/grub/menu.lst
```

reboot

---

### Post by superthin on 2008-09-20
**@Locutus_of_Borg** : I followed your instructions exactly.
When I restarted my PC, I could choose Ubuntu or Windows XP. With Windows XP: boot process was OK. While choosing Ubuntu, many lines of boot process display.

At the end of chain of messages was:

```

rio0/input/input1
[   34 139237]VFS: Cannot open root device "sda9" or unknown-block(0,0)
[   34 139322]Please append a correct "root=" boot options; here are the available partitions:
[   34 139418]Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

And my PC was halted. Press any keys was useless.

What should I do?

Thanks you very much.

-----------
P/S: I booted into Windows XP and checked the ISO Image I downloaded from [www.ubuntu.com](www.ubuntu.com) with an MD5 utility: exactly. And I checked CRC with my CD was burned from ISO Image. My PC was not halted or out off power when I installed Ubuntu. My HDD has no bad (I bought it a month ago and scandisk has no error).

Aha, my HDD is Segate Baracuda IDE ATA (not SATA, not SCSI). Why did Ubuntu think it was **/dev/sda** ? I think it must be **hda**, not **sda**.

---

### Post by Chelives1928 on 2008-09-20
I'm expieriencing the same problems hung up on **kernel panic- not syncing vfs unable to mount root fs on unknown-block  (0,0) ubuntu intrepid**  Let me know if there is any other information that I can provide for you.  I've checked other topics but none seemed to have helped.

---

### Post by caljohnsmith on 2008-09-20
Replace your menu.lst with this one and I think it all should work:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
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
[COLOR="Red"]timeout 15[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#hiddenmenu[/COLOR]

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
# kopt=root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
[COLOR="Red"]root (hd0,8)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
[COLOR="Red"]root (hd0,8)[/COLOR]
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cf96a88d-d5e6-415d-981f-7af12fab521e ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
[COLOR="Red"]root (hd0,8)[/COLOR]
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]Title Windows XP
root (hd0,0)
makeactive
chainloader +1[/COLOR]
```

---

### Post by superthin on 2008-09-20
I used Partition Magic in DOS to convert swap partition from Primary to Logical.

**fdisk -l** will output:

[IMG]http://img379.imageshack.us/img379/4592/hddvn4.png[/IMG]

Here is **/boot/grub/menu.lst** :

```

timeout=15

title Ubuntu 8.04 LTS
root (hd0,8)
kernel /boot/vmlinuz-2.6.24-19-generic  root=/dev/sda9

title Windows XP SP2
root (hd0,0)
makeactive
chainloader +1

```

These are directories and files (I boot LiveCD and create temp directory **/ubuntu** and mount **/dev/sda9 /ubuntu**)

[IMG]http://img509.imageshack.us/img509/15/hdd2is1.png[/IMG]

[IMG]http://img176.imageshack.us/img176/9042/hdd3wl1.png[/IMG]

The contents of /etc/fstab (opened with gedit /ubuntu/etc/fstab - I mounted /dev/sda9 /ubuntu):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cf96a88d-d5e6-415d-981f-7af12fab521e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ab5241c2-e560-467a-ae83-7387d94e043d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Please take my hands and dip them in Ubuntu's liquid :) 

Thank you very much!

---

### Post by bumanie on 2008-09-20
Grub error can be caused by a couple of things the most common way of fixing it is to reinstall grub via the live cd. Try booting form the live cd and going to terminal.
> sudo grub > root (hd0,8) > setup (hd0) > quit and reboot and see if that works. As said that is the most common cure for grub 17 error. If this doesn't work post back. Am a bit concerned about the kernel panic - often occurs if there is a problem with ram.

---

### Post by Khalis7 on 2008-09-20
Hello everyone. Just want to tell that actually there is another way to repair grub error without using livecd. You can google for super grub, it's a GUI tool that can help reinstall your grub. Try it. It's really easy to use and I had use this tool whenever I messed up the grub. Cheers :)

---

### Post by Chelives1928 on 2008-09-21
I'm expieriencing the same problems hung up on kernel panic- not syncing vfs unable to mount root fs on unknown-block (0,0) ubuntu intrepid Let me know if there is any other information that I can provide for you. I've checked other topics but none seemed to have helped.

---

### Post by MasterNetra on 2008-09-21
Ubuntu Interpid is still in Alpha stage. :p Try Hardy, i would wait until the release date to use Interpid Chelives. :p Unless your bug testing. :)

...And super grub does work. :)

---

### Post by Chelives1928 on 2008-09-21
So I already had Hardy on the Hard drive and I was upgrading but now I just want to get back to it if i can. I'm running the hardy live disk right now trying to find a solution on the hangup.  What do you think?

---

### Post by MasterNetra on 2008-09-21
I think you should probably backup up whatever you don't want to lose then re-install hardy from CD. Probably save you time and a lot of pain.

---

### Post by Chelives1928 on 2008-09-21
There's no way to just revert back to the hardy that was already there or fix my current problem with it hanging on the error regarding the "cannot find fs"  Do you know of a fix for that because then I wouldn't have to lose anything.

---

### Post by MasterNetra on 2008-09-21
You could always get Super Grub onto a disk and try to do a fix on grub? Otherwise i don't see much of a choice...Because it looks like a issue on grubs end.

---

### Post by Chelives1928 on 2008-09-21
When I was looking throughout the forums I noticed it was a common problem.  The only bad thing is that none of them were working for me or some didn't relate.  So i'll keep asking around here and hopefully find something.  Thanks for your help though.

---

### Post by 73ckn797 on 2008-09-21
Ditto's on the SuperGrub. It works!!

You should find it here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by meierfra. on 2008-09-21
superthin: did you ever try caljohnsmiths suggestion from post #5?

If yes, what happened after reboot? Did you get any error messages? Does the Grub menu appear at boot up?

---

### Post by Chelives1928 on 2008-09-22
> **meierfra. said:**
> superthin: did you ever try caljohnsmiths suggestion from post #5?

If yes, what happened after reboot? Did you get any error messages? Does the Grub menu appear at boot up?



it says that I do not have the sufficient permissions to save the new menu.lst  I'm using the live hardy cd right now.  How would I go about making that change to the menu.lst through the live cd?

---

### Post by caljohnsmith on 2008-09-22
> **Chelives1928 said:**
> it says that I do not have the sufficient permissions to save the new menu.lst  I'm using the live hardy cd right now.  How would I go about making that change to the menu.lst through the live cd?
My advice in post #5 was actually for superthin, the OP of this thread, so it unfortunately won't help you.

---

### Post by bumanie on 2008-09-22
You can't revert or do an equivalent of system restore following a distro upgrade. Don't believe super grub disk will help. Upgrades often work, but there is a warning that upgrades could break the system - unfortunately that seems to be the case for you. Personally, I always do a fresh install rather than an upgrade.

---

### Post by Chelives1928 on 2008-09-22
> **caljohnsmith said:**
> My advice in post #5 was actually for superthin, the OP of this thread, so it doesn't apply to you; I think meierfra might have accidentally confused you with the OP.


darn....doyou have any suggestions for the situation I'm in I haven't found an answer and now I'm stuck using the live cd and possibly re-installing Hardy....let me know if there is any information that I can provide.

---

### Post by Chelives1928 on 2008-09-22
nothing yet huh?

---

### Post by 73ckn797 on 2008-09-22
superthin,

In all that I have been reading here I wonder if you could try the following:

press escape when boot up starts countdown for grub. Go to the first Ubuntu line and press "e". That will allow you to temporarily edit the drive assignment. Try changing the hd0.8 to hd0.9. That appears to be the Linux drive from the "menu.lst" you provided. I think that you can then press "b" to boot after the edit. (there are options listed on screen) If that works then you know you have the correct partition, Ubuntu will load. You can then, once in the system, do the following in "Applications", Accessories", "terminal":

type: gksudo gedit /boot/grub/menu.lst

That will open the grub menu for editing.

Edit the entries for the drive designation to what worked, save the file, type "exit" in terminal and reboot to confirm.

Let me know what happens. The Supergrub disk can fix it for you also.

---

### Post by kansasnoob on 2008-09-22
> **superthin said:**
> I used Partition Magic in DOS to convert swap partition from Primary to Logical.

**fdisk -l** will output:

[IMG]http://img379.imageshack.us/img379/4592/hddvn4.png[/IMG]

Here is **/boot/grub/menu.lst** :

```

timeout=15

title Ubuntu 8.04 LTS
root (hd0,8)
kernel /boot/vmlinuz-2.6.24-19-generic  root=/dev/sda9

title Windows XP SP2
root (hd0,0)
makeactive
chainloader +1

```

These are directories and files (I boot LiveCD and create temp directory **/ubuntu** and mount **/dev/sda9 /ubuntu**)

[IMG]http://img509.imageshack.us/img509/15/hdd2is1.png[/IMG]

[IMG]http://img176.imageshack.us/img176/9042/hdd3wl1.png[/IMG]

The contents of /etc/fstab (opened with gedit /ubuntu/etc/fstab - I mounted /dev/sda9 /ubuntu):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cf96a88d-d5e6-415d-981f-7af12fab521e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ab5241c2-e560-467a-ae83-7387d94e043d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Please take my hands and dip them in Ubuntu's liquid :) 

Thank you very much!

Hey all, this was the OP's last post!

We don't know the status!

I think that was two days ago!

---

### Post by kansasnoob on 2008-09-22
> **Chelives1928 said:**
> nothing yet huh?

You need to start a new thread specific to your problem.

While many boot/grub problems are similar they're always "machine specific"!

Please, start your own thread and you'll likely get some help!

---

