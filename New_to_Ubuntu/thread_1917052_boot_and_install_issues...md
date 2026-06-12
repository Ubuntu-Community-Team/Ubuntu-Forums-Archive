---
title: "boot and install issues.."
date: 2012-01-29
forum: New to Ubuntu
---

### Post by spillage on 2012-01-29
Hi All.

Just recently i got a inramfs message or something like that so I booted up from my live cd as i read that i needed to replace a file. i discovered that even through nautilus i cannot access any drives. They all show up if i try to install from the live cd and all partitions are there also in gparted but like i said i cannot access them and cannot get ubuntu to even install on any of them.


I cannot understand why this is. I dont even want to have to do a fresh install and would prefer to try to fix the issue but cannot understand why i cannot access any of the drives.

any help or advise would be appreciated.

Spill.

---

### Post by spillage on 2012-01-29
sorry using 10.04 and have 2 x 600gb drives and a 40gb.

---

### Post by 2F4U on 2012-01-29
Can you show us the error message?

---

### Post by spillage on 2012-01-29
it now will only go to GRUB> and will not show the old message.

although i get this when trying to mount from live cd.

Unable to mount

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by oldfred on 2012-01-29
Not sure what problem is. I might try a filecheck to see if that is an issue.

#From liveCD so everything is unmounted,swap off if necessary, change example of sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

