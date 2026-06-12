---
title: "How unique is a particular install on a hard drive ?"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by Rich13 on 2013-02-13
I installed Ubuntu 12.04 on an old Lenovo T60 laptop.  It has a 1.83 GHz Centrino Duo processor, 2 Gb RAM, DVD drive.   The laptop has something subtly wrong with it, as it does not reliably boot from the hard drive every time, it takes perhaps 6-12 trys to get a proper boot, but once booted, it seems to run quite stable and I have had it running for several days continuously.  The HDD is actually a new Samsung SSD.   I have not been able to figure out what the boot issue is ... the SSD replaced the original HDD as I thought the symptoms pointed to a flaky HDD, but no luck.  There is only Ubuntu installed on the SDD in a single partition, no other OS.

Can I simply swap the SSD into another laptop ?  I may have access to a Dell D630 laptop, which is a Core2 Duo, 2 GHz, with 2 G RAM and a DVD drive.   Is Ubuntu clever enough to automatically adapt, or will I need to do a completely new install ?

Thanks for your comments.

---

### Post by deadflowr on 2013-02-14
I don't know how adaptable ssd drives are, but I've moved hdds from one system to another with no problem.

The only thing that can cause any real problems, is if you've installed proprietary drivers.

Ubuntu doesn't tie itself to the hardware like Windows systems do.

Edit: Also, I don't know, and am not going to look up the architecture of the two computers you're using, so I don't know if they 32-bit or 64-bit.
However, you were using a 64-bit version of Ubuntu, and tried to move the disk to a system that does not support 64-bit it will not work.
If you installed the 32-bit version, then there shouldn't be any problem, as 32-bit can run on either 64 or 32-bit system, but 64-bit only run on 64-bit system.

---

### Post by Warren Hill on 2013-02-14
Give it a try.

For the most part Ubuntu seems to adapt.  Its possible you may have driver issues if the hardware is very different.  But it costs nothing, but a little time, to try it.  If it all goes wrong then re-install.

---

### Post by Rich13 on 2013-02-14
Thanks for both comments.  Both laptops are 32 bit and the install is 32 bits.  I thought that Ubuntu was not as tied in as Windows .... watching what the recovery mode screen goes through as it seems to search and detect all sorts of things on the machine, made me think it was much more flexible and accomodating, but I was wondering what others thought.  

Thanks again !

---

### Post by grahammechanical on 2013-02-14
I suggest that your first boot be through Recovery Mode>Resume as that loads Ubuntu without using the video drivers. The difference between the video adapters may cause problems. Once you are at a desktop you can either log out and log back in and see what happens or use Additional Drivers to see if you can get a driver suitable for the video card. You may need to experiment.

Regards.

---

