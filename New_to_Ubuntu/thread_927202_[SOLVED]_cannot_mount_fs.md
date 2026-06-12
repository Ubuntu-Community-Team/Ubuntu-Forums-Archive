---
title: "[SOLVED] cannot mount fs"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Chelives1928 on 2008-09-22
I had an installation of hardy that I was using and I wanted to upgrade to Intrepid.  I was upgrading and upon the restart I received that error message and it won't let me get to the desktop.  Right now I'm using the hardy live cd.  Here is the oput of fdisk and menu.lst and let me know if anyone can help me get back to my original hardy installation or fix whats going on.  I've looked on the forums and no one has really come up with an answer to my specific problem that has worked that's why i'm posting this again.


```

```# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-3-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro single

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu intrepid (development branch), memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1




Disk /dev/sda: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0xba07c583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       23190      442379   462784512    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e952e94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22585   181413981    7  HPFS/NTFS
/dev/sdb2           22586       22950     2931862+  82  Linux swap / Solaris
/dev/sdb3           22951       30401    59850157+  83  Linux

---

### Post by cariboo on 2008-09-22
It would be much easier for us to diagnose your problem if you let use know what the error message was. I'm assuming it was a grub error of some sort, as you posted the grub menu list. Alos it would help if you posted the output of:

```
sudo fdisk -l
```

Jim

---

### Post by Chelives1928 on 2008-09-22
> **cariboo907 said:**
> It would be much easier for us to diagnose your problem if you let use know what the error message was. I'm assuming it was a grub error of some sort, as you posted the grub menu list. Alos it would help if you posted the output of:

```
sudo fdisk -l
```

Jim


There it is....the exact message was "kernel panic VFS: unable to mount root fs on unknown-block (0,0) "




```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0xba07c583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       23190      442379   462784512    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e952e94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22585   181413981    7  HPFS/NTFS
/dev/sdb2           22586       22950     2931862+  82  Linux swap / Solaris
/dev/sdb3           22951       30401    59850157+  83  Linux

```

---

### Post by jemate18 on 2008-09-22
could you type and paste the output of 

> df -h

so we could see which partition fs is mounted to

---

### Post by jemate18 on 2008-09-22
```
title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
[COLOR="Red"]root (hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet

```

After the df -h command, may be we should change your
[COLOR="Red"]root (hd1,2)[/COLOR]

to other entry depending on the partition mounting

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> could you type and paste the output of 



so we could see which partition fs is mounted to




```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
tmpfs                 506M   32K  506M   1% /tmp
/dev/sdb3              57G   53G  1.3G  98% /media/disk
/dev/sda2             442G  429G   14G  97% /media/disk-1

```

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> ```
title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
[COLOR="Red"]root (hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet

```

After the df -h command, may be we should change your
[COLOR="Red"]root (hd1,2)[/COLOR]

to other entry depending on the partition mounting


I tried making changes to the menu.lst previously but it won't let me because of lack of permissions.  I'm usijng the live cd is there a way to get around this?

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
tmpfs                 506M   32K  506M   1% /tmp
/dev/sdb3              57G   53G  1.3G  98% /media/disk
/dev/sda2             442G  429G   14G  97% /media/disk-1

```

is this the complete output?

are there no entries for / and or /boot ?

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> is this the complete output?

are there no entries for / and or /boot ?




```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
tmpfs                 506M   32K  506M   1% /tmp
df: `/home/ubuntu/.gvfs': Transport endpoint is not connected
/dev/sdb3              57G   53G  1.3G  98% /media/disk
/dev/sda2             442G  429G   13G  98% /media/disk-1

```






This is all that shows up.

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> I tried making changes to the menu.lst previously but it won't let me because of lack of permissions.  I'm usijng the live cd is there a way to get around this?


Oh so permission...


Ok... once you have boot the live cd...

1. Open a terminal
2. df -h
3. locate the device on which / or /boot reside (suppose you have sda6 for /boot)
4. sudo mount /dev/sda6 /mnt
5. cd /mnt
6. cd boot/grub
7. sudo pico menu.lst
8. edit the file and save by typing CTRL + X

---

### Post by jemate18 on 2008-09-22
is /boot inside your /media/disk or /media/disk-1? if yes then do the device /dev/sda2 for the steps i gave you above

or is it in /dev/sdb3 ..... just find where /boot resides

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> Oh so permission...


Ok... once you have boot the live cd...

1. Open a terminal
2. df -h
3. locate the device on which / or /boot reside (suppose you have sda6 for /boot)
4. sudo mount /dev/sda6 /mnt
5. cd /mnt
6. cd boot/grub
7. sudo pico menu.lst
8. edit the file and save by typing CTRL + X




from what i've posted which one has the root and or boot?

---

### Post by Chelives1928 on 2008-09-22
i've found the folders root and boot in the media/disk

---

