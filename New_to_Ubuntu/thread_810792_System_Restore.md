---
title: "System Restore?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-28
I have read in many posts that after downloading System Updates something breaks. For example screen resolution issues, wifi access, sound etc. Indeed, I lost my sound following a very large update download. To fix the problem I had to reinstall from scratch. Since then I have been reluctant to download any updates that Update Manager prompts me about for fear of breaking something again.

My objective: To set up some kind of system backup routine where I can restore my system to a previous state should any future updates break my machine, without having to install from scratch.

I have read this post:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

which seems to achieve this objective but I don't know why the recommendation is to exclude some directories. Additionally, it appears this HOWTO was written for a previous Ubuntu version. I'm running Gutsy Gibbon. Do the same excluded directories apply for Gutsy and are there any more I need to add?

Likewise would this work if I upgraded to 8.04 and wanted to go back to 7.10?

Any and all advice would be greatly appreciated.

Thanks in advance.

Mark, in the UK.

---

### Post by logos34 on 2008-05-28
You want to use Partimage. (from a livecd because root cannot be mounted)

---

### Post by Oldsoldier2003 on 2008-05-28
> **mapes12 said:**
> I have read in many posts that after downloading System Updates something breaks. For example screen resolution issues, wifi access, sound etc. Indeed, I lost my sound following a very large update download. To fix the problem I had to reinstall from scratch. Since then I have been reluctant to download any updates that Update Manager prompts me about for fear of breaking something again.

My objective: To set up some kind of system backup routine where I can restore my system to a previous state should any future updates break my machine, without having to install from scratch.

I have read this post:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

which seems to achieve this objective but I don't know why the recommendation is to exclude some directories. Additionally, it appears this HOWTO was written for a previous Ubuntu version. I'm running Gutsy Gibbon. Do the same excluded directories apply for Gutsy and are there any more I need to add?

**Likewise would this work if I upgraded to 8.04 and wanted to go back to 7.10?**

Any and all advice would be greatly appreciated.

Thanks in advance.

Mark, in the UK.
reverting to a previous version of ubuntu is best done with a reinstall. there is no mechanism to rollback, and having mixed dependencies is bad news.

The best thing to do is set up your system the way you like it and then back it up completely or build a live cd/dvd before you upgrade, so that you can easily go back by a fast reinstall. 

Another method is to do a fresh install of the new version and then once you are happy just delete the old version and update grubs menu.lst. This method is good in that you don't touch your "old faithful" install in any way so there is no worry about reverting.

---

### Post by logos34 on 2008-05-28
> **Oldsoldier2003 said:**
> The best thing to do is set up your system the way you like it and then back it up completely or build a live cd/dvd before you upgrade, so that you can easily go back by a fast reinstall. 

Another method is to do a fresh install of the new version and then once you are happy just delete the old version and update grubs menu.lst.

I totally disagree.

Considering what you said:
> 
My objective: To set up some kind of system backup routine where I can restore my system to a previous state should any future updates break my machine, without having to install from scratch.


Partimage is a lot faster. I use it all the time for taking a system snapshot before major updates and upgrades. Windows sys restore uses the same basic approach using MS tools.

---

### Post by Oldsoldier2003 on 2008-05-28
> **logos34 said:**
> I totally disagree.

Considering what you said:



Partimage is a lot faster. I use it all the time for taking a system snapshot before major updates and upgrades. Windows sys restore uses the same basic approach using MS tools.

if you look at the post i highlighted his thoughts about doing a dist "downgrade'

---

### Post by mapes12 on 2008-05-28
> or build a live cd/dvd before you upgrade, so that you can easily go back by a fast reinstall.How do I make one of these please?


> Another method is to do a fresh install of the new version and then once you are happy just delete the old version and update grubs menu.lst. This method is good in that you don't touch your "old faithful" install in any way so there is no worry about reverting. I need to use alternate CD's mainly because my graphics do not support the res LiveCD's load into my system. Would an alternate CD install still give me the option of keeping my previous Ubuntu version. How do I edit the "grubs menu.lst" and where do I find it and what version do I find it, 7.10 or 8.04?

Many thanks.

---

### Post by Oldsoldier2003 on 2008-05-28
> **mapes12 said:**
> How do I make one of these please?


 I need to use alternate CD's mainly because my graphics do not support the res LiveCD's load into my system. Would an alternate CD install still give me the option of keeping my previous Ubuntu version. How do I edit the "grubs menu.lst" and where do I find it and what version do I find it, 7.10 or 8.04?

Many thanks.

