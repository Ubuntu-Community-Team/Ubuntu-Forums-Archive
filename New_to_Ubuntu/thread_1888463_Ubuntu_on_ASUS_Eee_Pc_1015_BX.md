---
title: "Ubuntu on ASUS Eee Pc 1015 BX"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by nick-88 on 2011-11-29
[FONT=Tahoma]Hello! I need some help because I'm a really beginner!
I bought ASUS Eee PC 1015 BX.
It's a 10 inch netbook which has:
- AMD® Fusion APU C60 1.0GHz (dual core)  Processor
- AMD® Radeon HD 6290 graphic card
- 1 Gb RAM
- 320 Gb HDD

I'm searching a good Ubuntu OS to install on it. I've noticed that there's this version:[/FONT][FONT=Tahoma][COLOR=black] **ubuntu-10.04-netbook-i386.iso** .

What do you think about it?
Will it work on my netbook?
Will it be stable?

PS: [/COLOR][/FONT][FONT=Tahoma][COLOR=black]I've read that the Ubuntu Netbook Edition (was it the same of the file above?) has been merged into the Desktop Edition [/COLOR]from Ubuntu 11.04. Is it worth downloading it?
What about Aurora or EasyPeasy? I'm confused!!! :confused:
[/FONT][FONT=Tahoma][COLOR=black] 
Thanks
[/COLOR][/FONT]

---

### Post by asifnaz on 2011-11-29
> **nick-88 said:**
> [FONT=Tahoma]Hello! I need some help because I'm a really beginner!
I bought ASUS Eee PC 1015 BX.
It's a 10 inch netbook which has:
- AMD® Fusion APU C60 1.0GHz (dual core)  Processor
- AMD® Radeon HD 6290 graphic card
- 1 Gb RAM
- 320 Gb HDD

I'm searching a good Ubuntu OS to install on it. I've noticed that there's this version:[/FONT][FONT=Tahoma][COLOR=black] **ubuntu-10.04-netbook-i386.iso** .

What do you think about it?
Will it work on my netbook?
Will it be stable?

PS: [/COLOR][/FONT][FONT=Tahoma][COLOR=black]I've read that the Ubuntu Netbook Edition (was it the same of the file above?) has been merged into the Desktop Edition [/COLOR]from Ubuntu 11.04. Is it worth downloading it?
What about Aurora or EasyPeasy? I'm confused!!! :confused:
[/FONT][FONT=Tahoma][COLOR=black] 
Thanks
[/COLOR][/FONT]
Well come to Ubuntu 
Your laptop can run almost any Ubuntu version . I suggest you to downlaod latest version that is 11.10

---

### Post by nick-88 on 2011-11-29
[FONT=Tahoma]Thanks! I'll try and let you know! :)[/FONT]

---

### Post by nick-88 on 2011-11-30
I'm having some trouble with the boot from USB.
Hopefully I'll solve them and let you know.

---

### Post by asifnaz on 2011-11-30
> **nick-88 said:**
> I'm having some trouble with the boot from USB.
Hopefully I'll solve them and let you know.

what kind of trouble please explain so that I can help you .And can you tell how did you prepare Ubuntu USB ..?

---

### Post by nick-88 on 2011-11-30
I've had some troubles with the boot from USB, but I've solved them!
To run USB boot I had to:
- create a bootable USB with ubuntu11.10;
- insert it before starting the PC;
- press ESC repeatedly until a window with boot options comes out;
- select USB drive.
I hope this would be useful for someone else! :)
I tried it without installing. The first time the touchpad didn't work. I retried and now all seems to be working fine! :D
Now I'll create a partition and I'll install Ubuntu in it! I'll let you know how it works!

---

### Post by asifnaz on 2011-11-30
I am looking forward to your response towards Ubuntu . At start you may find something

less than ideal , don't worry , ask here and people on Ubuntu forums are more than happy to helps others .

Community will never let you down

---

