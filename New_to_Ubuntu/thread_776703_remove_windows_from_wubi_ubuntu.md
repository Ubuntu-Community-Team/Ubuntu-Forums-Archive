---
title: "remove windows from wubi ubuntu"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by stepan2 on 2008-04-30
Hi guys. I gave hardy heron a try using wubi , and am loving it so far. I moved some files form my windows directory into hardy and now have decidced that i dont have a need for windows anymore. i was wondering if there was a way i can remove windows , and keep wubi ubuntu , increasing the space to my entire hard-drive of course. I am hoping to do this within ubuntu. would i remove the host folder?

---

### Post by halitech on 2008-04-30
I don't believe this will work as Ubuntu is installed on a FAT(32) partition using wubi and requires windows to stay put. I would recommend backing up whatever you want to save (cd, dvd, network removable drive) and then install fresh if you want to wipe windows completely. I would recommend also keeping a copy of windows install for when you need help and are having trouble with Ubuntu, just in case unless you are a complete idiot like myself and go full bore and take a sink or swim attitude.

---

### Post by Dylnuge on 2008-04-30
I don't know a ton about Wubi, but from what I do know, it operates using files in the Windows partition somehow.

If that is true, then unfortunatly there isn't a way to completly remove Windows.

However, you can do the following:

1. Delete all unneeded files from your Windows partition. This means cleaning everything, uninstalling unneeded programs, deleteing My Documents (or at least everything inside it), etc.

2. Defragment your drive so that pretty much everything lies at the front sector. Alternativly, you can purchase a software like PartitionMagic, which will do this when you resize the Windows partition.

3. Using GParted, resize the Windows partition so that all of the unused space is removed.

4. Add a partition in the unused space for Linux.

That will give you some extra space.

The other option is to back up your data, wipe your HDD, and then install Ubuntu over it.

---

