---
title: "Configuring an rsync server and clients"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by anoldguy on 2013-12-08
The more I search, the more contradictory source/destination info I am finding.  Here is what I want to do: 

I have built an Ubuntu PC with three additional disc drives to be used as a “server” for storing copies of my other PCs.  I have three “client” PCs running Ubuntu and one with Windows 7.  All Ubuntu versions are 12.04 and later.  I want to back up my home folders that contain documents, e-mail, photos, home video, MythTV, etc. in case of a disc failure.  I also make a three-generation back up on a USB drive that I take to my safe deposit box a couple of times a year. 

1. Do I use rsync commands on my “server” PC to mirror the files from the “client” PCs, or “push” the rsync from each “client” PC to the “server PC?

2.  If the rsync command is run on my “server” PC and I am using ssh, do I generate ssh keys on each of the “client” PCs and copy the “client” ssh keys to the “server” PC so it can log in to the clients?

3. The “server” 4 TeraByte disc drives are not yet formatted.  I am planning to format each disc for one large partition in Ext4.  I could make a folder for each of my “client” PCs on a “server” disc.  Can I span discs on the “server” so that if one of the “server” discs was filling up, rsync would go to the next disc on the “server”?  My MythTV PC will have the largest need for file space, it could easily overflow a 4 TB disc in the future.  I do not want to use RAID; every I/O makes activity/wear on all three discs.

---

### Post by papibe on 2013-12-08
Hi anoldguy.

I use rsync a lot for both its main purpose, mirroring, and as a backup tool. 

Having said that, you would need to write backup scripts that use rsync, and also some automation tasks (using cron or anacron for instance). Those then would have to tested and debugged, so you end up with a working system.

With that in mind, I'd recommend taking a look at backup tools that let you the only concern of 'what, when and where to'. Most of the Linux tools would use rsync underneath anyway.

Im the case of Windows, there are several ports, and tools that use rsync as a base: deltacopy, cwRsync, or even the CygWwin framework, but I'd recommend to take a look at [Duplicati]("https://sites.google.com/a/duplicati.com/duplicati/").
> **anoldguy said:**
> 2.  If the rsync command is run on my &#8220;server&#8221; PC and I am using ssh, do I generate ssh keys on each of the &#8220;client&#8221; PCs and copy the &#8220;client&#8221; ssh keys to the &#8220;server&#8221; PC so it can log in to the clients?
Yes. Note that you generate a pair. One private that remains on the client, and a public that needs to be added to the user's ~/.ssh/authorized_keys on the server.

In most cases client machines pushes data to the server, because the server is always on, but clients are not.

However, if you take a look at the approach that [BackupPC]("http://backuppc.sourceforge.net/") has, you'd notice that in this case the server pull changes from the clients. Since you seem to take backup seriously, and think of you home network, as I do, as a small business, I would recommend considering a comprehensive solution as BackupPC.

I hope that helps a little. Let us know if you have more questions.
Regards.

---

### Post by SeijiSensei on 2013-12-09
> **anoldguy said:**
> 2.  If the rsync command is run on my &#8220;server&#8221; PC and I am using ssh, do I generate ssh keys on each of the &#8220;client&#8221; PCs and copy the &#8220;client&#8221; ssh keys to the &#8220;server&#8221; PC so it can log in to the clients?

You only need to create one key for the root user on the server, then use ssh-copy-id to copy that key to the root user on each client.

> 3. Can I span discs on the &#8220;server&#8221; so that if one of the &#8220;server&#8221; discs was filling up, rsync would go to the next disc on the &#8220;server&#8221;?  My MythTV PC will have the largest need for file space, it could easily overflow a 4 TB disc in the future.  I do not want to use RAID; every I/O makes activity/wear on all three discs.

Well, you could use RAID0 to create a single filesystem that spans all three disks rather than something like RAID5 which writes to all of them simultaneously.

Another method to combine disks is [LVM]("https://wiki.ubuntu.com/Lvm").  You can create a virtual LVM volume that spans multiple physical volumes.

I think the first of these is easier to implement than automatic "fail-over" unless you have some experience writing shell scripts.  Then you could run the script on the server to pull the backups from the clients, but add code to check for the amount of free space available on the selected filesystem. If it falls below the minimum, choose a different device.  Something like this:

```

MIN_SPACE=1000000000000  # one terabyte
BACKUP_DEV=/dev/sdb1
BACKUP_SPARE=/dev/sdc1
SPACE_AVAIL=$(df | grep $BACKUP_DEV | awk '{print $4}')

if [ "$SPACE_AVAIL" > "$MIN_SPACE" ]
then
     mount $BACKUP_DEV /media/backup
else
     mount $BACKUP_SPARE /media/backup
fi
[etc.]

```

That's pretty inelegant, but you get the idea.

LVM can be rather complex to set up, so whether it is easier than writing a script to rotate volumes depends on your level of experience.

---

