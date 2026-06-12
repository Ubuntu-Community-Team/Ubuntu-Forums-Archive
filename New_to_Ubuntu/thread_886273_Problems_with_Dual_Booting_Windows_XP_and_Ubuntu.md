---
title: "Problems with Dual Booting Windows XP and Ubuntu"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-11
Hello.  I have run into some problems dual booting Ubuntu 8.04 with Windows XP.  GRUB does not show up at boot time.  Please tell me if I need to give you more information or what I should do.

My boot.ini is as follows

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

Disk Management Screenshot:

[[IMG]http://img388.imageshack.us/img388/8169/screenshotmx5.th.gif[/IMG]](http://img388.imageshack.us/my.php?image=screenshotmx5.gif)

Not sure if this applies, but there is some sort of error in my hard disk:
[[IMG]http://img514.imageshack.us/img514/3158/screenshot2np9.th.gif[/IMG]](http://img514.imageshack.us/my.php?image=screenshot2np9.gif)

---

### Post by hellodoggie on 2008-08-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8a0e8a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13637   109539171    7  HPFS/NTFS
/dev/sda2           13638       26692   104864287+   5  Extended
/dev/sda5           13638       26692   104864252+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x165d12b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20669   166023711    7  HPFS/NTFS
/dev/sdb2           20670       24321    29334690    f  W95 Ext'd (LBA)
/dev/sdb5           20670       24165    28081588+  83  Linux
/dev/sdb6           24166       24321     1253038+  82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xae920fdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      238202   120053776+   7  HPFS/NTFS

---

### Post by BGFG on 2008-08-11
Hi,
How did you install Ubuntu ? Through windows or did you boot into the Live cd? also, Is ubuntu on a different drive or a partition you created ?

---

### Post by hellodoggie on 2008-08-11
Menu.lst from boot/grub

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
# kopt=root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by BGFG on 2008-08-11
in the ubuntu Installation, did an option come up asking you if you wanted to add grub to the xp bootloader ?

---

### Post by hellodoggie on 2008-08-11
> **BGFG said:**
> Hi,
How did you install Ubuntu ? Through windows or did you boot into the Live cd? also, Is ubuntu on a different drive or a partition you created ?

Plopped in the Live CD and choose the 'Install Ubuntu' option.  Ubuntu is on a partition I created (see above image).](*,)

---

### Post by hellodoggie on 2008-08-11
Tried Start-up manager, but it doesn't work.

---

### Post by hellodoggie on 2008-08-11
> **BGFG said:**
> in the ubuntu Installation, did an option come up asking you if you wanted to add grub to the xp bootloader ?
The answer is 'no'

---

### Post by Living2007 on 2008-08-11
Well, Grub must have been installed. BTW what error number do you get when Grub tries to load?

---

### Post by kansasnoob on 2008-08-11
OK, look:

> /dev/sdb1 * 1 20669 166023711 7 HPFS/NTFS
/dev/sdb2 20670 24321 29334690 f W95 Ext'd (LBA)
/dev/sdb5 20670 24165 28081588+ 83 Linux
/dev/sdb6 24166 24321 1253038+ 82 Linux swap / Solaris


Now in Linux talk basically sda = drive #1, sdb = drive #2, sdc = drive #3, etc. In Grub talk, because GRUB starts with #0, sda = hd(0,x), sdb = hd(1,x) etc. (x = partition #). Clear as mud:confused:

So Ubuntu is on sdb or hd(1,x) .............. now which partition?

Well it's on sdb5 so you should be booting hd(1,4) whereas your menu list shows hd(2,4), but we,re still only part way there, hold on and let me look up something in my notes, and please run this by a few others here first since I could be asleep at the wheel!

---

### Post by Living2007 on 2008-08-11
> **kansasnoob said:**
> OK, look:

Now in Linux talk basically sda = drive #1, sdb = drive #2, sdc = drive #3, etc. In Grub talk, because GRUB starts with #0, sda = hd(0,x), sdb = hd(1,x) etc. (x = partition #). Clear as mud:confused:

So Ubuntu is on sdb or hd(1,x) .............. now which partition?

Well it's on sdb5 so you should be booting hd(1,4) whereas your menu list shows hd(2,4), but we,re still only part way there, hold on and let me look up something in my notes, and please run this by a few others here first since I could be asleep at the wheel!
And the answer should be
[SIZE=5]"[/SIZE][SIZE=5]hd(1,5)"[/SIZE]
If not try
[SIZE=5]"hd(1,3)"[/SIZE]

---

### Post by kansasnoob on 2008-08-11
OK, I think, you need to enter the GRUB configuration mode by first booting into Live CD mode (run with no changes) and:

```
sudo grub
```

then press Enter. 

Then type in the following commands in sequence:
- root (hd1,4)
- setup (hd1)
- quit
- exit 

I really wish someone else could double check me before you tried this though!

And I still have to figure out the changes to the Windows entry in the menu list.

---

### Post by kansasnoob on 2008-08-11
> **Living2007 said:**
> And the answer should be
[SIZE=5]"[/SIZE][SIZE=5]hd(1,5)"[/SIZE]
If not try
[SIZE=5]"hd(1,3)"[/SIZE]


Why would sdb5 be anything other than hd(1,4)?

---

### Post by Living2007 on 2008-08-11
I can't remember if hd(1,0) resorts to the first partition

---

### Post by kansasnoob on 2008-08-11
> **Living2007 said:**
> I can't remember if hd(1,0) resorts to the first partition

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by kansasnoob on 2008-08-11
If I'm right so far, and I'd give that about a 90% chance, then XP is on sdb1 which means GRUB sees it as hd(1,0), so the lines of the menu list that say:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

Should just say:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows XP
root (hd1,0)
makeactive
chainloader +1 

Rather than removing the entire old text you could just comment out the unwanted lines like:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
# title Microsoft Windows XP Professional
# root (hd2,0)
# savedefault
# makeactive
# map (hd0) (hd2)
# map (hd2) (hd0)
# chainloader +1

I'd also do that for the unneeded Vista entry just above that. 

Oh, and since I didn't mention it, to do all of this first reboot into Ubuntu (not the Live CD) ............. hey you'll know if I was right so far or not ............. and then:

```
sudo gedit /boot/grub/menu.lst
```

Remember to save and quit before closing the text editor!

Oh, and if you haven't already please create a backup of your menu list.

Again, I really wish someone else could double check me on this!

---

### Post by caljohnsmith on 2008-08-11
Please correct me if I'm wrong, but according to Hellodoggie's fdisk output, he has bootable NTFS partitions on all three HDDs:
```
sda1
sdb1
sdc1
```
According to the screen shot he provided, he wants to boot the Win XP that is on sdc1. Now if Grub sees the order of his HDDs as the same as BIOS does, his Win XP entry in grub would then use (hd2,0). But unfortunately Grub does not always see HDDs in the same order as his BIOS, so he may have to use a different entry. 

But in his first post, Hellodoggie said he wasn't even able to get to Grub at startup. Therefore, I think the first thing he should do would be to check that Grub is installed to the MBR of his Ubuntu HDD, and then tweak his BIOS to make sure that the Ubuntu HDD is the first in the boot order.

To make sure Grub is installed to the MBR of his Ubuntu HDD:
```
sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> exit
```
Once he gets Grub loading properly, we can help him tweak his menu.lst to load Win XP.

---

### Post by hellodoggie on 2008-08-11
I don't get any error number.  Grub doesn't load at all.

---

### Post by hellodoggie on 2008-08-11
Okay, I see the grub boot loader now
but when I press 'ubuntu 8.04, kernel 2.6.24-16-generic'
I get Error 21: Selected disk does not exist press any key to continue.

:):)

