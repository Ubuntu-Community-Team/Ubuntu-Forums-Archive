---
title: "Dual Boot"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by daniell59 on 2008-08-20
Please forgive what may appear to be an ignorant question. My knowledge is limited.
I am in the process of building a new computer.
I would like to run both Vista and Ubuntu. Would I be better off with two hard drives one for Windows the other for Ubuntu?
My thought is that if I mess up with Ubuntu, the problem will not affect windows.

Thanks

---

### Post by skymera on 2008-08-20
I dual boot XP and Ubuntu, on 2 seperate hard drives.

I find that if GRUB is messed up etc Windows can still boot from the other hard drive.

As said below you can run both from one disk with partitioning.

---

### Post by pmsumner on 2008-08-20
You can happily run Ubuntu and Windows on the same HDD.  There's really no need to do it on separate disks.

---

### Post by tarps87 on 2008-08-20
You can use either, you will need to use two partitions which won't interfere with each other. The only advantage with two is if you install the grub (allows you to select which os you want to load) and Ubuntu on one drive and vista on a slave/ second drive you can remove the Ubuntu drive set the vista on to master and it will work without having to repair the boot sector.
If you want any of this explaining in more detail feel free to ask

---

### Post by Sef on 2008-08-20
Whatever way you install Vista and Ubuntu make sure that Vista is on the first hard drive (hda) or on the first partition (hda1).

---

### Post by KrispyDavis on 2008-08-20
> **Sef said:**
> Whatever way you install Vista and Ubuntu make sure that Vista is on the first hard drive (hda) or on the first partition (hda1).

Does this also apply to installing XP and Ubuntu?

---

### Post by nothingspecial on 2008-08-20
Yep

---

### Post by KrispyDavis on 2008-08-20
Thanks.

I have one further question:
I currently have my documents on a partition of my master drive and my music folder on a slave drive. Will I be able to access these from Ubuntu?

---

### Post by nothingspecial on 2008-08-20
You will be able to access the external drive from Ubuntu no problem. As for the other I don`t know, the only partition I`v ever created is a 100% Ubuntu one.
However I would advise backing up your docs and unmounting your external drive before you install either os - I remember a post along the lines of "Help, I just installed Ubuntu on my dads PC, I chose use entire disk. Have all his files gone?"

---

### Post by xouns on 2008-08-20
I'm dual booting XP and Ubuntu and i see all my drives (NTFS, Ext3 and Fat32) using Ubuntu. Sadly, Xp cannot read the Ext3 drive (Ubuntu main), so that is the only drawback. This will only make me use Ubuntu more, though ;)

---

### Post by sandysandy on 2008-08-20
yes. as long as u do not overwrite them during installation.

---

### Post by mlentink on 2008-08-20
> **xouns said:**
> Sadly, Xp cannot read the Ext3 drive (Ubuntu main), so that is the only drawback. This will only make me use Ubuntu more, though ;)

Have a look at [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tarps87 on 2008-08-20
> **Sef said:**
> Whatever way you install Vista and Ubuntu make sure that Vista is on the first hard drive (hda) or on the first partition (hda1).

I have XP on my second hard drive (set to slave) and it runs fine. I've managed to get a virus which forced me to reinstall, so I just pulled out the Ubuntu drive set the XP drive to master, reinstalled it and swapped the dives back without having to mess about with the boot loader.

---

### Post by daniell59 on 2008-08-20
> **Sef said:**
> Whatever way you install Vista and Ubuntu make sure that Vista is on the first hard drive (hda) or on the first partition (hda1).

Please explain, why should Vista be on the first hard drive?

Thanks

---

### Post by sandysandy on 2008-08-20
> **daniell59 said:**
> Please explain, why should Vista be on the first hard drive?

Thanks

i have windows on second partition and am facing no issue.

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by tarps87 on 2008-08-20
> **MarkieB said:**
> a word of warning though: do you want all those windows viruses to have access to all your partitions?


That's the reason I don't use it. I use to share my music on a fat32 partition and one day I booted XP walked off while it loaded only to come back and it 'repairing' the shared partition. It went through truncating all the file, I have never figured out why it did this, it was just lucky I hadn't deleted it off my Ubuntu drive.
Thinking about it I only have a Ubuntu and a recently reinstalled xp one so I may have 60GBs floating around unpartitioned. #-o

---

### Post by falcon61102 on 2008-08-20
daniell59,

The reason most people suggest having Vista or any windows install on the first drive is because microsoft initially designed it to run off the first hard drive/partition and as we all know, windows is not the most flexible OS.  

There are ways around this as you have read, but for the least amount of complications, it is easier to install your windows OS first and then install Ubuntu either on the second parition or hard disk.  No matter what physical order they are in, you can still choose which one you wish to boot first or automatically so it really doesn't matter once you set them up.  It's just to make the setup itself easier on you.  Less work, that's all.

---

### Post by xouns on 2008-08-20
> **MarkieB said:**
> a word of warning though: do you want all those windows viruses to have access to all your partitions?

Hmmm, nice cautioning...seems that this would be a backup plan, in case things go wrong with Ubuntu. Moreover, I've never liked installing programs with kernel access to Windows, or divers or whatever, for all the good reasons. I have a stable reliable install, and like to keep it that way. Thanks for the tip, though!

---

### Post by Bucky Ball on 2008-08-20
> **xouns said:**
> Sadly, Xp cannot read the Ext3 drive 

You got it. Windows does not recognise EXT3 at all, which is why you need the FAT32 to share files between the two OSs. Something to keep in mind when planning partitions. :)

