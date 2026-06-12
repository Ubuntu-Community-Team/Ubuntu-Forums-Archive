---
title: "Best Method Backing Up Installation"
date: 2014-07-12
forum: New to Ubuntu
---

### Post by cedric9 on 2014-07-12
I have Ubuntu 14.04 LTS on my old Pentium 4 with 1.5GB of Ram.  I have two hard drives installed, my primary master is an 80GB IDE connected directly to the mother board.  My secondary master is an old IDE - DVD Burner.   I also have an 80 GB SATA drive connected to a PCI controller card installed on my system.  

My system boots from the 80GB IDE drive, and there is a 30GB ext4 partition, and also a 1.5GB swap partition on this drive.  The rest of the 80GB IDE drive is occupied by a ntfs partition containing My Documents, from when XP was installed on this system.  The SATA drive is also partitioned with a ntfs partition, and contains misc files.

During the time I was running XP, I used to boot from a 2003 Norton Ghost CD, and make an image of "C:\" onto an external USB hard drive.  This method worked good for many years, but I understand that version of Ghost I'm using isn't compatible with ext4 partitions that I'm now using.  

I guess that I'm looking for a way to boot from a CD and to then create a back up image on 500 GB WD external drive?

Any advice appreciated.

---

### Post by Vladlenin5000 on 2014-07-12
Considering the present configuration I would rather backup the user files and reinstall from scratch while removing the old NTFS partitions, than making an image of it. This is just me...

You can use Clonezilla for the same purpose you previously used Norton, either on its own bootable CD or included in many other more complete boot CDs like Parted Magic which in turn can also be found within Ultimate Boot CD and others.

---

