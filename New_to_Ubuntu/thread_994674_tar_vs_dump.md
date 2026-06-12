---
title: "tar vs dump"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by sazan on 2008-11-27
hi
i was going thru backup tools and came across two tools used in linux tar and dump.. 

but it is hard for me to figure out what is the difference between the two and which is more efficent...??

tar is an archieve and dump is similar to mirroring ..is it??

---

### Post by Michael.Godawski on 2008-11-27
Some reading:

[http://perbu.livejournal.com/5821.html](http://perbu.livejournal.com/5821.html)

Here a quote from
[http://www.nabble.com/tar-vs-dump-to5825392.html](http://www.nabble.com/tar-vs-dump-to5825392.html)
> 
 Backing up live systems, open files and  
data bases can be complex & there are more than a few pitfalls which  
many commercial apps try to resolve. In the end, you must do your own  
homework & pick your poison. 

A good collection of Linux Backup resources... 
[http://www.linux-backup.net/](http://www.linux-backup.net/)
[http://www.debianhelp.co.uk/backup.htm](http://www.debianhelp.co.uk/backup.htm)

Some Backup Docs 
[http://www.backupcentral.com/thebook.html](http://www.backupcentral.com/thebook.html)
[http://tldp.org/LDP/sag/html/sag.html#BACKUPS-INTRO](http://tldp.org/LDP/sag/html/sag.html#BACKUPS-INTRO)
[http://www.seifried.org/security/index.php/Linux_Backup_Guide](http://www.seifried.org/security/index.php/Linux_Backup_Guide)
[http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/backup-rest.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/backup-rest.html)
[http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-The-Ultimate-Solution-v2.0.pdf](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-The-Ultimate-Solution-v2.0.pdf)  
#pg787 
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch34_:_Basic_MySQL_Configuration#MySQL_Database_Backup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch34_:_Basic_MySQL_Configuration#MySQL_Database_Backup)

I have used find + cpio for years, very flexible (scriptable + excludes)  
& can span partitions gets paths right. 
# EXCLUDE='^./lost\+found$|\.rpm$' 
# find /home -xdev -depth -print | egrep -v ${EXCLUDE} | cpio -dumpav  
/mnt/backup 
[http://marc.theaimsgroup.com/?l=jaxlug-list&m=111177853101808&w=2](http://marc.theaimsgroup.com/?l=jaxlug-list&m=111177853101808&w=2)
[http://www.debianhelp.co.uk/cpiocommand.htm](http://www.debianhelp.co.uk/cpiocommand.htm)

Cloning: dd, Images and MondoRescue can be useful... 
Wonders of 'dd' and 'netcat': Cloning OS harddrives 
[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)
[http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html](http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html)
Mondo Rescue 
[http://www.mondorescue.org/about.shtml](http://www.mondorescue.org/about.shtml)
[http://www.systemimager.org/](http://www.systemimager.org/)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
Ghost for Linux + NTFS Disk Image Cloning - supports network imaging 
[http://directory.fsf.org/g4l.html](http://directory.fsf.org/g4l.html)
g4u - Harddisk Image Cloning for PCs - BSD based 
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Snapshots are another popular solution... 
Create Incremental Snapshot-style Backups With rSync And SSH - HowtoForge 
[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

---

### Post by m_l17 on 2008-11-27
For backing up using tar take a look a this thread:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup")

I prefer using rsnapshot:

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

They have a good How to:

[http://www.rsnapshot.org/howto/]("http://www.rsnapshot.org/howto/")

Another How to:

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

---

