---
title: "[SOLVED] Undelete user account"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-09-09
I feel like such an idiot. I was walking my dad through creating an account with adduser. I created an account on my computer (called test) to explain each step to my dad. I finish and want to delete the account. Instead of running ```
sudo deluser --remove-home test
``` I ran ```
sudo deluser --remove-home justin
``` which is my user account. It did give an error, saying that it couldn't delete me because I was logged in. 

My question is: how do I undo this? The most important thing is the recover my files. It's a reiserFS partition. I would also like to recover the account, but that's not the most important part. 


Thanks

---

### Post by P13808 on 2008-09-09
Sorry, but you can't.  Linux(or anything based off UNIX) has no undelete.  If you made a backup you can recover it, but other than that, that file is gone.

EDIT: This link might have some useful information, IF you fit the narrow specifications. [http://www.glug-howrah.org/modules.php?name=Forums&file=viewtopic&t=400](http://www.glug-howrah.org/modules.php?name=Forums&file=viewtopic&t=400)

---

### Post by jemate18 on 2008-09-09
> **P13808 said:**
> Sorry, but you can't.  Linux(or anything based off UNIX) has no undelete.  If you made a backup you can recover it, but other than that, that file is gone.

EDIT: This link might have some useful information, IF you fit the narrow specifications. [http://www.glug-howrah.org/modules.php?name=Forums&file=viewtopic&t=400](http://www.glug-howrah.org/modules.php?name=Forums&file=viewtopic&t=400)

Yup... I found no article and links about undelete.. Its just once it is deleted, it will never be brought back.. unless you have the backup

---

### Post by Titan8990 on 2008-09-09
This is why it is better practice to lock the accnts password instead of deleting it.


sudo passwd -l test

---

### Post by egalvan on 2008-09-09
OK, I'm no rocket scientist, or Linux Guru,

but I went Googling and found

**Results 1 - 10 of about 421,000 for [COLOR="Red"]linux file recovery[/COLOR]. (0.28 seconds) **

---

### Post by jbrown96 on 2008-09-09
Thanks for the replies. I found an article on how to do it. File recovery is dependent on the file system. Aparently, ext3 has pretty good recovery functions. ReiserFS has a function that will work, but it is not advertised as that. This guide is from [http://antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments]("http://antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments")
If you are trying to recover files from your root partition, it will break your system. See note below.
   >  1. Once you realize that you've lost data, don't do anything else on that partition - you may cause that data to be overwritten by new data.
   2. Unmount that partition. e.g., umount /home
   3. Find out what actual device this partition refers to. You can usually get this information from the file /etc/fstab. We'll assume here that the device is /dev/hda3.
   4.

      Run the command: reiserfsck --rebuild-tree -S -l /root/recovery.log /dev/hda3

      You need to be root to do this. Read the reiserfsck man page for what these options do and for more options. Some interesting options are '--rebuild-sb, --check'

      After the command finishes, which might be a long time for a big partition, you can take a look at the logfile /root/recovery.log if you wish.
   5. Mount your partition: mount /home
   6. Look for the lost+found directory in the root of the partition. Here, that would be: /home/lost+found
   7. This directory contains all the files that could be recovered. Unfortunately, the filenames are not preserved for a lot of files. You'll find some sub-directories - filenames within those are preserved!
   8. Look through the files and copy back what you need.

This will probably (it did mine) destroy your root partition. Because it tries to rebuild all deleted files, it messes up system files. I was able to copy my files to another disk, but I will have to reinstall Kubuntu because the system refuses to boot.

---

