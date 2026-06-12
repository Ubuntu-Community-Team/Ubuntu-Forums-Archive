---
title: "Plz help!!! Crash maded fatal deadly crash!!!"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by WoAnerges on 2008-11-10
Someone help me PLZ!!!!!!!!!

i've was installing new games from "Add/Remove" util, and at the download of packages stage, my system freezes! (it is always **cking freezes :'(((  )  I decide to reset Computing machine, because i have nothing left to do - even mouse doesent move. THIS LINUX ALWAYS FREEZES!! ((((((((((((((((((((((((((

and when i reboot my system, linux ubuntu make me an ***king surprise! my system CRASH and i can do nothing to recover my sys :'(

i maked an screen of the error, that appears. here it is:

[[IMG]http://img.pixs.ru/images/PA130182JP_7647551_109512.jpg](http://pixs.ru/?ref=109512)

PLEASE HELP ME WITH THIS! i like linux, i migrated no so long time ago from stupid commercial windows, i but those natural crashes, make me really bad, and now i associate linux with crashes, freezes, errors or similar ((( . i don't want to stay with thinking about linux is so bad, help me someone, please, to return linux ubuntu looks greatest system ever been for me.

T H A N K____Y O U,____G O O D____P E O P L E ! ! !

Tags:
[
kernel panic
root= can't mount
]

---

### Post by WoAnerges on 2008-11-10
Someone help me PLZ!!!!!!!!!

i've was installing new games from "Add/Remove" util, and at the download of packages stage, my system freezes! (it is always **cking freezes :'(((  )  I decide to reset Computing machine, because i have nothing left to do - even mouse doesent move. THIS LINUX ALWAYS FREEZES!! ((((((((((((((((((((((((((

and when i reboot my system, linux ubuntu make me an ***king surprise! my system CRASH and i can do nothing to recover my sys :'(

i maked an screen of the error, that appears. here it is:

[[IMG]http://img.pixs.ru/images/PA130182JP_7647551_109512.jpg[/IMG]](http://pixs.ru/?ref=109512)

PLEASE HELP ME WITH THIS! i like linux, i migrated no so long time ago from stupid commercial windows, i but those natural crashes, make me really bad, and now i associate linux with crashes, freezes, errors or similar ((( . i don't want to stay with thinking about linux is so bad, help me someone, please, to return linux ubuntu looks greatest system ever been for me.

T H A N K   Y O U,   G O O D   P E O P L E ! ! !

---

### Post by Peter09 on 2008-11-10
Can you boot into recovery mode?

---

### Post by WoAnerges on 2008-11-10
recovery mode does'nt boot as same as normal mode. instalation cd doesn't have ANY recovery options :((((((
what should i do??? :(

---

### Post by Peter09 on 2008-11-10
Can you boot the live CD?

---

### Post by WoAnerges on 2008-11-10
Live CD is booting. i can observe from "test" OS my file sys, can observe files

---

### Post by Peter09 on 2008-11-10
From this thread:
[http://ubuntuforums.org/showthread.php?t=210820&page=2](http://ubuntuforums.org/showthread.php?t=210820&page=2)

>  Re: how to repair grub
I found something a little easier....No good to original poster but for other like me who have this problem

Boot from the Live CD. From the console run:

sudo grub

From the new grub command line run ( customized to your system ) the following commands.

>root (hd0,2)
>setup (hd0)


Replace the partition and hard disks for your system.

(hd0) = the MBR for the hard disk which is where grub needs to install itself too for it to load on bootup.

(hd0,2) is the partition which contains your grub files. This could be your root partition or perhaps a boot partition.

Hope this helps.
Last edited by RTB-UK; November 4th, 2006 at 03:13 AM..
RTB-UK is offline Report Post   	Reply With Quote

---

### Post by WoAnerges on 2008-11-10
GRUB is LOADING CORRECTLY! i loaded windows XP, from GRUB, to post this issue. I not sure really whatis GRUB, but i think, that problem in Ubuntu OS, not in GRUB. why i need to recover GRUB, if it is loading and working PERFECT?? here is writen to make root hd 0,2 but my root situated in hd 0,3.. O_o

---

### Post by Peter09 on 2008-11-10
I guess the problem is whether your boot file is correct and in the right place. I believe grub will generate the boot block again if you tell it to.

---

### Post by Sef on 2008-11-10
Moved to absolute beginners.

Have you tried going into safe mode when booting up?  Instead of putting in your name and password, go to options first.

---

### Post by WoAnerges on 2008-11-10
safe mode isn't booting just like normal mode. this crash appears just after i pressing "enter" on Normal mode ubuntu or safe mode option in GRUB. 
what options? the system is not booting.

---

### Post by WoAnerges on 2008-11-10
ok. ill will try to! so i must do just same as it is writen in quote, that You give me above my last post, or i must do little another? Thank You.

---

### Post by oilchangeguy on 2008-11-10
the op has two threads on the same subject:
[http://ubuntuforums.org/showthread.php?t=977455](http://ubuntuforums.org/showthread.php?t=977455)
can a mod please merge these?

---

### Post by Peter09 on 2008-11-10
Yo may need to change the drive names from the quote

---

### Post by WoAnerges on 2008-11-10
change the drive names? where drive names is can be seen and how do i know do i need to change the drive names or not? and how to do this?

---

### Post by Peter09 on 2008-11-10
Here is a thread which may help you more.

[http://ubuntuforums.org/archive/index.php/t-76652.html](http://ubuntuforums.org/archive/index.php/t-76652.html)

Note that I do not know if it is just your MBR which is messed up or your system. We can but hope its the MBR.

---

### Post by overdrank on 2008-11-10
Threads merged :)

---

### Post by JKBurton on 2008-11-10
Can anyone else see the image he posted?  All I get when I try is a login screen in Cyrillic.

---

### Post by overdrank on 2008-11-10
> **JKBurton said:**
> Can anyone else see the image he posted?  All I get when I try is a login screen in Cyrillic.

Edit my error pic is there now :oops:

---

### Post by WoAnerges on 2008-11-10
Hey! Anyone! HELP ME PLZ!!!!!!!!!!!!

---

### Post by WoAnerges on 2008-11-10
Please! Don't leave me alone with this trouble! anyone know an answer, how to repair that stuck? :(
is Linux is really so bad? i, when i was on windows XP, thinked about linux, that it is an great system, but i so disapointed now :(
i really don't knew that it is so not stable. little error - and all system is on CRASH. its so sad to has Acquaintance with linux in that way - all i get from it - is errors, stabilized freezes and slower work than in windows. is really linux is so bad, that it is appears on my computer? :(

---

### Post by WoAnerges on 2008-11-10
i still don't know what i have to do to repair Ubuntu.

---

### Post by philinux on 2008-11-10
If nobody esle can help then I suggest backing up any valuable data using the live cd and reinstall.

---

### Post by WoAnerges on 2008-11-10
i tryed to boot Ubuntu in RECOVERY MODE and theres a new info appears - it is more informative. i have grabbed it!
Please look! maybe theres in here may be answer!
I DON'T KNOW HOW TO USE THUMBNAILS. please, firgive me for not using that possibility.

i'm not a specialist in linux sys, but i think that trouble in root device, or it's name.. what can you say?

here is snapshot:

[thumbnail]
[IMG]http://pixs.ru/showimage/PA130188JP_2212418_109627.jpg[/IMG]
[/thumbnail]

---

### Post by philinux on 2008-11-10
Ok. Use the livecd to look at your system. Two commands
You need to mount your drive to get the info.
```
sudo blkid
```
This will give the block id of your partitions
```
cat /etc/fstab
```
This will show what should be mounting. It **could be** that the blockid's dont match.

---

### Post by WoAnerges on 2008-11-10
Here it is what it answeres:

```


ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="5E3C3CFE3C3CD32F" LABEL="windows" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="daa94d28-9495-43a1-8c6b-796f5b57c4c2" 
/dev/sda4: LABEL="Ubuntu" UUID="f3b98fc4-9d20-45f8-af03-79328f1b17f7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="C4ECD6FBECD6E728" LABEL="Store" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
ubuntu@ubuntu:~$ 



```

so what now? (:
thank's - you, philinux, starting to make me feel positive (:

---

### Post by philinux on 2008-11-10
Are you sure thats the fstab from your hard drive on /dev/sda4

Here's mine for comparison only and note i have home on it's own partition which you do not. Your system has swap on /dev/sda3 and root+home on /dev/sda4
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b0dea6a-f902-4412-8746-a6f9ee7cc32f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=39759482-7d7a-4398-b338-2cdf7ed2e99d /home           ext3    relatime        0       2
# /dev/sda2
UUID=41d5d5ba-4485-462c-bb71-309d7d42359b none            swap    sw              0       0

```

---

### Post by WoAnerges on 2008-11-10
i don't know. i just typed the commands from "TRY UBUNTU WITHOUT ANY CHANGES OF YOUR COMPUTER". i run it from a CD with Ubuntu instalation disc, opened cmd and typed commands, that you give me. so, what i should do next? oh.

---

### Post by philinux on 2008-11-10
Browse your hard drive from the live cd and find fstab in /dev/sda4.

You'll have to browse /media/disk I think when it's mounted.Then browse the folder etc and look for the file fstab. Double click it to display it's contents.

---

### Post by WoAnerges on 2008-11-10
All disks mounted - the sys answer is still:

```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0
ubuntu@ubuntu:~$ 


```

Yes!! i found this file))))
Here is it's contents:

 /media/ubuntu/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=f3b98fc4-9d20-45f8-af03-79328f1b17f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=daa94d28-9495-43a1-8c6b-796f5b57c4c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

and this from /etc/fstab:

```


aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0


```

---

### Post by WoAnerges on 2008-11-10
so, i must replace contents of file /etc/fstab with contents of file /media/ubuntu/fstab?

ok i will try that now.

Added 2 mins later:

:((( i can't change file /etc/fstab contents - look's like i don't have permissions from live cd to do that.

Added 15 mins later:

I changed permissions by using command ```
sudo chmod 777 /etc/fstab
``` and replaced files contents. now i will make a little reboot of computing machine (:  .

Added 8 mins later:

After i changed /etc/fstab file contents from
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```
to contents from file /media/ubuntu/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=f3b98fc4-9d20-45f8-af03-79328f1b17f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=daa94d28-9495-43a1-8c6b-796f5b57c4c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

it didn't help because after reboot file returns to it's previous contents:
```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```

so no changes was done. ):

suxx. what i have to do?

Added 3 mins later:

Oh! I got! i dont have to change /etc/fstab file contents, because it is virtual temporary filesystem and file /etc/fstab is returned to previous contents because it was in live CD filesystem. so, real file, that must interest me is in /media/ubuntu/etc/ and it's contents is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=f3b98fc4-9d20-45f8-af03-79328f1b17f7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=daa94d28-9495-43a1-8c6b-796f5b57c4c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

ok. and as always i don't know what to do (:

---

### Post by WoAnerges on 2008-11-10
sorry. accidently posted the same post two times.

---

### Post by jimv on 2008-11-10
Run this command from the Live CD to check that partition for errors, then try booting up when it finishes.

```
sudo fsck -py /dev/sda4
```

---

### Post by JKBurton on 2008-11-10
Here's a thread I found where someone earlier had your problem (well, same symptom anyway) and found a solution:
[http://ubuntuforums.org/showthread.php?t=27709](http://ubuntuforums.org/showthread.php?t=27709)

Best of luck,
Keith

---

### Post by WoAnerges on 2008-11-11
Is this will help? it will not damage or change my sys in some way???

```

boot from live cd

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

change source list into Breezy.

apt-get install initrd-tools
apt-get remove linux-image-2.6.10-5-686

it will remove 2.6.10 and install linux-image-2.6.12-2-686 .
Of course, I think it is still beta version..
but at least I can boot my system.

```

Where is the good mega-hackers, when poor user need for their support? :'(

---

### Post by WoAnerges on 2008-11-11
i tryed. it doesen't helped. too many errors, while doing that.

---

### Post by philinux on 2008-11-11
Use the livecd to backup your important stuff to say a usb stick or dvd and reinstall. Put home on it's own partition too if you do this then reinstalling in future is a really easy.

---

### Post by Tomatz on 2008-11-11
Looks like disk errors to me.

Boot the **live cd** and do the following:

Open a terminal and type

```
sudo fdisk -l
```

Then your drives will be listed. Look fo the drive/partition that uses the **Linux** filesystem (under system in the table).

Note its **drive number** **(example marked in red)** we will need to use this to run a disk check (fsck).

You should see something like the following:

```
Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e03e3

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]**_/dev/sdc1_**               1        9327    74919096   83  Linux[/COLOR]
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris
```

As you can see mine is [COLOR="Red"]/dev/scd1[/COLOR].

Yours won't (probably) be called scd1 but thats what you need to find out.


Now in a terminal type:

```
sudo fsck -p /dev/[COLOR="Red"]DRIVE NUMBER[/COLOR]

```
*E.g for me it would be **sudo fsck -p /dev/scd1**.*

;)

---

### Post by WoAnerges on 2008-11-11
That's, what i got:

```

ubuntu@ubuntu:~$ sudo fsck -p /dev/sda4
fsck 1.41.3 (12-Oct-2008)
Ubuntu: clean, 193808/2310144 files, 4754340/9237375 blocks
ubuntu@ubuntu:~$ 

```

look's like disk check completed in 0,5 seconds......

---

### Post by WoAnerges on 2008-11-11
> **philinux said:**
> Put home on it's own partition too if you do this then reinstalling in future is a really easy.

What did you meaned? Please, recommend me, how to use my hard disk drive to install Ubuntu. How to create a linux file system step by step to make linux be perfet in file system meaning?
what can\must i do\change on hard drive? i always mounting FS (ext3) in "/". i should mount it in "/home"? Please recomend me, how to make it perfectly, because i'm an migrator from windows, and not so good in understanding of linux-type FS.
-------------------------------------------------------------------------

i have:

---

### Post by Tomatz on 2008-11-11
Can you boot now the fsck has completed?

---

### Post by WoAnerges on 2008-11-11
no. so i backuped data and formated sda4.
so can anyone guide me how to create in best way my File System for Ubuntu?

---

### Post by tarps87 on 2008-11-11
When installing select manual at the partition section of the install:
The root partition: 10GB's to 20GB's should be plenty for the root partition.
Format ext3, mount point = /

The swap partition: at least 1 1/2 times the size of your ram if you want to hibernate your computer, if not any size.
Mount = swap

For the home partition: the rest of the free space.
Format ext3, mount point = /home

If you are using the live cd to install the partitioner should be easy to follow but if you have any problem just post back

---

### Post by Tomatz on 2008-11-11
Can you boot now the fsck has completed?


[EDIT]

Disregard that. Didn't realise you were reinstalling ;)

---

### Post by WoAnerges on 2008-11-11
> **tarps87 said:**
> 

For the home partition: the rest of the free space.
Format ext3, mount point = /home



have you seen my hard disk architecture?
so i must make 10 or 20 gib for "/"
and as much as i can for "/home"?
why not use all avialble space for "/"?
what is the difference?
is "ext3" the best fs?

---

### Post by Tomatz on 2008-11-11
There is plenty of documentation already available:

[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

;)

---

### Post by tarps87 on 2008-11-11
> **WoAnerges said:**
> have you seen my hard disk architecture?
so i must make 10 or 20 gib for "/"
and as much as i can for "/home"?
why not use all avialble space for "/"?
what is the difference?
is "ext3" the best fs?

You can use all the space for /
One of the previous posts suggested a separate home partition (/home) the advantage of this is that the OS and your data are separate so if you need to reinstall you will not loose your data.
With the separate partitions from Ubuntu it looks as it would with one drive and from windows I don't believe it can see either partitions by default.
If you want just the / partition just select all the free space and ignore the bit about /home

You can use ext2 or ext3, ext3 has journalling which is suppose to be more reliable after 'improper' shutdowns so I would suggest using ext3

---

### Post by WoAnerges on 2008-11-11
i asking  what you, guys, thinking about it. how it make to make it great :)
or you always making everything, using standarts and dogmas? 0_o

---

### Post by WoAnerges on 2008-11-11
ok! now i got that! thank you guys! thank you for take your time for helping me!

---

### Post by Tomatz on 2008-11-11
> **woanerges said:**
> ok! Now i got that! Thank you guys! Thank you for take your time for helping me!

np :)

---

### Post by philinux on 2008-11-11
> **WoAnerges said:**
> ok! now i got that! thank you guys! thank you for take your time for helping me!

Really glad you got it sorted.:)

---

