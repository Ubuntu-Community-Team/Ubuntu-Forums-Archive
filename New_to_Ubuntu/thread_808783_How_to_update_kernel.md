---
title: "How to update kernel"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-26
I think I've update to kernel 2.6.24-17 using Update Manager. Anyway, i still see conky display 2.6.24-16. Maybe there is still step to take but I really dont know? Hope someone can assist me.

---

### Post by drs305 on 2008-05-26
> **wariskampar said:**
> I think I've update to kernel 2.6.24-17 using Update Manager. Anyway, i still see conky display 2.6.24-16. Maybe there is still step to take but I really dont know? Hope someone can assist me.

What does this say (it will tell you the kernel version):
```
uname -r
```

If it still says -16, reboot and notice your choices in the grub boot menu.

---

### Post by dRock1286 on 2008-05-26
maybe that conky was created for that specific kernel?  I don't know, just throwing an idea out there...

---

### Post by iaculallad on 2008-05-26
> **wariskampar said:**
> I think I've update to kernel 2.6.24-17 using Update Manager. Anyway, i still see conky display 2.6.24-16. Maybe there is still step to take but I really dont know? Hope someone can assist me.

Use this [guide]("http://ubuntuforums.org/showthread.php?t=85917") and see it for yourself.

---

### Post by wariskampar on 2008-05-27
@drs305; this the outcome:
aznan@aznan-laptop:~$ uname -r
2.6.24-16-generic

@dRock1286; i'm pretty sure conky is ok (it just retrieves the info anyway). 

can anyone tell me how to change kernel? maybe that will do it

---

