---
title: "Let us speak about filesystems"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by deri on 2013-04-03
I am quite new to Linux. Been using around a year now, switched back from windows. I have only ext4 filesystem on my kubuntu. I just read that ZFS has released a new version of it's own filesystem. And i do know that there are other filesystems as well. 

Does anyone have knowledge over switching filesystem to another? Or does the linux tottaly die if you suddenly change your fs?

---

### Post by haqking on 2013-04-03
> **deri said:**
> I am quite new to Linux. Been using around a year now, switched back from windows. I have only ext4 filesystem on my kubuntu. I just read that ZFS has released a new version of it's own filesystem. And i do know that there are other filesystems as well. 

Does anyone have knowledge over switching filesystem to another? Or does the linux tottaly die if you suddenly change your fs?

You would need to format your partitions to the new filesystem which means backing up your data and then doing a reinstall.

you can convert ext3 to ext4 but that is cause they are closely related.

I imagine if you need to ask such a question then you probably dont have a valid reason to change ? What is your reason ?

---

### Post by agent-squirrel on 2013-04-03
The alternative filesystems that exist are usually for a highly specialized purpose and so I would imagine the change would make little to no differance to you.
The BTRFS filesystem is what is set to replace the ext4 FS in the future and you will be able to convert from ext4 to BTRFS in place.

---

### Post by d0006 on 2013-04-03
Ext4 is currently the best general purpose filesystem for Linux. Xfs can offer some advantages for very large files such as media files. As [**[COLOR=#000000]agent-squirrel[/COLOR]**]("http://ubuntuforums.org/member.php?u=327044") said, btrfs will replace ext4 someday.

---

### Post by dyan on 2013-04-03
If you are just using for general purpose then yea do as hagking said back-up + reinstall to ext4.

Honestly, I wouldn't bother changing that until I really need to reformat that specific partition. Ext 3 already has journaling which is the most essential part of ext.

---