### Post by jemate18 on 2008-09-22
try /dev/sdb3 on the instruction I gave above

---

### Post by Chelives1928 on 2008-09-22
Okay i'm on the step where i open up the menu.lst in the terminal...what do i need to change?

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> Okay i'm on the step where i open up the menu.lst in the terminal...what do i need to change?

```
title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
[COLOR="Red"]root (hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet
```

You have to change root(hd1,2) 

hd1 means the second hard disk.... it starts with 0.

2 means the 3rd partition of that hardisk.... again it starts with 0

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> ```
title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
[COLOR="Red"]root (hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet
```

You have to change root(hd1,2) 

hd1 means the second hard disk.... it starts with 0.

2 means the 3rd partition of that hardisk.... again it starts with 0



So i'm going to go ahead and change the first entry to hd 1,1 since it's ont he second disk and there are only 2 partitions and its on the 2nd partition.  Now how do i save the menu.lst in the terminal?

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> So i'm going to go ahead and change the first entry to hd 1,1 since it's ont he second disk and there are only 2 partitions and its on the 2nd partition.  Now how do i save the menu.lst in the terminal?

If that's your setup.. then do it.......:) make sure that / resides on that partition since the code root(hd1,1) will look for your / (root) partition there......

to save it (if you use pico)

type CTRL o (hold CTRL then press o) for save

type CTRL x (hold CTRL then press x) for exit

---

### Post by Chelives1928 on 2008-09-22
No didn't work...I set it at 1,1 because in that folder was the original boot and root folders here is the disk i was looking at and changed the menu.lst to.



