---
title: "So Angry at Vista...I broke my PC"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by DBA777 on 2008-10-28
After a year of deciding Vista sucks, I tried to install Ubuntu as a dual boot. I am running a Dell E520 and I immediately had parition problems because Ubuntu would not install.  Well, it would seem to install, but never got an option to boot from it.  I then proceeded to "tweak" my disk partitioning even though I am not sure what I did.  No, nothing boots and it will says I have no operating system.  I backed up everything and don't need to recover anything.  I would just like to do a clean install of Ubuntu (still running Vista on a laptop) on my desktop and see if I can function in life without Microsoft's crap. I can still boot the Live CD and have tried numerous installs with different partitioning options but Ubuntu will not boot.  Any help will be appreciated. Pretty ignorant relevative to what I am trying to do but I can follow directions.

---

### Post by scorchgeek on 2008-10-28
I think you need to erase everything and delete all partitions in the installer, then create a new one for Ubuntu.

---

### Post by damis648 on 2008-10-28
When you install Ubuntu, you choose to use the entire disk for installation? And you do not change any GRUB (bootloader) options in the Advanced section?

---

### Post by DBA777 on 2008-10-28
yes, chose the entire disk and didn't touch Grub settings.

---

### Post by DBA777 on 2008-10-28
ok, how do I do that?

---

### Post by damis648 on 2008-10-28
What happens when you boot up? Do you just get a blinking cursor?

---

### Post by DBA777 on 2008-10-28
I get "Grub" and then nothing.  No blinking cursor or anything.

---

### Post by billgoldberg on 2008-10-28
> **DBA777 said:**
> After a year of deciding Vista sucks, I tried to install Ubuntu as a dual boot. I am running a Dell E520 and I immediately had parition problems because Ubuntu would not install.  Well, it would seem to install, but never got an option to boot from it.  I then proceeded to "tweak" my disk partitioning even though I am not sure what I did.  No, nothing boots and it will says I have no operating system.  I backed up everything and don't need to recover anything.  I would just like to do a clean install of Ubuntu (still running Vista on a laptop) on my desktop and see if I can function in life without Microsoft's crap. I can still boot the Live CD and have tried numerous installs with different partitioning options but Ubuntu will not boot.  Any help will be appreciated. Pretty ignorant relevative to what I am trying to do but I can follow directions.

Download and burn the gparted live cd (could be on the ubuntu live cd too, not sure) and boot from it.

Format every partition, maybe even join the back together.

Then install install ubuntu.

--

Btw, this is a linux forum, not an ms-bashing forum. Your behaviour is in violation of the CoC you agreed to upon joining this forum.

---

### Post by DBA777 on 2008-10-28
ok, will try that. 
Sorry, did not mean to offend.  Just wanted to give context of why I would go down a path that I am not qualified for.

---

### Post by billgoldberg on 2008-10-28
> **DBA777 said:**
> ok, will try that. 
Sorry, did not mean to offend.  Just wanted to give context of why I would go down a path that I am not qualified for.

You didn't offend (well not me), just letting you know so you don't get any infractions.

---

### Post by DBA777 on 2008-10-28
Does it matter what file system I should format with?

---

### Post by billgoldberg on 2008-10-28
> **DBA777 said:**
> Does it matter what file system I should format with?

Ubuntu uses ext3 as a standard, I prefer Reiserfs.

It doesn't really matter.

---

### Post by Bölvaður on 2008-10-28
> **billgoldberg said:**
> Download and burn the gparted live cd (could be on the ubuntu live cd too, not sure) and boot from it.


It is on the ubuntu live cd.

I would say put that disk in and check if you can see if something is installed on the hard disk drive.

If it is so, I think that it might be that the videocard driver is needed. (that is when you boot from live cd it uses the default driver.. that got name beginning with V. And when you have installed it is wrongly set to a driver that is not working for you)

---

### Post by boof1988 on 2008-10-28
Using a Ubuntu 8.04.1 LiveCD, I was able to boot to LiveCD.  Then, while in LiveCD use System->Administration->Pertition Editor to partion the HD.  When I did this, I wasn't able to partition the Windows part of my HD since it was locked.  But there may be a way to unlock/unmount any locked partitions, I just don't know them yet.

