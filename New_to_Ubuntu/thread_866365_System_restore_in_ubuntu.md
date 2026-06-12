---
title: "System restore in ubuntu"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by koba101 on 2008-07-21
Hi,

This question must have been asked to death, but I can't find anything on search (or it's not working)

what's the equivalent of system restore in ubuntu?  I know there's no registry...what could i do to preserve the system settings and installations?

---

### Post by cprofitt on 2008-07-21
This link is a link to a wiki article on backup and restore.

This is but one of the numerous ways to backup and restore your system.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by Xerp on 2008-07-21
I use partimage and mkCDrec. Clonezilla is another option.

---

### Post by ibuclaw on 2008-07-21
Have you heard of Apple Mac's TimeMachine?

Well, there seems to be some development in creating a similar OpenSource app called TimeVault.

[https://launchpad.net/timevault](https://launchpad.net/timevault)

It may get imported into the Ubuntu Repositories in due time...
But for now, the deb files are freely availiable to download/install.

Regards
Iain

---

### Post by stoneybroke on 2008-07-21
From synaptic try downloading sbackup v0.10.4 this will automatically backup your system daily at a preset time fully configurable it will save a full backup then only partial ones after that its very good you will find it under System Administration after its installed

Hope that helps.

---

### Post by stmiller on 2008-07-22
> **koba101 said:**
> Hi,

This question must have been asked to death, but I can't find anything on search (or it's not working)



[http://ubuntuforums.org/showthread.php?t=866481](http://ubuntuforums.org/showthread.php?t=866481)

[http://ubuntuforums.org/showthread.php?t=423639](http://ubuntuforums.org/showthread.php?t=423639)

[http://ubuntuforums.org/showthread.php?t=232147](http://ubuntuforums.org/showthread.php?t=232147)

[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+system+restore](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+system+restore)

:popcorn:

---

### Post by ardchoille42 on 2008-07-22
There is a very nice LiveCD called [SystemRescueCd]("http://www.sysresccd.org/Main_Page") that has PartImage on it. The reason I use this LiveCD is because PartImage requires that the drive you're copying be unmounted. I use that on a weekly basis to backup my entire drive to a tarball, takes about 10 minutes. I once had to restore my main drive and that took about 10 minutes.

Besides PartImage, this LiveCD has tons of admin tools, I highly recommend this LiveCD to anyone.

---

### Post by koba101 on 2008-07-22
ok,

I'm gonna need to study in depth all these resources.

Before the forum upgrade I used to type the thread's topic and the search results appear, now that doesn't happen and the search always returns no results (pity)

---

### Post by hyper_ch on 2008-07-22
> **koba101 said:**
> what's the equivalent of system restore in ubuntu?  I know there's no registry...what could i do to preserve the system settings and installations?

backups, backups, backups... do them regurarly.

---

### Post by billgoldberg on 2008-07-22
> **koba101 said:**
> Hi,

This question must have been asked to death, but I can't find anything on search (or it's not working)

what's the equivalent of system restore in ubuntu?  I know there's no registry...what could i do to preserve the system settings and installations?

There is no such a thing in Ubuntu.

--

Second question: Use a separate /home .

---

### Post by Melindrea on 2008-07-22
I think my question fits into this topic (which is the reason I'm asking it here rather than making a new topic):

If I want to, for various reasons, reinstall Ubuntu on my computer, but don't like the idea of spending the next day and a half getting my settings correct, and all the programs, etc... What do I need to backup? Or is it spread over so many places that it can't be done?

Thank you,
Melindrea

---

### Post by hyper_ch on 2008-07-22
(1) you probably should save /home
(2) you probably should save /etc
(3) you probably might wnat to save more stuff
(4) you probably should make a list of installed applications so that you can re-add them through a simple script.

---

### Post by Melindrea on 2008-07-22
Any suggestion on what other stuff I might want to save?

And wee! Finally a goal for my first non-schoolwork BASH-script. =)

---

### Post by Jordanwb on 2008-07-22
I use an Acronic boot CD, and try not to brick the OS.

---

### Post by mvavrik on 2008-07-22
This is by far the easiest way to completely backup and restore your Ubuntu system, and it saves all your Compiz settings, which can be a nightmare to set up again.

I had to do this after a nasty update, two days ago.

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by timzak on 2008-07-22
I use Clonezilla, which basically is Partimage with a more intuitive front-end and built-in support for NTFS and support for multiple PC restores.  It functions very similarly to Ghost or Drive Image (commercial equivalents).  You can image an entire disk, or certain partitions.  It asks you for the source, destination, you pick the compression level, and it does its thing.  If you're looking to back up files or folders, this isn't for you.  This does the whole drive/partition.

---

### Post by slimx3m on 2008-07-22
i would also recommend you clonezilla. i used it once and it worked perfectly.  i clone a whole hd (small) to a hd (big) and the only extra thing that i had to do was resize unallocated partition and that was it.

---

### Post by audwan on 2008-07-22
> **Melindrea said:**
> (...)
If I want to, for various reasons, reinstall Ubuntu on my computer, but don't like the idea of spending the next day and a half getting my settings correct, and all the programs, etc... What do I need to backup? Or is it spread over so many places that it can't be done?
(...)

All your files, and most of your settings, are in /home, so your definitely want to back that up. I set up /home on a separate partition. If you do this you don't even need a backup, **although I strongly recommend it**. You just reinstall and choose *not* to format /home.

As for programs, I usually install these again after a reinstall. You can check the log or even generate an install script in Synaptic, so you can install the same packages again.

---

### Post by Melindrea on 2008-07-22
@audwan: That's a big part of the problem. When I set up Ubuntu I had no clue that I would want to put /home in a separate partition. =) So, I'm going redo and do right. =)

I'll check the synaptic to see if I can find how to generate the script, sounds a good idea (if not as fun as scripting it myself >.>). Thank you. =)

</threadnapping>

---

