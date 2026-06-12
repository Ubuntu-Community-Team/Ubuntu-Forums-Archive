---
title: "Autochk Program Not Found - SKIPPING AUTOCHK"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by BostonBigGuy on 2008-08-16
[b]yep it's me again ... I found or was directed to a link to make a bootable disc so i would be able to unhide the partition that has been hidden by ubuntu when i installed it.

Now here is my problem ... My laptop (dell) doesn't have a floppy disk drive ... Only a cd drive ... Any other suggestions would be very helpful ... Going on for a while and just like to get my laptop back up and running again ...

I'm able to load live/cd and able to see all my files but can't get into the dos program to unhide the partation ...

Please direct or explain to me step by step on how to fix this autochk program ... Thanks in advance for any help ...[/b]

---

### Post by Dill on 2008-08-16
This may be helpful:

[http://ubuntuforums.org/showthread.php?t=467691&highlight=autochk](http://ubuntuforums.org/showthread.php?t=467691&highlight=autochk)

Also, what's the boot disc to which you're referring? Is it the MS-DOS floppy? That's the only relevant boot floppy that I can think of, but most boot discs are bootable CDs, so could you perhaps post the link that you were given?

Cheers, 
Dylan

---

### Post by p_quarles on 2008-08-16
Hmm. Can you explain the problem a bit more? Ubuntu doesn't create any hidden partitions. There may be alternative tools available if we can figure out exactly what the problem is.

---

### Post by BostonBigGuy on 2008-08-19
Let me try in detail as too what happen ...

I received the Ubuntu CD in the mail and I placed it into my CD Drive on my laptop ...

There was 3 choices to pick from ...

I choose to install Ubuntu along side of WinXP so I would be able to switch back and forth ...

But when I tried to log onto WinXP I got that dreaded error ...

autochk program not found - SKIPPING AUTOCHK

The only way I can boot up my DELL Laptop is by putting in the Ubuntu CD and run it LIVE ...

I can see all my files on my hard drive but I can't log into WinXP or Ubuntu without the CD ...

Just a countious loop or endless loop ...

Is that enough info ...

Thanks

---

### Post by alienexplorers on 2008-08-19
Does your windows /boot/grub/menu.lst look like this at the end of the file.
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=11e5a808-45f5-41fb-8b43-5f2a8af9016d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2008-08-19
So when you boot your HDD (not a CD), what do you get on startup? Do you get any Grub menu at all allowing you to pick Windows or Ubuntu? Do you get any Grub errors? Or can you then choose Windows and it gives you that "autochk program not found" error immediately? Please explain more in detail if you want help sorting out the problem. :)

---

### Post by BostonBigGuy on 2008-08-19
Here we go right from scratch ...

WHEN I TURN THE COMPUTER ON (LAPTOP DELL INSPIRON | B-130

----------------------------------------------

Please select the operating system to start:

Microsoft Windows XP Home Edition
Ubuntu

Use the up and down arrow keys to move the highlight to your choice.
Press ENTER to continue.

For troubleshooting and advanced startup options for Windows, press F8.

------------------------------------------------

When I choice Microsoft Windows XP Home Edition ... this happens

Windows begins to load ...

Then blue screen with message:

autochk program not found - SKIPPING AUTOCHK

and goes back to first screen at startup.

------------------------------------------------

When I choice Ubuntu ... this happens

GRUB4DOS 0.4.3 2008-06-30, Memory: 636K / 1014M, CodeEnd: 0x41A38
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list the possible completions of a divice/filename.  ESC at any time exits.  ]

grub>  _  BLINKING CURSOR

-------------------------------------------------

Thanks

BostonBigGuy

---

### Post by caljohnsmith on 2008-08-19
OK, well that explains alot; you didn't originally mention that you were using GRUB4DOS with a modified Windows XP bootloader to load either Windows or Ubuntu. I'm curious, but is there any reason you don't want to just put Grub in the MBR and let it control the booting process? Probably at least 95% of the Ubuntu users on a multiple-boot system go with using Grub to control their booting process, rather than modify their Windows XP boot loader to work with Grub. I think it would be much simpler.

---

### Post by BostonBigGuy on 2008-08-19
I'M LOST :(  But I'm sure you will explain what I did and how to fix my problem so that I can use both and so on and so on ... I'm a real nebie with this UBUNTU so I know I have a lot to learn ... So my BIG question is:

