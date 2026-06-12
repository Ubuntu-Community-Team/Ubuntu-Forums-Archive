---
title: "I can't use my /home drive!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Duranix on 2008-05-18
Hi everyone,

I formatted my harddrive last night and just made one huge, single partition. I then went and put ubuntu on it, and realised what I did later, so I booted up my live CD and resized the original partition, and then made another partition which I intended to put stuff on. Gparted wouldn't let me make a logical drive so I just left it as ext3 Primary and made it.

Now when I boot into ubuntu, I can't put stuff on that partition, regardless of the fact that it has 270something gig free >.>

I can gksudo and put stuff on it, but thats kind of going around the problem and other people have to use my computer too.

---

### Post by Xiong Chiamiov on 2008-05-18
Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=4984670&postcount=17"), and [this one]("http://ubuntuforums.org/showpost.php?p=4984648&postcount=14") too.  The specifics will be a little bit different, but essentially it should be the same.

---

### Post by hyper_ch on 2008-05-18
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Duranix on 2008-05-18
> Take a look at this post, and this one too. The specifics will be a little bit different, but essentially it should be the same. 

I tried following that first link, but when I go into manage groups, everything is greyed out. I've tried changing permissions but it just says "Permissions unknown" and wont let me touch anything.

> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

My home partition is already seperate from my ubuntu partition.

---

### Post by Xiong Chiamiov on 2008-05-18
You'll have to tell the controls you want to make changes as root.  I'm not sure quite how it works in GNOME, but there should be a button somewhere to unlock it.

---

### Post by HotShotDJ on 2008-05-18
> **Duranix said:**
> My home partition is already seperate from my ubuntu partition.

Argh, I might just alt+f2 Gksudo.I have a suspicion of what is going on here... but I need you to post the contents of /etc/fstab for me to confirm that suspicion.

EDIT:  Don't mess with "Users and Groups" just yet.

EDIT #2:  I'll also need the output of "sudo fdisk -l" (run it in a terminal without the quotes.  That last letter is a lowercase L)

---

### Post by Duranix on 2008-05-18
Heres my Fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=fd233cc3-0224-47d9-85be-258b5d8ab8a2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=116d7161-9f7e-4027-a720-095f12678aa2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




and my Sudo fdisk -l



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x374f374e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16c216c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         747     6000246   83  Linux
/dev/sdb2           36107       36481     3012187+   5  Extended
/dev/sdb3             748       36106   284021167+  83  Linux
/dev/sdb5           36107       36481     3012156   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a3be45f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14594   117220792+   7  HPFS/NTFS



Thanks man :) The 80gb harddrive is just an old ntfs filestorage I use. Ubuntu and my home are on the 300gb one :P

---

### Post by HotShotDJ on 2008-05-18
> **Duranix said:**
> Thanks man :) The 80gb harddrive is just an old ntfs filestorage I use. Ubuntu and my home are on the 300gb one :PNo problem... suspicion confirmed. :)  Stand by while I fix your fstab.

---

### Post by HotShotDJ on 2008-05-18
Ok... edit as root (gksudo gedit /etc/fstab) your fstab and add the following line:
```
/dev/sdb3     /home     ext3     defaults     0 2
```
Now reboot.  Should be all fixed up.

---

### Post by Duranix on 2008-05-18
Thanks man! You rock :)

---

### Post by HotShotDJ on 2008-05-18
> **Duranix said:**
> Thanks man! You rock :)Lets not get too excited until you reboot and confirm that my fix actually works. :)

---

### Post by Duranix on 2008-05-18
heh, it works :)
Thanks ;)

---

### Post by HotShotDJ on 2008-05-18
> **Duranix said:**
> heh, it works :)
Thanks ;)
I'm pleased that I could help.  Be careful when re-sizing and re-formating partitions.  Sometimes, because of the way Ubuntu sets up the fstab (notice those long UUID strings?), you can render your system unbootable.  Its easy to fix, but it can drive you up a tree when it happens (person experience here. :) )  In many ways, the UUID method is FAR superior than the traditional way of writing fstab entries, but sometimes it can bite you in the rear-end.  Fortunately, you dodged that bullet this time.

---

