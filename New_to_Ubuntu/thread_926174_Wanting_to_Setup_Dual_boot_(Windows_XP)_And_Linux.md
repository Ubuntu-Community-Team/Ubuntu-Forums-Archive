---
title: "Wanting to Setup Dual boot (Windows XP) And Linux"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by spiritsongtress on 2008-09-21
Currently Running Linux (Ubuntu) on my laptop.. but unfortunately some items don't wanna work on my laptop 9like my webcame) so I wanna dual boot Windows XP (I have a disk), what's the procedure to do it without wiping any files on my computer... (currently external HD is down so I can't move files to protect them... first :(

Can someone give me a step by step procedure?

---

### Post by lisati on 2008-09-21
First of all, make a backup of your important data. That way, if something gets messed up while you're finding your way around setting up the dual-boot, you're in with a chance if recovering it.

The next thing to be aware of is that Windows is not nearly as respectful of other OSes on your system as Linux is, so even if you manage to get both Linux and Windows on your system, you may need to download a tool such as "SuperGrub" to be able to set up the ability to choose between them at boot time.

You'll also need either a Windows CD or a "recovery partition" on available - a genuine Windows disk, is best, preferably one which came with your computer as it will have the necessary drivers on it. (Be careful of the "don't ask too many questions where it came from" variety of disk. Apart from potential legal problems, there's also a chance of malware.)

I've no experience of installing Windows on a system which already has Linux, so I'll happily hand over to someone else more knowledgable of the details.

---

### Post by scorchgeek on 2008-09-21
You need to install Windows, then boot from the Live CD and reload GRUB onto the computer. I think this can be done with the "update-grub" command, but if it doesn't work, then you might have to keep looking.

---

### Post by eternalnewbee on 2008-09-21
Hi there.
In my experience you need need to install windows first, make a partition you want to use for Ubuntu. Then reboot and install Ubuntu on that partition. Hoped that helps...

---

### Post by avinash_destiny on 2008-09-21
First install xp to a partition.
(Dont install into the partition where ur ubuntu and swap are installed)
After this you can load grub within windows or using live cd.


using live cd:

after loading live cd open terminal.
type ```
sudo grub
find /boot/grub/stage1

```

after this you will get something like
(hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])

```
root hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])
setup (hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])
```


colored thing should be replace by the output u got from "find .." i.e (hd?,?)
Then restart the system

Now you should see grub loading

After loading ur ubuntu open terminal .
type:
```
sudo update-grub
```

Now ur grub includes Xp

reply back if anthing goes wrong

---

### Post by kansasnoob on 2008-09-22
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by spiritsongtress on 2008-09-26
Ok I managed to Windows XP up and running but now I can't back into Linux. I know I need to install GRUB or another boot loader.. does anyone know how to do that from windows XP?

Please help!

---

### Post by -Zeus- on 2008-09-26
> **spiritsongtress said:**
> Ok I managed to Windows XP up and running but now I can't back into Linux. I know I need to install GRUB or another boot loader.. does anyone know how to do that from windows XP?

Please help!

You need to get your Ubuntu live cd, and boot to Ubuntu.  Then, follow these instructions to restore GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by spiritsongtress on 2008-09-26
> **avinash_destiny said:**
> First install xp to a partition.
(Dont install into the partition where ur ubuntu and swap are installed)
After this you can load grub within windows or using live cd.


using live cd:

after loading live cd open terminal.
type ```
sudo grub
find /boot/grub/stage1

```

after this you will get something like
(hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])

```
root hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])
setup (hd[COLOR="Red"]0[/COLOR],[COLOR="Red"]0[/COLOR])
```


colored thing should be replace by the output u got from "find .." i.e (hd?,?)
Then restart the system

Now you should see grub loading

After loading ur ubuntu open terminal .
type:
```
sudo update-grub
```

Now ur grub includes Xp

reply back if anthing goes wrong

I am soooooo close! I have Grub working but I can't get the windows to Show up. Grub is working though... but I am having trouble making it go 'Windows XP' after I hit escape.. it lists all the Linux kernals but not windows... I've tried to do both methods.. and it doesn't show up

---

### Post by spiritsongtress on 2008-09-28
I esstenially have Grub working, but don't have it to show XP.
 I'll retry the steps and see what I get

---

### Post by kansasnoob on 2008-09-28
> **kansasnoob said:**
> [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

The last page of that tutorial explains it. It even has graphics.

---

### Post by kansasnoob on 2008-09-28
> **spiritsongtress said:**
> I esstenially have Grub working, but don't have it to show XP.
 I'll retry the steps and see what I get

OK, as I think about it, the last page of that guide is a good starting point, but your windows may be on a different partition than "hd (0,1)" so (assuming you can now boot into Ubuntu) please post the output of 

```
sudo fdisk -l
```

(that's a lower case L)

and also the output of:

```
cat /boot/grub/menu.lst
```

---

### Post by spiritsongtress on 2008-09-28
The output of :sudo fdisk -l

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x378a3789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1696    13623088+  83  Linux
/dev/sda2   *        1697       14009    98904172+   7  HPFS/NTFS
/dev/sda3           14010       14593     4690980   82  Linux swap / Solaris


and the output of:cat /boot/grub/menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=feb689d1-92ef-4baa-98ea-d155be3ca6a3 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb689d1-92ef-4baa-98ea-d155be3ca6a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb689d1-92ef-4baa-98ea-d155be3ca6a3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=feb689d1-92ef-4baa-98ea-d155be3ca6a3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=feb689d1-92ef-4baa-98ea-d155be3ca6a3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by kansasnoob on 2008-09-28
Is Ubuntu booting OK?

Or are you having to run the Live CD?

---

### Post by spiritsongtress on 2008-09-28
Ubuntu is booting fine. I am running it from my hD after reinstalling GRUB.

---

### Post by kansasnoob on 2008-09-28
OK.

In terminal copy-n-paste the following command:

```
sudo gedit /boot/grub/menu.lst
```

Again that's a lower case L. This opens the Menu List in a text editor.

Where you see these lines:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

Change timeout 3 to timeout 10. That'll give you ten seconds to select which OS to boot.

Just below that you see:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

Change that to:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

You see I added a # and space in front of hiddenmenu. That's called commenting out. Your Grub Boot Menu won't be hidden when you boot up now.

Next scroll clear to the bottom of the list and "copy-n-paste" these lines to the bottom of the list:

> title Windows XP
root (hd0,1)
makeactive
chainloader +1 

Then at the top of the screen click on save.

Then click on File > Quit.

You should now be able to boot either Ubuntu or Windows.

---

### Post by kansasnoob on 2008-09-28
If you get that done another nice trick is adding startupmanager. You can either get it in synaptic or just go to terminal and:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration > Startup Manager:

[ATTACH]86667[/ATTACH]

[ATTACH]86668[/ATTACH]

You see you can change the length of timeout, which OS is default, or on the last tab you can even select how many kernels to keep in the menu (I suggest 2, mine says 1 but I'm in Intrepid which has a new option).

---

### Post by spiritsongtress on 2008-09-29
Well I managed to break my computer AGAIN! I accidently delted the Ubuntu partion (but luckly backed up my files on a friends flash drive.)

Could someone walk me though creating a partition and loading Linux back on with Vista (Home Premimum)? Please?

I Have a system Rescue CD and an UBUNTU (7.10) Live CD.

---

