---
title: "grub and triple boot"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Falc7 on 2008-05-20
Hi
I had a double boot, ubuntu and vista (for warranty purposes), but i wanted XP for gaming to, so i made an extra partition, installed XP. Grub disappeared, so i used the supergrub livecd to bring it back. However, when i click to load the vista partition, it loads, XP, and there is no option marked XP in grub. how can i sort this out?

edit: i know the vista partition is still there, i can see it here through ubuntu

---

### Post by Joeb454 on 2008-05-20
Ideally, you needed to install XP, Vista then Ubuntu (this is how I set my triple boot up).

Though you could reinstall the Vista bootloader (if you have a Vista disc) and use that, I think it *should* pick up the XP partition. Then reinstall Grub (again) so that when you choose Vista, it will then give the option of XP or Vista.

---

### Post by Falc7 on 2008-05-20
could i use that easy bcd thingy?

---

### Post by Joeb454 on 2008-05-20
Possibly, I don't know, you'd need to boot into Vista first to use it though, I think this is where your problem is :( Sadly I can't be any more help, sorry

---

### Post by Inxsible on 2008-05-20
Can you post the output of ```
sudo fdisk -l
```-l is lowercase L. Also post the output of ```
cat /etc/fstab
```

---

### Post by Falc7 on 2008-05-20
This first one:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x452f1e71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8725    70083154    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            8795        9433     5120000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9434       18595    73593765    5  Extended
/dev/sda4           18596       19457     6924015    7  HPFS/NTFS
/dev/sda5            9434       18216    70549416   83  Linux
/dev/sda6           18217       18595     3044286   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS



The 2nd one:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0a1abf59-5c2d-4cd0-adda-eaccdee267a9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9544d419-bbb7-4605-bbed-e61c43f74a55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Inxsible on 2008-05-20
Great, now post the output of ```
cat /boot/grub/menu.lst
``` This time please use the code tags. Its just easier to read that way.

You probably dont have any Windows installed in the 500Gig right?. Vista and XP are both installed in the 160Gig drive, correct ?

---

### Post by Falc7 on 2008-05-20
yep no OSs installed on the 500gb, all on the 160gb

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
# kopt=root=UUID=0a1abf59-5c2d-4cd0-adda-eaccdee267a9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0a1abf59-5c2d-4cd0-adda-eaccdee267a9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0a1abf59-5c2d-4cd0-adda-eaccdee267a9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
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
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by Inxsible on 2008-05-20
So you have two entries for Vista. I am assuming that one of them is XP. But I cant say which one.

Now, one of the OS is in sda3, correct? But that is an extended partition so you need to point to the logical partition beneath it which would be sda4 (since that's NTFS).

So in the [COLOR=Red]very last entry[/COLOR], change the```
root (hd0,2)
``` to ```
root (hd0,3)
``` See what it loads up. If it loads XP, then you can come back into Ubuntu and also change the header to Windows XP from Vista, just so that it is clearer.


If that doesn't work at all, post back and we can try something else.

---

### Post by Falc7 on 2008-05-20
How would i change the last entry? I am very unskilled with the terminal.
I have two vista entries even before i installed XP, i think one of them is a vista recovery manager or something, it came with the pc

thanks for your help :)

From looking in the partition manager, XP is on /sda2, and vista is on /sda 3 or 5, i am not sure, 3 seems to encompass 5 (as well as /sda6, the linux swap partition). And /sda4 is the recovery vista manager partition

---

### Post by jalirious on 2008-05-20
Hi, I have a triple boot xp-gutsy-hardy. Hardy was the last OS to be installed, as so has the menu.lst.

If I wipe the hardy partition how to I go about getting it to read from the gutsy menu.lst list to boot? 

I'm worried that if I wipe hardy I will have no way to boot into my other two partitions.

Cheers, Ben.

---

### Post by Inxsible on 2008-05-20
> **Falc7 said:**
> How would i change the last entry? I am very unskilled with the terminal.
I have two vista entries even before i installed XP, i think one of them is a vista recovery manager or something, it came with the pc

thanks for your help :)

From looking in the partition manager, XP is on /sda2, and vista is on /sda 3 or 5, i am not sure, 3 seems to encompass 5 (as well as /sda6, the linux swap partition). And /sda4 is the recovery vista manager partition
Great this is what I was looking for.

Ok. Starting from the top.

Open up a Terminal (Applications>>Accessories>>Terminal). Then type in ```
gksudo gedit /boot/grub/menu.lst
``` This will open up the file where you need to make changes.

