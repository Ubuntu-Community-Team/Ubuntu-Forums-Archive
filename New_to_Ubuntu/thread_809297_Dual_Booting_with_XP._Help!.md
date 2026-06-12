---
title: "Dual Booting with XP. Help!"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-05-27
Hey guys. I need some help. I have one physical unit where I ve installed ubuntu in one partition, and I later installed xp in another partition. My problem is that know my machine just boots straight to xp, without any option to boot in my pre-installed ubuntu system instead. HELPPPP!!!

---

### Post by dRock1286 on 2008-05-27
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by cdtech on 2008-05-27
You just need to install the GRUB bootloader into the MBR of your drive.

With the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,2) then you would enter root (hd0,2)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

Hope this helps.....

---

### Post by Jackfrost123 on 2008-05-27
Yeah, cdtech it helps a lot, thanks for the detailed advice haven't tried it yet, but it looks like it will solve my issues. You 're a champ.

Just one question, what about the supergrub program that the other user suggested. Any use in trying that too?

---

### Post by kansasnoob on 2008-05-27
You may find this tutorial helpful:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

That's the tutorial I used for my first dual boot and I managed to muddle my way through it.

The point you're at now, just pay special attention to the sections:
"Reinstall GRUB to the MBR", and "Modify the Boot Menu".

Hopefully the graphics in the tutorial might be helpful to you.

---

### Post by cdtech on 2008-05-27
> **Jackfrost123 said:**
> Yeah, cdtech it helps a lot, thanks for the detailed advice haven't tried it yet, but it looks like it will solve my issues. You 're a champ.

Just one question, what about the supergrub program that the other user suggested. Any use in trying that too?

I'm just trying to keep it simple for ya. Without having to learn about other software, just to get the grub working. The command line is your friend.

Your welcome....

---

### Post by Jackfrost123 on 2008-05-27
I get "error 17: cannot mount selected partition"

---

