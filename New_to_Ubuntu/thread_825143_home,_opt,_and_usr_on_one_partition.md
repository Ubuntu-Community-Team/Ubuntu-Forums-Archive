---
title: "/home, /opt, and /usr on one partition"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Forgotten Path on 2008-06-10
I plan on re-setting up (is that a word?) my Ubuntu 8.04/Windows XP dual boot.  I would like to put /opt, /usr, and /home on one partition without having to use symlinks.  I have been searching multiple forums and have pretty much figured out its possible, but haven't been able to find any specific examples.  I have found a fstab that looks like

> /dev/hdaXX     /usr     ext3     defaults     0  1
/usr/local/home     /home     none     bind     0  0

How would I configure a fstab to use a partition with three folders (opt, usr, and home) for /opt, /usr, and /home?
Is it possible to use

> /dev/hda1     /     ext3     defaults     0  1
/dev/hda2/opt     /opt     ext3     defaults     0  0
/dev/hda2/usr     /usr     ext3     defaults     0  0
/dev/hda2/home     /home     ext3     defaults     0  2

or would I have to create some mount point, like

> /dev/hda1     /     ext3     defaults     0  1
/dev/hda2     /combo     ext3     defaults     0  0
/combo/opt     /opt     none     bind     0  0
/combo/usr     /usr     none     bind     0  0
/combo/home      /home     none     bind     0  2

or am I completely off the mark altogether?  I would appreciate any feedback.

---

### Post by bodhi.zazen on 2008-06-10
> **Forgotten Path said:**
> How would I configure a fstab to use a partition with three folders (opt, usr, and home) for /opt, /usr, and /home?

Use :

```
/dev/hda1 / ext3 defaults 0 1
/dev/hda2 /combo ext3 defaults 0 2
/combo/opt /opt none bind 0 0
/combo/usr /usr none bind 0 0
/combo/home /home none bind,nodev,nosuid 0 0
```

---

### Post by Forgotten Path on 2008-06-11
Hey, thanks bodhi.zazen.  Is there any way you could give me advice on how to copy the folders to their new partition?  I can't do it during installation because the partition will be NTFS.  I have used the instructions at [http://www.psychocats.net/ubuntu/seperatehome](http://www.psychocats.net/ubuntu/seperatehome) with success, although the folders permissions got all out of whack and had to be corrected (although that might have been NTFS's fault).  I also found [_this_]("http://www.go2linux.org/how-to-move-home-directory-to-another-partition") which seems a lot easier, but I'm afraid its to good to work well...

Thanks again, you've saved me alot of headache.  :)

---

### Post by bodhi.zazen on 2008-06-11
You can not use a NTFS partition for /home, /opt/ or /usr (NTFS does not support permissions). You will need to use a linux native partition (ext3).

---

### Post by Forgotten Path on 2008-06-11
I am currently using an NTFS partition as /home.  I used fstab to correct the permissions:

```
/dev/sda4 /home ntfs-3g uid=brent,gid=users,umask=133 0 2
```

And everything seems to be working fine...

Is it a super bad idea to use NTFS?  I have figured out how to use an ext3 partition as Documents and Settings in WinXP, but (of course) it is much more difficult to copy the folder and tell Windows where it moved to then it is on Ubuntu.  I would have to edit about a hundred thousand (it seems like) registry entries, and I am much more comfortable editing fstab then I am mucking about in Windows' registry.

---

### Post by maybeway36 on 2008-06-11
I suppose you could use NTFS as /home, but you will only ever be able to have one user on the system.

---

### Post by bodhi.zazen on 2008-06-11
You can "work around" the permissions issue for NTFS partitions, but you will likely run into problems eventually. What will you do when you want to make a script or set the permissions of a single file ?

IMO it is "OK" to use NTFS as a shared data partition, but you should convert to ext3 for /home /opt /usr.

Is there some reason you do not want to use ext3 ?

---

### Post by Forgotten Path on 2008-06-11
sda1 --> NTFS --> Windows XP OS
sda2 --> Ext3 -->Ubuntu 8.04 OS
sda3 --> NTFS or Ext3 -->Shared partition
sda4 --> extended
..sda5 --> FAT32 --> Windows XP Page File
..sda6 --> linux-swap --> Ubuntu Swap Partition

The shared partition, sda3, would have four folders:  home, opt, usr, (all for Ubuntu) and Program Files (for WinXP).  It could go either way, NTFS or Ext3, I was just trying to avoid the registry editing in WinXP.  

My problem is this:  Ubuntu's NTFS-3G drivers are there from install, but it won't allow me to mount NTFS folders as system folders (probably to prevent the permission issues).  The Ext2FS driver for Windows can't be slipstreamed into the installation files, so I can't use unattended install to use an Ext3 partition as my Program Files directory...  So I have two choices:  copy Ubuntu folders and edit fstab, or copy WinXP folders and edit the god-forsaken registry.  I was just trying to choose the easiest method.

Does Ext3 (or technically Ext2) support Windows' file permissions?  If it does, it may be worth the registry fight, even though I plan on only having one user (on both Ubuntu and WinXP).

What's the quickest, easiest, but still safe way to copy Ubuntu's /home, /opt, and /usr files over to an NTFS partition?  I may end up trying shared NTFS and shared Ext3 just to see how well each works...

Thanks again, guys!

---

### Post by Forgotten Path on 2008-06-11
Okay, I just found out from [www.fs-driver.org](www.fs-driver.org) that the Ext2 driver doesn't preserve Linux file permissions when you access Ext2/3 partitions from Windows.  However, it doesn't really say whether or not Windows' own file permissions would work correctly or not.

---

