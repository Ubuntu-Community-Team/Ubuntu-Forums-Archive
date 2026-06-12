---
title: "Re-named &amp; Access New HD"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Pepperoni on 2008-06-04
I have a couple of issues.  I have 3 hard drives in my system.  The first hard drive has Ubuntu.  The other two were unformatted.  I plan on using them to hold video files and as backup storage.  I used gparted to set them up as ext3, but I can't write to them.  I thought the gparted would take care of permissions as well.  Would someone point me in the right direction to get these two drives write-acessable?  Thanks.  I'd also like to change the name of the drive to something a little more specific, so is that easily fixed too?  Thanks for your help.

---

### Post by wolfen69 on 2008-06-04
this won't directly help your problem, but i always make storage partitions FAT32 or NTFS, just so i wont have any problems with permissions.

---

### Post by onero on 2008-06-04
> **Pepperoni said:**
> I have a couple of issues.  I have 3 hard drives in my system.  The first hard drive has Ubuntu.  The other two were unformatted.  I plan on using them to hold video files and as backup storage.  I used gparted to set them up as ext3, but I can't write to them.  I thought the gparted would take care of permissions as well.  Would someone point me in the right direction to get these two drives write-acessable?  Thanks.  I'd also like to change the name of the drive to something a little more specific, so is that easily fixed too?  Thanks for your help.

So they're mounted but owned by root, is that correct? You can just change the owner of the drive. Assuming you have your drive mounted in a folder in /media:

```
sudo chown -R [user]:[user] /media/[your drive]
```

Be sure to replace [user] and [drive] with your username and the folder where your drive is mounted, respectively.  The -R flag means recursive, which means it will change the owner for all the files and folders in that drive.

---

