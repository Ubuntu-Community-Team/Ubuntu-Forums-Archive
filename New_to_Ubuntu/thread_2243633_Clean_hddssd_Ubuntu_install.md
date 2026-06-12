---
title: "Clean hdd/ssd Ubuntu install"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by henk418 on 2014-09-10
Hello,

I've been searching for a few days but I'm not sure/understanding the things I can find so I hope someone can help me out.

I have a Asus Ultrabook (UX52VS) with a 500GB HDD and a 24GB SSD, I screwd up the recovery partitions and more so I can't get the original windows back unless I will send it for a "repair". But as many like you, I hate windows so I would like to install Linux only.

Should I install ubuntu on my 24GB SSD or on the bigger 500GB HDD?
And how do I setup the SSD for cache like the stock laptop/windows does? (If I should install Ubuntu on the HDD)

I'm no expert but still learning :)

---

### Post by christopher9 on 2014-09-10
If the install finds any evidence of another OS, it will prompt you during the install process on what you desire to do:  install alongside another OS, erase any other OS, install with LVM, or 'something else' ....if you want Ubuntu installed by itself,  select to 'erase' any other OS and let it take care of partioning the drives...it knows what to do....I have a SSD/HDD hybrid laptop and it runs perfectly fine after installing this way...

---

### Post by webra on 2014-09-10
Hi !

I have a similar setup on my computer and I use the SSD for the root partition / and the 500Gb Hd för the /home partition.

---

### Post by henk418 on 2014-09-10
@cristopher9: installing is no problem for me, I just wan't to know what's the best solution. when Windows was installed on the hdd I've had Linux on the SSD and it was fast as a dragracer, but I read different opinions about data loss/etc...

@webra, you mean installing linux on the ssd and move the home partition in linux to the hdd?

---

### Post by Mark Phelps on 2014-09-10
> And how do I setup the SSD for cache like the stock laptop/windows does? (If I should install Ubuntu on the HDD)


The closest thing to that is using the SSD for swap -- but that would be an ENORMOUS waste of SSD space!  It would actually work faster if you installed Ubuntu to the SSD and used the hard drive for your large files.

---

### Post by oldfred on 2014-09-10
I have seen several users install / (root) partition to SSD and /home and or data partitions to rotating hard drive.
Often better than caching as system is running from SSD, not running from slower HD.

I also prefer to include /home inside / so user settings which are also system related and used more are faster. But link all data folders like Music, Documents etc to data partition(s) on hard drive. My /home is 2GB of my 11GB install in a 27GB / partition. But most of the 2GB is my .wine for Picasa, so hidden user settings are very small. But I also move some program folders that have lots of data like Firefox or Thunderbird profiles into data partition. Any new program that starts storing lots of data in /home soon gets moved.

If totally new install you can install in UEFI or BIOS boot mode, but I suggest you keep gpt partitioning. Windows only boots from gpt partitioned drives with UEFI, but Ubuntu can boot with either BIOS or UEFI from gpt if correctly supporting partitions efi for UEFI and bios_grub for UEFI are on drive.

I also like to have another install on hard drive as emergency boot, test install for experimenting and or whatever. Allocating 15 or 20GB on larger hard drives is not a lot.

You will have to turn off Intel SRT and remove any RAID meta-data that SRT has created on drives.
Some other users posted this info with older versions, but with 14.04 the installer does work a bit better:
 > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

I would include then an efi partition on both drives, so each drive could boot without the other, even if currently you do not want to install another Ubuntu on hard drive. It is difficult to add efi at beginning of drive later if it has lots of data.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by henk418 on 2014-09-10
@ mark

that is indeed what I've experienced before, but I wan't to be sure I do it right.
At this moment I have Ubuntu on the HDD and it is 3 times slower when it was installed on the ssd.

I read some things about data loss on ssd's after a few years, is this something to worry about?
Not that I have very important things om my laptop, but it would be disappointing when I didn't backup my stuff..

---

### Post by henk418 on 2014-09-10
thanks oldfred and the rest :) for the info, I will try it later these days..

---

### Post by oldfred on 2014-09-10
Not sure about the smaller SSD that are built in. 
But they say the newer SSDs have lives comparable to hard drives. 

But never assume any drive lasts forever, have good backup procedures.
If system is on SSD, you really only need to backup /home and /etc. Perhaps a few other manually configured files like grub if you edit it. Almost as easy to reinstall as it is to restore, as your user settings are all in /home and that must be well backed up.

---

