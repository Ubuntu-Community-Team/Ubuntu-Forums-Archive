---
title: "Flashdrive doesn't think I own it"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by Ed W. on 2016-11-19
I'm having problems with a Toshiba Transmemory flashdrive that won't let me add files to it after formatting.  The message under permissions says, "You are not the owner." I recently wiped the computer hard drive and loaded Ubuntu 16.04, could this be part of the problem?

---

### Post by kurt18947 on 2016-11-19
After you wiped and restored the hard drive, did you recreate the same user accounts? Linux file ownership is good for security but can sometimes be a bit of a PITA. You need to have the same user name on the new install as on the old. If the files I'm storing on a flash drive are not sensitive, I often use FAT32 or NTFS formatted drives because those file systems don't support linux file permissions so no permissions issues.

---

### Post by kpatz on 2016-11-19
When you say "after formatting", do you mean after formatting the flash drive or the computer hard drive?

If the flash drive, what file system type did you put on it?  FAT32? NTFS?  ext4?  Something else?

---

### Post by Ed W. on 2016-11-20
Sorry, I loaded 16.04 LTS over 14.04 without saving 14.04- i didn't click the upgrade option, I thought it would be a cleaner option the way I did it.  I didn't know about linux file permissions.  Then when two of my flashdrives worked just fine, but one didn't I formatted the flashdrive to ext 4.  That's when it said you're not the boss of me.  Following the above advice I redid the flashdrive file system to NTFS.  Now it appears to be working, Thanks!  I appreciate the time and help.

---

### Post by yancek on 2016-11-20
Linux files/directories all have owner:group and permissions which you can determine by running the command:  ls -l /home/ed/somefile  (just an example) on any file or directory.

Windows filesystems don't use the standard Linux owner:group and permissions.
Flash drives are generall mounted/accessed under /media/user so you could run the command:  ls -l /media/ed (assuming Ed is your actual username) to find the owner:group and permissions for your flash drives.  If you are not the owner of, for example, a flash drive labelled as flash under /media/ed, you can give yourself ownership with a simple command:

sudo chown ed /media/ed/flash  (as an example)

---

### Post by kingneutron on 2016-11-29
--To avoid permissions problems like this in the future, I recommend creating a separate /home partition - this will survive an OS (re)install and you keep all your per-user settings.  Also, you could have backed up and restored /etc/passwd* and /etc/shadow from the previous install to recreate existing accounts. FYI

---

