---
title: "security update on Raid"
date: 2023-06-30
forum: New to Ubuntu
---

### Post by codelearner1029 on 2023-06-30
This is my RAID setup configuration, and I want to perform security updates on the disk mirrors one by one, starting with sda and then moving on to sdb. Is this possible? can someone provide steps to follow

```
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT 
sda       8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1    8:1    0   9.3G  0 part 
&#9474; &#9492;&#9472;md0   9:0    0   9.3G  0 raid1 / 
&#9500;&#9472;sda2    8:2    0   7.5G  0 part 
&#9474; &#9492;&#9472;md1   9:1    0   7.5G  0 raid1 [SWAP] 
&#9500;&#9472;sda3    8:3    0     1K  0 part 
&#9500;&#9472;sda5    8:5    0  20.5G  0 part 
&#9474; &#9492;&#9472;md2   9:2    0  20.5G  0 raid1 /home 
&#9492;&#9472;sda6    8:6    0  55.9G  0 part   
    &#9492;&#9472;md3   9:3    0  55.9G  0 raid1 /var 
sdb       8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1    8:17   0   9.3G  0 part 
&#9474; &#9492;&#9472;md0   9:0    0   9.3G  0 raid1 / 
&#9500;&#9472;sdb2    8:18   0   7.5G  0 part 
&#9474; &#9492;&#9472;md1   9:1    0   7.5G  0 raid1 [SWAP] 
&#9500;&#9472;sdb3    8:19   0     1K  0 part 
&#9500;&#9472;sdb5    8:21   0  20.5G  0 part 
&#9474; &#9492;&#9472;md2   9:2    0  20.5G  0 raid1 /home 
&#9492;&#9472;sdb6    8:22   0  55.9G  0 part   
    &#9492;&#9472;md3   9:3    0  55.9G  0 raid1 /var 
sr0      11:0    1  1024M  0 rom
```

---

### Post by TheFu on 2023-06-30
Just because something might be possible, that doesn't make it a good idea.

If you want an easy fallback, then you should have deployed a volume manager with snapshot capabilities.  RAID1 is meant to solve 2 issues - and only 2 issues.  
a) surviving a single failure
b) improving READ performance.

When we choose to break a mirror, we've just destroyed the entire reason for having RAID1.  The only time we should break a mirror is when there's a failure and we are replacing that hardware.

Any other issue should be solved using another solution/tool.  I'd use LVM, but you could use ZFS if you prefer or simple backups that can be restored quickly.  RAID is never a replacement for backups. Never.

---

### Post by MAFoElffen on 2023-06-30
+1 on all said.

I'm trying to wrap my head around trying to figure out what you think you are doing? What kinds of 'security updates' do you think you need to do in a segmented fashion **below** the level of the OS?

Let me introduce myself... Once upon a time, I was the Project Leader for the 'mdadm-gui' project (now dead). It died when TheFu convinced me that making mdadm too easy for new users was dangerous. LOL. There was more, but that was what one of the major things it boiled down to.

As far as I know, there was a security update to mdadm, but to the utility itself. Not to the created mdadm volumes that it created. When there was updates to mdadm where it had to change the format of the metadata, then you had to backup everything that was on the volumes, destroy the volumes, create new, then restore back onto those volumes... Because you couldn't just reformat the metadata of the volume (including the mdadm version of) without doing that.

Which is one of the main reasons, for myself, that I migrated everything I have away from mdadm to a Volume Manager with RAID capabilities inside it, instead of having things on top of RAID. First to LVM2, then to ZFS. With both those, you can update the volume manager and update the volumes 'Live', online, without any risk or extra work. Both these are every flexible and adaptable, with many years of production service experience showing proven dependability.

In providing server services, the name of the game is 'uptime'. In a disaster, I proved during much testing, that it is easier and faster to install restore a fresh system image with a Volume Manager, then restore the infrastructure, without a RAID base underneath it. Depending where the failure was, some of those took days, compared to under an hour. It took me years to open my eyes to that reality, and change the way I saw things clearly. In getting back up to provide a service, sometimes repairing what is broken (there) takes much longer than just installing and getting back to where you were.