### Post by nick-88 on 2011-11-30
So, it's very hard!!! :(
I've got another problem: I think 1Gb of RAM is not too large, so I prefer hold some memory for a swap partition.
The problem is that there are already 4 primary partitions:
- a 16 Mb partition for UEFI --> maybe it's better don't touch it;
- a 100 Gb NTFS partition with Windows7;
- a 15 Gb FAT2 partition (hidden) - maybe a recovery one? - ;
- a 183.07 Gb NTFS partition empty.
There's a maximum of 4 primary partitions and swap partition has to be a primary too, like Ubuntu partition.
I don't want to delete UEFI and the recovery partition because I'm afraid of making some mistakes and putting out of action everything!
What should I do?

---

### Post by Barfication on 2011-11-30
Hi,

since Windows Vista it's possible to shrink the Windows partition from within Windows itself. So you could make the 100 gb partition smaller. 

You can also change the size of the 183 gb partition. I think (but I am not sure) the 183 gb partion is to store data on. 

You can access the data from the NTFS partion from Windows and Linux. Ubuntu generally uses the ext4 filesystem. You cannot access an ext4 partition from within Windows. Windows does not support that.

So if you want to use Windows as well it might be wise to use the 183 gb partition so store your music and stuff on. 

Otherwise you could just remove the whole partition. 

After shrinking (and maybe removing) partitions you have empty space on your harddisc left. 

When you fire up the Ubuntu installer you can install it on the free space left on the drive. 

Good luck!

---

### Post by nick-88 on 2011-11-30
> **Barfication said:**
> Hi,

since Windows Vista it's possible to shrink the Windows partition from within Windows itself. So you could make the 100 gb partition smaller. 

Hi! The problem isn't memory, but it's the maximum of 4 partitions! So I have to decide what partition delete to make space for the swap one!
Would it be the same if I make a swap file?

---

### Post by Barfication on 2011-11-30
Sorry, 

I did not read well. 

Maximum of 4 partitions. Hmm. Bummer. 

If I understand well you can have a maximum of 4 **primary** partitions. 

Luckily you can make partitions inside partitions. Those are secundary partitions. 

So you can make a partition in the 183 gb partition for linux. In that partition then comes a partition for ubuntu and one for the linux swap. Inside the 183 gb partition you can make a partition for data as well. 

Hope it works!

---

### Post by roger_1960 on 2011-11-30
Hi

I have a dual boot on a 1011PX, very similar.

Suggest before you change anything you follow the asus instructions and create an external recovery backup which will allow reinstall of factory state if needed.  YUou can't do it after you have changed partitions (at least I couldn't!)

I deleted the 183Gb partition using gparted and then installed into the empty space (both ubuntu and swap were created as logical partitions within the space) by using the "install alongside exiting" option.  All works with no problems.  You should disable "fast boot" in BIOS before installing or grub might not work.

---

### Post by Barfication on 2011-11-30
Might be useful:

You can also edit your partitions using the Ubuntu live-cd.

The program you can use is called gParted. It's already installed on the live-cd.

---

### Post by Barfication on 2011-11-30
I was a bit too late. Roger already mentioned gparted. :-)

---

### Post by nick-88 on 2011-11-30
> **roger_1960 said:**
> Suggest before you change anything you follow the asus instructions and create an external recovery backup which will allow reinstall of factory state if needed.  YUou can't do it after you have changed partitions (at least I couldn't!)
Hi, Roger! It's the first thing I've done: I've made 2 backups: the first with Asus Recovery System and the second with the specific Windows7 tool. I don't know if they've saved the same files...

> **roger_1960 said:**
>  I deleted the 183Gb partition using gparted and then installed into the empty space (both ubuntu and swap were created as logical partitions within the space) by using the "install alongside exiting" option.  All works with no problems.  You should disable "fast boot" in BIOS before installing or grub might not work.
I also noticed that there was this option, but I wanted 2 fully indipendent systems and I've read that the "Install alongside exiting" option makes it work slowly!
I can't create a primary partition and then a logic one in the remaining space because it's "unusable"!

> **Barfication said:**
> The program you can use is called gParted. It's already installed on the live-cd.
I've tried with Gparted too, but it's the same problem!

What will it happen if I:
- delete Windows7 recovery partition - I've made 2 backups hopefully! - Will they work if the system crashes?
- delete EFI partition? Will BIOS and the overall system run properly?

---

### Post by jodlajodla on 2011-11-30
Hello!

Can you tell me if HD 6250 on EEE PC 1015 BX works well with Unity 3D, or are there any glitchs? Did you see any tearing (when you moving windows around - fast) or when you're playing video?

