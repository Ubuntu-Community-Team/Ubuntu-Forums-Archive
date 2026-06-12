---
title: "Best way to backup a Ubuntu computer"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by markwco on 2014-03-06
I recently installed Ubuntu for the first time on an old ex-Windows desktop.  I actually am more familiar with using Mac computers and for backup use have used SuperDuper which basically mirrors the drive to an external hard drive.  I have since purchased an external hard drive to use for a Ubuntu backup.  Since I'm new to Ubuntu I am not familiar with backing up a Linux machine. I basically want a complete backup of my internal hard drive where if for any reason the internal hard drive fails I could simply replace it and restore from my backup.  What is the best way to back up a Ubuntu machine?  Thanks in advance.

---

### Post by vld2 on 2014-03-06
Hello.
You didn't specify do you want automated backup or you plan to do it manualy.
Ubutu has a backup solution that is installed by default and it's called Déjà Dup. Also I heard good things about Clonezilla but that's a bootable tool...
I am also quite new in Ubuntu world so I would appreciate any advice from experienced users... :-)

---

### Post by PotatoHead007 on 2014-03-06
Like **vld2** said, Déjà Dup comes pre-installed with Ubuntu, and it does the job perfectly in my experience. You can set it to backup automatically every day/week etc, so its not much of a hassle. just make sure your backup drive(HDD i suspect) is always pugged in. As you probably know, putting backups on the HDD you backup is not a good idea ;)

---

### Post by david98 on 2014-03-06
Iv'e use deja and clonezilla and would recommend them to any one but if you were just after a simple way to back up use deja it's extremely easy to use and comes pre installed as others have mentioned.

---

### Post by mastablasta on 2014-03-06
some more automatic options:
grsync/rsync
backintime
luckybackup


for manual imaging:
mintbackuptool
redobackup

---

### Post by nunecas123 on 2014-03-06
There's bootable solutions like Hiren's BootCD which have tools to clone your hard-drive at any given time.
There are also Linux solutions for backup, and as other suggested, Dejà Dup is a good and simple solution.
There's one which I don't think someone has referred: Pybackpack.

---

### Post by monkeybrain20122 on 2014-03-06
A really easy to use (well it is command line but only two commands really) software for cloning is fsarchiver. It is better than clonezilla in that it puts no limitation on the target partition where you want to restore your image to,--of course has to be big enough to hold the contents,-- while clonzilla has the stupid requirement that the target has to be at least as big as the original partition even though the latter may be mostly empty. This to me is a major show stopper as I often move my installations around to different drives. 
See post#25 and 26 for a brief idea and example.

