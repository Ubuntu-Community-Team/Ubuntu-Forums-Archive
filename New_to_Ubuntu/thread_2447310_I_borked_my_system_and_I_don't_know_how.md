---
title: "I borked my system and I don't know how"
date: 2020-07-16
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-16
Hello all,

So I had finished setting up my new PC and had installed everything I wanted, so my plan was to create a new partition on my old Seagate 1TB SSD and use Timeshift to back up to that. Long story short, the Ubuntu 20.04 'Disks' tool seemed to be having some trouble working with the drive, it took forever to format a tiny 20GB partition, then when I decided I wanted to rename it it took forever to delete the partition. Finally got it sorted but when I tried to create a Timeshift image in that partition it hung on 6.66% (a bit ominous) and I had to cancel.

Then for some reason the partiton was being mounted at /run/timeshift/ when previously on 18.04 it was always /media/[user]/ which is where partitions I made on the drive, using my laptop, are still mounted on my PC.

Basically I couldn't erase the partially completed images under /run/timeshift using the file manager so I just ran 'sudo rm -d -r /run/timeshift' and was immediately met by a blue screen with only the Gnome side bar / top bar remaining. I rebooted and it just went straight to Grub, I tried going into the UEFI and just booting from the drive but it still went to Grub.

I couldn't be bothered to poke around with it so I just re-installed.

What happened? why is /run/timeshift so critical?

---

### Post by rbmorse on 2020-07-16
Looks like when you setup Timeshift and assigned a directory for it to use for the backup store it claimed it as it's own.  

Surprised the system didn't give you a "disk/file/partition in use" warning when you tried to act on it, but Timeshift does it's own thing and that, by-in-large, is why I don't use it.

---

### Post by GhX6GZMB on 2020-07-16
Well, if you can't even get the disk to format and mount correctly, how do you expect Timeshift (or any other program) to cope? Get your partitions formatted and right first.

---

### Post by jcdenton1995 on 2020-07-16
> **ml9104 said:**
> Well, if you can't even get the disk to format and mount correctly, how do you expect Timeshift (or any other program) to cope? Get your partitions formatted and right first.

Like I said, it did format eventually, it just took about 20 minutes, and it did mount the partition, just in a different place than I expected.

---

### Post by jcdenton1995 on 2020-07-16
> **rbmorse said:**
> Surprised the system didn't give you a "disk/file/partition in use" warning when you tried to act on it, but Timeshift does it's own thing and that, by-in-large, is why I don't use it.

I'm not sure if it's the same thing but when I tried to delete the directory as my user account it failed and told me it was a read only file system?

---

### Post by GhX6GZMB on 2020-07-16
I'm sure you're aware that Timeshift only works on ext4 filesystems? Far too few facts and too much unspecific info here. Timeshift does not mount partitions (or rather: file systems), _you_ do.
For a removable/temporary drive, /media or /mnt are the right places. For a fixed drive it should be /dev. /run/timeshift must be some kind of emergency mount.

---

### Post by jcdenton1995 on 2020-07-16
Yes I'm aware, I went with ext4 anyway as I don't use anything other than Ubuntu right now.

I'm actually a little suspicious of the external SSD itself as it has started playing up a little, nothing major and seems to resolve itself, but I did make a second backup of some stuff on there I didn't want to lose as I half expect it could pack up at any moment!

---

### Post by mastablasta on 2020-07-17
wouldn't it be easier to just use BTRFS or ZFS for snapshots?

---

### Post by jcdenton1995 on 2020-07-18
> **mastablasta said:**
> wouldn't it be easier to just use BTRFS or ZFS for snapshots?

I have no idea to be honest as I don't know how all the different methods work, I'm just a humble Linux Layman :)

---

### Post by TheFu on 2020-07-18
> **ml9104 said:**
>  
For a removable/temporary drive, /media or /mnt are the right places. For a fixed drive it should be /dev. /run/timeshift must be some kind of emergency mount.

