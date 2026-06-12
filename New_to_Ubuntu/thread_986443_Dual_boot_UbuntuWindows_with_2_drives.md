---
title: "Dual boot Ubuntu/Windows with 2 drives"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Chris62 on 2008-11-18
I have recently been given a new computer with two SATA II hard drives. It came without an operating system so I have installed Windows XP Pro on the C: drive and tried to install Ubuntu 8.10 on the second drive.

I have done this before, on my old computer and that of a friend who wanted to try Ubuntu. I used a live CD and installed Ubuntu on the second drive in each case. All I did was to click on "Install" fill in the details that were asked for and the name of the drive to receive Ubuntu and that was all. At the end of it I had a dual boot machine and no problems.

I tried this on the new machine and have had nothing but problems. At the end of the Ubuntu installation I got "Error 21" on re-booting and was unable to boot into either Windows or Ubuntu. Making the second drive the boot drive did nothing. I re-installed Windows and tried installing Ubuntu on the second drive again, and again I got "Error 21"

The first time round, the boot loader was put on C: which appeared to be the default option and was where it went before, and the second time round it was put onto the second drive. When I made the second drive the boot drive the system said it couldn't see the drive even though it produced a boot menu for Ubuntu.   Making the c: drive the first drive enabled me to boot Windows but didn't give an option to boot Ubuntu.

Could some kind person suggest what I am doing wrong and how I can get my machine to boot either Windows or Ubuntu. I had assumed that the process today would have been exactly the same as on the two occasions when it was successful. I haven't yet got the confidence to get rid of Windows completely and install Ubuntu on the C: drive so it will have to go on the other drive or not at all.

---

### Post by caljohnsmith on 2008-11-18
The problem might well be a bug with the installer, because I've helped others with similar setups and Grub errors after a fresh install. How about first reinstalling Grub to the MBR (Master Boot Record) of your external drive by booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also the output of:
```
sudo fdisk -lu
```
Reboot, set your BIOS to boot the external drive, and let me know if anything changes. We can work from there if you want. :)

---

### Post by adou2012 on 2008-11-19
> **caljohnsmith said:**
> The problem might well be a bug with the installer, because I've helped others with similar setups and Grub errors after a fresh install. How about first reinstalling Grub to the MBR (Master Boot Record) of your external drive by booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also the output of:
```
sudo fdisk -lu
```
Reboot, set your BIOS to boot the external drive, and let me know if anything changes. We can work from there if you want. :)

I have a similar problem. I have a 30GB Master and an 80GB Slave. I tried to split the slave in half, part staying Windows XP and part to use for Ubuntu. I burned my own CD and installed 8.10. Everything seemed to go just fine; however, now my computer wants to boot with grub instead of Windows, but I get the simple "Error 21" message.
I feel like such a novice with this, sorry if i'm missing something simple, but thanks to anyone that could help. :)

---

### Post by Chris62 on 2008-11-19
Hello Caljohnsmith,

Thanks for your message to which I replied but something happened and it seems to have got lost.

I got the following response to the "find" command:

(hd2,0)

that was to the command "find /boot/grub/stage1"

the other command "find /grub/stage1" produced "Error 15: File not found"

I didn't do the 'root' command yet. I have had to re-install Windows a couple of times already and thought I would wait to see what you said.

However, doing "sudo fdisk -lu" produced the following:

Disk /dev/sda 320 GB

Device     Boot    Start             End        Id      System
/dev/sda1   *       63             218323349     7     HPFS/NTFS
/dev/sda2         218323350        1250274689     5    Extended

Disk /dev/sdb  320 Gb

Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc   160 Gb

Device    Boot    Start          End      Id       System
/dev/sdc1  *       63          300432564   83      Linux
/dev/sdc2        300431565      312576704   5      Extended
/dev/sdc3        300431628      312576704  82      Linux swap / Solaris

So where do we go from here? having ened up a couple of times with an unbootable machine, I don't want to do the second set of commands without your advice in case the machine becomes unbootable yet again.

