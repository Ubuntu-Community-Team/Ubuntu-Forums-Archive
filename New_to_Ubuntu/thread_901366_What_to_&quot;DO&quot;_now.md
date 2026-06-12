---
title: "What to &quot;DO&quot; now?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by FireDancers on 2008-08-26
The 64 bit version mentioned I could install without partitioning, at least I think that's what the install page said.

That sounded easy, just click that tab and it automatically installs the "dual boot" which also keeps Vista & it's programs in place if needed.  Did I get that right?  

Running from the Live CD there isn't any reason to load software, since they won't be downloaded to a hard drive, right?

Am I understanding this correctly?  I'll wait a day or two before installing anything, to let a few of you chime in.  

Also, what are the "other" ubuntus for?  I mean the "k"ubuntu, etc.?  I guess one's a "lite" version for slower computers & laptops?

Another question, there's a ton of software available....So, how do you decide which to try?  Is there a list of the "Best" (or better) ones?  I don't have time to try 28,000 downloads...or even read that many titles & descriptions!  Any tips?




thanks,
Glenn

---

### Post by nicedude on 2008-08-26
The 64 bit version mentioned I could install without partitioning, at least I think that's what the install page said.

You can't really install any Linux without it having its own partition to live on, outside of Wubi that is which is a Linux install inside windows and I wouldn't recommend it.

That sounded easy, just click that tab and it automatically installs the "dual boot" which also keeps Vista & it's programs in place if needed. Did I get that right? 

YEP

Running from the Live CD there isn't any reason to load software, since they won't be downloaded to a hard drive, right?

NOPE

Am I understanding this correctly?  I'll wait a day or two before installing anything, to let a few of you chime in.  

READ A DUAL BOOT VISTA & UBUNTU GUIDE

Also, what are the "other" ubuntus for? I mean the "k"ubuntu, etc.? I guess one's a "lite" version for slower computers & laptops?

UBUNTU & KUBUNTU are of similar speed etc one uses the Gnome desktop environment and the other uses KDE ( you should be able to see which one uses KDE ). Go with Ubuntu for better support and more users to help you out etc.

Xubuntu is for older PC's and uses the XFCE desktop, which is lighter on resources.

Another question, there's a ton of software available....So, how do you decide which to try? Is there a list of the "Best" (or better) ones? I don't have time to try 28,000 downloads...or even read that many titles & descriptions! Any tips?

Just be glad there are 28,000 choices ( most are not actually software but libraries and other things software needs but there are allot of software choices ). With Vista you get notepad and microsoft drawing program that would bore a 2yr old, just hey give us a bunch of money & thanks sucker. Now you have a choice that costs 0$ and can perform just as well when setup correctly, what could be better than that ?

---

### Post by echo314 on 2008-08-26
Well you can install software in the LiveCD to see how it works with your hardware. For most programs this does not matter, but I'm not sure of your needs. 

The other flavors of Ubuntu (Kubuntu, Xubuntu) have different default desktop environments, which control the look and feel of your user interface. You can always install one, and then try another by installing it through the repos and then just choosing it when booting up (for example, I can choose  between Gnome and KDE4.)

For your software needs, just ask. I always find the best suggestions on these forums.

---

### Post by FireDancers on 2008-08-26
You can't really install any Linux without it having its own partition to live on, outside of Wubi that is which is a Linux install inside windows and I wouldn't recommend it. [quote]



So, does the 64bit version automatically partition so I don't have to worry about understanding that?  It seems like I'd want it to put ubuntu on the second HD since that one is totally empty.  Is that right, or does it matter?

---

### Post by Sef on 2008-08-26
> So, does the 64bit version automatically partition so I don't have to worry about understanding that? It seems like I'd want it to put ubuntu on the second HD since that one is totally empty. Is that right, or does it matter?

There is an option to use the whole drive.   Make sure that you are installing it on the empty hard drive and not the one with Windows on it.   If Windows is not on the primary hard drive, then there may be boot problems.

If you are not sure, which is the empty one, then from the Live CD, System > Administration > Partiton Manager.   hda/sda will be your primary hard drive and hdb/sdb will be your second hard drive.

---

### Post by WRDN on 2008-08-26
> **FireDancers said:**
> **So, does the 64bit version automatically partition** so I don't have to worry about understanding that?  It seems like I'd want it to put ubuntu on the second HD since that one is totally empty.  Is that right, or does it matter?

Yes and no. The installer can create the required partitions itself (root and swap), but if you want to dual boot with Vista, then you may want to create the partitions manually. This can be done with Vista's own disk manager, or a different tool such as GParted on the Ubuntu LiveCD. You would need to remove the partition(s) on the second drive, then leave the "unallocated space" as it is. Now, start the installer, and at the partitioning stage, select to use the second drive. This will use the unallocated space, and automatically create the root and swap partitions in it. If you want a finer degree of control, then select Manual partitioning (on the partitioning stage of the installation) and you can assign the root and swap partitions, among others. Many would recommend you create the partitions before the installation, then select Manual partitioning. From reading partitioning documentation, it is recommended you create a root, swap and home partition. This allows you to reinstall Ubuntu without losing your files or program settings (which are stored in the home partition).

---

### Post by pi.boy.travis on 2008-08-26
Another thing, make sure you backup all your important data before doing ANYTHING with partitions.

---

### Post by nicedude on 2008-08-26
You can put it on the second hard drive but this can cause complications ( others will say it wont blahblah and they are right in that if done right it won't but I have sat and helped half a dozen people here in the past that managed to screw up their system doing so ). The complications are kinda complicated as I would have to explain how grub bootloader loads etc and you should just read up on this stuff before attempting it, if you want it to work right the first time ( please google the following two subjects "vista hardy dualboot" & "how does grub work" and read-up as these two topics will cover most of the basics of what you will need to do and such.

In general I like to use 1 disk for systems and then all the other physical disks for data, this way I keep it clean and simple.

As to whether it will do everything for you, I am not sure because I never use the "let partitioner choose" option when installing ( I am not a big fan of letting other things choose how it will set itself up ) and instead I always use the manual partitioner. In general you would need to use live CD and resize your Vista partition to make room for Ubuntu ( how big I have no idea as I have no idea what size your drive is but I like 20GB-30GB for the Ubuntu partition ) and after making the room on the partition you would reboot with the livecd again ( this will reset the partition tables on the disk ) and then choose install and when I partition I just make a 2GB SWAP partition and a 20GB-30GB EXT3 partition with a mount point of / ( which means root and must be done to work ) then it will install and configure everything else for you.


Hope this helps

---

### Post by pi.boy.travis on 2008-08-26
I agree.  1st HD for OS, 2nd for data, 3rd mirror first, 4th mirror 2nd

---