[http://ubuntuforums.org/showthread.php?t=2205907&page=3](http://ubuntuforums.org/showthread.php?t=2205907&page=3)

Fsarchiver is in the repo.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

I use unision for file backup and syncing. It doesn't compress, just creates an identical copy somewhere else so may or may not be what you are looking for. unison is also in the repo (sudo apt-get install unision-gtk)

---

### Post by whitesmith on 2014-03-06
Clonezilla is dependable but the documentation is written in Taiwan by an ESL speaker. Even the simplest command is poorly phrased and, regrettably, capable of multiple interpretations. Other than that I think of it as "Ghost for Linux" without the capability of file-by-file restores. You should peek at sbackup, which can be scheduled to do full and incremental backups.

---

### Post by ibjsb4 on 2014-03-06
> **mastablasta said:**
> some more automatic options:
grsync/rsync
backintime
luckybackup

Not mention, rsync comes with the default install.  Its a terminal only app, but can be dressed up with a GUI (grsync, luckybackup ..)

---

### Post by markwco on 2014-03-07
Hello,

Thanks for all the replies.  I probably should have clarified but the backup will be on an external hard drive which will actually be stored in a fireproof safe.  It's something that I may run weekly or either when I do a lot of work on the machine and make a lot of changes.
Looking at all the replies it looks like Deja Dup is a good one to use.  I will also look at Clonezilla as a possible 2nd option.  I won't need an option that is bootable though .  
For some reason when I last upgraded to a new Ubuntu release it wiped out my hard drive.  I know it was user error and I'm just learning about this.  With a new LTS release coming soon I'll be updating to that and want to make sure I have a reliable backup this time in case I run into that problem again.

---

### Post by 1clue on 2014-03-07
I would install Linux on the external drive, same distro and everything.  That way it's bootable if your disk crashes.

Then I would back up ONLY your data:  User directories, if you have services you've configured then those files, that sort of thing.  Keep a list of license keys somewhere for any commercial software, or whatever.  You could write a script for that.

Once in awhile, boot from the external and do an update so you don't fall too far behind on software.

IMO automated backup solutions are a bad idea.  You leave it go, confident that you have a complete solution and years go by, your setup changes and what's critical isn't backed up.  Definitely, a backup solution that uses a proprietary format or backup-only media is a bad idea.  I recommend against compression, because if you do so then one bad bit of data will invalidate the entire archive.

Whatever solution you use, you need to actually restore a backup somehow and be sure that you're really backed up.

I've been running backups since the late 80s.  I've used just about every technology as a backup device.  I was using tapes at one point, had a crash and found out that I couldn't read data off of any of my tapes.  Since then I've spent my time trying to find the simplest solution possible, and the highest reliability possible.

My current practices depend on how much it costs for downtime.  If it's just a workstation that I don't use much, I make sure I have a current install CD or USB stick, and just back up the data.  I put it in /mountPointOfBackupDisk/2014-03-07/path/from/root/of/original/file.

If it's a critical system, the only difference is that the entire disk is the backup, it has the same Linux on it and the file goes in exactly the same spot it would be on the boot disk, making a bootable backup that would only be missing a few software updates but not much data.

The only other thing is, I have at least 2 backup disks for each installed disk.  I swap the disks each backup.  That means the backup has been in service less than the drives you use, so your backup is less likely to be bad.

---

### Post by zircon_34 on 2014-03-08
> **1clue said:**
> I would install Linux on the external drive, same distro and everything.  That way it's bootable if your disk crashes.



I was wondering, do you a) install linux on the external drive as you would create a live usb or b) install linux on the external drive using another live usb to boot into the normal install like you would for your computer and then partition your external drive etc...?

---

### Post by monkeybrain20122 on 2014-03-08
> **zircon_34 said:**
> I was wondering, do you a) install linux on the external drive as you would create a live usb or b) install linux on the external drive using another live usb to boot into the normal install like you would for your computer and then partition your external drive etc...?

No, not like a live usb, it is a full install. It is b). I have several installations on external drives, they are really handy and can be booted off different machines. When I visit my family in another continent I  don't even bring my laptop, just an external drive with a clone of my system and boot it off my dad's computer. :) But just for backup purpose it is more convenient to make an archive of your file system with something like fsarchiver and restore it as required. I just switched computer, basically cloned the system in the old laptop and restored it to the new one and that's it.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by zircon_34 on 2014-03-08
> **monkeybrain20122 said:**
>  I just switched computer, basically cloned the system in the old laptop and restored it to the new one and that's it.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

I think that sounds great, especially the cloning of a full system to be able to kind of sync it on other computers, I was looking for something like that so you dont have to reconfigure the whole distro if you get a new computer for example.

---

### Post by monkeybrain20122 on 2014-03-08
> **zircon_34 said:**
> I think that sounds great, especially the cloning of a full system to be able to kind of sync it on other computers, I was looking for something like that so you dont have to reconfigure the whole distro if you get a new computer for example.

Or you can also clone it to an external hard drive so you have a full install without doing b) (still need to partition the drive) The tricky part is in order to be able to boot that off the same computer (which has an identical OS) you may need to change the uuid of the clone or the original (or it gets confused). This involves editing fstab and grub.cfg and may be tricky if you haven't done it before. Again this is very handy. I have a partial clone on an external (not the whole thing, only the relevant system files) so if I want to do something risky like updating with experimental graphic driver I can test it out on it first before doing it on my real system.

