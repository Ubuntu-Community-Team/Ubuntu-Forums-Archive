---
title: "Only boot and lost+found left on filesystem"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by arikshtiv on 2012-06-09
So after my ubuntu crashed a few times(probably because of bad blocks) it completely stoped working and it showed me the grub rescue.

So I connected my hard drive to my other computer and ran fsck and grub-install, but dammit one I mounted it I found only two folders: boot and lost+found.

This is what I get at the end of fsck.ext4:
/dev/sdb6: 334630/6012928 files (0.3% non-contiguous), 3421080/24020224 blocks

Where are all of those 300 thousand files?

PS: I've tried restoring the superblock from almost all backups, using [this tutorial]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/").

I am running Ubuntu 12.04 if that's of any help.

Thanks for any help.

---

### Post by critin on 2012-06-09
I've been able to restore deleted partitions with this free tool.  I needed it portable so I used flash, but it works on cd's also.

[http://www.partitionwizard.com/bootable-flash-drive.html](http://www.partitionwizard.com/bootable-flash-drive.html)

---

### Post by arikshtiv on 2012-06-09
Well I've recovered the partition but the problem is that the filesystem is almost empty.

Can it fix the filesystem?

---

### Post by philinux on 2012-06-09
> **arikshtiv said:**
> Well I've recovered the partition but the problem is that the filesystem is almost empty.

Can it fix the filesystem?

Photorec from the testdisk suite might do it. 

Use testdisk which is in ubuntu's repo. This can be installed in a live cd or usb session. Part of testdisk is photorec which can recover all sorts of files.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Read up before you use it. You need a target partition to recover the files to. This must not be the same partition that contains the deleted files.

---

### Post by arikshtiv on 2012-06-09
> **philinux said:**
> Photorec from the testdisk suite might do it. 

Use testdisk which is in ubuntu's repo. This can be installed in a live cd or usb session. Part of testdisk is photorec which can recover all sorts of files.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Read up before you use it. You need a target partition to recover the files to. This must not be the same partition that contains the deleted files.

From my experience with photorec it is made for recovering files, so it just creates a bunch of folders with files, and it doesn't keeps the directory tree.

---

### Post by philinux on 2012-06-09
> **arikshtiv said:**
> From my experience with photorec it is made for recovering files, so it just creates a bunch of folders with files, and it doesn't keeps the directory tree.

If you have your data backed up I would reinstall. If not then photorec can at least try to recover some of your data.

Badblocks maybe sounds like a bad disk too.

---

### Post by arikshtiv on 2012-06-09
Yeah the disk is very fauly but I can't replace it yet
I found now like 700 bad blocks, and it fixed the filesystem but all of the files are somehow in lost+found after running:
```
fsck.ext4 -c /dev/sdb6
```

So I'm not sure as to what to do, I don't have a backup, so I am thinking either trying to restore the folder structure or reinstalling.

---

### Post by philinux on 2012-06-09
> **arikshtiv said:**
> Yeah the disk is very fauly but I can't replace it yet
I found now like 700 bad blocks, and it fixed the filesystem but all of the files are somehow in lost+found after running:
```
fsck.ext4 -c /dev/sdb6
```

So I'm not sure as to what to do, I don't have a backup, so I am thinking either trying to restore the folder structure or reinstalling.

Quick google,  two top links and others look interesting, good luck. [http://www.google.com/search?hl=en&safe=off&client=ubuntu&hs=zNQ&channel=fs&gl=uk&q=ubuntu+all+files+in+lost+and+found&oq=ubuntu+all+files+in+lost+and+found&aq=f&aqi=&aql=&gs_l=serp.12...0.0.0.88482.0.0.0.0.0.0.0.0..0.0...0.0.GT6UCMarU0E](http://www.google.com/search?hl=en&safe=off&client=ubuntu&hs=zNQ&channel=fs&gl=uk&q=ubuntu+all+files+in+lost+and+found&oq=ubuntu+all+files+in+lost+and+found&aq=f&aqi=&aql=&gs_l=serp.12...0.0.0.88482.0.0.0.0.0.0.0.0..0.0...0.0.GT6UCMarU0E)

---

