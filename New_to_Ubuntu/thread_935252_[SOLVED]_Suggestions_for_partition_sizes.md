---
title: "[SOLVED] Suggestions for partition sizes"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by akelsall on 2008-10-01
While waiting for my new HDD to arrive, I've been reading some threads and have some ideas of how I should partition my HD. However, I'd like some more of your opinions. Here are the details. 

New HDD size: 500Gb

What I'm planning to do with it:

1. run Ubuntu as my host OS (of course!)

2. possibly run VMWare to run Windows until I learn enough about Linux to ditch it. I really don't want to dual boot because it's just a pain having to reboot to switch between OS's.

3. Run Dynamips (a program that simulates Cisco routers)

4. Run Cisco Call Manager (which is Linux-based)

5. Copy all my user data from my old drive to this one and keep the old HDD as a backup for a few months.

So, a few questions.

I've read where people suggest 10Gb-15Gb for the root directory. Is that sufficient?

I'm guessing I need to create an NTFS partition to run Windows on, correct? If so, would 10Gb be enough?

Swap file size. There seems to be a lot of opinions on this one. Some say 2Gb will be fine, others say 2X your RAM size. I've got room to spare, but should I set aside 6Gb for swap (currently have 3Gb RAM installed on a P4). 

If I want to copy files from my old drive (running Windows), can I simply drag and drop the files into Linux, or is there an intermediate step I must take? If so, does it apply to all file types? That is, do I need that intermediary step for both data files and say, MP3 files, or just the data files?

Right now, I have my Windows HD split into three partitions. As we all know, Windows just labels the logical partitions D, E, etc. How can I do something similar with Linux, or do I even NEED to do that with Linux?

Thanks,

Andy

---

### Post by LowSky on 2008-10-01
15GB would seem fine to me, I doubt you will use more, but a /home partition should be where you store your files and should be big enough to fit what you need.
Swap file is where many people have dissagreements, personally I don't even use Swap. My computer is fast enough and has enough memory that Swap never is utilized, I also never use sleep or hibernate so you can add those to my reason. If you think you need it, and you never know go by the rule of double your RAM, beucase things like Hibernate and suspend copy what on your RAM to your SWAP.

COpy what kind of FIles? MP3/documents/videos... youll be fine. Games and programs wont workout so well.

Linux will use 2 partitions from a normal install, one for Root ("/") and one for Swap. May I suggest a partititon for your /home directory. The best thing to do is make 2-3logical partitions then make one extended, use the extended for all you other files or even other operating systems and/or SWAP.

---

### Post by Paqman on 2008-10-01
There's no right or wrong way to set your system up, really, but here's my take on your questions:
> **akelsall said:**
> 
I've read where people suggest 10Gb-15Gb for the root directory. Is that sufficient?


Not including the user's directories in /home, Ubuntu would fit in well under 10GB (probably more like 6-8GB). Since users store their data in /home, that's the one that needs space.

You can mount /home on a seperate partition. In fact it's very handy to do. If you did that, then 10-15GB for / is tons. If you're leaving /home on the same partition as / (which is the default install) then make it as big as you can, to give you room for your data.

The default install, using the whole hard drive, will create a small swap partition and use the whole rest of the drive as / (including /home). A common alternative is: small swap, 10GB /, the rest for /home.

> 
I'm guessing I need to create an NTFS partition to run Windows on, correct? If so, would 10Gb be enough?


Not if you're only running it as a VM. The VM would live on your Ubuntu partitions.

If you are installing Windows dual-boot, then it depends on what apps you're going to install. General rule of thumb: 20GB for XP, 30ish for Vista.

> 
Swap file size.


A lot of the advice you'll get is outdated. Now that PCs have large amounts of RAM, swap is less important. If you plan to use hibernation, you'll need your swap to be at least as big as your RAM. Otherwise with 3GB you'll probably never touch swap, so I wouldn't bother making it any bigger than 1GB. 

> 
If I want to copy files from my old drive (running Windows), can I simply drag and drop the files into Linux, or is there an intermediate step I must take? If so, does it apply to all file types? That is, do I need that intermediary step for both data files and say, MP3 files, or just the data files?


Ubuntu will quite happily be able to browse your old NTFS drives/partitions. So you can either copy them over, or just leave them where they are (effectively using your old NTFS partition as a data partition) The only problem you might have is with file extensions that are specific to some weird Windows app. Even those aren't too bad, since most of the Windows-specific stuff (eg: .wmv, .doc, .xls) can actually be opened by Linux apps.

