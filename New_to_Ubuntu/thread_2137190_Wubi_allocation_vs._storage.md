---
title: "Wubi allocation vs. storage"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by ScooterBoogles on 2013-04-20
I installed Ubuntu via Wubi, and I selected 18 gigs for my installation size.

Does that mean I can only store 18 gigs of photos, music, videos, etc. within Ubuntu?

---

### Post by jimafternoon on 2013-04-20
Yes. But Wubi is not a full install, it's like Ubuntu with training wheels, something to test software on and/or try out Ubuntu for a while to see if you like it. 

If you end up liking it, you'll want to do a real install. JMO.

---

### Post by 3rdalbum on 2013-04-20
> **ScooterBoogles said:**
> I installed Ubuntu via Wubi, and I selected 18 gigs for my installation size.

Does that mean I can only store 18 gigs of photos, music, videos, etc. within Ubuntu?

Jimafternoon is right. But to clarify, as long as you have free space on your hard disk or a USB drive, you can use it for storage of ordinary files. However, your home folder + operating system + programs cannot go above 18 gigabytes.

---

### Post by bcbc on 2013-04-20
You can access/store files under /host (the host NTFS partition) - the benefit is that it's more reliable and also Windows can easily access them. For any data you store in /home, I recommend backing it up in case one of the training wheels falls off. This is especially true for photos, videos etc. personal data that take up a lot of space and are generally precious - you don't want that to be stored on the virtual disk Wubi uses.

---

### Post by ScooterBoogles on 2013-04-20
Great, thanks so much! I have two follow-up questions:

1) Which install method do you recommend using for the full install?
2) Can you point me to some documentation for /host (NTFS partition) because I don't actually know what that means....it's noob country over here!

Really appreciate your help.

---

### Post by Impavidus on 2013-04-20
1: To do a full install, first make sure you have unallocated space ready on your disk. Download the .iso, burn it to a dvd or usb and boot from it. See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) or [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) for more instructions. It's best to use windows tools to shrink windows partitions. Windows Vista or 7 will give problems otherwise.
2: A partition is a series of 0s and 1s on a disk, that can be interpreted as a file system with a directory tree. In there you can find files, which themselves consist of a series of 0s and 1s on a disk. In windows, maybe on the C or D partition (or drive, as it is called by windows), wherever you installed wubi, you can find the file root.disk. This is a file, nothing more than a series of 0s and 1s, that wubi interprets as a complete partition containing an entire file system, the Linux root file system. After all, they're both a series of 0s and 1s. At one point in that file system, at the directory called /host, Linux mounts a different file system. This file system is the partition on which the root.disk file is located. This means that the entire directory tree of your C or D partition is present inside the /host directory in the Linux directory tree, including the file containing the Linux directory tree itself – but not in a readable form, as it contains the raw data instead of a readable directory structure.

---

### Post by bcbc on 2013-04-20
The host NTFS partition is available with full access (read/write) under /host
e.g. to find your user documents Windows Vista/7/8 you can go to /host/Users/yourname/Documents
in Windows XP it would be /host/Documents\ and\ Settings/yourname/My\ Documents

Documentation?: [https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

---

### Post by ScooterBoogles on 2013-04-21
Thanks again everybody!

---

### Post by ScooterBoogles on 2013-04-21
I want to mark this thread as Solved but I don't see the command under the Thread Tools drop-down.

---

### Post by Impavidus on 2013-04-21
See here: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by ScooterBoogles on 2013-04-21
got it!

---

