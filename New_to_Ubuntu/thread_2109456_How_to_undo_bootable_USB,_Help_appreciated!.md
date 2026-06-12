---
title: "How to undo bootable USB, Help appreciated!"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by Jaeman on 2013-01-27
Hey there! so I formatted my external 500 gb hard drive to be a bootable usb. how do I undo this so I can use my external hard drive regular again? Some people have said "format it" but how do I do that? thanks

---

### Post by Nr90 on 2013-01-27
Are you running linux?
If so: 
0. install gparted
1. open gparted
2. select your USB HDD
3. remove all partitions
4. create a new partition of the max size on your USB HDD (format as NTFS for windows support, if you only need linux support format as EXT4)
5. apply

---

### Post by Jaeman on 2013-01-27
> **Nr90 said:**
> Are you running linux?
If so: 
0. install gparted
1. open gparted
2. select your USB HDD
3. remove all partitions
4. create a new partition of the max size on your USB HDD (format as NTFS for windows support, if you only need linux support format as EXT4)
5. apply

I'm not running linux yet, still waiting for my hdd to arrive. I'm on windows currently.

---

### Post by Nr90 on 2013-01-27
Don't have access to a windows pc atm, but I think you need a tool called disk management. Find it in the control panel and run that.
Remove every partition on the USB HDD.
Create one large NTFS partition.

---

### Post by Jaeman on 2013-01-27
> **Nr90 said:**
> Don't have access to a windows pc atm, but I think you need a tool called disk management. Find it in the control panel and run that.
Remove every partition on the USB HDD.
Create one large NTFS partition.

Thanks, I figured it out! i had to locate, select, erase it, then create primary partition, select and activate it, format and activate it but i got it! thanks

---

### Post by Nr90 on 2013-01-27
Glad you figured it out.
You can mark this thread as solved

---

