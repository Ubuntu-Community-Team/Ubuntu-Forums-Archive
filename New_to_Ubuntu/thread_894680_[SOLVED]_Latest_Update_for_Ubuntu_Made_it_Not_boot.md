---
title: "[SOLVED] Latest Update for Ubuntu Made it Not boot"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Musick Man on 2008-08-19
Hi,

Earlier this morning, i noticed that i had some updates that needed to be installed on my Ubuntu computer. So i start to download them.

Seeing that it might take a while, i left the computer. 

I went back to it about 2 and a half hours later, to find that the screen is completely Black, and i can only move my mouse around in the screen. After a few attempts at trying to get a log in window, i decided to just turn the computer off via the power button on the tower. After it had powered down, i let it sit for 10 seconds, and booted it back up. It came to the boot loader, and i chose to boot Ubuntu 8.04 (Something that i dont rebrember) .19 (I think that is what it said)

After i pressed enter, that is where the errors started flowing in. It started the Ubuntu loader, where it says ubuntu, and has the orange loader, then it said something about the partition could not be read, and then it flashed a few times, then it brought up this whole long list of terminal things, with errors in them, then at the end it said, 

root@[My computers name]

Like a terminal. And i could not do anything after that. 


After i tried the recovery mode, and it brought up the same thing. I also tried the .18 ubuntu one, and it also did not work.

Help would be greatful.

MusickMan

---

### Post by tangibleorange on 2008-08-19
ok. could you boot into an ubuntu live CD and post the output of this command:
```
sudo fdisk -l
```

---

### Post by Musick Man on 2008-08-19
Sure thing. i will edit this post in about 5 minutes with the answer



Edit:

Well i ran fdsk or something like that. Because it said there was a error and that i had to run it manually. 

So i did. And after repairing a lot of things, i got back into my system. The only thing that is wrong is, i lost all my drivers, and all my computer settings, so the screen res is really big, and a lot of other things are wrong, but from what i see now, nothing is too broken. 

But one thing, it tells me that i have 107 updates to download and install. Should i do it? Or not. 

And to answer ^

Here is what i see when i put in that code

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e57bef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10292       19929    77417235    5  Extended
/dev/sda3           10200       10291      738990    7  HPFS/NTFS
/dev/sda5           19648       19929     2265133+  82  Linux swap / Solaris
/dev/sda6           10292       19364    72878809+  83  Linux
/dev/sda7           19365       19647     2273166   82  Linux swap / Solaris

Partition table entries are not in disk order


That is what i see. But i am not using the live CD. Should i boot up the live CD and do it on there? Or is what i posted good for you?


Edit 2:

Ok, I am running int problems now. There are a lot of things missing in the menus. There is no Restricted Drivers Manager. And there are also a lot of other things missing.


Another Error:

Started Synapic Package Manager. Got This

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Musick Man on 2008-08-19
I made a lot of edits in my last post. And i keep running into problems.

For now, i am just trying to change my screens res.

There is not a button in System ---> Administration ---> Restricted Drivers Manager, so i can not set my graphics card to be used. 

The Synapic Package Manager will not start, so i can not tell it that it is ok to use my graphics card, which i cant enable anyway.

---

### Post by tangibleorange on 2008-08-19
ok. we can fix the synaptic problem with this command at a terminal:
```
sudo dpkg --configure -a
```
restricted drivers manager can be launched by typing this at a terminal:
```
gksu jockey-gtk
```

as for the rest, i don't know. if that install is not to essential for you, it might be worth backing up all your files to an external HDD and simply re-installing.

---

### Post by Musick Man on 2008-08-19
Well i am back in business for now. Everything seems to be working great. 

Thanks for all your help. I really appericate it. I will post if i come across any other errors. 


Musick Man

---

### Post by tangibleorange on 2008-08-19
ok good luck! please mark this thread as solved and make a new one if you encounter any more problems!

---