Thanks for booth answers!

---

### Post by nick-88 on 2011-11-30
I've got the [FONT=Tahoma]AMD® Radeon HD 6290 graphic card, but I haven't tried it so far! I've opened only the example video when I tried Ubuntu on my USB pen! It worked fine! =)
[/FONT]

---

### Post by roger_1960 on 2011-11-30
Hi again

By "install alongside existing", I don't mean using wubi. The option I mean will give you 2 independant systems.  Are you trying to reformat the space created using gparted?  I meant that you use the install function on the live CD to do that.

Yes, the asus recovery system should reinstall to factory state if needed (even to a new disk if installed).  Haven't tried it though!

---

### Post by Barfication on 2011-11-30
[B]@nick:
[/B]
I actually think the way Roger described is the way to go. I can't see how it makes things slower since you'll still get Ubuntu inside a separate directory. 

After deleting the empty 183 gb partition you will end up with 3 partitions. So there is 183 gb of space remaining for the creation of a fourth primary directory. I just checked on my laptop to see how it is partitioned. (It's installed in the same way Roger described.) The installer will make a fourth primary partition using the empty space and inside that partition you get a secondary partition for Ubuntu and an other for the swap. So you will end up with only 4 primary partitions.

You won't get an extra partition for your data from within Windows and Linux but I don't know if you even want that. 

I do not recommend deleting the Windows7 recovery partition! Better safe than sorry.

---

### Post by nick-88 on 2011-11-30
> **roger_1960 said:**
> By "install alongside existing", I don't mean using wubi. The option I mean will give you 2 independant systems.  Are you trying to reformat the space created using gparted?  I meant that you use the install function on the live CD to do that.
I've tried both the ways! Now I follow your suggestion! :)

> **roger_1960 said:**
> Yes, the asus recovery system should reinstall to factory state if needed (even to a new disk if installed).  Haven't tried it though!
I don't want to be the first to try this experience too!

---

### Post by Barfication on 2011-11-30
> **Barfication said:**
> [B]@nick:
[/B]
I actually think the way Roger described is the way to go. I can't see how it makes things slower since you'll still get Ubuntu inside a separate **directory. **


I meant **partition.** :cool:

---

### Post by nick-88 on 2011-11-30
I've deleted the 183 Gb partition and I've created 3 partition:
1. Ubuntu files;
2. swap partition;
3. empty space.

PS: I didn't expected the cam to work, but it worked perfectly! Awesome! :D

---

### Post by Barfication on 2011-11-30
Cool!

so I understand you already finished installation?

---

### Post by Barfication on 2011-11-30
Have you installed the proprietary AMD graphics driver?

---

### Post by roger_1960 on 2011-11-30
Great!

If you want (ever) to boot the Asus linux install I think you have to enable it from within W7.  It didn't appear in the boot list in my grub window at startup.

---

### Post by nick-88 on 2011-11-30
> **Barfication said:**
> Cool!

so I understand you already finished installation?
Yes!!! I'll try!

---

### Post by nick-88 on 2011-11-30
> **Barfication said:**
> Have you installed the proprietary AMD graphics driver?
No! If it's all ok, I won't touch anything!

---

### Post by nick-88 on 2011-11-30
> **roger_1960 said:**
> Great!

If you want (ever) to boot the Asus linux install I think you have to enable it from within W7.  It didn't appear in the boot list in my grub window at startup.
When I've restart, a screen with Ubuntu and Windows7 options was displayed! Too much easy!:KS

---

### Post by roger_1960 on 2011-11-30
Hi

Have fun with Ubuntu!  In a couple of months I bet you'll be back asking how to remove windows altogether.  If you do want to, by far the simplest way is to backup (always) and then do a clean install of ubuntu wiping the whole drive.  I'm going to wait for 12.04 before doing this.  I kept W7 because I had paid for it, but to be honest I never use it.

---

### Post by calmire on 2012-03-12
> **asifnaz said:**
> Well come to Ubuntu 
Your laptop can run almost any Ubuntu version . I suggest you to downlaod latest version that is 11.10

I just found it extremely SLOW running ubuntu 11.10 on this netbook. meanwhile it's quite fluent with win7 ult.
I dont know what's wrong .

---

