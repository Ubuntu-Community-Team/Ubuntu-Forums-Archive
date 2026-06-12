---
title: "cryptswap1 is not ready"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by chron3 on 2013-02-05
When I boot my system, I always see "dev/mapper/cryptswap1" is not ready. So I checked out fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=ef804506-aec3-4438-bdeb-3f966fca9d88 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=bcdef8cd-8a24-48c5-869d-1f6a12d158e6 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

Then I checked out blkid:

```
/dev/sda1: LABEL="System-reserviert" UUID="8606DDFE06DDEF65" TYPE="ntfs" 
/dev/sda2: UUID="A24EE2594EE225AF" TYPE="ntfs" 
/dev/sda6: UUID="ef804506-aec3-4438-bdeb-3f966fca9d88" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="6800eca7-179a-4b6a-a515-784428af91b2" TYPE="swap"
```

Now I'm not quite sure how to edit fstab correctly. What should I do to make the error massage go away?

---

### Post by furything on 2013-02-05
Are you using a laptop or a desktop PC?

Do you need to encrypt swap or can it just be a plain partition?

You can disable by following [http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)
Your exiting fstab shows the original swap and the encrypted '/dev/mapper/cryptswap1'

Makes me wonder if the encryption service is not running up quick enough prior to it trying to mount the encrypted folder.

---

### Post by chron3 on 2013-02-05
I'm using a notebook (Lenovo ThinkPad) and I don't need to encrypt the swap partition.

> **furything said:**
> You can disable by following [http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

This worked perfectly, thank you very much! Just had to change "vim" to "gedit".

---

### Post by furything on 2013-02-05
Glad it worked
You can install vim if you want but another standard editor is 'vi' some people use nano, kate gedit but yes in any future instruction supplement the editor with the one of your choice.

Don't forget to mark the thread as solved!!

---