---

### Post by 1clue on 2014-03-09
I don't clone system files.  The easiest way to get the operating system back is to install it over IMO.  As well, copying the system files takes time which causes your backup to take longer.

The only reason to have your backup bootable is this:  If you have a system where downtime costs you money, AND you make regular backups AND you take those backups to a different place (not the same building, etc.) then it makes sense to have a complete bootable system.  Having a removable drive with a bootable system on it, you can back up your files to that system in the exact same places as the main drive, and then when the main drive crashes you have a fully working system just by booting from the removable.

Otherwise IMO it makes no sense to have a bootable backup.

---

### Post by monkeybrain20122 on 2014-03-09
> **1clue said:**
> I don't clone system files.  The easiest way to get the operating system back is to install it over IMO.  As well, copying the system files takes time which causes your backup to take longer.

The only reason to have your backup bootable is this:  If you have a system where downtime costs you money, AND you make regular backups AND you take those backups to a different place (not the same building, etc.) then it makes sense to have a complete bootable system.  Having a removable drive with a bootable system on it, you can back up your files to that system in the exact same places as the main drive, and then when the main drive crashes you have a fully working system just by booting from the removable.

Otherwise IMO it makes no sense to have a bootable backup.

Sorry dude, I find your reasoning makes no sense whatsoever.
  
What if an update kill your system? How would reinstalling help if you get the same bad updated version of foo in the repo?

The root partition is typically small so cloning it would take much less time than backing up your data in  whatever method (How big is your / partition, 15G , 20G? Maybe 30G max) so it doesn't add much by way of overhead. I can't see how reinstalling the OS, all the software and updates, all the tweaking etc would be faster and easier than just restoring a 20G / partition. It typically takes me about 10 minutes or less for a 16 G / partition, less than half the time of reinstalling the OS alone (about 20 minutes for Ubuntu) and I don't have to do anything, just enter one command and I don't even need to sit in front of the computer).

And cloning the boot system is not just for restoring when it crashes, It also allows other possibilities say testing risky operations before you do it on your real system or transferring to another machines, or repartitioning hd and rearranging partitions: it is a lot faster and safer to simply delete everything in the hd and repartition and then restore the clones than to resize/move boot partitions. Just because you can't see the use doesn't make it pointless.

---

### Post by Mark Phelps on 2014-03-09
This is what the OP was asking for when starting this thread: > if for any reason the internal hard drive fails I could simply replace it and restore from my backup.

A backup of selected files does not satisfy this request; instead, an image backup will allow them to restore a working version in only a few minutes.