### Post by bumanie on 2008-05-27
Please post output of > cat /boot/grub/menu.lst and > sudo fdisk -l (That's a lower case L) You should aslo keep your eye on the post by spamzilla who is having similar issues. You should also look here for help with grub [http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by cdtech on 2008-05-27
> 17 : "Invalid device requested"

What method did you use?

---

### Post by Jackfrost123 on 2008-05-27
cdtech, You are quoting me correctly in terms of the no. 17 error, but I get "cannot mount selected partition" instead of "invalid device requested". And I used the method you suggested.

bumanie, here's what I get:

no such file or directory for the first command.

And for the second: (in my next post)

---

### Post by Jackfrost123 on 2008-05-27
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fae34c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4844    38909398+  83  Linux
/dev/sda2            4845        4971     1020127+  82  Linux swap / Solaris
/dev/sda3   *        4972        7296    18675562+   7  HPFS/NTFS

Disk /dev/sdb: 1027 MB, 1027603456 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         124      995998+   6  FAT16

---

### Post by Maestro23 on 2008-05-27
Nevermind.

---

### Post by Duck2006 on 2008-05-27
> **Jackfrost123 said:**
> ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fae34c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4844    38909398+  83  Linux
/dev/sda2            4845        4971     1020127+  82  Linux swap / Solaris
/dev/sda3   *        4972        7296    18675562+   7  HPFS/NTFS

Disk /dev/sdb: 1027 MB, 1027603456 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         124      995998+   6  FAT16

To setup grub from the live cd in the terminal type

sudo grub
find /boot/grub/menu.lst
root (hd0,0)
setup (hd0)
quit

Then add windoze to the menu.lst

#title		Windows NT/2000/XP
#root		(hd0,2)
#savedefault
#chainloader	+1

---

### Post by Jackfrost123 on 2008-05-27
duck, I am just trying out your way, it seems the first half worked ok, now I am trying to find menu.lst to add the lines you suggest. Problem is grub is not under /boot/grub but I find a grub directory in several places, namely, /rofs and /usr.

Ok i find one melu.lst under grub/examples/

And one grub-menu.lst

I am going to edit all, four, of them.

---

### Post by Jackfrost123 on 2008-05-27
ah... f$#$@ it... Its root and read only, so  I got to changer permissions in the terminal and I don't know how to do this. Can someone verify please that at least I am about to edit the right files?

---

### Post by Duck2006 on 2008-05-27
This 
#title Windows NT/2000/XP
#root (hd0,2)
#savedefault
#chainloader +1

should have looked like this

title Windows NT/2000/XP
root (hd0,2)
savedefault
chainloader +1

This should help with editing the file that belong to root.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Maestro23 on 2008-05-27
> **Jackfrost123 said:**
> ah... f$#$@ it... Its root and read only, so  I got to changer permissions in the terminal and I don't know how to do this. Can someone verify please that at least I am about to edit the right files?

Use **gksudo** to give you admin rights to edit the file.

> gksudo gedit /boot/grub/menu.lst

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo](https://help.ubuntu.com/community/RootSudo?highlight=(RootSudo))

---

### Post by Jackfrost123 on 2008-05-27
ok, after doing what I said I did, following the advice of another poster, nothing loads up at the moment, I get the same error message, and even ubuntu installation wont start.

//edit ok guys, great, letme try doing what you said, I am still  unclear though as to why grub is in these two directories I mentioned and which menu file is the correct one to edit, but I am going to go ahead and do it.

---

### Post by Jackfrost123 on 2008-05-27
Maestro,

I used your way to edit menu.lst, it opens up in an editor window, and when I add the code and try to save it, it gives me back "could not save the file /boot/grub/menu.lst unexpected error file not found"

I was kinda expecting that since I couldnt find the menu.lst file in such a directory...

---

### Post by Maestro23 on 2008-05-27
> **Jackfrost123 said:**
> Maestro,

I used your way to edit menu.lst, it opens up in an editor window, and when I add the code and try to save it, it gives me back "could not save the file /boot/grub/menu.lst unexpected error file not found"

I was kinda expecting that since I couldnt find the menu.lst file in such a directory...

Sorry Jack, I just went back thru the thread and saw that you were not even booted into Ubuntu yet.

---

### Post by Jackfrost123 on 2008-05-27
no probs man, I really appreciate the help anyway, and I like the community spirit a lot, it was high time I got rid of windows altogether to tell you the truth. I am 29 and I 've been using this piece of s h i t windows software since when I was 14, jesus christ...

Anyway, first I hope I sort out this one.

---

### Post by Jackfrost123 on 2008-05-27
guys, anyone?

---

### Post by Jackfrost123 on 2008-05-27
I managed to edit the menu.lst lines (found it wasn't looking at the /boot of the drive but of the usb pen drive, and used gksudo nautilus to edit the menu) but I still get Error 17: cannot mount selected partition....

Great I thought the error had to do with windows, but if selected windows boots a ok, instead I can't get to my ubuntu installation...ssshhhhsss...

---

### Post by kansasnoob on 2008-05-27
It's much, much easier to install Ubuntu after installing XP.

There's even a neat video:

[http://video.google.com/videoplay?docid=-6104490811311898236&q=](http://video.google.com/videoplay?docid=-6104490811311898236&q=)

But I learned with APC's guides:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

And I'm glad I took the time. Now every computer I own is dual booted (or more) and I've introduced nearly 40 other folks to Ubuntu or it's derivatives. Freespire and gOS made me take the first look since "Lindows" and I'm happy as a Humingbird that found a fresh flower!

Once you get past the initial learning curve it's great!

Although I still have trouble with the terminal and text based commands it's all worth learning!

---

### Post by Jackfrost123 on 2008-05-27
yeah but I d already installed and used ubuntu for quite some time...I guess I could re-install it but I wouldn't wont to mess this up too, and I already have my preferences and progs in the already installed version.

---

### Post by Jackfrost123 on 2008-05-28
bump. Anyone?

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-28
You know, if you're having trouble Dual booting with XP you could choose some of the other linux based kernels like Debian or Fedora like I am:D

---

### Post by bumanie on 2008-05-28
Hi Jack, could you post output of > cat /boot/grub/menu.lst as you have done some editing on it.

---

### Post by Jackfrost123 on 2008-05-28
since I am booting from the live cd (live usb pen drive to be exact) it outputs "no such file or directory" since I presume looks for the menu.lst in the usb not in the hd. And I don't know how to open a terminal for the hard disk.

//edit ah for god's sake, now I got to ask a question about the forum too? Well...I login in via my laptop and then it throws me out again so I can't post the output I got from my gksudo nautilus and editing the menu.lst. It just shows thank you for logging in and then asks me to login again. I even logged out from my other pc but still...what the...

I saved it to the network drive to paste it here, still can't login with laptop:

ok:

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
# kopt=root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title Windows NT/2000/XP
root (hd0,2)
savedefault
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by bumanie on 2008-05-28
You should be able to access the grub menu via a live cd/usb. I am on a windows computer (at work at present), so forgive me if I'm wrong, but I think this is the path, go to Places, double click on filesystems and open the drive ubuntu is installed on. You should see a boot file. Double click on it and you should see a grub file. Double click it and inside you should see a text file titled grub menu.lst. Open it and copy/paste the output to the forum. Hopefully from that and the output you provided earlier re your drive setup (fdisk -l), we'll hopefully be able to reinstall grub form the live cd/usb and get everything working again. Still may have to edit the /boot/grub/menu.lst via gksudo nautilus as you did yesterday, but need to see the list first. I guess, you could get the list via gksudo nautilus if you wish.
A good site to read about booting/grub issues is [here]("http://www.users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by bumanie on 2008-05-28
I have some instructions that I hope will work written out and will post later. Firstly, can you  boot into windows at all? I am wondering whether you need to fix windows mbr before tackling grub.

---

### Post by Jackfrost123 on 2008-05-28
thanks bumanie, yes I can presently boot into windows.

---

### Post by bumanie on 2008-05-28
Well, that's good. I think if you edit your /boot/grub/menu.lst as below, everything should work.

Firstly you need to change all the ubuntu entries to (hd0,0) because that is the partition ubuntu is installed to. I think you are getting the error 17 as a result of grub looking for ubuntu on (hd0,2) and finding xp there instead.
Also you  are missing an important line that breaks linux OSes from the non-linux OSes.
Under this line (bottom of the /boot/grub/menu.lst)
### END DEBIAN AUTOMAGIC KERNELS LIST
 you need to add this (Copy and paste to chainloader +1)

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3

title        Windows NT/2000/XP
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
chainloader    +1

Save the list and try rebooting.
I have added the map commands to try to make windows not worry that it is not on the first partition of the drive.
All being well, you should be able to boot into both OSes. Good Luck, I hope it works.

---

### Post by Jackfrost123 on 2008-05-28
Great, I am just testing it out.

//edit 1 Ok, bumanie I am posting you the last portion of menu.lst to see what changes I did based on  your code, I still get error 17 and cannot mount partition but I am able to see windows xp in the bootloading menu. Maybe I didn't do the correct changes you suggested.

//edit 2

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Windows NT/2000/XP
root (hd0,2)
savedefault
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3

title Windows NT/2000/XP
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
chainloader +1

---

### Post by bumanie on 2008-05-28
> **Jackfrost123 said:**
> Great, I am just testing it out.

//edit 1 Ok, bumanie I am posting you the last portion of menu.lst to see what changes I did based on  your code, I still get error 17 and cannot mount partition but I am able to see windows xp in the bootloading menu. Maybe I didn't do the correct changes you suggested.

//edit 2

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0eca8e32-1404-4347-956f-ad042f8080c2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

[COLOR="Red"]title Windows NT/2000/XP
root (hd0,2)
savedefault
chainloader +1[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3

title Windows NT/2000/XP
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)
chainloader +1

You have to get rid of the windows entry in red. Then save and try again. Sorry I may not have made that clear.

---

### Post by cdtech on 2008-05-28
Hey Jackfrost123, I see you still have some issues with your loader. I just got back from out of town.

Hey bumanie, he will still have to install the loader into the MBR of the primary drive.

Jackfrost123, if your booting into Windows and you can also see Ubuntu's GRUB  menu, how are you booting into Window's and able to see the GRUB bootloader? The reason I ask is that you can only have one MBR per drive.

If you can boot into the Live CD and bring up the desktop you can mount the partition that Ubuntu is on. Does this make sence to you?

---

### Post by Duck2006 on 2008-05-28
> map (hd0,0) (hd0,3)
map (hd0,3) (hd0,0)

No need to map the drive, windoze is already on the first drive.

---

### Post by Jackfrost123 on 2008-05-28
hey guys.

bumanie, I just what you said, will test it now.

cdtech, hey buddy. First I am given the option to press esc and see the bootloader (which is this menu that comes up I supppose where you choose either of three versions of ubuntu (normal, recovery, command (i think)) and one of xp. But in any case I get an error code and then the choice of os. I don't understand what your point is. The mbr must be what grub takes care of right?

Yes it does make sense your last sentence, that's where I am now, in the live cd, where the ubuntu install on the disk mounts automatically and that's how I edit the menu.lst. Maybe the confusion on your part is that the last you heard of me I couldnt even find menu.lst, but I have.

---

### Post by Jackfrost123 on 2008-05-28
Duck, should I remove these lines then?

SUCCESS. in parts at least, just loaded into ubuntu, but took me through a black screen with a lot of command options appearing and checked (i didn't have to do anything) which I don't remember happening other times, this happened just after the first graphical ubuntu screen.

OK. FAILURE. When I press esc to acess the boot menu and select xp, i get: :error 13, invalide or unsupported executable format.

Sigh....

---

### Post by cdtech on 2008-05-28
So if you get to the bootloader (GRUB) pressing "c" will put you at the grub prompt. That's where you do the find /####, and this gives you an error?

After you do the find then root then setup, grub finds all the OS available on your system for you, after that when you boot into Ubuntu you can edit your menu.lst for windows if needed.

---

### Post by Jackfrost123 on 2008-05-28
Cd tech, I will try doing what you just described.

Currently, I can boot into ubuntu, but when I try xp I get this error message: "error 13, invalide or unsupported executable format."

How can it be so hard to just get it to work...

---

### Post by Jackfrost123 on 2008-05-28
^^^^^^

---

### Post by Jackfrost123 on 2008-05-29
bump.

---

### Post by joshedmonds on 2008-05-29
Alright Jack, I see a lot of people are trying to help, but can we go right back to basics?

When you booted into Ubuntu using the liveCD this is what your drives were recognised as:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49fae34c

Device Boot Start End Blocks Id System
/dev/sda1 1 4844 38909398+ 83 Linux
/dev/sda2 4845 4971 1020127+ 82 Linux swap / Solaris
/dev/sda3 * 4972 7296 18675562+ 7 HPFS/NTFS

Disk /dev/sdb: 1027 MB, 1027603456 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 124 995998+ 6 FAT16
```

You have a 40 gig partition for Ubuntu, a 1 gig swap and 19 gig for Windows XP

You only have one hard drive, so this is hd0. Ubuntu is on (hd0,0) or sda1, swap is (hd0,1) or sda2 and Windows is (hd0,2) or sda3

When you installed Ubuntu, Grub was installed into the MBR at (hd0), and the file menu.lst that Grub reads was installed at (hd0,0)/boot/grub/menu.lst

The way that programs are organised in linux is not at all like Windows. If you find a file in a different directory e.g. /usr then that file's location is related to its function. Only the file at /boot/grub/menu.lst is the one Grub will read from

You need to mount the partition that Ubuntu is installed on, then open a terminal and type:

```
gksu nautilus
```

to open nautilus with root permissions. 

Find your mounted partition (probably under /mnt/disk or media/disk) and open the file /boot/grub/menu.lst

You posted a fairly convoluted menu.lst. In the terminal move to the directory containing the file and run this to back it up:

```
cp menu.lst menu.lst.bak
```

Now we can play with the file without worrying about all the good work done so far.

Copy and paste the following overwriting all the other options near the bottom of the file (remember you just backed up:)):

```
## ## End Default Options ##

title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro
initrd		/boot/initrd.img-2.6.24-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Home Edition
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

Don't worry about how much has been taken out, I am trying to make it easy for you to see how it works, you can go back and add memtest etcetera later. I've changed some things like the UUID to an sda so you can more easily troubleshoot, and removed some options that are unnecessary for right now - they should be added back when the problem is solved.

I'm not sure why some of the other options such as mapping were added in, but that may just be my lack of specialised knowledge of grub - for now leave them out.

I would also change a couple of options in the menu.lst file to help for now. Change

```
timeout 3
```

to

```
timeout 10
```

to give yourself more time, and comment out this line

```
hiddenmenu
```

like this

```
#hiddenmenu
```

so you see the menu without having to hit ESC

Save your menu.lst and reboot without the liveCD

It sounds like you don't need to reinstall Grub, as you boot into it at the moment, so let me know how you go

---

### Post by Jackfrost123 on 2008-05-29
hey josh, thanks for the great help buddy, I am reading through it at the moment. Again, thanks for taking the time, it's people like (and of course the other guys that have tried to help) that make it worthwhile.

//edit:
hey jonathan, a few things:

I learned gksudo, it seems gksu is the same thing? right? Strange for me from a dos background that one function has two names. Anyway I got the nautilus window with root priviledges ok ( let me first say I am using the ubuntu installation on the hd, not the usb key) but got this too as an error message in the terminal: 

"** (nautilus:6068): WARNING **: Unable to add monitor: Not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

When I copied and renamed menu.lst to menu.lst.bak in nautilus, the interface showed it as menu.lst~ the moment I renamed it, I supose this is some sort of convetion, that .bak files show up with a ~ in the end to denoto back ups.

Is everything under # a comment? and Why do some comment have double ##?

"It sounds like you don't need to reinstall Grub, as you boot into it at the moment, so let me know how you go"

I don't quite understand this...

Anyway buddy, I did what you said, and I'm rebooting. Let's go...

---

### Post by Jackfrost123 on 2008-05-29
WORKS LIKE A CHARM!!!

OMG!!! I CANT BELIEVE YOU 'VE FINALLY FIXED IT!

Although it does output quite a lot of stuff when entering ubuntu. I can't thank you enough buddy.

I got to run for work now but I ll be back in a couple of hours.

---

### Post by joshedmonds on 2008-05-29
Glad I could help.

Firstly, the number of hashes is irrelevant - as soon as you put one there the line is not executed, however it may help highlight section headings etc. If there is a convention relating to the number of hashes I'm more than happy to be corrected.

The reason you now see a lot of commands when booting is as a result of what I took out of your menu.lst

The words:

```
quiet splash
```

stop you seeing the startup scripts at work. 

The recovery mode that Ubuntu puts into your menu.lst is a boot mode without the quiet - you should put it back in so if you do have a problem when booting you can diagnose it.

This would be my suggested changes to menu.lst:

```

## ## End Default Options ##

# Ubuntu 8.04, kernel 2.6.24-16-generic
title		Ubuntu 8.04
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

# Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
title           Ubuntu 8.04 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

# Ubuntu 8.04 memtest86+
title           Ubuntu Memory Test
root            (hd0,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows XP Home Edition
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

I'm pretty sure it's correct, but hopefully you've now learnt enough about how Grub works to fix it otherwise :)

Before you put it in, you should probably create another backup file, using:

```
sudo cp menu.lst menu.lst.goodbak
```

or similar. I actually put the date into the filename of any file I backup because it's likely you'll end up doing it multiple times.

Please have a look through the threads for grub problems now you know what you're doing, and if possible help someone out (or even link to this thread if appropriate). The best way to maintain your skills and knowledge is a bit of practice.

---

### Post by kansasnoob on 2008-05-29
I've been following this thread and had no idea how to help. I'd long ago have said the heck with it and done a complete reinstall.

Therefore the reason for my thank you.

Jackfrost should jump to the front of the line for having a tenacious spirit also!

Kudos to all involved!

---

### Post by joshedmonds on 2008-05-29
Thanks. Few people have the time to give a customised answer, or explain why you do something (rather than paste this, type this).

As well as my 2 'real' computers running 8.04, I've been playing around with as many lightweight distros as I can find on an old PIII 450mhz, and the first thing you need to master is the bootloader or you'll be staring at the same distro forever!

As I said above, the best way to learn is to practice, so once I had it down pat on my machines, I've started searching out this type of problem (Grub appears but doesn't work properly) to increase the knowledge of the community as well as my own.

---

### Post by Premium_User on 2008-05-29
Very nice postings Josh!  I too have had problems with the menu.lst file in the past.

Nice to see someone able to reply with helpful information that can sum it up to make it look so simple.

Thanks again, I'm sure I'll be back to this thread for refrence one day. lol

---

### Post by Jackfrost123 on 2008-05-30
kansas, hey buddy! Well, to tell you the truth I can't believe I hung in there for a solution either, I got this close to dissing it all! But it was thanks to the help of the guys here that I didn't lose hope completely.

josh, you're the man here. Period.

This I am sure will function as a reference in the knowledge database of the community, I have used the search funtion countless times here for all sorts of issues before resorting to ask the question myself.

Ok, now that dual boot is sorte, let me get rid of windoze and get some serious os as a secondary os to ubuntu, like another linux distro...hehehehehe....

---

