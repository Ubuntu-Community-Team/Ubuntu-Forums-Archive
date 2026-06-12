---
title: "Installing Ubuntu over another distribution, do I lose my files?"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Batzilla7 on 2014-04-18
I've been having a lot of trouble with the Linux distribution I've been using, so I'm seriously considering going to Ubuntu over my existing Linux distribution.  The problem is, I have files on the old distribution that I don't want to lose and I haven't backed them up properly.  If I install Ubuntu over the old system, are my files going to be lost?  If I have backed them up properly, will Ubuntu recognize them when I've installed it?

---

### Post by clementchiew on 2014-04-18
depends where you store the files. if it is together with the system files (same partition), you might want to move them over to an empty partition because you will be wiping your current partition with the system files. yeah. I think it works like that.

---

### Post by carl4926 on 2014-04-18
> **Batzilla7 said:**
> I've been having a lot of trouble with the Linux distribution I've been using, so I'm seriously considering going to Ubuntu over my existing Linux distribution.  The problem is, I have files on the old distribution that I don't want to lose and I haven't backed them up properly.  If I install Ubuntu over the old system, are my files going to be lost?  If I have backed them up properly, will Ubuntu recognize them when I've installed it?
Unless your /home is a separate partition, then yes, you will loose your files.

---

### Post by 3rdalbum on 2014-04-19
If your old distribution was based on Ubuntu (i.e. Linux Mint, ElementaryOS, etc) then you can use the "Something Else" function of the installer. Set the mountpoint of your old partition to / and DON'T click the "format" checkbox. Ubuntu will install, but preserve the contents of /home so you won't lose any data in your home directory. I've done this several times before when /home is on the same partition as /, it's been a feature of the Ubuntu installer since 2009.

This might also work if you are starting from a non-Ubuntu distribution, and in fact I see no reason why the Ubuntu installer would treat any other distro differently in this regard. But I'm not 100% sure of it. Make a backup of your files.

EDIT: If you installed your old distro with a seperate partition for /home, then use "Something Else" and set the mountpoint of your /home partition to /home, and once again DON'T click the "format" checkbox. Then set your / partition to the mountpoint / and you can format that one if you wish. Your files in /home will be preserved.

---

### Post by buzzingrobot on 2014-04-19
*Strongly* suggest backing up those files elsewhere no matter what approach you take, and especially if you have lilttle or no experience with partitioning. Partitioning takes a split second and formatting begins immediately after you commit to proceeding with the install.  There is no time to recover if you click the button and then realize you made a mistake.

The "Something Else" section of the installer is the manual partitioning approach.  You can reuse existing partitions or create new partitions. If you reuse an existing partition, you have the choice of formatting it or not. If you create new partitions, they wlll automatically be formatted. (New partitions are created if you choose one of the other options.)

If your existing /home folder is on separate partition, then you can avoid selecting the formatting option and that partition will be added to the filesystem as is.  The existing home folder will be the new /home folder after the install completes. The files will be there. (You can't do this if /home is not on a separate partition.)

Note that applications install their configuration files in your /home folder.  Those may vary between distributions, or even different releases of the same distribution or application.  Some manual reconfiguration will likely be needed after the install.

---