> 
Right now, I have my Windows HD split into three partitions. As we all know, Windows just labels the logical partitions D, E, etc. How can I do something similar with Linux, or do I even NEED to do that with Linux?


Partitions are numbered differently. On the first physical drive they would be sda1, sda2, etc. If you had a second drive it would have sdb1, sdb2, etc.

What you'll actually see when from the Ubuntu desktop though is  devices enigmatically named "xxGB Volume". So you won't see either your Windows drive letters or their Linux designations. If you want more descriptive names than just the size, then it's pretty easy to mount them to a folder with a more descriptive name (you could even mount them to folders called something like "E Drive" if you wanted)

---

### Post by akelsall on 2008-10-01
Thanks for the feedback. I have a couple of follow-up questions if you don't mind. You mention using 2-3 logical partitions, making one of the extended. Are you referring to the ext3 filesystem, or something else?

I'm having a little difficulty wrapping my head around the partitions thing (in respect to Linux). I've been a Unix end-user for some time, but have never tried running Linux on a PC. So, for example, right now, I have my WinPC HD set up with three partitions (C, D, and E). Here's where I'm confused. I read that user data goes under /home. I Understand that part. Here's where I'm confusing myself. If I want to "emulate" the structure I have on my WinPC, do I create two more partitions for this (in addition to root, swap, and /home)? Hope this is making sense. 

Thanks,

Andy

---

### Post by akelsall on 2008-10-01
Thanks, for the feedback. I do recall reading that it's a good idea to create a separate /home partition so if things get corrupted in the / directory, you can wipe it out and rebuild it without damaging you user data. Is that correct?

Are you saying that if I run VM, I can install Windows as a VM without having to partition any part of the drive as an NTFS filesystem? That would keep things simple. 

Good info on using a mount point to "rename" a drive!

Thanks,

Andy

---

### Post by Kellemora on 2008-10-01
Hi Ak

/sda1 is equivalent to Drive C: on Master hard drive.
/sda2 is equivalent to Drive D: a partition on Master hard drive.

/sdb1 is equivalent to Drive E: on SLAVE hard drive (2nd hard drive)
/sbd2 is equivalent to Drive F: a partition on Slave hard drive.

Etc.

If you have a Maxtor Drive as your Master hard drive and a 
Seagate drive as your slave drive.
/sda would be the Maxtor and /sdb the Seagate.

The number following it is which Partition on that hard drive you are looking at.
As an example:  You may have WinDoze on /sda1 and Ubuntu on /sda2 in a dual boot single hard drive system.

TTUL
Gary

---

### Post by Paqman on 2008-10-01
> **akelsall said:**
> Thanks for the feedback. I have a couple of follow-up questions if you don't mind. You mention using 2-3 logical partitions, making one of the extended. Are you referring to the ext3 filesystem, or something else?


Linux generally uses ext3, yes. Your swap partition would be formatted simply as swap. Extended partitions don't have their own filesystem, they're just a wrapper that contains partitions of other filesystems.

Note that Windows can't read ext3 by default, but Linux can read and write to the Windows NTFS filesystem.

> 
I'm having a little difficulty wrapping my head around the partitions thing (in respect to Linux). I've been a Unix end-user for some time, but have never tried running Linux on a PC. So, for example, right now, I have my WinPC HD set up with three partitions (C, D, and E). Here's where I'm confused. I read that user data goes under /home. I Understand that part. Here's where I'm confusing myself. If I want to "emulate" the structure I have on my WinPC, do I create two more partitions for this (in addition to root, swap, and /home)? Hope this is making sense. 


Root is a bit like C drive. It's the only partition you're guaranteed to have. Mounting /home on it's own partition would be like taking the Windows Documents and Settings folder, and giving it a drive letter. If D and E are just for data, then to emulate that you could create actual partitions if you like. Just remember that you can only have 4 primary partitions, so if you want to create lots you'll need an extended partition to create some of them inside.

> **akelsall said:**
> Thanks, for the feedback. I do recall reading that it's a good idea to create a separate /home partition so if things get corrupted in the / directory, you can wipe it out and rebuild it without damaging you user data. Is that correct?

Yep, it also means you can share a single /home between different distros, and that you don't lose all your settings and data if you reinstall.

> 
Are you saying that if I run VM, I can install Windows as a VM without having to partition any part of the drive as an NTFS filesystem? That would keep things simple. 


Yep. VMs run inside completely virtual hardware. The actual hardware you've got doesn't need to be compatible with the virtualised OS at all.

---

### Post by akelsall on 2008-10-02
Thanks to all of you for the clear, detailed info. This will definitely help me when I begin setting up Ubuntu in the next few days.

Andy

---

