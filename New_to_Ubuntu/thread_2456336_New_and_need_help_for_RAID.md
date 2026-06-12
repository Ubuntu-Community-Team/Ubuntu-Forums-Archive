---
title: "New and need help for RAID"
date: 2021-01-09
forum: New to Ubuntu
---

### Post by clctr13760 on 2021-01-09
I'm new to Linux, as in the boot file is created on a flash drive, but nothing is installed, and I'm looking for some direction in getting everything set up.  My current setup is a SSD that I want to use as a boot drive and two HDD's that I would like to set up in a software RAID 1 format.  The system will primarily be used as a Plex media server, so I was wanting some redundancy to keep from losing my DVD library. I seem to be confusing myself the more I search around on this subject.  Is the process done entirely during setup/install of ubuntu, or will I get the RAID set up after installation and by using the terminal?

---

### Post by DuckHook on 2021-01-09
Welcome to the Forums, clctr13760

The easiest way would be to install Ubuntu onto the SSD first without touching either of the two HDDs. They can be set up afterwards.

What you call software RAID can be done any number of ways.

The old way would be to use mdadm. This has the advantage of being tried and true, so it just works. Its big disadvantage is that it is inflexible. It uses the least overhead, but with even reasonably recent HW, this is a nonissue, so low overhead can no longer be counted in its favour.

Newer methods involve either LVM or a next gen file system like ZFS. I use both, but have come to prefer ZFS. Either will give you not only mirroring, but also snapshots (and restores), cloning, easy filesystem expansion/contraction, etc. I cannot begin to tell you how useful such functionalities are. But their biggest plus in my books is the ability to now use containers for added security and app segregation. If these functionalities are Greek to you for now, not to worry. You don't need to use them, nor ever understand what they are. But if you get to the point where such extra functionality would be useful, then having your filesystem already set up for them is both forward thinking and ultimately rewarding.