CAN YOU HELP ME TO GET MY LAPTOP BACK SO I CAN USE BOTH OPS

SIMPLE of course is much BETTER :-)

THANKS

BostonBigGuy

---

### Post by caljohnsmith on 2008-08-19
No problem, we can help you through this, but first can you provide a link to whatever guide you followed to install the grub4dos program and modify your Windows bootloader? We will have to undo some of those steps before we can put Grub back in your HDD's master boot sector (MBR).

---

### Post by BostonBigGuy on 2008-08-19
lol

I just used the cd that I got in the mail ... I followed the instructions on the cd from UBUNTU ...

---

### Post by caljohnsmith on 2008-08-19
Well since your Windows XP boot loader is modified, let's first concentrate on getting Grub back in the MBR so you can boot Ubuntu at least, and then fix your Windows boot files later if we need to.

Please boot up your Ubuntu Live CD, open a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return a partition in the form (hdX,Y), if if does proceed:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Next post the output of:
```
sudo fdisk -lu
```
And where it shows a partition with "linux" under "system", that should be your Ubuntu partition in the form /dev/sdaX. Use that:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
And post the output of the above commands.

---

### Post by BostonBigGuy on 2008-08-19
When I type in the terminal box:

**sudo grub**  I GET:

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list the possible completions of a divice/filename ]

**grub> find /boot/grub/stage1**

Error 15: File not found

**sudo fdisk -lu**

Error 27: Unrecognized command

**sudo mount /dev/sdaX /mnt**

Error 27: Unrecognized command

**cat /mnt/boot/grub/menu.lst**

Error 12: Invalid device requested

---

### Post by caljohnsmith on 2008-08-19
I think when you ran that fdisk command, you must have still been in the Grub command line. If you see the [COLOR="Blue"]grub>[/COLOR] prompt, you can exit it by typing "quit". Anyway, you should see a bash prompt similar to:
```
ubuntu_user@Ubuntu-PC:~$

```
Try again following my instructions starting with doing the "fdisk" command.

---

### Post by BostonBigGuy on 2008-08-19
Here's what I get now ...

sudo fdisk -lu

[B]Disk / dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Divice ..... Boot ... Start ... End ... Blocks ... Id ... System
/dev/sdal .. . * ........ 1 .. 9729 . 78148161 ... 17 .. Hidden HPFS/NFTS[/B]

sudo mount /dev/sdaX /mnt

**mount: special device /dev/sdaX does not exist**

cat /mnt/boot/grub/menu.lst

**cat: /mnt/boot/grub/menu.lst: No such file or directory**

END

---

### Post by caljohnsmith on 2008-08-21
Can you copy and paste back here the exact output of that "sudo fdisk -lu" command? If you don't have internet access from your Live CD, you could copy/paste the results to a USB flash drive or even a floppy for example. But I need to see the full results of that command to help you. Also please post the output of:
```
sudo grub
grub> find /grub/stage1
grub> quit
```

---

### Post by BostonBigGuy on 2008-08-21
**Cal ... Could you IM me at NESNRacing on AOL ... For some reason we are not clicking with this posting thing ... I'd call you on the phone if you want ... I have US and Canada service that I don't get charge for ... Hope we can solved this problem as I think I'm misunderstanding your request so by phone or IM we can do it in real time ... Thanks for all the help**

---

### Post by geneven on 2008-11-18
I'm working on this kind of problem on my computer and if I don't misunderstand this discussion, the problem really has little to do with Ubuntu.

Here is the best source I have found so far:

[http://www.ehow.com/how_2225045_autochk-program-not-found-error.html](http://www.ehow.com/how_2225045_autochk-program-not-found-error.html)

Unfortunately, it talks about using a floppy disk (what are those? I saw some years ago...) and I have been having problem making a boot disk that works properly (and I don't have the original Windows system disk).

The problem is almost virus-like in its deceptiveness, in that just uninstalling some antivirus program (for me it was Pccillin, I think, but for most people it is norton) in a totally legitimate way (In windows, running the control panel utility for removing programs; you tell it to uninstall something and the next thing you know you can't boot! This is not how things are supposed to happen -- when you pick add/remove software it should either just remove the software or warn you or something)

---