I should have mentioned before that the "C:" drive, which contains Windows XP and is partitioned into Logical C: and logical D: drives, is a RAID array. The second (internal) drive is also a SATA II drive but id independent of the RAID array

---

### Post by caljohnsmith on 2008-11-19
Can you change your BIOS to boot your Ubuntu sdc drive on start up? If not, it could be tricky trying to get Grub to boot from your RAID array. If you can change your BIOS to boot the sdc drive, then to install Grub to its MBR and make it bootable just do:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
And then you should be able to boot the sdc drive and at least get a Grub menu when you boot it; it might be that booting Ubuntu from the Grub menu will give you a Grub error though, but that's not a big problem at all. You've won 90% of the battle if you can just get a Grub menu when you boot the sdc drive; so let me know if you can get that far, and we can work from there. :)

---

### Post by Keen101 on 2008-11-19
It should work fine if you install windows onto one hard drive, and then set that drive to SLAVE. Then set the other drive to MASTER, and install Ubuntu.

---

### Post by adou2012 on 2008-11-20
So basically.. The Slave drive already had some files on it... is there any way that I can just remove Linux from my desktop... preferably without losing too much data on either hard drive?
I still want to try it, I just figure I'll install it on this laptop that I hardly ever use since I need to reformat it anyways.

---

### Post by bumanie on 2008-11-20
All you should need to do is to format the drive with ubuntu on it and then use your windows disk (xp) in console mode to fix windows mbr. If you have vista, it's recovery disk should repair the mbr. If you need help, post back with details of you OS and someone will help.

---

### Post by Chris62 on 2008-11-20
hello again Caljohnsmith,

I already changed the BIOS to boot from the sdc drive and I get the GRUB menu without the Windows option and when I click on the Ubuntu option it says it can't find the drive i.e. the drive which has already got the GRUB menu.

I wasn't able to give the full output from 'fdisk -lu' yesterday but here it is now:

Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd66571ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   218323349   109161643+   7  HPFS/NTFS
/dev/sda2       218323350  1250274689   515975670    5  Extended

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f6000c

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x489ed60b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300431564   150215751   83  Linux
/dev/sdc2       300431565   312576704     6072570    5  Extended
/dev/sdc5       300431628   312576704     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I don't think I can do the other options mentioned by keen 101,adou2012 and bumanie (many thanks for your trouble) because I understand that there are no masters and slaves with SATA II drives

---

### Post by bumanie on 2008-11-20
Could you post the output of > cat /boot/grub/menu.lstWhat I suggested does not have any thing to do with master or slave. It is purely getting rid of windows off sdc and re-writing the boot files for windows to boot from independent of grub. Wait for caljonsmith if you like, he is pretty much a guru on this stuff and I have no real experience with a raid setup.

---

### Post by caljohnsmith on 2008-11-20
That's great news you got the Grub menu, Chris62; as I mentioned before, that's usually the hard part. Getting your Grub's menu.lst working usually isn't a problem, so how about booting your Live CD, and please post the output of the following:
```
sudo mount /dev/sdc1 /mnt
sudo blkid
cat /mnt/boot/grub/menu.lst
```
And you installed Ubuntu 8.10, true?

---

### Post by Chris62 on 2008-11-20
Hi caljohnsmith, I thought that things were improving but I'm not there yet. I reinstalled Ubuntu to the second disc by disconnecting the main ("C:") drive. Now, by altering the boot order in the BIOS I can boot either into Windows or Ubuntu depending on which drive I make the first one.  Next, I added these lines to "menu.lst" after the line that reads   ###END DEBIAN KERNELS LIST:

title        Microsoft Windows XP Professional
root noverify  (hd2,0)
map  (hd2) (hd0)
map  (hd0) (hd2)
chainloader +1

