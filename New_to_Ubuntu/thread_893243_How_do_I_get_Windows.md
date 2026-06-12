---
title: "How do I get Windows??"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by xreaper on 2008-08-18
Okay, I'll try and make this as short and simple as possible:

I have a 160gb hard drive that run ubuntu from(ubuntu uses 100gb partion)
and the boot sector is broken. so I reformatted and did a manual install with making my second hard drive master, and installing the boot files onto it (/boot) and the rest onto 100gb of my 160gb hard drive (/)

SO... my computer boots off the small hard drive and then runs off the 100gb ubuntu partion.

Now, what I was hoping that someone could tell me is how to install windows 98se on the other 60gb (roughly) partion? 

Note: I've already formatted the 60gb partion to FAT32

Any help or guidance would be very much appreciated.

---

### Post by jualin on 2008-08-18
For Windows 98 you need a Floppy Boot disk unless the Windows 98 cd has a boot option. In that case go to the BIOS to make the computer Boot the CD first and then just follow the Windows 98 instructions on how to install it.

---

### Post by xreaper on 2008-08-18
yeah, i have a cd that has the setup thing on it. but, I've heard that when you install windows on your hard drive it wipes grub.. =[ and I have no idea how to get it back..

---

### Post by xreaper on 2008-08-18
oh, and yes i have set the bios to boot off cd first. =]

---

### Post by jualin on 2008-08-18
Check out this [link]("http://www.bootdisk.com/bootdisk.htm") which have Boot disks in case Windows 98 doesn't want to boot. After you boot using the boot disk on the link you have to navigate using the "change directory command" to your Cdrom letter, usually something like > cd d: should make the trick. And then run the command > setup.exe or check for the available files with the directory command > dir

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> yeah, i have a cd that has the setup thing on it. but, I've heard that when you install windows on your hard drive it wipes grub.. =[ and I have no idea how to get it back..

In that case after you install Windows 98, use [Super Grub Disk]("http://www.supergrubdisk.org/") to restore Grub.

---

### Post by xreaper on 2008-08-18
wow I have no idea what you just said lol, sorry, I'm a bit of a newbie when it comes to all of this.. do you think u could basically 'spell it out' to me? feel free to degrade me to a 5 year olds level =P

---

### Post by xreaper on 2008-08-18
okay, just wondering though, how would I set up my windows partion?
all on the 60gb partition? or is there a way to get it to boot from the small hard drive?

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> wow I have no idea what you just said lol, sorry, I'm a bit of a newbie when it comes to all of this.. do you think u could basically 'spell it out' to me? feel free to degrade me to a 5 year olds level =P

No problem, I have been there ;). You should install Windows 98 and after you install Windows 98 you have to restore GRUB (Ubuntu Boot loader) using the Super Grub Disk. My "weird" explanation above was in case you don't know how to install Windows 98. Feel free to ask anything else.

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> okay, just wondering though, how would I set up my windows partion?
all on the 60gb partition? or is there a way to get it to boot from the small hard drive?

How many hard drives do you have and what sizes are they?

---

### Post by xreaper on 2008-08-18
okay =] so you mentioned about super grub boot disk? where would I find that and how would I use it? what does it do? lol =D

---

### Post by xreaper on 2008-08-18
uhh lets see:
160gb hdd:
100gb ubuntu ext3 partion + 55gb FAT32 +5gb swap space

12gb hdd:
3.36gb ext3 partion (for the boot thingy) + 9.32gb swap space

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> okay =] so you mentioned about super grub boot disk? where would I find that and how would I use it? what does it do? lol =D

You find it [here]("http://www.supergrubdisk.org/") and it basically restore GRUB without you having to tweak any configuration file. Pretty much it restores GRUB the easy way, without manually editing the Grub configuration file.

---

### Post by Ripfox on 2008-08-18
It restores grub after you instll Windows on that free space you mentioned, as the windows install will probably wipe grub out. He gave you the link to the super grub disk in his post I think...

---

### Post by xreaper on 2008-08-18
okay, so I'll burn it as an .iso image for the cd?

and about the whole windows thing...
how would I go about installing it? all on one hard drive?

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> uhh lets see:
160gb hdd:
100gb ubuntu ext3 partion + 55gb FAT32 +5gb swap space

12gb hdd:
3.36gb ext3 partion (for the boot thingy) + 9.32gb swap space

What I would do is set up Windows 98 either on the 9.32GB partition or on the 55 GB partition. Also remember that you don't need that much swap space. A good amount is always twice your RAM. For instance I have 512 MB of RAM so my swap is only about 1 GB. also you don't need 2 swap spaces, one is enough.

---

### Post by xreaper on 2008-08-18
okay. i cant put windows on my 9gb partion because of the whole 'that partion is used to boot my second hard drive thing'. so on 55gb partion it is then? lol

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> okay. i cant put windows on my 9gb partion because of the whole 'that partion is used to boot my second hard drive thing'. so on 55gb partion it is then? lol

Since you said in your earlier post that 9.32 GB were used as SWAP you can use this for Windows 98, just make sure to format it. If it is too complicated you can just install it on the 55 GB partition, if you don't mind wasting  space

---

### Post by |{urse on 2008-08-18
just install windows and redo w/ supergrub

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

[http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/) <--- download

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). <--- or read this.

---

### Post by xreaper on 2008-08-18
okay, so, JUST to get this through my thick head =\...

If I install windows 98 on my 55gb partion, and grub is gone, when i install grub on my small hard drive again, it will still be able to locate my 100gb ubuntu partion?

---

### Post by jualin on 2008-08-18
> **xreaper said:**
> okay, so, JUST to get this through my thick head =\...

If I install windows 98 on my 55gb partion, and grub is gone, when i install grub on my small hard drive again, it will still be able to locate my 100gb ubuntu partion?

It should work. Also checkout the last link l{urse suggested if you run into any problems.

---

### Post by xreaper on 2008-08-18
okay, il try the install now. just downloading the sgd now. thatnks heaps for all your help =] if something goes wrong I'll just shoot out another message =]

---

### Post by jualin on 2008-08-18
Feel free to ask. I will be here a little longer. If I don't respond I will take a look at it tomorrow morning.

---

### Post by xreaper on 2008-08-18
hey.... I tried to install windows through the cd, but it keeps coming up something about needing to create a 'dos' partion? 

and I was also just wondering... is it possible to fix the boot sector of my 160gb hard drive? if so, how?

thanks in advance to any help.

---