I suspect this is a mistake.  Nothing should be mounted under /dev/
Typically, /run/ is use for PID files and process named-pipes or FIFOs.  Stuff under /dev/ or /proc/ or /sys/ or /run/ really shouldn't be touched by admins or humans ... well, sometimes an admin may need to manually create a device to access to specific driver but I haven't needed to do that in about 20 yrs.

---

### Post by TheFu on 2020-07-18
> **mastablasta said:**
> wouldn't it be easier to just use BTRFS or ZFS for snapshots?

Snapshots aren't a backup. They are part of a backup solution, but until the data gets off the original drive is isn't a backup.

For someone new, I wouldn't ever suggest they use either ZFS or BTRFS.  Those are so different from what Windows has I don't think a noob's mind can handle the mind-blowout. ;)

There are lots of easier backup solutions compared to the issue our poor OP is having, but I can't imagine it would be worse than just learning from these mistakes (don't do X again) and continuing with the current tool.

---

### Post by TheFu on 2020-07-18
> **jcdenton1995 said:**
> I have no idea to be honest as I don't know how all the different methods work, I'm just a humble Linux Layman :)

We all have days like that, trust me.  Often, I'll ignore reality and insert my own fantasy for how software works, only to be humbled. I just hope that I'm humbled before completely forgetting what I did so that I can undo it.  Plus, I have automatic, daily, versioned, backups that can be restored in 30-45 minutes. ;)

---

### Post by GhX6GZMB on 2020-07-18
@TheFu:
Not my thread, but thank you for the last two replies here. They express an understanding for newbies that I appreciate, instead of the just the "super-duper experienced UNIXPro" throwing abbreviations in all directions and groaning over the newbie's ignorance.

---

### Post by jcdenton1995 on 2020-07-19
haha yes, the problem is there is just so much to know that there's just no time to research everything to the nth degree, I would go mad. I can't remember.

Looking back through my notes, it appears that whatever guide I was going off said that to do BTRFS backups you a) need BTRFS tools installed and b) BTRFS can only backup to a system folder, not an external drive. Thus I went with rsync and then in the time since I forgot these two reasons but just stuck with it.

I don't actually know if either of these things are 100% true, I tend to find I read a lot of how to's online that make statements as if they are absolute truth, and then at some point later I find out that they were only half truths with more nuance to them, as usually there is a workaround.

---

### Post by GhX6GZMB on 2020-07-19
Dunno if this is helpful to you, but here's a little HOWTO I wrote on system restore using Timeshift (I've used it myself a couple of times after coming to a cropper):
[https://ubuntuforums.org/showthread.php?t=2447108](https://ubuntuforums.org/showthread.php?t=2447108)

---

### Post by mastablasta on 2020-07-20
> **jcdenton1995 said:**
> 
Looking back through my notes, it appears that whatever guide I was going off said that to do BTRFS backups you a) need BTRFS tools installed and b) BTRFS can only backup to a system folder, not an external drive. Thus I went with rsync and then in the time since I forgot these two reasons but just stuck with it.


as i understood you were trying to make snapshots of files (like a restore point). this is not a true backup, but it helps with a quick restore (e.g. you overwrite the data file accidentally and you need the old one back). however BTRFS and ZFS4Lnux filesystems offer this option out of the box.


for easy backup to external drive i use Areca. you set it up in GUI (all parameters) it creates a script that you then add to cron to be executed at the times you chose. you can then manage and restore files from the Areca GUI or use a file manager. depending if files are encrypted or not.
i use it also on windows.

---

### Post by jcdenton1995 on 2020-07-20
> **mastablasta said:**
> as i understood you were trying to make snapshots of files (like a restore point). this is not a true backup, but it helps with a quick restore (e.g. you overwrite the data file accidentally and you need the old one back).

