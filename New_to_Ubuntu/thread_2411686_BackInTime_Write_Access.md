---
title: "BackInTime: Write Access"
date: 2019-02-02
forum: New to Ubuntu
---

### Post by barddzen on 2019-02-02
[SIZE=2][FONT=arial]Hello,

I am trying to setup BackInTime and haven't been able to get it to start.  I have setup all of the settings, folders, and options but when I try to start a backup I get a dialog:

"Can't write to: /mnt/backups Are you sure you have write access?"

This mount point is to a Synolog DS216+ NAS where I've setup a folder to receive the backups.

I am mounting this location using the following command:

sudo mount -t -cifs //192.168.1.115/UbuntuBackup /mnt/backups -o username=backintime,password=[thepassword]

I've made sure this folder has the proper rw permissions.  In fact, I'm testing out various backup software and DejaDup, fwbackup both already are backing up to this folder without issue, but BackInTime seems to think there is a read-write permissions issue.

Any thoughts on what I might need to change to make this work?[/FONT][/SIZE]

---

### Post by TheFu on 2019-02-02
I haven't used B-i-T in about 5 yrs, so things may have changed, but at that time .... back-in-time required full Unix permissions in the backup area so user, group, 32-bit permissions and ACLs could be stored.  CIFS doesn't provide this.  Any tool based on rsync used for backups will have similar issues.  Especially those that use hardlinking for the different versions.  Hardlinking loses the permissions changes over time which might be very important or not.  This was the main reason I stopped using B-i-T for backups, except for end-user files (effectively just the $HOME) and nothing else.

If you want back-in-time to work correctly, the backup area should have a Unix file system, it must support hardlinking, and if it is on the LAN, NFS should be used.

DejaDup is based on duplicity and it chunks the data and the permissions into bites, so pretty much any sort of storage can be used.

---