### Post by varunendra on 2014-07-13
I second clonezilla. A recent discussion on disk/partition imaging : [http://ubuntuforums.org/showthread.php?t=2231434](http://ubuntuforums.org/showthread.php?t=2231434)

My suggestions (also about AptOnCD - a tool for a different but related stuff) are in [post=13058825]post #15[/post] there.

---

### Post by mastablasta on 2014-07-13
Redo Backup is another option also using parted.

---

### Post by cedric9 on 2014-07-13
Thanks for the advice everyone.  The reason why I decided to keep my ntfs partitions, is because I have quite a few documents stored on them, that I need to access on a regular basis.  At this point I could still go back to Windows, if I needed too, and I don't yet feel confident enough to completely burn all my bridges.  (Are there any negative consequences to having both ext4 and ntfs partitions?)

Are there any thoughts regarding which of the two programs are more reliable, [COLOR=#000000]Clonezilla or [/COLOR][COLOR=#000000]Redo Backup?  I was considering Perfect Image, but then I read that Perfect Image isn't reliable, and that it often creates backup images that are not accurate.[/COLOR]

---

### Post by mastablasta on 2014-07-14
there is no problem using both **for data**. Linux can read and write to NTFS and apparetnly now Windows can as well?! : [http://ubuntuforums.org/showthread.php?t=2233953](http://ubuntuforums.org/showthread.php?t=2233953)
one issue if you have only linux as OS and use NTFS partition for data (you can't use uit for OS or porgrams) is that if something is wrong on it you can't run checkdisk. workarround is to cretae a Windows rescue or some Windows boot disk and put checkdisk on it.

clonezilla and redobackup both use same backup utility. they only have different user interface. redobackup is more simplistic with less options, while clonezilla has many options and a bit stranger interface (no go back button for example) they do have documentation with pictutre for the selected backup type and you can just follow those. clonezilla is more for pro's while redobackup is ment more for home user that want's a simple interface for backup.

otherwise there are also GUIs that will provide you an interface for time scheduled backups. for example weekly backup, monthly...

of course as with all Linux stuff - you can always just use comand line tools. :P

---

### Post by cedric9 on 2014-07-15
It looks like Redo Backup is probably the way to go for someone like me, with limited Linux experience.  I'll try using it to make an image, and then I'll try restoring it to a spare IDE drive I have. If the restored partition can boot my machine, I'll come back and mark as solved in a few days.

Also, I didn't think about not being able to properly maintain my ntfs partitions when I removed XP from my system.  I suppose that I could run chkdsk from my bootable XP installation CD, but I don't think that there is anyway to defrag my ntfs partitions without Windows actually running on my machine?  I suppose that eventually I will have to get off the fence, and decide if I'm really going to make Ubuntu my OS or not. Right now I kinda feel the same way I did when Windows 95 out.  Ubuntu seems pretty cool, but every once in a while it seems to give me a problem that shouldn't be that difficult to solve.

---

### Post by mastablasta on 2014-07-15
oh yes defraging is also a Windows thing. Linux ext partitions don't need it as they do not get fragmented as much. in fact most of Linux file systems have very little fragmentation. 

if you use NTFS just to save data then fragmentation will not really occur in NTFS. fragmentations happens when you read and write same file over and over. e.g. game saves, office documents editing etc. 

clonezilla can do disk to disk clone  -I used this when my disk (windowsXP) started loosing it so I cloned it all to larger new disk, replaced the disks and booted from new disk: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

what you do with redo is save a compressed image. and yes it can boot. here is how you do it with clonezilla:
image create & save:
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)
image restore: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/02_Restore_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/02_Restore_disk_image)

disk image will be smaller than disk space as it compresses the occupied and unoccupied disk space. so let's say you create and image of 20 GB drive that has 10 GB taken. image will take 10 GB or less depends on what kind of files are on the disk drive. 

redobackup is so easy to use and it's GUI is preety much self explanatory.

the only thing is that they are based of Ubuntu 12.04 and use an older kernel. while this works fine on older computers, it would be good to have an updated version that supports newer machines as well. I guess it will be out when it's ready and when they have the time. I am not sure if they update kernel with their updates.

---

### Post by cedric9 on 2014-07-15
Will I also need to back up the swap partition, or can I simply create a new one if  need to?

---

### Post by Vladlenin5000 on 2014-07-15
> **cedric9 said:**
> Will I also need to back up the swap partition, or can I simply create a new one if  need to?

Your second option.

---

### Post by cedric9 on 2014-07-17
I was able to to use [COLOR=#000000]Redo Backup to create an image, and to restore that image to a bare hard drive without any problems.  However, on my first attempt to  boot from the newly created partition, the system seemed to hang for about two minutes at the splash screen, before proceeding to the login screen.  After that, I logged into my usual session, and everything seemed to be alright.  I rebooted a couple of times, and the hang at the splash screen seemed to resolve itself.  

It looks like Redo Backup is the way to go.[/COLOR]

---

### Post by varunendra on 2014-07-17
Congratulations to you and mastablasta! :)

@mastablasta,
Does redo backup also have the capability to create an auto-recovery bootable (iso/zip-for-usb) image like clonezilla has? I'm too busy these days, so would love to save the time to experiment myself if you could confirm that. Thanks!

---

### Post by LastDino on 2014-07-17
One another way I personally dealt with maintaining NTFS data storage partitions was to move my data to some other partitions/disk if available and format it using g-parted to NTFS only. But really, if it is just data, you will be probably worry free about this for long durations like 6 months to even year or so.
In my case I did not have any Windows installed for that whole time, but keeping NTFS data partition sort of became habit from my dual booting days. 
(Which did came in handy, but that's another story)

---

### Post by cedric9 on 2014-07-18
I'm sorry but your question is way over my head.  At this point I know so little that anything I say will most likely not be correct.  I picked Redo Backup because it had pretty icons to click on.  All I know is that my own computer seems to be working, but beyond that I'm pretty useless.

---

### Post by cedric9 on 2014-07-18
I thought about copying all of my documents to an external HD, and then simply creating new ext4 partitions to replace my old ntfs partitions, and then copying my documents back. (Would that work?)  But at this point I'm simply not confident enough with Ubuntu.   I'm thinking that maybe I might go with a dual boot configuration, using Windows 7 along side Linux, or maybe I should simply think about buying a new machine.  Believe it or not, I've been using the same computer with very little modification since 2003!

---

### Post by mastablasta on 2014-07-18
> **varunendra said:**
> 
@mastablasta,
Does redo backup also have the capability to create an auto-recovery bootable (iso/zip-for-usb) image like clonezilla has? I'm too busy these days, so would love to save the time to experiment myself if you could confirm that. Thanks!

i am not sure. i think it is more designed to cretae image for backup. it is basically just a gui for parted which is the same software used by clonezilla i believe.

> **cedric9 said:**
> I thought about copying all of my documents to an external HD, and then simply creating new ext4 partitions to replace my old ntfs partitions, and then copying my documents back. (Would that work?)  But at this point I'm simply not confident enough with Ubuntu.   I'm thinking that maybe I might go with a dual boot configuration, using Windows 7 along side Linux, or maybe I should simply think about buying a new machine.  Believe it or not, I've been using the same computer with very little modification since 2003!

that will work. i copied them to netowrk disk on Windows xp and once the OS was installed i copied them back.

documents and data are ok to put on NTFS. programs are another matter.

---

