---
title: "Linux partition wiped out"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by El Tito on 2013-02-19
This morning I woke up (still half asleep), and accidentally selected the windows repair/recovery in grub. Cancelled when I was prompted, and when the reboot took place,
I got a grub rescue screen.
I tried to reinstall grub with a live cd (by the way I was using a Debian Wheezy iso, and the same OS was installed), and after searching for my linux partition (fdisk -l , blkid ...),
I found that it was wiped out somehow (103GB of free space where It was supposed to be my linux).
I suppose this is not recoverable, is it?, I believed that the windows recovery utility, only wrote in the MBR to set windows as the only OS.

Thanks in advance.

---

### Post by El Tito on 2013-02-19
I think I will install kubuntu again. Anyway, I'm still curious about the wiping if anyone knows something.

---

### Post by coldcritter64 on 2013-02-19
Have a look into the use of testdisk (in the repoitories) for partition recovery. If the windows utililty only changed the mbr (which includes the partition tables), then the linux install may still be recoverable, if it is needed that is or if you've re-installed kubuntu, it may have been recoverable but is too late ;).

Testdisk step by step guide : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) : For yor future reference if it happens again :), cheers.

---

### Post by El Tito on 2013-02-19
Thank you very much coldcritter64. I think that page is exactly what I was looking :p

---