Guide for setting up mdadm: [https://www.golinuxcloud.com/configure-software-raid-1-spare-disk-linux/](https://www.golinuxcloud.com/configure-software-raid-1-spare-disk-linux/)
Guide for setting up LVM: [https://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](https://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)
Guide for setting up ZFS: [https://linuxconfig.org/configuring-zfs-on-ubuntu-20-04](https://linuxconfig.org/configuring-zfs-on-ubuntu-20-04)

---

### Post by clctr13760 on 2021-01-09
Thank you for the information and links to the different options.  I was looking at ZFS in the beginning, but I was under the impression that it creates a pool, essentially combining the two separate HDD's into one big volume.  I'll check out the link, but is there something I was missing with that style?  I'm glad to hear that I can do the installation first, and then get the RAID set up later, since I shorted myself by 1 SATA cable ](*,).

---

### Post by TheFu on 2021-01-09
Before dealing with RAID, what is the backup solution?  Solving that first really is necessary and will help build some of the needed skills. RAID is never a replacement for backups.

Google found this: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
Definitely create partitions to hold the array BEFORE creating the array. Do not write directly to the whole drive.

I've never attempted this in the installer. I've always added arrays post-install.

+1 for using zfs or lvm+filesystem, but both may be too complex for someone new to linux.  There are many new terms and ideas. Snapshots alone would be sufficient reason for me. They make solid, uncorrupted, backups foolproof.

---

### Post by DuckHook on 2021-01-09
> **clctr13760 said:**
> …I was looking at ZFS in the beginning, but I was under the impression that it creates a pool, essentially combining the two separate HDD's into one big volume…
When creating, you can define the pool as mirrored: ```
man zpool
```
Note to **not** use any of the **raidz** but use **mirror**.

---

### Post by DuckHook on 2021-01-09
> **thefu said:**
> before dealing with raid, what is the backup solution?  Solving that first really is necessary and will help build some of the needed skills. Raid is never a replacement for backups. +1

---

### Post by clctr13760 on 2021-01-09
> **TheFu said:**
> Before dealing with RAID, what is the backup solution?  Solving that first really is necessary and will help build some of the needed skills. RAID is never a replacement for backups.

I honestly hadn't gotten that far yet, as I was still weighing the complexity of my aspirations vs setting this up through windows. I haven't had a chance to read through the links yet, so I'm still looking into it.

---

### Post by clctr13760 on 2021-01-09
After reading through the links, I'm leaning towards ZFS.  When it comes to backups, are the ZFS snapshots only done manually, or is this something that can be set up to run on a schedule automatically?  I may be getting ahead of myself, but more curious than anything.

---

### Post by DuckHook on 2021-01-09
Please really note TheFu, one of our resident gurus. Excellent advice.

Snapshots are not backups. Not even close. They are used to roll back to a known good state after a foul&#8209;up, such as a bad upgrade. I use it for containers that have entire quasi&#8209;independent OSes on them—a variant of VMs. They have saved my keester on many occasions, but then, I like to tinker and sometimes will push the envelope with custom changes. All such experimentation is carried out on the virtual OS within the container: hence the utility of snapshots and rollbacks.

If you screw up your filesystem, then mirrored drives will simply mirror your now unusable file system. i.e. You are attacked by ransomeware. You will now have two copies of an inaccessible disk. This is why TheFu has categorically stated in the past that mirrors are an illusion of a backup. Without a true backup, you would be just as dead in the water.

Mirrors are for system redundancy—a completely different issue. When one disk goes down, the other can still serve requests. They are used in mission&#8209;critical scenarios where, say, a commercial website cannot ever be down, else money flies out the door. I have *never* seen a home use situation that qualifies.

I use ZFS in a 4 HDD raidz1 configuration for my tiny little RPi&#8209;based server. Its primary role is to become one big HDD with a bit of redundancy. Backups are handled entirely separately (and is a topic unto itself).

I don't know why you want to mirror, so just gave you the links. The better advice here is TheFu's, who asks you to examine why you need mirroring in the first place.

It may make more sense for you to have a proper backup strategy/setup, then just bridge the two HDDs for double storage capacity, since a Plex server is not remotely "mission critical".

Re: scheduling

Almost anything can be scheduled. In this case, a simple cron job would do it. But again, what would be the point? …given that snapshots are not for data integrity.

---

### Post by clctr13760 on 2021-01-10
Coming to the realization that I know enough to get myself into trouble.  I was under the impression that mirroring would suffice as a backup, so I hadn't given it much thought.  My initial thought was that if I ran the system mirrored, then it would save me the time of ripping my media again if a drive failed.  I guess I'm having trouble differentiating a mirror from a snapshot from a true backup.

---

### Post by DuckHook on 2021-01-10
> **clctr13760 said:**
> &#8230;My initial thought was that if I ran the system mirrored, then it would save me the time of ripping my media again if a drive failed
If a drive fails and does so in very specific ways (for HW reasons), then yes, the other HDD chugs away taking up the load. You would then replace the failed drive, re-activate mirroring and the replacement drive would shortly be identical to the surviving drive again.

But if you mistakenly delete half your files, then the mirrored drive would delete those files too. After all, that's what mirroring is supposed to do. If you need an old version of a file (say, an accounting database) from last month because you only discovered an error today, then without a backup, you are also out of luck. In my aforementioned scenario, you are hit by ransomware: a mirrored setup would just mirror the corruption. Both drives are now identically encrypted.
> I guess I'm having trouble differentiating a mirror from a snapshot from a true backup.
Here's what I suggest:

[LIST=1]
[*]Forget I ever mentioned "snapshots". That's just a high&#8209;falutin concept that has no application to your needs. When you are ready to look into it, you will know what it is.
[*]Likewise, mirroring, whether through mdadm, LVM or ZFS is not what you need.
[*]Backups are essential. With your setup, a possible setup would be to use only one drive actively as your data storage. Use the second drive passively to duplicate the contents of the first drive, but only periodically at your instigation. That way, a mistake/menace in one drive does not automatically propagate to the other. This gives you basic redundancy without much trouble. But it's still not a backup.
[*]For your real backups, here is what's important: you need to define a hierarchy of your data. Not all data is of like importance. Here's mine in ascending order of importance:
[list=a]
[*]Operating system: Worthless data. It can always simply be reinstalled. Ubuntu takes me less than 30 minutes to install from beginning to end. I don't ever bother backing my OS up.
[*]Convenience data: This is stuff that I already have source media for&#8212;CDs, DVDs, BDs. It's a pain to rip these to HDD again, but so what? It's just a matter of putting in the time. I rely on my redundant disks to give me enough protection here to feel safe.
[*]Important data: Family photos, home videos, etc. If I lost this stuff, Mrs DuckHook would kill me or I would consider doing so myself. Purely personal value, but high value. Many are okay backing this stuff up on some sort of cloud storage. After all, they have high personal value but are of little worth to bad guys. If you are okay with the metadata floating around out there on the cloud, then paying for an outside storage basket gives excellent peace of mind. Depending on how much of this you've got, it could get pricey though.
[*]Critical data: This is stuff like personal letters, contact databases, accounting databases, e-mail databases, tax/financial records, medical records etc. Stuff that's deeply personal and can be used to attack your assets or steal identity. And if lost, would constitute a true hardship or disastrous loss of records. This stuff is volatile (changes daily/weekly), highly sensitive and extremely valuable. Thankfully, these files also tend to be small. Mine fit on a USB stick. These can therefore be backed up cheaply and easily.[/list]
[/LIST]
There it is. A quick and dirty backup regime. There are so many variations on the above and there's no one&#8209;size&#8209;fits&#8209;all solution. Each person's needs are different and each needs to spin their own solution. It takes work and it takes thought, but when disaster strikes, you will pat yourself on the back that you were prepared. There are at least a dozen backup apps available for Linux. All Ubuntu flavours come with a backup utility called Déjà-Dup. For instructions, please see: [https://www.linux.com/learn/total-system-backup-and-recall-deja-dup](https://www.linux.com/learn/total-system-backup-and-recall-deja-dup)

I'm not recommending this package. It is simply the one that is prepackaged so involves the least work and research.

BTW, those USB sticks are so cheap that I do two at once and keep one set off site at, say, my kid's place. A bank safety deposit box also does nicely.

Good luck and Happy Ubuntu-ing!
DH

---

### Post by TheFu on 2021-01-10
Nicely laid out DuckHook.

I have a plex server.  Media files are huge and I can't afford to do proper, versioned, backups due to the cost of storage, but I can have a delayed mirror of the media files used by plex.  For that, I use rsync a few times every week. Nothing on my Plex system uses RAID.  This year, the OS HDD which contains the plex DB and metadata plus about 3TB of media failed. It was an inconvenience for a few days until a replacement HDD arrived. There wasn't any data loss besides a few TV recordings from that week. I think my plex system has about 36TB of storage connected, so about 18TB of media. There are 10 HDDs connected.

The OS and my personal files on the plex server are handled similar to what DuckHook does.  I do not backup the OS either. I do backup the settings and OS data like the Plex metadata and DB using versioned backups.  We'll ignore snapshots, but I use them as part of my backups to ensure no corruption happens of that information.

For things that need versioned backups, rsync isn't the best choice. Some more reading:

A simplified backup script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.

Restoring backups: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

rsnapshot: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)

Until you've actually restored a system using your backups (and only your backups), you don't really have a solution. Plan on the first 5 attempts failing and tweaking the backups over time to capture some other useful information about the system to address other problems where a full restore isn't the best option.

---

### Post by clctr13760 on 2021-01-10
> **DuckHook said:**
> 
[LIST=1]
[*]
[LIST=a]
[*]Convenience data: This is stuff that I already have source media for—CDs, DVDs, BDs. It's a pain to rip these to HDD again, but so what? It's just a matter of putting in the time. I rely on my redundant disks to give me enough protection here to feel safe.
[/LIST]
[/LIST]
This is the only data that will be on this system, and all important files are on my main PC with copies on spare flash drives.

TheFu,
Thank you for the links to more reading.  I've never had a true backup solution, as the files I was worried about, just made it to a flash drive since they weren't very large.  If something went wrong (which thankfully never has) I planned on copying them back after the problem was fixed.

---

### Post by TheFu on 2021-01-10
> **clctr13760 said:**
>  I've never had a true backup solution, as the files I was worried about, just made it to a flash drive since they weren't very large.  If something went wrong (which thankfully never has) I planned on copying them back after the problem was fixed.

Everyone is like you, until there is a problem and 80% of your data is lost.  That happened to me decades ago.  That wasn't enough for me to get backup religion, however.  I did get weekly-to-quarterly mirror religion.  That saved me a few times, then I had gotten a few clients and was running some servers for them.  In a professional shop, not having backups would be career ending, so I spend the time, the effort, did lots of testing of different solutions, but all the time had my mirroring answer before coming up with what I use today.  You can skip all that effort by jumping to the decades proven solution immediately.

There is another option, of course.  If you buy a $400 NAS device, most of them will have a way to backup to an external USB drive and to multiple cloudy services like S3-Glacier, Dropbox, and a number of other paid backup providers online.  You'll have a local copy. You'll have the RAID box. You'll have some off-site backups for the really critical stuff which can also be encrypted.  Trading money for time and expertise is a good solution for many people.

---

### Post by rsteinmetz70112 on 2021-01-11
Mirroring will protect you somewhat from hardware failure. It will not protect you from yourself or from malicious software. Backups are essential to be able to recall data from one or more hopefully isolated backups which have more than one version.

---