[[IMG]http://img87.imageshack.us/img87/5869/screenshotnr7.th.png[/IMG]](http://img87.imageshack.us/my.php?image=screenshotnr7.png)[[IMG]http://img87.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by jemate18 on 2008-09-22
can you paste the contents of /boot

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> can you paste the contents of /boot




[[IMG]http://img530.imageshack.us/img530/971/screenshot1zo5.th.png[/IMG]](http://img530.imageshack.us/my.php?image=screenshot1zo5.png)[[IMG]http://img530.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by jemate18 on 2008-09-22
> title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet

title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic (recovery mode)
root (hd1,2)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro single

on the first entry of your menu.lst is searching for
> kernel /boot/vmlinuz-2.6.27-3-generic

Ow... I know this will be another time consuming but have you tried
root(hd0,1) in your menu.lst ?

---

### Post by jemate18 on 2008-09-22
also i noticed, in the last picture you have posted...

there is a 
initrd.img.2.6.24-16-generic

and 
initrd.img.2.6.24-19-generic

but it doesnt have
[COLOR="Red"]initrd.img.2.6.27-3-generic[/COLOR]

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> on the first entry of your menu.lst is searching for


Ow... I know this will be another time consuming but have you tried
root(hd0,1) in your menu.lst ?

change it to 0,2?

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> also i noticed, in the last picture you have posted...

there is a 
initrd.img.2.6.24-16-generic

and 
initrd.img.2.6.24-19-generic

but it doesnt have
[COLOR="Red"]initrd.img.2.6.27-3-generic[/COLOR]


So what does that mean?  I'm  going to change it to 0,2 and tell you what happens.

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> So what does that mean?  I'm  going to change it to 0,2 and tell you what happens.

yes...

---

### Post by jemate18 on 2008-09-22
I also experienced your problem last three days... And so I shared what I did.......

I hope this helps you fix it..

---

### Post by Chelives1928 on 2008-09-22
Okay i changed the first entry and rebooted.  I got a message that said that the target drive doesn't exist.  I changed the entry from 1,2 to 0,2.

---

### Post by jemate18 on 2008-09-22
Well I think here is the problem...

since you have
initrd.img.2.6.24-16-generic

and
initrd.img.2.6.24-19-generic

but it doesnt have
initrd.img.2.6.27-3-generic


your new kernel which is the 2.6.27-3-generic fails to load because it is missing initrd.img.2.6.27-3-generic

---

### Post by jemate18 on 2008-09-22
Check this out.. In your menu.lst you have the 1st entry
> title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet
-> there is no initrd.......


and for the second entry 


> title Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
[COLOR="DarkRed"]initrd /boot/initrd.img-2.6.24-19-generic[/COLOR]
quiet


I think that is causing the problem.......

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> Check this out.. In your menu.lst you have the 1st entry

-> there is no initrd.......


and for the second entry 





I think that is causing the problem.......





So is there a way to solve the problem or do i have to re-install hardy?

---

### Post by jemate18 on 2008-09-22
So your new kernel is missing the initrd.....

This is what the initrd does
"This initrd image will contain the necessary modules (scsi, ext3, etc.) so you can mount your "real" root filesystem and then use pivot_root to replace the initrd root filesystem with the "real" root filesystem."

Upon looking back at your configuration/setup

You have two harddisk
sda (primary)

sdb (slave)
with partition

sdb2 
sdb3 (where root and boot resides)

therefore 

root(hd1,2) is correct( Im so sorry, I have mislooked it) 1 is your slave disk which is sdb and 2 is your third partition which contains root and boot

So if you are missing this initrd

you have to create it using command line tools.

Yes there is a way of solving it... but it includes a lot of command line works.....

Yes if you want you can reinstall HARDY...

OR you can try to eliminate the first TWO entries in your menu.lst so that the 3rd entry will be the default.... (I hope this works)

Remove this
> title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
quiet

title Ubuntu intrepid (development branch), kernel 2.6.27-3-generic (recovery mode)
root (hd1,2)
kernel /boot/vmlinuz-2.6.27-3-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro single

so that this will be the default
> title Ubuntu intrepid (development branch), kernel 2.6.24-19-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=ab5324ee-ba76-46d3-a7ab-db42886bdd50 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> So your new kernel is missing the initrd.....

This is what the initrd does
"This initrd image will contain the necessary modules (scsi, ext3, etc.) so you can mount your "real" root filesystem and then use pivot_root to replace the initrd root filesystem with the "real" root filesystem."

Upon looking back at your configuration/setup

You have two harddisk
sda (primary)

sdb (slave)
with partition

sdb2 
sdb3 (where root and boot resides)

therefore 

root(hd1,2) is correct( Im so sorry, I have mislooked it) 1 is your slave disk which is sdb and 2 is your third partition which contains root and boot

So if you are missing this initrd

you have to create it using command line tools.

Yes there is a way of solving it... but it includes a lot of command line works.....

Yes if you want you can reinstall HARDY...

OR you can try to eliminate the first TWO entries in your menu.lst so that the 3rd entry will be the default.... (I hope this works)

Remove this


so that this will be the default



okay and afterwards do i restart and try it out?

---

### Post by jemate18 on 2008-09-22
yes.... and I hope it works....

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> yes.... and I hope it works....


yeah me too   :)  thanks again for your help....brb

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> yes.... and I hope it works....


well sorry didn't work.  The changes showed up on the grub upon reboot but when I choose the first entry it began to load with the ubuntu splash screen and then afterwards it went to a  dialogue box that said something about being only able to load in low-graphics mode and that's where it hung up.  the mouse wouldn't move and i couldn't get passed that.

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> well sorry didn't work.  The changes showed up on the grub upon reboot but when I choose the first entry it began to load with the ubuntu splash screen and then afterwards it went to a  dialogue box that said something about being only able to load in low-graphics mode and that's where it hung up.  the mouse wouldn't move and i couldn't get passed that.

So the current kernel 2.....-19 kernel is ok since it began loading the splash screen... 
The trouble is somewhere I think in your packages.. When you have upgraded to Intrepid... The upgrade didnt go smoothly...... some packages where updated, and some where not. Therefore leaving other dependencies breaking...... So that explains why you didnt have the initrd for your new kernel Intrepid.... 

In your situation, it loads the current kernel perfectly(2.6......-19) however, the other dependencies broke and so it can't successfully log you and leaving your system hang

---

### Post by jemate18 on 2008-09-22
Just re install Hardy......

Sorry If I wasnt able to fix your problem.......

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> So the current kernel 2.....-19 kernel is ok since it began loading the splash screen... 
The trouble is somewhere I think in your packages.. When you have upgraded to Intrepid... The upgrade didnt go smoothly...... some packages where updated, and some where not. Therefore leaving other dependencies breaking...... So that explains why you didnt have the initrd for your new kernel Intrepid.... 

In your situation, it loads the current kernel perfectly(2.6......-19) however, the other dependencies broke and so it can't successfully log you and leaving your system hang


that makes sense...is there anyway to fix it?

---

### Post by jemate18 on 2008-09-22
> **Chelives1928 said:**
> that makes sense...is there anyway to fix it?

The best way is to reinstall your HARDY so that the packages will be in their default (initial state)....

Anyway... Your error problem is caused by an interrupted upgrade or an upgrade which didn't finished successfully.

---

### Post by Chelives1928 on 2008-09-22
> **jemate18 said:**
> The best way is to reinstall your HARDY so that the packages will be in their default (initial state)....

Anyway... Your error problem is caused by an interrupted upgrade or an upgrade which didn't finished successfully.


alrighty then...at least we figured out the problem...thanks for your help there.

---

### Post by jemate18 on 2008-09-22
In this experience WE BOTH LEARNED from trials and mistakes. I hope that others who view this post may also learn...

Thanks to all...

---

### Post by zobcat on 2008-10-30
I have this exact same problem. I came to the forums looking for a way to create my missing initrd.img file and found this thread. I ran the search with initrd in it. So every instance of initrd was bright red. It was fun watching them evade you guys for the short time that they did. Good work.

Anyway, I guess it must be a pain to create the file. Thanks for clearing things up.

---

