---
title: "Reconfigured my drive using GParted"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by BigZ1981 on 2013-05-29
**[SOLVED]**

Hi all, I recently decided to drop windows from my dual boot & stick with kubuntu 13.04.  Here's the thing: with windows I partitioned off the stuff I wanted to save so I can reformat & reinstall windows as necessary without losing my stuff. Now I'm wanting to do the same thing using kubuntu. I reinstalled kubuntu & merged my kubuntu partition with the one I was using for windows & that went fine, so I installed GParted & was able to pull more unallocated space to merge into my kubuntu partition.  Now I moved everything from ntfs partition into my kubuntu partition to format the ntfs partition into a logical ext4 partition.  Now I'm being told I have no write access on this new partition.  What am I missing?  Mind you, although I'm a techie, I'm still new to linux.  =)

---

### Post by dino99 on 2013-05-29
you can set your user as admin, and/or set the right on the partition 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user](http://askubuntu.com/questions/43570/change-owner-of-internal-hard-drive-partition-from-root-to-user)

---

### Post by newb85 on 2013-05-29
Setting your user as admin won't give you the kind of write permissions you want for the partition.  (In fact, I would bet the OP's user *is* admin.)  Unless, of course, you enjoy using sudo for all your day-to-day file operations. ;)

I'm guessing that the way you have it set up, the partition is owned by root, and only root has write permissions.  Using sudo, you can change the read and write permissions of the partition to everyone.

---

### Post by coffeecat on 2013-05-29
> **BigZ1981 said:**
> Now I'm being told I have no write access on this new partition.  What am I missing?  Mind you, although I'm a techie, I'm still new to linux.  =)

Change the ownership of the ext4 filesystem with the chown command. You do this by mounting it, and:

```
sudo chown yourusername: /path/to/mountpoint
```

Change "yourusername" to your account name, and don't forget the trailing colon (that ensures your default group is applied too), and change /path/to/mountpoint to whatever it is. If you need help with that, post back.

That command will allow you to write to the partition from your account, but not from another account with a different UID. If you have multiple accounts, you could also adjust the permissions of the filesystem with:

```
sudo chmod 777 /path/to/mountpoint
```

But that would allow anyone to read-write to the partition, and is less secure.

---

### Post by BigZ1981 on 2013-05-29
I thought it might be something like that, but I couldn't find anything in the interface.  It figures I'd have to do this in command line.  Thank God I've had to learn basic chmod when I learned how to build & code websites.  Otherwise I would have been clueless as to this whole process.  chown worked.  Thanks!

---

