---
title: "Multiple Hard Drive Question"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by kermtfrg on 2013-03-02
I have 6 physical volumes totaling around 9TB.  The logical volume, "homeserver", shows 8.99TB in Webmin.  If I run df -kh it shows the size as 4.4T.  Where is the rest of the storage?  
```

  --- Logical volume ---
  LV Name                /dev/mediaserver/homeserver
  VG Name                mediaserver
  LV UUID                ax3phG-oLdJ-Dzz6-97Ql-fNX4-5ztk-CKf9Fs
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                8.99 TiB
  Current LE             2356143
  Segments               6
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/mediaserver-root         86G  4.1G   78G   5% /
udev                                2.9G  4.0K  2.9G   1% /dev
tmpfs                               1.2G  960K  1.2G   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                2.9G  4.0K  2.9G   1% /run/shm
/dev/sda1                           228M   51M  166M  24% /boot
/dev/mapper/mediaserver-homeserver  4.4T  2.8T  1.5T  65% /media
```

---

### Post by tgalati4 on 2013-03-02
From the man page for df:

DESCRIPTION
       This  manual  page  documents  the GNU version of df.  df displays the amount of disk space available on the file system containing each file name
       argument.  If no file name is given, the space available on all currently mounted file systems is shown.  Disk space is  shown  in  1K  blocks  by
       default, unless the environment variable POSIXLY_CORRECT is set, in which case 512-byte blocks are used.

Perhaps use the -B switch and set a block size that matches what you know to be true.  The df utility is pretty simple and makes assumptions about disk devices.  If those assumptions are wrong then it will output incorrect file system sizes.  The -k switch locks in 1K block size.  What does this show?

```
df -h
```

---

### Post by kermtfrg on 2013-03-02
I'm sorry but how does running df with any other options going to help me?  I can see that half of my storage is not available to me. I am not very good in reading the info from the terminal so I've been using Webmin quite a bit to get my info. The volume group size is 9.10 TB, the logical volume size is 8.99TB yet if I look at the logical volume in a file manager it shows the total size as 4.10 TB.  I'm not sure what I did to lose the other 5 TB.

One thing I tried was to setup mirroring but it gave me error about not enough extents or something so I assumed it didn't work.  Am I wrong?  Is it working?  How can I turn it off if it is working?

---

### Post by tgalati4 on 2013-03-02
If you do have mirroring turned on, then you would indeed lose 1/2 of your disk space.

---

### Post by kermtfrg on 2013-03-02
How do I find out if it is turned on or not?

---

