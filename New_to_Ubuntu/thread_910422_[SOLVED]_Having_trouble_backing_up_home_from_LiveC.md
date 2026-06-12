---
title: "[SOLVED] Having trouble backing up /home/ from LiveCD"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by gldearman on 2008-09-04
Hi.

I currently have Dapper installed on my PC, and I was planning on doing a clean install of Hardy, rather than going through the updates.

I cannot presently boot Dapper, since I installed a new video card without properly configuring it (figuring that I was about to overwrite Dapper anyway).  As a result, GDM cannot be started.  So, I am trying to work from the Ubuntu 8.04 Live CD.

Before overwriting Dapper, I would like to back up all the documents, etc. that are in my /home directory.  I have a second hard drive with plenty of space for this.  It is installed as the slave on IDE2, and I would like to back up to partition #3 -- I think that should be hdd3, right?  The Live CD, however, seems to be calling it sdb3.

So, first I mount the partition I would like to back up to:
```

sudo mount -t ext3 /dev/sdb3 /mnt
```

That seems to work OK.

Then, I go to the /home directory in my Dapper partition:

```
cd /media/disk/home/
```

And that gets me to the proper directory, since that is where the Live CD appears to be mounting my Dapper partition.

Then, we get to the problem.  I try to back up with:

```
sudo find . -depth -print0 | cpio --null --sparse -pvd /mnt/
```

And that operation fails.  The find command appears to be working fine, but the cpio command returns an error for every file passed to it:

```
{filename} cannot stat:permission denied
```

Can anyone tell me why I am getting this error and how to fix it?

Or, alternatively, how to boot my Dapper installation directly to a command line, so that I don't have to launch GDM and can run the backup from Dapper instead of the Live CD?

Thanks in advance,

gldearman

---

### Post by philinux on 2008-09-04
Why not just use the cp command.

Also you should consider moving home to it's own partition. Much easier install then.

[Psychocats]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Titan8990 on 2008-09-04
> Or, alternatively, how to boot my Dapper installation directly to a command line, so that I don't have to launch GDM and can run the backup from Dapper instead of the Live CD?

From the GRUB menu select "recovery mode". If grub does not present you with a menu by default then you will have to hit tab to bring up the menu.


Personally, I would use rsync for this or you could clone the whole partition using clonezilla.

---

### Post by gldearman on 2008-09-05
> **philinux said:**
> Why not just use the cp command.

Because I can't read very well, apparently.  I was reading [ _the archiving section at Debian reference._]("http://www.us.debian.org/doc/manuals/reference/ch-tips.en.html#s-archiving")  I got as far as why cp was (previously) not used for this sort of thing.  Then, I stopped reading, missing the part about how GNU cp "no longer has these limitations."  So, yeah, cp would have worked.

> **philinux said:**
> Also you should consider moving home to it's own partition. Much easier install then.

Yes, I definitely will have a separate home partition on this new install.  Thanks.

> **Titan8990 said:**
> From the GRUB menu select "recovery mode". If grub does not present you with a menu by default then you will have to hit tab to bring up the menu.

D'oh!  Every time I log in, I see the "recovery mode" option in the GRUB menu.  I know that it is there in case I bollix my system and can't log in.  Yet, when I actually *do* that, I don't even *think* about trying it.

Thanks.  Recovery mode gave me a root prompt, and I was able to run the backup from that.

Thanks again to both of you.

---

### Post by Titan8990 on 2008-09-08
I'm a bit late but good to hear you got everything working properly.

---

