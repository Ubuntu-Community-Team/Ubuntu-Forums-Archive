---
title: "Is There No Reliable Backup Method Without LVM Filesystem?"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by jeff140 on 2015-10-20
My understanding from what I've read is that even using something like rsync (or other backup programs) to do file backups, you can't be sure the backup program will get 100% of the files 100% of the time because Linux doesn't have an equivalent to Windows VSS which allows for backing up files that may have been opened/locked when the backup ran.  Technically I think you would have to temporarily re-mount the file system in read-only mode before performing the backup correct?  OR, use the LVM file system.  

Is this true?

---

### Post by sandyd on 2015-10-20
Not that I know of unless you want to use something like CrashPlan, which polls for file updates. Using Syncthing or BtSync (or any other system that actually polls for updates) will sync the files when they become readable to the app.
That being said, Linux does not normally lock files during updates or during writing. Most shell scripts/programs that will lock a file probably use flock to achieve it.

If you really want, you can probably use flock to lock the file during updates. flock will wait for a lock to become available if a file is already locked. It won't be very efficient though - imagine waiting hours for a backup because some other process has decided to flock a file for 3+ hours....

If your adventurous, you can use btrfs though, which does support [snapshots]("https://btrfs.wiki.kernel.org/index.php/Incremental_Backup") of subvolumes.

Additional Info:
There seem(ed) to be work to create a snapshot system for ext4, but it has been [abandoned since 2011]("https://github.com/amir73il/ext4-snapshots/")
There are also multiple commercial alternatives including r1soft/etc

---

### Post by mastablasta on 2015-10-21
there are serious discussions (and legal checks) about including ZFS into Linux which is not here due to some legal restrictions. BTRFS is also already used by some distros and will probably become part of others in the future.

There are various backup programs that will do proper backups. after all most companies use Linux on servers and have to do backups (Google, Facebook...).

---

