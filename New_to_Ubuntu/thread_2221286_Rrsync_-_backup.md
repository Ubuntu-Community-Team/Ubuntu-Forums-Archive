---
title: "Rrsync - backup"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by il pepe on 2014-05-01
Need  some help bqcking up my ubuntu computer.

I have a script that makes incremental backups of my computer to a NAS.
But I would like to backup these backups just to be sure. (to a ubuntu desktop)

I'm working with the an monthly incremental backup for this one.
The problem is the size of the backup becomes quiet large. It has something to do with the links getting unlinked i guess. How do I solve this?

---

### Post by TheFu on 2014-05-01
Use a different backup solution that doesn't depend on hard-links.

---

### Post by Ralph L on 2014-05-01
I use LuckyBackup.  It is a front end for rsync.  It has the advantage that there is a single folder that contains your entire LATEST backup, so if you accidentally delete something it is easy to find and get back.  Also it automatically erases old backups (you set how many to keep) so that you don't use as much disk space.  I run 3 different backups--two of them to a usb disk and the third one to a different folder on my laptop hard disk.  This last backup is done automatically on a daily basis, only backs up the few folders/files that I am currently working on and changing, runs in a few seconds, and just provides an additional copy in case I accidentally delete something.  The other two backups are run weekly to a usb disk--one on Tues, one on Friday.  They are completely independent so if one goes bad, I always have the other one.  I use frcron to do the scheduling, since it has an option to schedule only one backup even if I have not used my laptop in several days.  I run LuckyBackup from a script to make up for a deficiency in it, whereby it deletes the oldest backup before it asks the user to plug in the usb disk (with the option of canceling the backup).

---

### Post by SeijiSensei on 2014-05-01
I'm guessing your NAS uses NTFS.

If you are backing up to an NTFS-formatted device, you'll encounter problems with things like symbolic links.  The NTFS filesystem has no understanding of such Unix-y primitives.  As a result, the symlinks must be followed and the linked files duplicated on the backup. 

You can get around this problem with a different strategy than rsync.  You would need to create a "[tarball]("http://www.computerhope.com/jargon/t/tarball.htm")" of the files and write that to the NTFS device.  Something like this:
```

cd /
sudo tar -cjpf /path/to/your/NAS/backups/mylinux.tar.bz2 . --exclude=proc/ --exclude=sys/ --exclude=run/

```
The file mylinux.tar.bz2 is compressed with the BZip2 algorithm.  The "-p" switch tells tar to preserve all the file attributes like modification date, owner, and permissions.  It also copies symlinks as links.  The three excluded entries are transitory mount points that are recreated at every boot.  This assumes you have mounted the NAS to /path/to/your/NAS/, e.g, /media/NAS, and are storing the tarball in the "backups" folder on that device.

If you can backup the entire NAS, and intend for it only to be used by Linux machines, then you could reformat the drive as ext4 and restore the backed-up files.  Then you can use rsync.

---

### Post by TheFu on 2014-05-01
Or use a backup system that is not dependent on the target file system type.  duplicity, rdiff-backup come to mind as options.  There are others, including gnutar. gnutar is just a little old-school for full-machine backups, but that is just an opinion.  There are lots of great backup tools for linux - most are based on librsync and highly efficient.

Before deciding on a new backup tool/method, try it out for a week or 2 on /etc. Then you will be able to see what it does, how it works, and most importantly - how to restore.  None of the backup solutions is perfect, so pick the warts you can live with.

I use rdiff-backup for the first copy (local network), then rsync to push the backup area off-site.  Restoring most of the machines here takes 30-45 minutes. Only very large data restores take longer, but the server is up and available.

---

### Post by il pepe on 2014-05-02
Hi,
thanks for all the replies!
I'm guessing with my rsync backup script from laptop to NAS, I already will have problems then if I ever want to recover? (NTFS<->linux)

tar-ring and rdiff-backup really look like good alternatives then.

Thanks a lot!

---

### Post by TheFu on 2014-05-02
Backing up the data, settings, programs isn't all there is on Linux systems. We also need the owner, group AND permissions for every file, directory, link, saved.  If you use ACLs, then those also need to be backed up.  If the backup method doesn't address those things, you have data, not recovery. That's fine for many sorts of things ... like videos, music, most of the large data we tend to store.  But it is NOT good enough for many things necessary to restore a system.  

Until you attempt a full recovery, you'll never know.  Stupid little things that we forget can completely screw up restores.  It is best to know this BEFORE you need it.

My rule of thumb is 
* less than 1GB - gnutar
* lots of small files, some that change daily, as in a $HOME or almost complete system backup - rdiff-backup
* large media files that do not change - rsync

I've written and presented about Linux backups many times over the years.  This search link will let you peruse those things from the most recent: [http://blog.jdpfu.com/search/backups/page/4](http://blog.jdpfu.com/search/backups/page/4)
Every backup method sucks in some way, including rsync, gnutar and rdiff-backup. The right tool for the right job is needed.

---

