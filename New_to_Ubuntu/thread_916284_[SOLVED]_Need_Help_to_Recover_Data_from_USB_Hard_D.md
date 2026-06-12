---
title: "[SOLVED] Need Help to Recover Data from USB Hard Drive"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by beagle1 on 2008-09-10
I have a 250Gb external USB hard drive, in ext3 format with about 80gb data.
The drive was reading little slow. Therefore tried to copy its contents back to internal drive. There were a few unrecoverable files (mp3) that I tried to delete.  Now the external drive no longer mounts.  I get the following error:

Cannot mount Volume.
Mount: wrong fs type, bad option, bad superblock on dev/sdb1. missing codepage or helper program or other error.

dmesg | tail  had the following line:

VFS: can't find ext3 file system on dev sdb1

I did some searching in the forum for my problem; could find an answer.

Is there any way to recover data from this external drive?

Thanks in advance,

Beagle

---

### Post by pytheas22 on 2008-09-10
You can try using the -f argument of 'mount' to force-mount the drive; sometimes this works (there are risks, though).  You can also use fsck to try to repair the errors on the disk--on ext3 there's a good chance that it will be able to fix everything with minimal data loss.

You can also install photorec, a disaster-recovery program, to recover some of your files:
```

sudo apt-get install testdisk
```

(photorec is part of the testdisk package.)

Then run it with:
```

sudo photorec
```

It will search the drive sector-by-sector looking for recoverable files and copy them into folders in the directory that you're cd'd into when you launch photorec (by default, your /home folder).

If I were you, I'd use photorec to recover whatever you can, then try to use fsck to fix the file system errors.  If even that fails, try to force-mount the partition, since at that point you have nothing to lose (and most of your data will already have been saved by photorec).

---

### Post by beagle1 on 2008-09-10
Thank you very much for the solution.
Photorec did the job very well.  The instructions are also clearly written.

Beagle1

---