### Post by WinEunuchs2Unix on 2014-09-10
> **henk418 said:**
> @ mark

that is indeed what I've experienced before, but I wan't to be sure I do it right.
At this moment I have Ubuntu on the HDD and it is 3 times slower when it was installed on the ssd.

I read some things about data loss on ssd's after a few years, is this something to worry about?
Not that I have very important things om my laptop, but it would be disappointing when I didn't backup my stuff..

I've read that SSD life is reduced by writing to it.  For this reason some recommend putting programs on there only because a program is only read after it has been written once.  Purists rant about Linux being superior to Windows because their programs are defined as read/write where as Linux is read only some place deep in the file system.

I've also read that large IT shops will swap out their SSD's every 3 months if they are being written to.  We're probably talking 100,000 transactions a day I guess.

Cache set defaults to read only, but data is still written to the cache.  However when a program saves data the option called "write-through" means it isn't written to the cached SSD but rather to the HDD.  If you pick the "write-back" option then data is written to the cache first and then to the HDD when it is idle.  A system shut-down (I mean "sudo reboot" and not unplugging the machine) is delayed while the SDD's cached data is written to the HDD.

Most people will use "write-through" instead of "write-back" for safety in which case the SSD's will have the longest possible life.  SSD used as a HDD has nothing to do with caching so of course it is read and written to all the time.

Because I'm laptop only which has a battery I'll be using "write-back" after Windows 7 has been running reliably for a couple weeks and I get comfortable with it (only 3 days using Win7-64 after 7 years of Win Vista-32).

I'm still trying to figure out how to install LINUX using the 11gb data portion of the 32 GB mSata and letting Intel SRT keep the non-volatile 19gb partition as it's own private Windows cache.  I'm assuming after I shut off Windows the 11gb portion for Rapid Start will be empty and the 19gb portion will still hold HDD accelerated data but more research is needed.

Anyway you slice it or dice it it's going to be fun, interesting and fascinating.

@oldfred: I read that dmraid is obsolete and intel recommends adadm now.  I have no experience with either.

---

### Post by WinEunuchs2Unix on 2014-09-10
My thoughts are to keep all of Linux (kernel and user space) on the HDD.  Why have the kernel modules on the SDD when they load into RAM and stay there anyway?  It's not like Windows DLL hell where program stuff is flying in and out of RAM all the time.  Or am I wrong here?

So I'd like to use bcache on the SDD to accelerate user space programs like google and nautilus for faster response time in those applications.  I also use Apache Open Office and those spreadsheets and word-like documents should be a lot snappier.  In a couple of years I'll be compiling kernels so I guess I'll have 1TB SSD's for everything and no cache will be needed but in the mean time the 32 gb SSD with 11 gb devoted to Linux cache to speed up the HDD seems like the best plan.

Maybe for christmas I'll buy a new 128gb or 256gb mSATA SSD to use as a cache for a new 1TB HDD.  The SDD can double as a drive to hold programs in a dedicated partition.  Intel SRT (Smart Response Technology) can only use up to 60GB for Windows I've read-- so there will be lots left over for Linux.

I've asked on another thread that any help setting up bcache on brand new HDD and SDD partitions would be appreciated.  Especially caveats when Intel SRT (Smart Response) is using 19GB for caching and 11 GB is reserved as system data presumably for Intel RST (Rapid Start).

Also I'm a little fuzzy on the "fake RAID" Intel uses and how it might impact bcache or Linux real RAID software.

---

### Post by Slim Odds on 2014-09-10
With ANY OS, you should be putting the system on the SSD. The vast majority of OS activity is reading executable files from disk and that where the SSD rocks. The old days of being overly concerned about writes is long gone for several reasons: modern SSD's have a much greater number of write cycles in their lifetime; all modern drives redistribute the writes around the drive to spread the wear out over the entire drive; TRIM is included in all major OS's, including Ubuntu. Even swap is fine as long as it's not going on continuously. If that is the case, you need a better system.

---

### Post by WinEunuchs2Unix on 2014-09-10
> **Slim Odds said:**
> With ANY OS, you should be putting the system on the SSD. The vast majority of OS activity is reading executable files from disk and that where the SSD rocks. The old days of being overly concerned about writes is long gone for several reasons: modern SSD's have a much greater number of write cycles in their lifetime; all modern drives redistribute the writes around the drive to spread the wear out over the entire drive; TRIM is included in all major OS's, including Ubuntu. Even swap is fine as long as it's not going on continuously. If that is the case, you need a better system.