One other option, which I have done in the past, is to burn a 'gpartd' liveCD.  When I've used one of these, there was no problem with any "locking" of the partitions.  It justs asks if you REALLY want to continue.

If you don't have one already, here's a [[COLOR="Blue"]link to gparted @ sourceforge.net[/COLOR]](http://gparted.sourceforge.net/livecd.php).  Where you can download an file you can iso burn to a CD.  There might be a way to get it off of Ubuntu but I don't know.

---

### Post by rickycodie on 2008-10-28
right click on the locked partition and select unmount, that should unlock it

---

### Post by P13808 on 2008-10-28
open the terminal from a live cd.

cd \
rm *

That should do a clean sweep of your computer.  Now run the partitioner.  Should be complete free space.  Make an ext3 partition.  Then it should install fine.  Oh, and try a different CD, it may be damaged.

---

### Post by boof1988 on 2008-10-28
> **billgoldberg said:**
> Ubuntu uses ext3 as a standard, I prefer Reiserfs.

It doesn't really matter.

I'm a noob... Why do you prefer Reiserfs?  I used [[COLOR="Blue"]this[/COLOR]](http://www.funnestra.org/ubuntu/hardy/#install) as a guide when I installed Ubuntu and the author seems to prefer it as well and I wondered what was  the reasoning of your preferences.  I can't tell the difference ***yet***.

---

### Post by boof1988 on 2008-10-28
> **P13808 said:**
> open the terminal from a live cd.

cd \
rm *

That should do a clean sweep of your computer.  Now run the partitioner.  Should be complete free space.  Make an ext3 partition.  Then it should install fine.  Oh, and try a different CD, it may be damaged.

Is the 'check CD for errors' (Ubuntu liveCD shows this as an option when it boots) an adequate error check?

---

### Post by DBA777 on 2008-10-28
no, I did not do a clean sweep but reformatted the partition and installed Grub on the same partition.  It appeared to install fine and them just got "Grub" with a blinking cursor.  The boot sequence does not appear to recognize Ubuntu is installed.

---

### Post by DBA777 on 2008-10-28
response to the clean sweep option

bash: cdrm*: command not found
ubuntu@ubuntu:~$

---

### Post by Bölvaður on 2008-10-28
nah when grub doesnt find any os there will be short error message and you will be returned to grub.
for me this sounds like there isnt even grub on there, just nothing.

And that command was:

cd /    (one line, this means, change directory to root)
rm      (this line means, delete it)

this one is better imo

rm / -R  (remove everything from root down recursivly)

You do it from terminal on the live cd.
On the live cd, find Applications &#8594; Accessories &#8594; Terminal And there type in either his 2 lines, or my one line :KS

---

### Post by DBA777 on 2008-10-28
I get

cannot remove '/-R': No such file or director

---

### Post by mkvnmtr on 2008-10-28
In your first post you said you still want to have Windows on your computer. This means you want to dual boot, correct? If so you first need to get back to your Windows system. I do not use Windows but if you have the disks you can restore your system. When you have it back and it is booting normally you can partition. The easy way is to defragment a time or two and then use the live disk to form two partitions. One for Windows that contains the Windows OS and another. Then when you go to install Ubuntu chose install in the largest free space. It should make 3 partitions. One for grub, one for swap and one for you Ubuntu system. Then when you restart grub should give you the choice of which system you want. You don;t need to do the partitioning yourself. It sounds like your problem is because you put grub on the same partition as your OS.

---

### Post by DBA777 on 2008-10-28
I don't want windows, just Ubuntu.

Under my Gparted I currently have:
/dev/sda1 ext 3 460G (5.76 used) with a boot flag
/dev/sda2 extended 5.79G
/dev/sda5 linux-swap 5.79G

and the indentical config under /dev/sdb

---

### Post by DBA777 on 2008-10-28
The default location for the GRUB install is (hdo).  Is this correct?
Other options are:
/dev/sda
/dev/sda1 Ubuntu 8.04.1
/dev/sdb
/dev/sdb1

---

### Post by ajwak95 on 2008-10-28
Use GParted, shrink the main partition to its smallest size, and leave it to be free space. Then when you try to install Ubuntu, select "Use largest continuous space". That should work.

---

### Post by ajwak95 on 2008-10-28
oops, wrong post!

---

### Post by DBA777 on 2008-10-28
it appears that Ubuntu is installed but Grub is not loading.  I have a Grub directory in my boot directory.  It there anything that I need to change in Grub directory?

---

### Post by Bölvaður on 2008-10-28
(my command was : "rm / -R" with whitespace between all 3)
The info you give looks good, so it is not the partitions.

perhaps we should take a look at your files:
try find boot/grub/menu.lst on the harddisk and post the last few lines that look like this:


title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=cc8a4d6d-acb4-4012-955b-d2175046322c ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet


*added*
there is a disk that is called "super grub disk" and it helps repair grub.

---

### Post by DBA777 on 2008-10-28
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2a9ad2f0-e9a4-4978-a8ea-1099b53499d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2a9ad2f0-e9a4-4978-a8ea-1099b53499d8 ro single
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2ffa409e-1820-405e-9754-fc77f4726692 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2ffa409e-1820-405e-9754-fc77f4726692 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by DBA777 on 2008-10-28
I tried rm / -R:
rm: cannot remove root directory '/'

---

### Post by eldragon on 2008-10-28
> **DBA777 said:**
> I tried rm / -R:
rm: cannot remove root directory '/'

ok, if i understand correctly, you want to install ONLY ubuntu on the HDD SDA. is that correct?

if so, do the following:

first, boot from the live cd.

once there, go to applications ----accesories ---- terminal

and there type:
```

$ sudo dd if=/dev/null of=/dev/sda

```

that should render your drive partition-less. mind you, IT WILL DELETE EVERYTHING.

once you did that. run the installer, let it decide everything when partitioning. it should find a blank hdd.

---

### Post by sdowney717 on 2008-10-28
most likely your going to like IBEX better.
It is almost oct 30, I have been using ibex and it is better than hardy. I always like to keep pushing ahead.
the partitioner on the live cd should give the option to delete everything on the drive.

---

### Post by DBA777 on 2008-10-28
Well I did it and it is still not booting.  Loaded up super GRUB CD and it can't seem to determine the problem either.  SGD keeps giving me Error 15: File not found when looking for /boot/grub/menu.lst or /boot/grub/grub.conf. I can see those files though so somehow, my boot/bios is not seeing Grub

---

### Post by boof1988 on 2008-10-28
> **DBA777 said:**
> Well I did it and it is still not booting.  Loaded up super GRUB CD and it can't seem to determine the problem either.  SGD keeps giving me Error 15: File not found when looking for /boot/grub/menu.lst or /boot/grub/grub.conf. I can see those files though so somehow, my boot/bios is not seeing Grub

Hi DBA777,

When you say "Well I did it..." do you mean the below stuff by eldragon or something else.

> **eldragon said:**
> ok, if i understand correctly, you want to install ONLY ubuntu on the HDD SDA. is that correct?

if so, do the following:

first, boot from the live cd.

once there, go to applications ----accesories ---- terminal

and there type:
```

$ sudo dd if=/dev/null of=/dev/sda

```

that should render your drive partition-less. mind you, IT WILL DELETE EVERYTHING.

once you did that. run the installer, let it decide everything when partitioning. it should find a blank hdd.

Are you trying to boot using a liveCD and is it a Ubuntu liveCD?

---

### Post by DBA777 on 2008-10-28
ok, I disabled the RAID array on my Dell and it loaded up perfectly. Thanks for the all the help

---

### Post by eldragon on 2008-10-28
> **DBA777 said:**
> ok, I disabled the RAID array on my Dell and it loaded up perfectly. Thanks for the all the help

ohh, i didnt catch up that raid array thingie. it wouldnt work unless you setup dm-raid first.

its quite complicated, and to be honest, you dont get that much performance out of it.

---

