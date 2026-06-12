---
title: "Big uh-oh moment with dueling hard drives"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by mccuisinart on 2011-09-17
**Relevant Components:**

Crucial CT064M4SSD2 m4 2.5" Solid State Drive - 64GB, SATA 6Gb/s

Western Digital Caviar Black WD5002AALX 500GB 7200 RPM 32MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive

**Situation:**

I set up a rig a while ago and didn't buy windows right away. I installed ubuntu initially. I loaded ubuntu onto the SSD and put all of my photos, music, etc, about 100 gigs worth on the Western Digital HDDrive in the meantime. I just got windows 7 and did a clean install with the intention to install ubuntu again for a duel boot system. After formatting the SSD and installing windows 7, I saw that I couldn't view my HDD under the computer folder, which was a bummer, so I figured I'd just boot ubuntu from my USB stick, and extract all of the data from it onto an external drive, format and re-partition it, and load it all back on. But now, when trying to mount and view HDD in ubuntu it says I don't have permission to view its contents.

I want to be able to extract all the data that I loaded onto the HDD, but I don't know how to get permissions to do it. Who can help me out?

**Other information:**

The HDD is still detected in both ubuntu and windows, but windows is telling me all of the capacity is free, and ubuntu can only tell me under volumes that the type of HDD is ext3 and the partition on it is Linux (0x83)

EDIT- viewing media/(hddrive), it's telling me that it has ~350 gigs of free space available, which is good, cause that means my data is still there! I just need to know how to get to it. In either system would be nice.

Thanks in advance. I love ubuntu and I want it running on my computer again, but I really want to get this HDD issue solved first, if possible.

---

### Post by nll on 2011-09-17
Have you tried running nautilus with root? Type *sudo nautilus* in the terminal and you should have permission to do anything.

---

### Post by mccuisinart on 2011-09-17
> **Danillo_Alvarenga said:**
> Have you tried running nautilus with root? Type *sudo nautilus* in the terminal and you should have permission to do anything.
Awesome. I'm glad it was this simple. Thanks very much!

---

### Post by bapoumba on 2011-09-17
Just to add gksudo should be used for graphical applications.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nll on 2011-09-17
You're welcome, fella! Cheers!

And I didn't know that, bapoumba, thank you!

---

### Post by bapoumba on 2011-09-17
> **Danillo_Alvarenga said:**
> 
And I didn't know that, bapoumba, thank you!

Welcome :)

Most of the time sudo will work. It is a good procedure however to use gksudo with graphical apps. Fixing is not very complicated but can be disturbing to some users.

---

### Post by srs5694 on 2011-09-17
Running as root to get around this type of permissions issue is sometimes useful but it can have long-term negative consequences, at least when copying the files to a Linux filesystem (ext3fs, ext4fs, etc.). Specifically, files you copy in this way may then be owned by root, which could set up a need to use root more in order to edit the files, add or delete files from subdirectories, and so on. Overuse of root in this way can be dangerous, since using root power eliminates many of the protections Linux uses to keep you from making mistakes like accidentally deleting all your program files. (If you copied the files to a FAT or NTFS volume, the permissions rules are different, so this concern doesn't really apply -- at least, not in quite the same way.)

In the long run, when you encounter this type of problem and want to copy files from one Linux filesystem to another, or between locations on one Linux filesystem, it's generally better to use root privileges to change the ownership or permissions on the files and directories that are causing problems. At the command line, you can do this with chown (to change ownership). You'd use the -R option to recursively change ownership or permissions if you've got a whole directory tree that's affected. The commands might look like this:

```

sudo chown -R fred: /path/to/directory

```

This changes ownership of /path/to/directory and all its files to fred (the colon signifies to change the group to fred's default group).

Alternatively, if the original files' ownership shouldn't be changed, you could copy the files as root and then change the ownership on the copies.

---

### Post by nll on 2012-05-20
By the way, those who don't like to use the terminal can change permissions in Nautilus itself running as root by right-click the file, selecting Properties and going to the Permissions tab.

---