Now in that file look at [COLOR=Red]the very last entry[/COLOR]. Change the following lines```
title        Windows Vista/Longhorn (loader)
root        (hd0,2)

``` to ```
title        Windows XP (loader)
root        (hd0,1)

```Save the file and then restart your computer and select "Windows XP". That should boot to XP and the other loader for Vista should load Vista.

---

### Post by Falc7 on 2008-05-21
@Jari, google supergrub
When i click the XP option from grub now, it says  NTLDR not found, and when i click the vista option is says error 12, invalid device requested.
I will give some more information that might help:

The end of that file says the following now:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

My partitions look like the following:
[http://img360.imageshack.us/my.php?image=screenshotdevsdagparteduw4.png](http://img360.imageshack.us/my.php?image=screenshotdevsdagparteduw4.png)

Last partition /sda4 is the vista recovery manager partition, /sda5 is vista, sda 2 is XP, ubuntu is /sda 1

---

### Post by bumanie on 2008-05-21
I have never done triple boot, but I believe you have to put the boot.ini files from xp into the vista bootlader, then you can install grub. Vista and xp have different bootloaders and although they recognise each other, they can't boot each other, that's why the boot files from xp need to get put with vista's boot files, this is assuming vista is on (hd0,0). After grub is installed, grub will see both of them. Alternatively as you previously asked, "can I use the bcd thingy?" , as far as I know, easybcd bootloader is meant to make triple booting fairly simple. It can be downloaded from [www.neosmart.com](www.neosmart.com) (I think). Good luck. Not sure how easybcd will work after all the changes you've made, but it's probably your best bet at present.
Another possibility is to make a separate grub partition and chainload the M$ OSes that way. instructions for that are [here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by Inxsible on 2008-05-21
> **Falc7 said:**
> @Jari, google supergrub
When i click the XP option from grub now, it says  NTLDR not found, and when i click the vista option is says error 12, invalid device requested.
I will give some more information that might help:

The end of that file says the following now:```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1

```My partitions look like the following:
[http://img360.imageshack.us/my.php?image=screenshotdevsdagparteduw4.png](http://img360.imageshack.us/my.php?image=screenshotdevsdagparteduw4.png)

Last partition /sda4 is the vista recovery manager partition, /sda5 is vista, sda 2 is XP, ubuntu is /sda 1If you are positive that sda5 is Vista, thn=en the entry for Vista should look like```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Windows Vista/Longhorn (loader)
root        (hd0,4)
savedefault
makeactive
chainloader    +1
```That should fix your Vista. Lemme see your image and get back to you about XP

---

### Post by Inxsible on 2008-05-21
After looking at your volume information, I am sorry to say, that I don't think you have Vista available. I see that you have a 67GB NTFS partition(sda1), a 5GB NTFS partition(sda2), and a 6.6 GB NTFS partition(sda4). The last two are too small to hold a Vista install. My Vista install (OEM) is about 27GB large.

Unless your Vista is in sda1, you have probably lost Vista. Also you have unallocated spaces between partitions. At this point of time, I would suggest you re-install everything. 

Start with XP, then Vista and then Ubuntu.

---

### Post by bumanie on 2008-05-21
> sudo apt-get install gparted and post screenshots of your drives please. From what I can see on fdisk -l there may be a vista or xp partition within the extended partition. As far as I know M$ OSes won't boot from within an extended partition. Also post the output of > sudo cfdisk I am not confident this will sort out your problems, but it worth a shot to look at these things.

---

### Post by Inxsible on 2008-05-21
> **bumanie said:**
> and post screenshots of your drives please. From what I can see on fdisk -l there may be a vista or xp partition within the extended partition. As far as I know M$ OSes won't boot from within an extended partition. Also post the output of  I am not confident this will sort out your problems, but it worth a shot to look at these things.
He already posted the screenshot about 3 posts up. Looks like he is in for a re-install. for atleast Vista or XP, coz I don't think either will fit into a 5 or 6.6 GB partition.

---

### Post by Falc7 on 2008-05-21
If vista was on /sda1, what code should be at the end of the /boot/grub/menu.lst file? 
I feel we are getting close to solving this.

I am quite sure vista is still here, i can still see all the vista program files through ubuntu, and i can copy files from my vista desktop onto my ubuntu desktop

In addition to the partitions you mentioned i also have large 67.28 partition (sda5), i also have the linux swap partition, 2.9 (sda6); which together make up /sda3, 70.18gb

I am starting to think vista is on /sda1, which is 66gb, and ubuntu is on the 67gb extended partition  /sda5
Perhaps it would have been easier to tell them apart if i had made them different sizes :)

---

### Post by Inxsible on 2008-05-21
If Vista was on sda1 and that's a big IF, the entry for Vista should read```
root (hd0,0)
```

---

### Post by Falc7 on 2008-05-21
It is very strange, i think you are right, i believe i might have over written vista with xp. When doing root (hd0,0), it brings up XP, and i can see all my vista files even though i am in XP. It seems i will have to reinstall everything

However, strangely, if you could take a look at this screen shot: [http://img403.imageshack.us/my.php?image=screenshot1bs6.png](http://img403.imageshack.us/my.php?image=screenshot1bs6.png)
the small partition i had intended for XP does have XP files in it. I can't understand why.

---

### Post by Inxsible on 2008-05-21
Can you post the output of ```
sudo fdisk -l
``` -l is lowercase L

---

### Post by Falc7 on 2008-05-21
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x452f1e71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8725    70083154    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            8795        9433     5120000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9434       18595    73593765    5  Extended
/dev/sda4           18596       19457     6924015    7  HPFS/NTFS
/dev/sda5            9434       18216    70549416   83  Linux
/dev/sda6           18217       18595     3044286   82  Linux swap / Solaris

```

Out of curiosity for how ubuntu works, how do you know what root(hdnumber,number) it should be from knowing which partition you are aiming at?

---

### Post by Inxsible on 2008-05-21
(hdX,*) - X = drive number & * = partition number  so sda = hd0  sda1 = hd0,0 sda2 = hd0,1 and so on. Note that the partition numbering starts from 0 as opposed to 1

---

### Post by Inxsible on 2008-05-21
Now you have 3 NTFS partitions. I would advise you to try them all out and see if you can login into XP and Vista or atleast one of them.  In the menu.lst try out these settings  ```
root (hd0,0)
```If that boots to something... note down what it booted to (XP or Vista)  Then try```
root (hd0,1)
``` and lastly```
root (hd0,5)
```If any of the two - i.e XP or Vista doesnt boot up after all those then you may have to re-install that OS.

---

### Post by Falc7 on 2008-05-21
edit:reading instructions....didn't see your post

edit2: will do that now

---

### Post by Inxsible on 2008-05-21
> **Falc7 said:**
> Should I just put it down as a lost cause and install all the three in the right order (XP, Vista, Ubuntu)

That would be best. I would also advise you to re-create the partitions and not leave unallocated space in between. You are wasting 585 MB between sda1 and sda2

---

### Post by meierfra. on 2008-05-21
You don't need to reinstall.  Your only problem is that XP overwrote the Vista Boot loader.  You can fix the Vista Boot Loader with EasyBCD (see my signature)

---

### Post by meierfra. on 2008-05-21
This is a better link:

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista")

---

### Post by Falc7 on 2008-05-21
I can try that then, can't hurt
If i use easyBCD, will is also let me log into ubuntu? Will i still be using grub?

Also,
with hd0,0= XP
hd0,1= NTLDR is missing
hd0,5= error 12, invalid choice is requested

---

### Post by meierfra. on 2008-05-21
> Also,
with hd0,0= XP
hd0,1= NTLDR is missing
hd0,5= error 12, invalid choice is requested

That is exactly what I would expect in your situation:

Windows always installs its boot information on a primary partition. XP is to dumb to recognize Vista, so it install its booting information onto (hd0,0), overwriting the Vista boot information.  Also Chainloading (hd0,0) will boot XP.

(hd0,1) contains no boot information, giving NTLDR is missing.


Grub cannot make  a logical partition active and  so returns "invalid choice" then you use "root (hd0,5), makeactive". You could leave out the makeactive, but (hd0,5) does not contain any boot information, so you still would get "NTLDR missing" or some other error. 


> If i use easyBCD, will is also let me log into ubuntu? Will i still be using grub?

EasyBCD will let you add Ubuntu to its boot menu.

But after EasyBCD fixed the Vista boot loader, you can also reinstall grub to the MBR.  "root (hd0,0), chainloader +1" will bring up the Vista Boot menu, which will contain Vista and XP.

---

### Post by Falc7 on 2008-05-22
great it has worked exactly as you said. Thanks both of you

---