I regularly use Clonezilla do do this, and have played around a bit with RedoBackup (which doesn't work on my most current Linux distro) -- and it gives me great comfort to know that I can mess around with virtually any settings, and/or install any apps or drivers -- and if anything goes wrong, I can get my fully working system back in less than 10 minutes, without having to know what files to restore.

---

### Post by monkeybrain20122 on 2014-03-09
> **Mark Phelps said:**
> This is what the OP was asking for when starting this thread: 

A backup of selected files does not satisfy this request; instead, an image backup will allow them to restore a working version in only a few minutes.

I regularly use Clonezilla do do this, and have played around a bit with RedoBackup (which doesn't work on my most current Linux distro) -- and it gives me great comfort to know that I can mess around with virtually any settings, and/or install any apps or drivers -- and if anything goes wrong, I can get my fully working system back in less than 10 minutes, without having to know what files to restore.

You should try fsarchiver really. Clonezilla doesn't work for my need as it requires the partition to restore the image to be at least the size of the original even though the original may be mostly empty. This is a major show stopper for me as I transfer my systems to other machines (which may have smaller hard drives) or external drives and sometimes I only need to clone certain parts of the system for experiments and testing (excluding unneeded directories) and it makes no sense whatsoever to have to set aside a partition as big as the original.

---

### Post by markwco on 2014-03-09
I'm going to look into fsarchiver and Redobackup.
I tried Deja Dup but what type of setting will I need to use to backup the entire computer?  Also, I tried using it with my external OWC Mercury On-The-Go hard drive.  Ubuntu won't recognize it and I posted about that in another post.  When I couldn't get it to recognize my external hard drive I figured I'd back it up to a folder on the computer's hard drive and then figure out another way to get it to the external hard drive but for some reason it wouldn't allow me to backup that way either.
As well, I thought maybe creating an image with an application such as Clonezilla may be my best choice.  I downloaded Clonezilla and booted with it but ran into the same problems.  I wasn't able to use my external hard drive and it woudn't allow a backup to the internal hard drive either.

---

### Post by kevdog on 2014-03-09
Not to be redundant here but you should probably have a few different backup strategies.

#1 - would be disc image backups.  Clonezilla or fsarchiver would fit this bill.  I like clonezilla since its just plain easy.  Call me lazy but I usually only create these types of backups a few times per year
#2 - file backups -- these would include personal files, images, etc -- usually non-system, user related files.  I really like rsync for this method.  I've looked into a few others such as rdiff-backup, obnam, etc, however rsync has been around for a long time and its very reliable.  In my opinion you really want your back up solution to be boring and time tested, rather than cutting edge just to save some disc space.

Whether you choose on-site or off-site backups is really dependent on your needs.  With the entire NSA thing, if choosing cloud backup, I'd try a method that encrypts cloud backups.  I'm not sure if DejaDup does encryption on the server -- I could be wrong about this however.

---

### Post by 1clue on 2014-03-09
> **monkeybrain20122 said:**
> Sorry dude, I find your reasoning makes no sense whatsoever.
  
What if an update kill your system? How would reinstalling help if you get the same bad updated version of foo in the repo?

The root partition is typically small so cloning it would take much less time than backing up your data in  whatever method (How big is your / partition, 15G , 20G? Maybe 30G max) so it doesn't add much by way of overhead. I can't see how reinstalling the OS, all the software and updates, all the tweaking etc would be faster and easier than just restoring a 20G / partition. It typically takes me about 10 minutes or less for a 16 G / partition, less than half the time of reinstalling the OS alone (about 20 minutes for Ubuntu) and I don't have to do anything, just enter one command and I don't even need to sit in front of the computer).

And cloning the boot system is not just for restoring when it crashes, It also allows other possibilities say testing risky operations before you do it on your real system or transferring to another machines, or repartitioning hd and rearranging partitions: it is a lot faster and safer to simply delete everything in the hd and repartition and then restore the clones than to resize/move boot partitions. Just because you can't see the use doesn't make it pointless.

Ya, but if you upgrade automatically on your main system, you might not know of a problem until you reboot.  I've had system uptimes of over 2 years in the past, had to reboot and found my system completely unbootable.  I no longer allow that sort of thing, but the key issue here is that you might do updates on your main drive, NOT reboot, and then do a backup because you think everything is fine.  That can trash your system too.  I can't tell you how many times I had a config file either overwritten or made obsolete by an update and not known about it until reboot.

If you periodically boot off of your backup drive and update it, then reboot again, then you know it works.  The software on the backup need not be bleeding edge, it just needs to work in most cases.  Better yet, you can boot off some non-critical system to do those updates.  If your critical system goes down, it might be from a lightning strike or some such, in which case your backup won't go to that system anyway.

---

### Post by monkeybrain20122 on 2014-03-10
> **1clue said:**
> 
If you periodically boot off of your backup drive and update it, then reboot again, then you know it works.  The software on the backup need not be bleeding edge, it just needs to work in most cases.  Better yet, you can boot off some non-critical system to do those updates.  If your critical system goes down, it might be from a lightning strike or some such, in which case your backup won't go to that system anyway.

My main system is my laptop so I reboot often so yeah I would know immediately if something doesn't work. I rent a room and move around/travel a bit a desktop is out of the question. :)

---

