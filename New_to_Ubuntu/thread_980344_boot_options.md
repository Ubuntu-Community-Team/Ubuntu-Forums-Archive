---
title: "boot options"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by chazn85 on 2008-11-12
hi all,

so ive installed vista after my ubuntu partition i can boot into ubuntu but currently i have 

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title 			VISTA
root			(sd0,0)
makeactive
chainloader +1

but it wont boot the vista partiton

any ideas

thanks

---

### Post by bumanie on 2008-11-12
Post output of > sudo fdisk -luAlso the entry for vista should be (hdx,x) grub still uses "H" to denote hard drives.

---

### Post by chazn85 on 2008-11-12
here is the output 


Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ab2ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   625139711   312568832    7  HPFS/NTFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3af0f4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   195318269    97659103+  83  Linux
/dev/sdf2   *   195318270   585938744   195310237+  83  Linux
/dev/sdf3       585938745   601586054     7823655   82  Linux swap / Solaris

---

### Post by chazn85 on 2008-11-12
for exmaple if i replace the (sd0,0) with (hd0,1) i get an invalif executable format

---

### Post by bumanie on 2008-11-12
How many hard drives have you got? Vista is sde and ubuntu sdf. Also please post output of > cat /boot/grub/menu.lst

---

### Post by chazn85 on 2008-11-12
output below

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
# kopt=root=UUID=fff6cc3a-9423-4837-aca5-e9947ab217cf ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fff6cc3a-9423-4837-aca5-e9947ab217cf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fff6cc3a-9423-4837-aca5-e9947ab217cf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fff6cc3a-9423-4837-aca5-e9947ab217cf ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fff6cc3a-9423-4837-aca5-e9947ab217cf ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

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
#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic 32 BIT (on /dev/sdb1)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00fe8fab-6d76-450c-b7a1-69c22338d38c ro quiet splash 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
#title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00fe8fab-6d76-450c-b7a1-69c22338d38c ro single 
#initrd		/boot/initrd.img-2.6.24-19-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title 			VISTA
root			(hd0,1)
makeactive
chainloader +1
chaz@chaz-desktop2:~$ 




i have 2 hard drives in answer to your question

thanks

---

### Post by bumanie on 2008-11-12
i am confused as to why the fdisk readout has two drives as sde and sdf. Technically, accepting those as 'being true' you should have (hd4,0) for vista and (hd5,0), but your boot/grub/menu.lst is calling the vista drive sda and ubuntu sdb (which sounds more correct). 
Sorry I have to go, but I just noticed that your UUID number has also changed - have you recently added a hard drive? Please output > sudo blkid. I apologise for not having time to follow this through, but with changed UUID numbers and the 'odd' drive designations, this will take a while to sort out and i have an appointment in 40 minutes. Don't worry there are plenty on the forums who can help. I will check back later and see how you went. In the meantime checkout [this]("http://users.bigpond.net.au/hermanzone/p15.htm"), it is a great guide to grub. Again sorry, I can't stay any longer.

---

### Post by chazn85 on 2008-11-12
my sudo gparted shows that sda1 is vista and sdb1 is ubuntu does that help anyone

---

### Post by chazn85 on 2008-11-12
and the output of sudo blkid is 

/dev/sda1: UUID="327AF9527AF91379" TYPE="ntfs" 
/dev/sdb1: UUID="fff6cc3a-9423-4837-aca5-e9947ab217cf" TYPE="reiserfs" 
/dev/sdb2: UUID="e8cc2626-12c7-4ae4-a91a-b05ddaa86383" TYPE="reiserfs" 
/dev/sdb3: TYPE="swap" UUID="988720c6-31ab-4a77-805e-9384e68789d8"

---

### Post by shacristo on 2008-11-12
I believe your Vista line should have

```
root (hd0,0)
```

I am a little confused as to why your grub menu lists two different Ubuntu installations on different drives.

---

### Post by chazn85 on 2008-11-12
> **shacristo said:**
> I believe your Vista line should have

```
root (hd0,0)
```

I am a little confused as to why your grub menu lists two different Ubuntu installations on different drives.

possibly as i used to have 32 bit ubuntu on the other drive until i installed vista

---

### Post by shacristo on 2008-11-12
Ah, well then it looks like grub has your drives out of order for some reason and Vista will probably need to boot to (hd1,0).  Let me know if that works.

---

### Post by chazn85 on 2008-11-12
no this time i got a parser error while trying to boot to vista

---

### Post by pastalavista on 2008-11-12
I would backup menu.lst and reboot with a [supergrub disk]("http://www.supergrubdisk.org/") and see what it makes of it. It's a pretty smart application.

---

### Post by caljohnsmith on 2008-11-12
I think I might see the problem; when you posted the fdisk output in your post #3, was that the full output? Because it only shows drives sde and sdf. Do you also have drives sda, sdb, sdc, and sdd? If you do, that's unfortunately why the previous suggestions haven't worked. How about posting the full output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by chazn85 on 2008-11-13
No i only have these two drives no sda, b etc.  

output of fdisk -lu is 

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ab2ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   625139711   312568832    7  HPFS/NTFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3af0f4e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   195318269    97659103+  83  Linux
/dev/sdf2   *   195318270   585938744   195310237+  83  Linux
/dev/sdf3       585938745   601586054     7823655   82  Linux swap / Solaris

both drives returns GRUB so the output of that is

for sde

8100

and sdf

ff00

Thanks

---

### Post by caljohnsmith on 2008-11-13
Since your Ubuntu Grub entries use (hd0,0), it looks like you are booting off your Ubuntu drive on start up. So first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Vista entry with:
```
title Windows Vista
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
```
Give that a shot and let me know how it goes, or what exactly happens if you run into problems.

---

### Post by chazn85 on 2008-11-13
That worked an absolute treat 

Thanks you have saved me a lot of hassle there!!

---

### Post by caljohnsmith on 2008-11-13
I'm really glad to hear it worked OK; cheers and have fun with Ubuntu. :)

---