Yes that's right, but what is the difference between a snapshot and a backup, does a snapshot technically become a backup when moved to an external device? would a snapshot be a backup if it included all hidden and configuration files* and *program data? or would it only be a backup if all three of these conditions were met? or is it the manner in which the information is stored that makes it a backup?

I'm aware Timeshift wouldn't backup user data and hidden files unless explicitly asked too, that's fine for me as I would prefer to tell it to backup my system and hidden files, and make backups of my user data separately.

I use Timeshift more so if I trash my system I don't need to download and configure all my programs and packages etc. because that's a real pain. I'm less concerned about my user data.

---

### Post by jcdenton1995 on 2020-07-20
> **ml9104 said:**
> Dunno if this is helpful to you, but here's a little HOWTO I wrote on system restore using Timeshift (I've used it myself a couple of times after coming to a cropper):
[https://ubuntuforums.org/showthread.php?t=2447108](https://ubuntuforums.org/showthread.php?t=2447108)

Thank you, I can see me referring back to this at some point in the future!

---

### Post by mastablasta on 2020-07-20
> **jcdenton1995 said:**
> Yes that's right, but what is the difference between a snapshot and a backup, does a snapshot technically become a backup when moved to an external device? would a snapshot be a backup if it included all hidden and configuration files* and *program data? or would it only be a backup if all three of these conditions were met? or is it the manner in which the information is stored that makes it a backup?


when we talk about snapshot we usually think about changes on drive being recorded at certain point in time. so it's not a full image of the drive but only changes. this takes up less space than full image. they can then be restored to that point. however this is usually done on the same disk as the OS or data is on. for example for experimenting virtualbox has snaphots that restore the whole virtual PC to previous state within seconds. some file systems (BTRFS, ZFS) also have this feature built into them along with other things. anyway the issue here is that if disk is damaged you snapshots will also be damaged.  

backups on the other hand are usually done to another media (that can easily be restored from, that is durable/robust and that is preferably 25km or more away form the point that is creating backups - so they can be recovered in case of natural disaster, fire in apartment...). TheFu has more knowledge about this.

backup can be full image backup or incremental (again changes are sent to another drive at specific intervals). they need to be tested regularly to see if you can actually restore them.

there are a couple of backup options with nice GUI available. I mentioned Areca, but Duplicati also works well. There is also "Back in time" which might fit your purpose.

I you like messing arround with OS i would really recommend virtualbox or similar virtualisation software. i have old single core PC with 4Gb ram and i can use it. so on modern PC it will work even better. you set up the OS which is done basically in same way as you would on PC or you can load premade image (skip install, just set user and password). and then take a snapshot and start messing around. plenty of guides with pics out there these days. and virtualbox has nice GUI even for beinners.

---

### Post by TheFu on 2020-07-20
For any storage volume management capable file system, a "snapshot" has a very specific meaning.  It is a built-in capability to freeze the currently used storage blocks and prevent updates to them.  Any modifications to those files must be written somewhere else on the available storage.  ZFS, BRTRS, LVM all support this style of "snapshot".

A "snapshot" in the way that **Back-in-Time** and, I suspect, **Timeshift** does is NOT that.  Those are very important distinctions, especially when it comes to backups.

The file system "snapshot", just freezes those blocks where they are, so we can make a 100% clean backup off those frozen pointers. It should be obvious that we can't create snapshots over and over and over and over for years without running out of space.  The typical use for snapshots is for nightly backups or just before doing system updates.  Once the backup finishes, the snapshot is deleted and those frozen blocks are not frozen anymore.  Without actually making a backups of the snapshot files/blocks, we don't actually have a backup on different storage.  So if the HDD/SSD fails, having that snapshot is useless.

A back-in-time "snapshot" is created using rsync and cp with hardlinking to reduce the total storage needed for each backup revision.  It is written to a different directory - hopefully, the person who setup the back-in-time snapshot selected that other directory to be on different physical storage. I used Back-In-Time on my Mom's PC for a few years. Wrote those "snapshots" to a USB external device, then once a week, I'd rsync the data to my house 3 states away for off-site storage.  Mom only had emails and Quicken stuff - Quicken ran in a virtualbox 1-program window, so she didn't actually know it was a VM. I'd setup the Quicken backup directory to be in her HOME so Back-In-Time would always have her data.  Back-in-Time creates snapshots every hour, by default, then selectively deletes them as time goes forward.  The schedule they used was pretty cool, but not ideal for what I thought should be used.  I didn't bother to learn how to create a custom schedule to satisfy my wishes.

Anyway, whenever someone says "snapshot", be certain you understand what they really mean.

---

### Post by jcdenton1995 on 2020-07-21
@TheFu Thanks, so what your saying is that the term 'snapshot' has a different technical meaning depending on the context.

 If in the context of a file system it means an in built capability to temporarily freeze an amount data so a complete copy can be properly and safely made of it, before that data is then un-frozen.

But in the context of Time shift a 'snapshot' is simply a record of the changes made since the previous snapshot, and ultimately all snapshots will be "descendants" of a more complete image.

I hope I've got that right!

---

### Post by jcdenton1995 on 2020-07-21
> **mastablasta said:**
> If you like messing arround with OS i would really recommend virtualbox or similar virtualisation software.

Thanks for the explanation, I'll look into setting up a VM at some point so I can play around with this kind of thing and see what happens before I commit to doing it on my real OS!

---

### Post by TheFu on 2020-07-21
> **jcdenton1995 said:**
>  But in the context of Time shift a 'snapshot' is simply a record of the changes made since the previous snapshot, and ultimately all snapshots will be "descendants" of a more complete image.

I hope I've got that right!

Someone more familiar with Timeshift would need to comment.  I can't tell and it could be that Timeshift on btrfs-mode uses 1 or both meanings.

---

### Post by GhX6GZMB on 2020-07-21
> **TheFu said:**
> Someone more familiar with Timeshift would need to comment.  I can't tell and it could be that Timeshift on btrfs-mode uses 1 or both meanings.

It's a terminology problem. Timeshift uses the term "Snapshot" for a backup, which is somewhat "marketing-speak". Sounds smart to some.
It's actually an incremental backup, at least in rsync mode. Never tried btrfs myself, so can't say.

---

### Post by mastablasta on 2020-07-22
> **ml9104 said:**
> It's a terminology problem. Timeshift uses the term "Snapshot" for a backup, which is somewhat "marketing-speak". Sounds smart to some.
It's actually an incremental backup, at least in rsync mode. Never tried btrfs myself, so can't say.

the marketing ploy explains the confusion then.

well like i said there are a couple of other easy to use GUI apps for backup out there. i tried kbackup. it didn't do anything at the time, just pretended it is backing up. probably they fixed the issue already, as i can see there is an update look. anyway sometimes if something doesn't work, it might be a good idea to try something else.

here is a nice list of backup software on wikipedia: [https://en.wikipedia.org/wiki/List_of_backup_software](https://en.wikipedia.org/wiki/List_of_backup_software)

---

### Post by GhX6GZMB on 2020-07-22
> **mastablasta said:**
> the marketing ploy explains the confusion then.
 anyway sometimes if something doesn't work, it might be a good idea to try something else.


Never said it didn't work. In fact, Timeshift has saved my butt dozens of times until now, including restore after a complete new install with HDD/SSD format.

My experience is, that it is very reliable, but you need to keep an eye on the settings and define exactly what you backup or restore. Expect it's the same with other backup programs.

---

### Post by mastablasta on 2020-07-23
> **ml9104 said:**
> 
My experience is, that it is very reliable, but you need to keep an eye on the settings and define exactly what you backup or restore. Expect it's the same with other backup programs.

this is the same with all.

there are some that offer reasonable and sane defaults, but you still need to do a check of these settings before committing to the service.

---

### Post by jcdenton1995 on 2020-07-23
Marking the thread as solved! Thank you all for the input

---

