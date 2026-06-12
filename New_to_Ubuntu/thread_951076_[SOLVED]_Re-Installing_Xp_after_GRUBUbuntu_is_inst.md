---
title: "[SOLVED] Re-Installing Xp after GRUB/Ubuntu is installed"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-10-17
I am going to re-install XP on my laptop in a smaller partition than it is on now.I have migrated what I need to Ubuntu and run any Win programs in VBox.. ( those that wont WINE )

Currently XP is taking 14GB and it s mostly garbage and I cant remove any more from it with killing it

So, I am going to shrink the partition to about 3-5Gb and grow my Linux part.( which I have done once before)

The reason I still need XP is that I have a program the mounts a SCSI drive, and the only way for me to mount it is via a USB adapter. There is no known Linux driver for it so I am stuck

Will I have any trouble with the boot loaders/Grub when I re-install XP, as  know that sometimes XP doesnt like being installed as a 2nd OS

---

### Post by saj0577 on 2008-10-17
Back up your grub menu.
When you have installed xp restore your grub menu and add xp to the bottom of it.

Just done a bit of searching and found this for you it seems quite helpful.

[Link To Website]("tinyurl.com/5hn5vy")

Saj

---

### Post by Diabolis on 2008-10-17
Yeah you'll stay in the safe side if you install windows in your very first partition. I don't know why but it will mess up your partition table and you won't be able to boot linux right after.

While at grub menu select your Ubuntu entry and press **e** so you can edit it. You can see all the available key options at the bottom. Then you have to edit the line that says **kernel**. Find something that looks like this: **(hd0,X)** where **X** may be any number. Then replace the **X** with **X-1** and thats it. Now boot with that entry.

This is just a temporal fix. If you don't want to do it every time you have to do the same thing in this file: **/boot/grub/menu.lst**

---

### Post by Ducatiboy Stu on 2008-10-17
Xp is already in the Grub menu, and I am shrinking the original partition it was loaded into and doing a fresh inst in that paprtition

Will it affect the first FAT32 partition that holds the boot info

---

### Post by Ducatiboy Stu on 2008-10-18
Well, things are not good

I re-installed Xp, and now I cant get grub up...

Gparted live CD shows 55Gd ( 60Gb HDD ) as unallocated..

when I run XP it still shows my Ubuntu Partitions...


When I run the XP install CD it shows 

[COLOR="Blue"]-: Partition1 FAT     47Mb
c: partition2 NTFS     31997Mb (17598 free)
Unpartitioned space    8MB
f: Partition4 ( unkown )   24254Mb ( 25254 free)
g: partition5 (unkown )    455Mb ( 455MB free )
h: partition3 ( unkown)    470Mb (470MB free)[/COLOR]

[COLOR="Black"]It seems my Ubuntu part is still intact as hd0,5 but I cant seem to get it to bee seen.

XP loads and runs fine.[/COLOR]

---

### Post by Elfy on 2008-10-18
You have to reinstall grub - easy enough :) Boot with your livecd and [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

---

### Post by Ducatiboy Stu on 2008-10-18
Nope..no joy....tried ALL the things in that link


I can mount and read, but grub wont play the game...

And i am on a different PC so I cant paste any code  :confused:

I was able to mount from the live CD, and see my partitions with fdisk...and go into my /home

---

### Post by Elfy on 2008-10-18
You could try to use supergrub then - burn as an iso and boot with it - follow the menus to the linux/grub and it will automatically fix it for you - that's the theory :)

It's always worked for me

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It might also be worth running ```
sudo fdisk -l
``` in aterminal from the livecd

---

### Post by Ducatiboy Stu on 2008-10-18
Yeah..

SuperGrub CD fixed it nicely


The menu can be a bit confusing, but it sorted it back to my original Grub menu..complete with colors..

Whatever XP does when installing, aint pretty...

Atleast I lost no data 

thanks Guys...:guitar:... owe you big time

No...back to shrinking/re-sizing as intended...:)

---

### Post by Ducatiboy Stu on 2008-10-18
MMM...Gparted LiveCd still tells me that the HDD is un-allocated

---

### Post by Elfy on 2008-10-18
You can't boot ubuntu from grub?

How about if you use supergrub to boot directly?

---

### Post by Ducatiboy Stu on 2008-10-18
I can boot from grub after fixing with supergrup LiveCD, but now my partition manager cant see any partitions and tell me the HDD is un-allocated.

Doesnt matter if I use inbuilt Ubuntu editor or Gparted LiveCD.

Apparently according to Gparted the HDD has no disk label.

fdisk -l lists all the partitions.

---