### Post by tact on 2008-05-27
When you boot up... and the grub menu comes up (you might have to hurriedly press esc to get the menu to show... does -17 appear there at all?

---

### Post by drs305 on 2008-05-27
> **wariskampar said:**
> @drs305; this the outcome:
aznan@aznan-laptop:~$ uname -r
2.6.24-16-generic

@dRock1286; i'm pretty sure conky is ok (it just retrieves the info anyway). 

can anyone tell me how to change kernel? maybe that will do it

If you have 17 installed, you aren't yet using it. You can check in synaptic to see if the 17 kernel is installed. Look for linux-image-2.6.24-17...  If it's not installed, you can mark it for installation and apply. Pick the same name as the 16 kernel name shown installed, just select the 17 version.

If you prefer, you should be able to go to System, Administration, Update Mangager and see if there are any updates available.

Once it is installed, if it doesn't start automatically on your next boot, you can do as tact suggested in the previous post and select the 17 kernel from the grub menu during boot. 

The other option is to go to System, Administration, StartUp-Manager. 
If you don't see StartUp-Manager in the menu, install it with:
```
sudo aptitude install startupmanager
```

In StartUp-Manager you can select which kernel you would like to boot (Boot Options tab, Default Operating System). You can also use StartUp-Manager to change some of the items you see on the boot grub menu.

---

### Post by wariskampar on 2008-05-27
17 was already selected in Synaptic. But still SUM dont have any option for 17 to choose. I also notice similar thread on this problem
[http://ubuntuforums.org/showthread.php?p=5053216#post5053216](http://ubuntuforums.org/showthread.php?p=5053216#post5053216)
maybe the 17 itself is the problem

---

### Post by drs305 on 2008-05-27
> **wariskampar said:**
> 17 was already selected in Synaptic. But still SUM dont have any option for 17 to choose. I also notice similar thread on this problem
[http://ubuntuforums.org/showthread.php?p=5053216#post5053216](http://ubuntuforums.org/showthread.php?p=5053216#post5053216)
maybe the 17 itself is the problem

synaptic will show what is installed, but not necessarily what will be booted. But kernel 17 not showing in SUM is puzzling. Can you please post the results of:

```
cat /boot/grub/menu.lst
```

Here is what mine looks like with kernel 17 installed on a 64-bit computer (but please post the complete results of yours):
```

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-... ro quiet
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-.. ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cdfc1bc0-... ro quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cdfc... ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet


```

---

### Post by wariskampar on 2008-05-27
here is mine. look like grub still use 16

aznan@aznan-laptop:~$ cat /boot/grub/menu.lst
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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a3972a39-4b18-43b1-9848-f5788689ccbf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a3972a39-4b18-43b1-9848-f5788689ccbf ro pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Absorbed on 2008-05-27
I think I have the exact same problem. I installed the updates for linux-ubuntu-modules-2.6.24-17-generic, which synaptic shows as installed, yet my menu.lst didn't update as I foolishly chose to keep my menu.lst when it asked during the update. Now I would like to update my menu.lst.

This is what it boots to presently:
```
uname -r
2.6.24-16-generic

```

I tried installing startupmanager, but it didn't give an option to switch to the -17 kernel.

---

### Post by drs305 on 2008-05-27
For wariskampar and Absorbed,

If you run the following it may present you with a some questions. One will ask if you want to update your grub menu or keep what you have. If you select keep what you have, I believe you will end up with what you currently have - 17 installed on your machine but not used because you didn't update grub.

That is what I did originally, but I went back, did it again, and the next time told it to update the menu.lst  I believe the 'keep what you have' was the second option on the list (but default), and the 'update' option was the first. It did keep the options I had manually changed, such as number of kernels to display and menu timeout. The reason for that is that my choices were outside the section that is updated. 

But enough ... try running this and see if you are presented with the option to create a new menu.lst. 
Backup (or to keep the filename simple by changing to menu.lst.bak:
```
sudo cp /boot/grub/menu.lst /boot/grub/**menu.list-'date %F'**
```
Then:
```
sudo update-grub
```

If this doesn't work, we can cut & paste later...

---

### Post by AlfyBoy on 2008-06-04
Thats exactly what happened to me, when updating from 17-generic to 18-generic, I pressed continue, and grub never was updated. I tried ```



[HTML]update-grub[/HTML]

It gave back this:

[PHP]Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
Searching for GRUB installation directory ... found: /boot/grub
done[/PHP]

But when:

[CODE]cat /boot/grub/menu.lst
```


[PHP]## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet[/PHP]


18-generic is not there.

Is there a way to correct this?

---

### Post by drs305 on 2008-06-04
> **AlfyBoy said:**
> Thats exactly what happened to me, when updating from 17-generic to 18-generic, y pressed continue, and grub never was updated. Y tried ```



18-generic is not there.

Is there a way to correct this?

Before changing grub setings, it is good practice to make a backup. If you think you may be making mulitiple backups, put a number after .bak (i.e. menu.lst.bak1):
[CODE]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

According to the update, grub is aware kernel 18 is on your machine. To verifify this, you can open synaptic and do a search for 'linux-image-2.6.24-18-generic". It should show up with a green check box showing it is installed. If it's not, select and install it if you wish.

To check which version is currently running run:
```
uname -a
```

If kernel 18 is not running, and you want it to, open StartUp-Manager ( System > Administration > StartUp-Manager ). On the 'Default operating system' you can select any installed kernel version.

You can also go to the 'Advanced' tab and look at "Limit the number of kernels in the boot menu'. If it is listed as 1, and the previous entry was listed as 17, that explains why you don't see kernel 18 in the startup menu. Changing the default operating system to 18 or changing the kernel view to 2 should allow you to see the kernel 18 option on the boot menu if it is installed.

If you still don't see kernel 18 on boot, you can edit the grub menu (back it up first). Note that this should have been done by grub automatically.
```
gksudo gedit /boot/grub/menu.lst
```

Add the following lines just above the current kernel 17 entry. The added section is in **bold type**. The amended section should look like:
```

## ## End Default Options ##

[B]title        Ubuntu 8.04, kernel 2.6.24-18-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro quiet splash
initrd        /boot/initrd.img-2.6.24-18-generic
quiet
savedefault

title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro single
initrd        /boot/initrd.img-2.6.24-18-generic
[/B]

title        Ubuntu 8.04, kernel 2.6.24-17-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-generic
quiet
savedefault

title        Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=34278c0c-f28e-4cb6-8b23-e7ba7f368cb7 ro single
initrd        /boot/initrd.img-2.6.24-17-generic


```

Save and close the file and reboot.

---

### Post by Nessa on 2008-06-04
Just curious, does Update Manager usually include kernel updates?

---

### Post by PmDematagoda on 2008-06-04
> **Nessa said:**
> Just curious, does Update Manager usually include kernel updates?

Yes it does.

---

### Post by Bubba64 on 2008-06-04
On the subject of the 18 kernel I noticed my computer although downloaded it, the default boot was still 17. I realized startup manager in synaptic wasn't installed which does a number of functions including the amount of kernels shown at startup but also can change the default booting kernel.

---

### Post by AlfyBoy on 2008-06-04
Thanks!!

---

### Post by AlfyBoy on 2008-06-04
Thanks!!!

> **drs305 said:**
> 
If you still don't see kernel 18 on boot, you can edit the grub menu (back it up first). Note that this should have been done by grub automatically.

Everything is A OK now

I still wonder, why it wasn't done automatically after update-grub?

---

### Post by drs305 on 2008-06-04
> **AlfyBoy said:**
> Thanks!!!



Everything is A OK now

I still wonder, why it wasn't done automatically after update-grub?

After I replied to your post I booted up my laptop and found that it hadn't updated the menu.lst. It did automatically update on the computer on which I had written my reply. Same settings on both.  Go figure :rolleyes:

---

### Post by AaronMT on 2008-06-04
Updating it manually through menu.lst worked for me. Upon the update today I clicked retain same settings in my boot file as well.

---