and guess what? Nothing!  No boot menu. If the Ubuntu drive is the first it just boots straight into Ubuntu without mentioning producing a menu or mentioning Windows and if the Windows drive is first it just boots into Windows
Being very new to all this I probably don't properly understand it all but I put (hd2) in the 'root' line above because 'grub> find'  said that the Linux drive with stage1 is (hd2,0)

I must have missed something but don't know what.  I looked at the examples and there is a line that starts '# groot=(hd0,0). Is this something that needs to be changed?

---

### Post by Chris62 on 2008-11-20
I have just realised that one can hide the boot menu so I have unhidden it BUT clicking on the Windows itm produces "Error 11: unrecognised device string"

I am not sure what that means

---

### Post by caljohnsmith on 2008-11-20
OK, to get the Grub menu on start up, make sure the "hiddenmenu" line in your menu.lst is commented like:
```
# hiddenmenu
```
Also you can change the "timeout" line for however long you want the Grub menu to display before it tries to boot the default OS (the time is in seconds). Also, at the bottom of your menu.lst, add the following entries for Windows (replace the one you have):
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Probably the first entry above will work, but the second entry is just in case. How about giving that a shot and letting me know if it works, and if it doesn't, let me know exactly what happens when you choose each entry above from the Grub menu.

---

### Post by Chris62 on 2008-11-20
I have just tried that. The hd2 one gave the message "Error 21: selected disk does not exist" and the hd1 version said "Error 11: Unrecognised device string"

In my original version I had read somewhere that it is better to put root noverify (hd1,0) is better than just root. But I don't know what the difference is

---

### Post by caljohnsmith on 2008-11-20
> **Chris62 said:**
> I have just tried that. The hd2 one gave the message "Error 21: selected disk does not exist" and the hd1 version said "[COLOR="Blue"]Error 11: Unrecognised device string[/COLOR]"

The Grub error you are getting above is because you have a small typo in that Windows entry you tried; if you use "root noverify" it's supposed to be one word:
```
title Microsoft Windows XP Professional
[COLOR="Blue"]rootnoverify[/COLOR] (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
Also, "rootnoverify" is different from "root" in that:
[QUOTE=Grub Manual]

**rootnoverify:**
Similar to root (see Section 13.3.31 [root], page 47), but don&#8217;t attempt to mount the partition. This is useful for when an OS is outside of the area of the disk that GRUB can read, but setting the correct root device is still desired. Note that the items mentioned in root above which derived from attempting the mount will not work correctly.[/QUOTE]
So rootnoverify will sometimes work when root doesn't. Normally it's not necessary to use rootnoverify to boot Windows, but you can use it if you want. Let me know how it goes. :)

---

### Post by Chris62 on 2008-11-20
I put rootnoverify but it made no difference. One of those menu items gives Error 11 and the other gives Error 21.

There are three lines in menu.lst:

## default grub  root device
# e.g. groot=(hd0,0)
# groot=

do I need to do anything with # groot= ? or am I just fishing in the dark? 

Its getting late here and I haven't eaten yet so I will resume this tomorrow. Thanks for your help so far.

---

### Post by caljohnsmith on 2008-11-20
OK, an error 11 is almost always due to a typo; did you copy/paste the Windows entries that I gave? If you can't do that, then you might have mixed up the letter "O" with zero for example (the entries use zeros and no letter Os). So which Windows entry gives the error 11?

---

### Post by Chris62 on 2008-11-21
Hello Caljohnsmith,

Success at last! As you suggested. there was a typo because I copied the Windows entries by hand from the old machine to the new one - I thought it might be quicker, given my current level of expertise with Ubuntu.

Just to let you know, it was the "hd1" entry that worked and not the hd2, which still gives Error 21.

Anyway, thanks for all your help, I really appreciate it as I was getting extremely frustrated and bad tempered about it before I thought of looking in the forum for help.

Regards,

Chris

---

### Post by caljohnsmith on 2008-11-21
That's great news it's finally working, Chris. Cheers and have fun with your OSes. :)

---

