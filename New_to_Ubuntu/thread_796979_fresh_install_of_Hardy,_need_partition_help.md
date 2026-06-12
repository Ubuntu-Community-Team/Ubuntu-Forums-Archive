---
title: "fresh install of Hardy, need partition help"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by JacobRogers on 2008-05-16
What partitions do I need?  I think I need a Primary ext2 journaling file system mounted at "/", but I keep getting this error, "The ext3 file system creation in partition #3 of SCSI1 (0,0,0) (sda) failed."

Any help?

---

### Post by Joeb454 on 2008-05-16
If you are not sure of the partitioning, just do a guided install.

If you want to run a dual boot with Windows, make sure you have free space first, and choose "guided: use largest continuous free space"

If not, just choose guided partitioning and let it use the entire drive :)

---

### Post by rlcomstock3 on 2008-05-16
You really only need two partitions to get started...

/  -- make it ext3 or reiserfs
swap -- make it double your ram

Recomendation....

/boot  --  50MB  ext2
swap   --  double ram
/      --  rest of your harddrive  ext3 or reiserfs

---

### Post by JacobRogers on 2008-05-16
Ok so I used gparted and deleted my previous ubuntu partitions and applied it, then I just restarted the wizard and told it to use the largest continuous blank space.  worked.

---

### Post by Jovec on 2008-05-16
> **JacobRogers said:**
> What partitions do I need?  I think I need a Primary ext2 journaling file system mounted at "/", but I keep getting this error, "The ext3 file system creation in partition #3 of SCSI1 (0,0,0) (sda) failed."

Any help?

First tell us more about your setup, particularly if you are going to install Ubuntu as your only OS or if it needs to share space with Windows.

I'd strongly suggest using guided partitioning unless you have a good understanding of your space needs. 

You technically need only a root partition "/", but a more common layout might be:

64-128 MB mounted as /boot
1-2 GB mounted as swap
4-8 GB mounted as /
All extra spaced devoted to /home

Ext3 is journaling, Ext 2 is not.

---

### Post by Raccoon1400 on 2008-05-16
boot from live cd, post output of fdisk -l(as root)

---

### Post by JacobRogers on 2008-05-16
everythings fine now, thanks for all your help.  I'm in my fresh install now

---

### Post by Joeb454 on 2008-05-16
Glad to hear it worked (and that was quick!)

---

### Post by Juggalowang on 2008-06-28
....

---