---

### Post by Paqman on 2008-08-20
> **Bucky Ball said:**
> You got it. Windows does not recognise EXT3 at all, which is why you need the FAT32 to share files between the two OSs. Something to keep in mind when planning partitions. :)

A shared partition doesn't have to be FAT32, you can use NTFS.

---

### Post by Bucky Ball on 2008-08-20
Hmm. I was under the impression that there were problems writing reliably to NTFS drives from Ubuntu, but not reading. I will do some more surfing on that one ...

---

### Post by daniell59 on 2008-08-20
> **skymera said:**
> I dual boot XP and Ubuntu, on 2 seperate hard drives.

I find that if GRUB is messed up etc Windows can still boot from the other hard drive.

As said below you can run both from one disk with partitioning.

I am ashamed to say that I do not know what GRUB is.

---

### Post by sandysandy on 2008-08-20
to quote wikepedia 
>  GNU GRUB ("GRUB" for short) is a boot loader package from the GNU Project. GRUB is the reference implementation of the Multiboot Specification, which allows a user to have several different operating systems on their computer at once, and to choose which one to run when the computer starts. GRUB can be used to select from different kernel images available on a particular operating system's partitions, as well as to pass boot-time parameters to such kernels.

GNU GRUB developed from a previous package called the Grand Unified Bootloader (a play on grand unified theory). It is predominantly used on Unix-like systems; the GNU operating system uses GNU GRUB as its boot loader, as do most general-purpose Linux distributions. Solaris has used GRUB as its bootloader on x86 systems since the Solaris 10 1/06 release. 

see this link also

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

regards

---

### Post by daniell59 on 2008-08-20
If I am going to use two hard drives, do I need to install GRUB? 
Also, By having two separate hard drives, will it make it less likey for a virus to jump to the second hard drive?

Thanks

---

### Post by xouns on 2008-08-20
Install XP first, then Linux. GRUB will be installed automagically, configured and all. It only chooses to put Linux as default, so if you want to boot XP, stay with your computer, though you may change this if you like.

Virusses can jump from one hdd to another, but since Linux is very different from XP it would do little to no damage. However, it can still erase the whole partition from either Linux or XP. So always be carefull.

---

### Post by cybrsaylr on 2008-08-21
> **daniell59 said:**
> If I am going to use two hard drives, do I need to install GRUB? 
Also, By having two separate hard drives, will it make it less likey for a virus to jump to the second hard drive?

Thanks

I have two dual boot setups, one for over a year. Both use 1 HDD XP/Ubuntu the other Vista/Ubuntu and have been sharing files between the partitions with no problems or viruses at all.

---

### Post by Bucky Ball on 2008-08-21
> **cybrsaylr said:**
> I have two dual boot setups, one for over a year. Both use 1 HDD XP/Ubuntu the other Vista/Ubuntu and have been sharing files between the partitions with no problems or viruses at all.

Ditto. And again, Linux is *not *Windows. You will quickly realise this and your approach and  mindset will change accordingly.

---

