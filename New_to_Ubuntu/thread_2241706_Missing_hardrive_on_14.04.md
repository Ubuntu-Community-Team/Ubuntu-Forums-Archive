---
title: "Missing hardrive on 14.04"
date: 2014-08-27
forum: New to Ubuntu
---

### Post by Jason_Kindorf on 2014-08-27
I am completely new to Ubuntu, and the only previous experience I have with linux is on Android. Today I installed 14.04 alongside Windows Vista since it's a shared computer and my brother is stubborn. After giving Ubuntu a once over I decided I loved it but soon noticed that I'm missing a hardrive, I have 120Gb Main boot which has Vista installed, A 20Gb and two other 80gb which I have stiped together for media and my Steam Library. So C: as boot, D: as spare where I have Ubuntu installed, and then I: as the striped media drive. (I:) is missing, all it will show me is C: and D:. Does anyone know how I can fix this or have some troubleshooting I can do? 

Thank you in advance.

---

### Post by yancek on 2014-08-28
Are you using the term 'drive' to mean partitions?  Do you have four physical hard drives or four partitions.  Is this from windows?  Windows default doesn't recognize Linux filesystems and shows them as unallocated or free space.  If you boot Ubuntu and open a terminal run the command:  sudo fdisk -l(Lower Case Letter L in the command), it will show drive/partition information.

---

### Post by gavin7 on 2014-08-28
In addition to the above, you could also get gparted

```
sudo apt-get install gparted
sudo gparted
```

This will show you the disk partitions... Note: Read about GParted before doing anything more than just reviewing your disk partitions, I have not had issues before but you could run into trouble if you removed say your boot partition...

---

