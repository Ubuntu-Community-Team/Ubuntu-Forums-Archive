---
title: "Just about to install (advice)"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2008-05-07
Hi, Just about to install 7.10 on my other pc which has a 20GB primary and 1TB slave, Both are RAW data (deleted partitions with a windows disc) Now I want to use the 1tb as storage, Would I just be able to access it store thing on it ? Or do i need to do something before installation or after ?

Thanks

---

### Post by mapes12 on 2008-05-07
In my experience the installation will detect both disks and create the Linux partitions and format them for you. You can choose which one you want the installation files to be loaded onto leaving the bigger disk as storage media. However, I haven't been lucky enough to use a 1TB disk so I don't know how Linux will handle the size.

If there's nothing critical you want to keep on your box give it a go and see how it goes.

---

### Post by Delever on 2008-05-07
If you don't already know: if 20GB disk is older and both are hard disks, 1TB disk performance is WAY faster, because it reads and writes much more data while spinning at the same speed. The best spot to place OS would be in the begining of your larger disk.

---

### Post by stchman on 2008-05-07
> **r5gtt2k3 said:**
> Hi, Just about to install 7.10 on my other pc which has a 20GB primary and 1TB slave, Both are RAW data (deleted partitions with a windows disc) Now I want to use the 1tb as storage, Would I just be able to access it store thing on it ? Or do i need to do something before installation or after ?

Thanks

When you boot up the LiveCD make the 1TB an EXT3 partition using gparted.

Leave the 20GB as free space.  During the install tell Ubuntu to install on the largest free space (20GB) and you will be good to go.

---

### Post by r5gtt2k3 on 2008-05-07
Thanks, It worked ok :D

---

