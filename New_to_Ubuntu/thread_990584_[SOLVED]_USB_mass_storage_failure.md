---
title: "[SOLVED] USB mass storage failure"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by WiseMaturin on 2008-11-22
I cannot seem to access my USB mass storage devices on 8.10
when I use ```
lsusb
```, I can see the devices are present.

But what do I need to do to access them?
When I use ```
sudo fdisk -l
``` I can see only one of them, but I still can't get ahold of them data!

---

### Post by fr.theo on 2008-11-22
have you tried "mount --help" in terminal?, usually it is sudo mount /dev/sde0 depending on what fdisk shows the drive device is labeled as. it is also good to paste you results of you lsusb and fdisk results to have a clearer understanding of what you have.

---

### Post by Gannon8 on 2008-11-22
Go to Places > <USB drive size> Media OR <partition label> and it should automatically mount it and open a window.

Anyway, post the output of:
```
sudo fdisk -l
```

You could also check the partition table with gparted:
```
sudo apt-get install gparted
gksudo gparted
```

---

### Post by WiseMaturin on 2008-11-23
I changed the names of the drives, and tried mounting them after and it worked fine. x_X

Thanks for you help though!

---

