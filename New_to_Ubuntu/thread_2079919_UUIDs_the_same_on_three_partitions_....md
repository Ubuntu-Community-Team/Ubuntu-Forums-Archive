---
title: "UUIDs the same on three partitions ..."
date: 2012-11-02
forum: New to Ubuntu
---

### Post by cwmoser on 2012-11-02
I've got 2 hard drives with Partitions having the same UUID.
I use Clonzilla to backup my OS partitions.
Partitions /dev/sda1, /dev/sda4, and /dev/sdb4 have the same UUID - see below:
Is there a way to fix this?

```

$ sudo blkid
/dev/sda1: UUID="a6536073-38bf-4faa-b69c-36caa8d029de" TYPE="ext4" 
/dev/sda2: UUID="1239405f-6acc-4cdc-a2c2-c5ca20afd6a5" TYPE="swap" 
/dev/sda3: LABEL="Home" UUID="006fba9b-f027-48b7-96ec-832d93ac9711" TYPE="ext4" 
/dev/sda4: UUID="a6536073-38bf-4faa-b69c-36caa8d029de" TYPE="ext4" 
/dev/sdb1: UUID="1a50ca13-e3c3-42bb-a6b0-c1b2f224fe22" TYPE="ext4" 
/dev/sdb2: UUID="124f94a4-a193-4267-bc0b-8679867bc418" TYPE="swap" 
/dev/sdb3: LABEL="HOME-2" UUID="439dcfb9-003e-44ac-80e0-9763de0b1210" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="a6536073-38bf-4faa-b69c-36caa8d029de" TYPE="ext4" 

```

---

### Post by cwmoser on 2012-11-02
I found a solution - use the tune2fs command to change
the UUID of a specific partition to a new random value:

$  sudo  tune2fs  -U  random  /dev/sdb4
$  sudo  tune2fs  -U  random  /dev/sda1


Carl

---

### Post by redmk2 on 2012-11-02
> **cwmoser said:**
> I found a solution - use the tune2fs command to change
the UUID of a specific partition to a new random value:

$  sudo  tune2fs  -U  random  /dev/sdb4
$  sudo  tune2fs  -U  random  /dev/sda1


Carl

That's all well and good, but the real question is how did this happen?  If you are backing up an image of the entire partition (not just the files on the partition), I'll bet the UUID is part of the backup.  The next time you back up you most likely will have the same condition (two partitions with the same UUID).

---

### Post by oldfred on 2012-11-02
And now all the UUID settings inside grub & fstab will not be correct unless you restore to the original UUID.

Usually cloned backups should to to offline locations so there is no issue.  For on-line backups I just use rsync to copy most of /home. I assume I will not need install as I will just do full clean install and reuse /home data.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by cwmoser on 2012-11-02
> **redmk2 said:**
> That's all well and good, but the real question is how did this happen?  If you are backing up an image of the entire partition (not just the files on the partition), I'll bet the UUID is part of the backup.  The next time you back up you most likely will have the same condition (two partitions with the same UUID).

The UUIDs were duplicated when I cloned a partition on one drive to another drive using Clonezilla.  I was preserving my OS.

Now that I am aware what is happening, I can deal with it the next time I clone.  Knowledge is power:-)

---

### Post by redmk2 on 2012-11-02
> **oldfred said:**
> And now all the UUID settings inside grub & fstab will not be correct unless you restore to the original UUID.

Usually cloned backups should to to offline locations so there is no issue.  For on-line backups I just use rsync to copy most of /home. I assume I will not need install as I will just do full clean install and reuse /home data.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Exactly!  +1 for rsync or rsnapshot.  I don't see any reason to clone partitions just to save the data.

---

### Post by cwmoser on 2012-11-02
> **oldfred said:**
> And now all the UUID settings inside grub & fstab will not be correct unless you restore to the original UUID.

Usually cloned backups should to to offline locations so there is no issue.  For on-line backups I just use rsync to copy most of /home. I assume I will not need install as I will just do full clean install and reuse /home data.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I sometimes have to use Grub Rescue to fix my boot.

BTW, can rsync be used to clone a root partition?

Carl

---