Nothing replaces a good backup strategy. Having the ability to do Snapshots does add ***very much*** value to easily and quickly getting back to point in time. I use them extensively, all the time. Especially to rollback updates or for reconfig's. But always have a good backup to fall back to.

So my question still is, what do you think you need to do, in the way of 'security updates', that is below the level of the OS? Which would be in regards to mdadm... Because most 'security updates' relate directly to the OS level... Am I confused by that logic?

---

### Post by codelearner1029 on 2023-07-04
Hi,
Its not just about security update rather any update may be version update or anything else....and it's not related to mdadm but the OS itself.

---

### Post by TheFu on 2023-07-04
> **codelearner1029 said:**
> Hi,
Its not just about security update rather any update may be version update or anything else....and it's not related to mdadm but the OS itself.

In the Unix world, to mitigate issues like you've described, we have 3 methods.
[LIST=1]
[*]Use the volume manager to take a snapshot
[*]Follow normal system backup methods
[*]Use snapshots AND create backups [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)
[/LIST]

"Snapshots" as claimed by most backup tools aren't really snapshots.  Proper snapshots are only possible if a volume manager is involved - LVM, ZFS, BTRFS. Anything else is **not** a real snapshot, regardless of the claim.  Some backup tools will use a volume manager along with snapshots, if it is available.  Timeshift is like that - but **timeshift** only does it when BTRFS is used, none of the other volume managers are used and if BTRFS isn't available, it will use **rsync**.   

rsync is fantastic. I use it daily, but not for proper versioned backups - with or without using a snapshot of the volume manager.  Proper, daily, automatic, backups are what differentiate between end-users and professional administrators.  There isn't much excuse for not having automatic, daily, versioned, backups these days.  A 2TB HDD which can hold hundreds of backup sets is $20-$40.  All the software necessary is free.  Scripts have been posted which can be used as-is to do that job.

And of course, no backup can be trusted until the restore is tested, so don't forget/avoid doing that critical step.  When properly setup and running, backups take a few minutes daily. 1-5min typically.  A full restore takes me between 30 and 45 minutes loosely broken down into 3 phases.  Fresh OS install, restore all data and settings, and lastly, install the previously installed packages using a list-o-packages that is created daily, just prior to creating backups, so it is always up to date. When the restore is completed, the system will be just like it was at the time the backup was taken (or close enough) that it won't matter.

The method I use avoids having to backup 5-10GB of OS files, since I only backup settings, not programs. Avoiding 5-10GB of backups for each system speeds up all backups, reduces backup storage needs, and simplifies the restore process since at restore time, just a minimal OS is installed.  By returning all data and settings to where they were in the directory system during recovery, we've decoupled the storage from the backups. It is not hard to completely change file systems uses on an OS using this method.  Going from ext4 to LVM+ext4 or ZFS is pretty easy, even with wiping the entire OS as the 1st step of the restore process.

And if you are using RAID, there are some RAID problems that can only be solved by destroying the RAID array, rebuilding it fresh, then restoring data from backups.

---

### Post by MAFoElffen on 2023-07-04
> **TheFu said:**
> In the Unix world, to mitigate issues like you've described, we have 3 methods.
[LIST=1]
[*]Use the volume manager to take a snapshot 
[*]Follow normal system backup methods 
[*]Use snapshots AND create backups [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html) 
[/LIST]

"Snapshots" as claimed by most backup tools aren't really snapshots.  Proper snapshots are only possible if a volume manager is involved - LVM, ZFS, BTRFS. Anything else is **not** a real snapshot, regardless of the claim.  Some backup tools will use a volume manager along with snapshots, if it is available.  Timeshift is like that - but **timeshift** only does it when BTRFS is used, none of the other volume managers are used and if BTRFS isn't available, it will use **rsync**.   

rsync is fantastic. I use it daily, but not for proper versioned backups - with or without using a snapshot of the volume manager.  Proper, daily, automatic, backups are what differentiate between end-users and professional administrators.  There isn't much excuse for not having automatic, daily, versioned, backups these days.  A 2TB HDD which can hold hundreds of backup sets is $20-$40.  All the software necessary is free.  Scripts have been posted which can be used as-is to do that job.