[http://ubuntuforums.org/showpost.php?p=4277073](http://ubuntuforums.org/showpost.php?p=4277073) is a nice tutorial on making a live cd from an existing installation. 

The alternate installer gives you the option to install Ubuntu wherever you want. You could have it overwrite your current ubuntu, install it into a different partion etc...

Once you are reaady to nuke an old ubuntu install the easiest way is to boot into your "good ubuntu" install and run gparted. the old partition wont be mounted so you can easily delete/reformat it without needing to boot a live cd. Then you would just remove the references to the older install in the file  /boot/grub/menu.lst  you'll need to use sudo in order to save your changes. If you reach that stage and need help just post the file and someone here will be able to help you.

---

### Post by twright on 2008-05-28
if you use xfs its on the fly snapshots might be a solution

---

### Post by mapes12 on 2008-05-28
> [http://ubuntuforums.org/showpost.php?p=4277073](http://ubuntuforums.org/showpost.php?p=4277073) is a nice tutorial on making a live cd from an existing installation. 

I like the the idea of making a live cd of my current installation. I have read the thread. Unfortunately, the author makes too many assumptions about the readers understanding of code variables. For example

> 1. Set some variables

Code:

export WORK=~/work
export CD=~/cd
export FORMAT=squashfs
export FS_DIR=casper


The WORK Directory is where our temporary files and mount point will reside.
The CD is the location of the CD tree.
FORMAT is the filesystem type. We you are going to use a compressed squashfs
FS_DIR is the location of the actual filesystem image within the cd tree.

Replace only the values highlighted in Magenta. I haven't a clue what the author is asking me to do?

---

### Post by Oldsoldier2003 on 2008-05-28
> **mapes12 said:**
> I like the the idea of making a live cd of my current installation. I have read the thread. Unfortunately, the author makes too many assumptions about the readers understanding of code variables. For example

 I haven't a clue what the author is asking me to do?

Having gone through the process and tweaking it to suit my needs I can tell you that all you need to do is cut and paste the commands and it works :)

---

### Post by mapes12 on 2008-05-28
> if you use xfs its on the fly snapshots might be a solution

Forgive my ignorance but what is "xfs" and "on the fly snapshots" please?

---

### Post by Hozza on 2008-05-28
I would upgrade if I were you, that way some glitches that you have experienced may be fixed.

---

### Post by mapes12 on 2008-05-28
> I would upgrade if I were you, that way some glitches that you have experienced may be fixed.

The point of the thread is that upgrading either your current version or to a new version can break things. The posts on this forum are testiment to that fact. The objective is to develop a robust "rollback" policy in case things go wrong.

But thanks for your contribution....

---

### Post by louieb on 2008-05-28
> **logos34 said:**
> You want to use Partimage. (from a livecd because root cannot be mounted)
+1 Thats what I do.  I run it from the [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). 
Just tried the [Clonezilla]("http://www.clonezilla.org/") CD it has a verry simple to use front end to  **partimage.**

---

### Post by twright on 2008-05-28
xfs is a very fast filesystem, it allows you to quickly dump its contents creating a reliable backup

rsync would be a good option also for backups

---

### Post by logos34 on 2008-05-28
> **mapes12 said:**
> Forgive my ignorance but what is "xfs" and "on the fly snapshots" please?

I was wondering about that too.  I read this in the wiki:
> [Snapshots]("http://en.wikipedia.org/wiki/XFS#Snapshots")

XFS does not provide direct support for snapshots, as it expects the snapshot process to be implemented by the volume manager. Taking a snapshot of an XFS filesystem involves freezing I/O to the filesystem using the xfs_freeze utility, having the volume manager perform the actual snapshot, and then unfreezing I/O to resume normal operations. The snapshot can then be mounted read-only for backup purposes. XFS releases on IRIX incorporated an integrated volume manager called XLV. This volume manager has not been ported to Linux. In recent Linux kernels, the xfs_freeze functionality is implemented in the VFS layer, and happens automatically when the Volume Manager's snapshot functionality is invoked.

So that means Ubuntu handles it through the VFS layer?

This is a really nice feature, and XFS is fast from everything I've heard, but I'll probably never use it because, alas, you cannot shrink xfs partitions and Grub does not support it (need separate /boot).

---

### Post by twright on 2008-05-29
> **logos34 said:**
> I was wondering about that too.  I read this in the wiki:


So that means Ubuntu handles it through the VFS layer?

This is a really nice feature, and XFS is fast from everything I've heard, but I'll probably never use it because, alas, you cannot shrink xfs partitions and Grub does not support it (need separate /boot).
i thinks it works via lvm
 
jfs is almost identical to xfs but it can be shrunk (but in a weird way)

if zfs ever gets supported in the kernel that will probably be the best option

---

