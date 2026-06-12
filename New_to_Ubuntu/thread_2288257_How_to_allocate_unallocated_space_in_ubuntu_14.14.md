---
title: "How to allocate unallocated space in ubuntu 14.14"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-25
/dev/sda1     fat32                   /boot/efi                512MiB
/dev/sda2     ext2                    /boot                     244MiB
/dev/sda3     lvm pv                 ubuntu-kylin-vg      465GB
unallocated   unallocated                                        1.02MiB

/dev/sdb1      fat32                                               512MiB
/dev/sdb2      ext2                    /media/ubuntu       244MiB
unallocated    unallocated                                       21.3GiB

How to do with my laptop unallocated space(21.3GiB)?
Can i used it constructively?

---

### Post by yancek on 2015-07-25
If you still have the Ubuntu install medium, boot it as it has the GParted disk partitioning software.  Just highlight the unallocated space in the GParted window and create a partition and select a filesystem for it.

---

### Post by oldfred on 2015-07-25
Is sdb actually an SSD in an Ultrabook?
Post this:
 sudo lshw -C Disk -short

---