And of course, no backup can be trusted until the restore is tested, so don't forget/avoid doing that critical step.  When properly setup and running, backups take a few minutes daily. 1-5min typically.  A full restore takes me between 30 and 45 minutes loosely broken down into 3 phases.  Fresh OS install, restore all data and settings, and lastly, install the previously installed packages using a list-o-packages that is created daily, just prior to creating backups, so it is always up to date. When the restore is completed, the system will be just like it was at the time the backup was taken (or close enough) that it won't matter.

The method I use avoids having to backup 5-10GB of OS files, since I only backup settings, not programs. Avoiding 5-10GB of backups for each system speeds up all backups, reduces backup storage needs, and simplifies the restore process since at restore time, just a minimal OS is installed.  By returning all data and settings to where they were in the directory system during recovery, we've decoupled the storage from the backups. It is not hard to completely change file systems uses on an OS using this method.  Going from ext4 to LVM+ext4 or ZFS is pretty easy, even with wiping the entire OS as the 1st step of the restore process.

And if you are using RAID, there are some RAID problems that can only be solved by destroying the RAID array, rebuilding it fresh, then restoring data from backups.
Bravo! Well worded and to the point.

His 2 posts have brought up so many issues with what was said, in so little words. without him realizing what those were. They brought up so many possibly misunderstood things at once. 

@codelearner1029 --

I could do a 2 hour lecture on this to Computer Science Students with Linux experience (already) and still not cover the required solutions to all the issues from what you said was "your plan", that you just posted in a single sentence...

Instead, remember these two commands.
```

sudo install mdadm
sudo mdadm --assemble --scan

```
If an Array fails, that last command will try to bring up your 3 RAID1 MD devices...

Those two commands in a console prompt, while booted from a Live Image Environment, will install what you need to work with mdadm and to assemble whatever RAID Array is related to the installed system. From then on, the LIE will see the MD devices, and be able to work with what is there. You could then mount the Array, and chroot into the installed system to do maintenance, recovery, repair, etc. You could also just fire up the installer and reinstall to those created raid containers. Whatever you wanted to do.

************************************************************************************************
RAID is NOT a substitute for Backups or a Disaster Recovery Plan. Reiterating what TheFu said, because something is possible, does not make it a good idea.

The disadvantages of both traditional hardware and software RAID is that is does not give warnings before it fails and goes into a degraded or failed state. Reassembling an Array on huge data may take days, and sometimes, because of the extra stress during a reassembly process, you will lose a second drive and lose everything.

RAID1 does not get capacity of performance benefits. It is a write once redundant method, so it risks failure from bit rot. It will not guaranty that when one disk fails that the other will come up without errors. A RAID1 risks a second disk failure twice that of RAID5 on reassembly.

I myself, used to use LVM2 on mdadm RAID... Over a decade ago. Many things have changed, grown and or changed in the last 15 years. I switched from doing that, to LVM2 RAID, then back to using ZFS with RAIDz. 

LVM2 uses MD to implement it's internal raid devices, and adds more to that. If using LVM2 RAID, LVM2 at least has a 'raid_fault_policy' that can warn or automatically bring in a spare when there are too many errors. It will also report strings similar to "read failed after 0 of 4096 at 0: Input/output error" when there is a problem. So adds warnings before a failure.

Since 'how' you worded and brought up the questions and discussion... TheFu brought up the idea of using self-healing CoW Volume Managers such as ZFS, BTRFS or ReFS... These try to detect and protect against bit rot, warn when there are errors,  and are meant to be self healing. But that is another discussion.

But if things go south, you have a good backup right?

The next you subject brought up as your plan for Release upgrades... Upgrade in place. Both TheFu and I were System Administrators from the UNIX world. We are fans of migrations to fresh, clean new installations. Upgrade in place is possible, but there are risks, and you will certainly carried over some things from the old with it. I could go into it in very much detail, but for now, I'll leave it at that. With migrations for release, you will have a better running, faster system, installed as designed for that release.

What release migrations also give you is a chance to use lessons learned from your last release, to improve your system infrastructure. You are not locked into doing things the same way for eternity.

Yes. You can do what you want. Many things are possible. RAID1 is more protected than just using a flat filesystem with nothing else. But if you are worried about how to be or feel more "secure", as that relates to reliability, and data integrity, there are other ways to plan, layout and manage your system resources. More things are possible, and may make more sense.

Just thoughts to think on.

---