That reminds me I have to move the "Odds" album from HDD iTunes to iPod.

Well I backed up "ANY OS" aka Windows 7 last night and it took 5 dvd's which at 4.7gb each is probably 20gb for the OS.  In reality I only use a fraction of the OS so why have it all on my 32gb SSD?

Thanks for the update on modern NAND used in SSD's.

I read something about TRIM last night is that something I need to install to use bcache?

---

### Post by Slim Odds on 2014-09-12
> **WinEunuchs2Unix said:**
> That reminds me I have to move the "Odds" album from HDD iTunes to iPod.

Well I backed up "ANY OS" aka Windows 7 last night and it took 5 dvd's which at 4.7gb each is probably 20gb for the OS.  In reality I only use a fraction of the OS so why have it all on my 32gb SSD?

You might want ask Microsoft that question. Was it backing up your data too?
I have a tons of stuff installed on my Ubuntu / paritition and it's about 7.1 GB

> **WinEunuchs2Unix said:**
> Thanks for the update on modern NAND used in SSD's.

I read something about TRIM last night is that something I need to install to use bcache?
One problem (there are many others) with the Internet is that there is a LOT of stale information in forums, blog, etc.
Particularly with the current pace of change in technology and computers.

TRIM is installed and executed automatically if Ubuntu detects an SSD (it's in /etc/cron.weekly).

---

### Post by WinEunuchs2Unix on 2014-09-12
> **Slim Odds said:**
> You might want ask Microsoft that question. Was it backing up your data too?
I have a tons of stuff installed on my Ubuntu / paritition and it's about 7.1 GB


One problem (there are many others) with the Internet is that there is a LOT of stale information in forums, blog, etc.
Particularly with the current pace of change in technology and computers.

TRIM is installed and executed automatically if Ubuntu detects an SSD (it's in /etc/cron.weekly).

OK.  I read a little bit about TRIM and it mentioned how it was a garbage collector to stop the SSD from caching too much irrelevant data from the HDD or something like that.  Because you say it's installed automatically I don't have to worry about learning more about it for a couple of weeks.

You are correct about the stale information because I've read 20 or more misleading links until I found this one: [https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows](https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows)

The gentleman has two 128 GB SSD's for caching + OS permanent installation.  He has two 1 TB HDD's for Data.  He dual boots with Windows 8 and Debian (sort of Ubuntu's Sister if you will).  He's using bcache under Linux (like I want to do) and Intel SRT under Windows (like I am now).  The difference is his SSD has an extra device for 8 times the size and he has an extra HDD for 4 times the data size.

He has written the meat & potatoes of using Linux bcache which includes other people's questions and answers in a debate style at the bottom of the web page.

---

### Post by henk418 on 2014-09-13
Thank you all, very much!

I have installed Ubuntu @ my SSD, moved the home partition by following these steps: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I'm smiling again :D

---

### Post by redrumrogue on 2014-09-13
A little late I know but here's my two cents (and it may only be worth that much!)  ... My machine has a 128GB SSD and a few HDDs, some of which are clubbed together in a logical volume.  I've installed ubuntu on the SSD just using the default partitioning settings (i.e. all of / is on the SSD including /home).  The installer will also create  swap partition automatically which will be automatically sized according to how much RAM you have.  If your SSD is only 24GB then I would be a little weary of this as if you have say 16GB of RAM then swap may take up most of the SSD!  I'm not sure how the installer would handle this scenario but you may have to manually set the swap partition size to have more control over that.  Anyway ... so my system storage is something like this ...

128GB SSD (/dev/sda) with / and swap on it
4TB logical volume (/dev/data/lvdata) - on this volume I have manually created my Downloads, Documents, Videos, Pictures, Music folders (mirroring what you get in your /home folder) and stored all my personal data in these folders.

After installing ubuntu on the SSD I edited my /etc/fstab file and added a line to mount my /dev/data/lvdata volume on /mnt/data and then added additional lines to "bind mount" the folders on my data volume on the empty folders in my /home folder.  Here is an extract from my /etc/fstab file ...

#/dev/data/lvdata
UUID=fac95f74-ae2b-412f-b799-93724804323e    /mnt/data    ext4    defaults    0    2
/mnt/data/Documents                /home/justin/Documents    none    bind
/mnt/data/Music                    /home/justin/Music    none    bind
/mnt/data/Videos                /home/justin/Videos    none    bind
/mnt/data/Pictures                /home/justin/Pictures    none    bind
/mnt/data/Downloads                /home/justin/Downloads    none    bind

This effectively redirects my /home folders to the folders on my HDD drive volume ( eg:  /home/justin/Documents is "redirected" to /mnt/data/Documents).  In this setup all user settings etc which are stored in /home/justin is still on the SSD but all my personal data is stored on the bind mounted folders on the HDD.   The advantage of doing this is that in the event of a re-install of the OS on your SSD you can just do a straight forward default install where everything goes on your SSD without affecting any data on your HDDs.  All user settings will be lost (no left overs from the previous installation) but your personal data will not be touched. This works very well for me.

---

### Post by Slim Odds on 2014-09-13
> **WinEunuchs2Unix said:**
> OK.  I read a little bit about TRIM and it mentioned how it was a garbage collector to stop the SSD from caching too much irrelevant data from the HDD or something like that.  Because you say it's installed automatically I don't have to worry about learning more about it for a couple of weeks.

Actually, TRIM has nothing to do with the HDD or caching. TRIM is a way for the OS to tell the SSD what parts of the drive are unused (freed from previous use). That way the SSD can efficiently distribute new files all over the SSD to even out the wear on the drive (limited write cycles per location).

> **WinEunuchs2Unix said:**
> You are correct about the stale information because I've read 20 or more misleading links until I found this one: [https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows](https://grepular.com/Disk_Caching_with_SSDs_Linux_and_Windows)

The gentleman has two 128 GB SSD's for caching + OS permanent installation.  He has two 1 TB HDD's for Data.  He dual boots with Windows 8 and Debian (sort of Ubuntu's Sister if you will).  He's using bcache under Linux (like I want to do) and Intel SRT under Windows (like I am now).  The difference is his SSD has an extra device for 8 times the size and he has an extra HDD for 4 times the data size.

He has written the meat & potatoes of using Linux bcache which includes other people's questions and answers in a debate style at the bottom of the web page.
It easiest to just put 'mostly random read' stuff (like the OS) on the SSD and put the 'mostly sequential read' stuff (like your media files, etc.) on the HDD. I use RAID0 to double the HDD read and write speeds for large data files.

---

### Post by WinEunuchs2Unix on 2014-09-13
> **Slim Odds said:**
> 
It easiest to just put 'mostly random read' stuff (like the OS) on the SSD and put the 'mostly sequential read' stuff (like your media files, etc.) on the HDD. I use RAID0 to double the HDD read and write speeds for large data files.

I like this idea.  After reading Justin's post about his 128gb SSD and 3 or 4TD hdd's I priced out some SSD's.  The local shop has a a Kingston 250GB SSD $70 off for a price of $110 (read $100 USD).  With that much SSD I can setup separate partitions for:

o Win7 OS (50gb?)
o Intel SRT Cache (60gb)
o Linux (20gb?)
o Linux Caching (60gb?)
o Linux Swap / Windows Page File (20 gb?)
o POW Project of the week (remaing 40 gb)

Some sort of background backup for POW during idle times should be setup in case Windows or Intel RST wipes out the SSD.  1 TB SSHD's are $95 and the laptop has 2 bays so RAID mirrored drives can be installed for $190. Plus a third HDD can be installed in the optical drive bay w/special caddy.

In the mean time I'm still going to slug away with the 32gb SSD and 500gb HDD using mdadm (to "see" Intel's fake raid) and bcache on the 11gb SSD partition set aside for linux.  btrfs (B-Tree File System) is becoming standard on some distro's and offers caching.  The developer of ext3 & ext4 file sytems likes btrfs.  There is something better than btrfs called EFZ but it seems better for shops with 300 HDD's not the laptop.

My first experience with mirrored drives were 20 lb. toaster sized 150 MB each costing $5,000 if I remember correctly.  My how times have changed since Novell file servers of 1995.

BTW I agree with your "easiest" scenario.  It's the difficult path that teaches you the most ;)

---

### Post by redrumrogue on 2014-09-15
To be precise I have 2 x 2TB Western Digital Black drives in a LVM volume group with a single striped logical volume (/dev/data/lvdata) using all the space.  This gives excellent read / write performance (AVERAGE read speed is around 200MB/s).  I also have 3 x 640GB Western Digital Blues in another volume group.  I use striped LVs on this VG for KVM virtual machines, again providing very good performance.

---

### Post by WinEunuchs2Unix on 2014-09-15
Sounds like an awesome system redrum.  It murders my specs :D -- 11 gb Cache mSATA III, 220 GB SATA II, Intel Fake-Raid 0, not even partitioned yet LOL.

---