> **caljohnsmith said:**
> Please correct me if I'm wrong, but according to Hellodoggie's fdisk output, he has bootable NTFS partitions on all three HDDs:
```
sda1
sdb1
sdc1
```
According to the screen shot he provided, he wants to boot the Win XP that is on sdc1. Now if Grub sees the order of his HDDs as the same as BIOS does, his Win XP entry in grub would then use (hd2,0). But unfortunately Grub does not always see HDDs in the same order as his BIOS, so he may have to use a different entry. 

But in his first post, Hellodoggie said he wasn't even able to get to Grub at startup. Therefore, I think the first thing he should do would be to check that Grub is installed to the MBR of his Ubuntu HDD, and then tweak his BIOS to make sure that the Ubuntu HDD is the first in the boot order.

To make sure Grub is installed to the MBR of his Ubuntu HDD:
```
sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> exit
```
Once he gets Grub loading properly, we can help him tweak his menu.lst to load Win XP.

---

### Post by hellodoggie on 2008-08-11
btw how I got it to work was to follow caljohnsmith's instruction:

sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

---

### Post by kansasnoob on 2008-08-11
> **hellodoggie said:**
> btw how I got it to work was to follow caljohnsmith's instruction:

sudo grub
grub> find /boot/grub/stage1
[should return a partition in the form of (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> exit

Awesome, be sure and give him a thanks and mark the thread solved!

---

### Post by hellodoggie on 2008-08-11
> **kansasnoob said:**
> Awesome, be sure and give him a thanks and mark the thread solved!

I still have some problem getting into ubuntu:

Okay, I see the grub boot loader now
but when I press 'ubuntu 8.04, kernel 2.6.24-16-generic'
I get Error 21: Selected disk does not exist press any key to continue.

---

### Post by caljohnsmith on 2008-08-11
Hellodoggie, just modify your menu.lst so that the Ubuntu entries have the same (hdX,Y) reference as what you got when you did that "find /boot/grub/stage1". In other words, if "find /boot/grub/stage1" returned (hd1,4) which is most likely, then that is what you would need in menu.lst:
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
[COLOR="Blue"]root (hd1,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```
Just be sure to use whatever "find /boot/grub/stage1" returned, and I believe that should work.

---

### Post by hellodoggie on 2008-08-11
Hello

I am still getting an error:

but when I press 'ubuntu 8.04, kernel 2.6.24-16-generic'
I get Error 21: Selected disk does not exist press any key to continue.

I have already changed the line to hd(1,4)

---

### Post by hellodoggie on 2008-08-11
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by caljohnsmith on 2008-08-11
Hellodoggie, when you do:
```
sudo grub
grub> find /boot/grub/stage1
```
Does it return (hd1,4) or something else? If it returns (hd1,4), then I'm not sure yet why you would be getting a Grub error 21 when you use that in your Ubuntu Grub entry.

Your fdisk output says your Ubuntu partition is on /dev/sdb5, which is (hd1,4) in Grub's Convoluted World, but the problem is that Grub may not see the order of your HDDs the same as your BIOS or fdisk. That's why it is important to use the command above to find your Ubuntu partition.

---

### Post by hellodoggie on 2008-08-11
It does return hd(1,4)

> **caljohnsmith said:**
> Hellodoggie, when you do:
```
sudo grub
grub> find /boot/grub/stage1
```
Does it return (hd1,4) or something else? If it returns (hd1,4), then I'm not sure yet why you would be getting a Grub error 21 when you use that in your Ubuntu Grub entry.

Your fdisk output says your Ubuntu partition is on /dev/sdb5, which is (hd1,4) in Grub's Convoluted World, but the problem is that Grub may not see the order of your HDDs the same as your BIOS or fdisk. That's why it is important to use the command above to find your Ubuntu partition.

---

### Post by hellodoggie on 2008-08-11
> **hellodoggie said:**
> It does return hd(1,4)

hmm...interesting.  It now returns hd(2,4)

---

### Post by caljohnsmith on 2008-08-11
OK, let's do a few sanity checks first, please post the output of:
```
sudo blkid -c /dev/null
ls /boot
```
And also post the output of: 
```
sudo grub
grub> find /boot/vmlinuz-2.6.24-16-generic
```

---

### Post by hellodoggie on 2008-08-11
:(:(:(:(:(

OK....this is getting weird
it was returning hd(1,4), then hd(2,4)
and I keep getting disk not found?

---

### Post by hellodoggie on 2008-08-11
> **caljohnsmith said:**
> OK, let's do a few sanity checks first, please post the output of:
```
sudo blkid -c /dev/null
ls /boot
```
And also post the output of: 
```
sudo grub
grub> find /boot/vmlinuz-2.6.24-16-generic
```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="0A38CAE438CACDBF" LABEL="backup" TYPE="ntfs" 
/dev/sdb1: UUID="3E34EA2A34E9E53D" TYPE="ntfs" 
/dev/sdb5: UUID="12425770DD201679" LABEL="Games" TYPE="ntfs" 
/dev/sdc1: UUID="42241D2C241D2487" TYPE="ntfs" 
/dev/sdc5: UUID="a5a07b74-e877-446f-a992-fbc280a59ff5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc6: UUID="d272c2a9-323c-49ff-aa73-02d7b06aa0e8" TYPE="swap" 
/dev/sdd2: LABEL="MATTHEW'S I" UUID="A244-F602" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 

ubuntu@ubuntu:~$ ls /boot
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-16-generic



       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/vmlinuz-2.6.24-16-generic 
 (hd2,4)

---

### Post by hellodoggie on 2008-08-11
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

Does this mean anything important?

---

### Post by caljohnsmith on 2008-08-11
Hellodoggie, are you changing your BIOS settings or something? In your post #2, fdisk clearly shows your Ubuntu is on /dev/sdb5. Yet your blkid output from your last post shows Linux is now on /dev/sdc5. 

Did you change anything between the time when "find /boot/grub/stage1" returned (hd1,4), and then when it returned (hd2,4)? If you didn't change your BIOS boot sequence or something, then you may have some sort of hardware issues at this point.

Anyway, try changing your Ubuntu menu entries in menu.lst to use (hd2,4) instead of (hd1,4) and see if that works.

---

### Post by hellodoggie on 2008-08-11
Ok.  I think I know what is happening.

I plugged in my IPod for charging.  That must be what is changing things.

---

### Post by hellodoggie on 2008-08-12
help anyone?

---

### Post by appi2012 on 2008-08-12
This page has great information on grub errors: It explains exactly why there is an error.
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

Also, what does:
```
sudo grub
```
```
find /boot/grub/stage2
```
return?

---

### Post by appi2012 on 2008-08-12
Make sure all your hard disks are connected. Also, you might want to install grub onto your main hard disk.

---

### Post by caljohnsmith on 2008-08-12
Did you try my previous suggestion of using (hd2,4), Hellodoggie? At this point, how about putting *both* instances of (hd1,4) and (hd2,4) in your menu.lst, because it looks like your Ipod is interfering with the drive order of the HDDs. If you have both instances in your menu.lst, one of them should work, and then it won't matter whether you Ipod is connected or not. In other words, in your menu.lst it would look like:
```
title Ubuntu 8.04, kernel 2.6.24-16-generic (hd1,4)
root [COLOR="Blue"](hd1,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (hd2,4)
root [COLOR="Blue"](hd2,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

---

### Post by hellodoggie on 2008-08-12
> **appi2012 said:**
> This page has great information on grub errors: It explains exactly why there is an error.
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

Also, what does:
```
sudo grub
```
```
find /boot/grub/stage2
```
return?

(hd1,4)

---

### Post by hellodoggie on 2008-08-12
> **appi2012 said:**
> Make sure all your hard disks are connected. Also, you might want to install grub onto your main hard disk.

How do you do this?

---

### Post by sandysandy on 2008-08-12
see here

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by hellodoggie on 2008-08-12
> **caljohnsmith said:**
> Did you try my previous suggestion of using (hd2,4), Hellodoggie? At this point, how about putting *both* instances of (hd1,4) and (hd2,4) in your menu.lst, because it looks like your Ipod is interfering with the drive order of the HDDs. If you have both instances in your menu.lst, one of them should work, and then it won't matter whether you Ipod is connected or not. In other words, in your menu.lst it would look like:
```
title Ubuntu 8.04, kernel 2.6.24-16-generic (hd1,4)
root [COLOR="Blue"](hd1,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (hd2,4)
root [COLOR="Blue"](hd2,4)[/COLOR]
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a5a07b74-e877-446f-a992-fbc280a59ff5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

still getting error 21

---

### Post by hellodoggie on 2008-08-12
hmm...I am now getting error 22: no such partition

I also notice that when it boots it says Grub stage1.5
does that mean something important?

---

### Post by hellodoggie on 2008-08-13
ok....
so I think the final word in this post is that things are not working well.
I am trying to restore the original windows xp boot sequence using fixmbr
I will be deleting the linux installation.

Later I will try installing vista and dual booting with that instead.  Maybe that will work better.

---

### Post by hellodoggie on 2008-08-14
jay73 solved my problem. here is his post (it is very informative):
[http://www.linuxquestions.org/questions/linux-newbie-8/problems-dual-booting-windows-xp-and-ubuntu-8.04-662615/?posted=1#post3246849](http://www.linuxquestions.org/questions/linux-newbie-8/problems-dual-booting-windows-xp-and-ubuntu-8.04-662615/?posted=1#post3246849)

Right, when grub comes up, select the line for Ubuntu and press E. Select the line that goes root(hdx,x) and press E again. Remove the two characters after the comma and hit the tab key. This will show the partitions on the hd that GRUB has been told to look on. If you don't see any linux partition, then clearly grub has the wrong information. In that case, press ESC and try the same trick, only you now try a different number for the hd. For example, if you tried hd(2 TAB then you should also try hd(1TAB and /or hd(0 TAB. Write down the details of your linux partition as soon as you find it (number of the hd and number(s) of thepartition(s)). Use the information to correct the root(hdx,x) line. When you are done, press b to boot. As soon as you manage to get in (or at least before you reboot/shut down), go into the boot/grub directory and edit your menu.lst to show the correct information.

---

