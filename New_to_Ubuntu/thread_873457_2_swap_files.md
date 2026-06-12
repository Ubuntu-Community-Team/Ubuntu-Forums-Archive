---
title: "2 swap files?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by cake_or_death on 2008-07-29
hi all - 

I'm new to Linux, and recently installed Hardy 8.04 on my Vaio CR series laptop.  Suspend and hibernate are not working.  I've read through several of the threads on this topic, but none of the suggested fixes have worked.  I'm looking at my partition editor now and it shows that I have two swap files:  /dev/sda5  and /dev/sda7.  I've reinstalled Hardy from the live cd twice after my obsessive tweaking of the system got a little out of hand and led me to a grub "error 22".  Both times I've selected the guided partitioning option.  Could this be why I have two swap files?  also, could the existence of dual swap files be what's preventing my suspend and hibernate from working?  any help would be much appreciated.

---

### Post by namegame on 2008-07-29
Also, the size of your swap partitions could affect the performance of your suspend/hibernate. I would recommend that your swap partition be the same size as your ram or even a bit larger just in case you have bad sectors.

EDIT: More experienced person took care of it.

---

### Post by PmDematagoda on 2008-07-29
The two Hardy install attempts might be the source of the problem with the two swap partitions. But about the suspend/hibernation issues, what are the specifications of your PC?

Edit:- Having two or more swap partitions as swap does not cause any problems in normal operation, but it may have an affect on suspend/hibernation, though I am not entirely sure about that. Perhaps you could just disable one swap partition through /etc/fstab(prevent it from mounting actually) and then try suspending or hibernating?

---

### Post by Sef on 2008-07-29
How much ram do you have?  1 GB and more ram needs only 1 GB swap, if any.

---

### Post by namegame on 2008-07-29
> **PmDematagoda said:**
> 

Edit:- Having two or more swap partitions as swap does not cause any problems in normal operation, but it may have an affect on suspend/hibernation, though I am not entirely sure about that. Perhaps you could just disable one swap partition through /etc/fstab(prevent it from mounting actually) and then try suspending or hibernating?

That's what I was wondering about.

---

### Post by cake_or_death on 2008-07-29
I've got both Vista and Ubuntu currently installed. My swap files are 3.23 GiB and 3.37 GiB.  Does Vista have its own swap file?  When I type the "free" command in the terminal, it only shows me the 3.37 GiB swap file, however, when trying to suspend using "sudo s2ram" command in the terminal, I'm told the swap file is not active.

---

### Post by kdb424 on 2008-07-29
That's weird. On the subject of size, the rule of thumb is 50% of physical ram for swap. No idea how to activate it, because I always did a no swap install.

---

### Post by eightmillion on 2008-07-29
You have to have a swap file at least the size of physical memory to be able to hibernate a laptop.

> Does Vista have its own swap file?
Vista has a page file that is not a separate partition.

Could you post the contents of your **/etc/fstab** please

---

### Post by cariboo on 2008-07-29
I had two swap files at one point, I am using Intrepid alpha 3 as my main operating system and have hardy as a backup in case things go wrong. I already had a 4GB swap partiton for hardy, and when I set up Intrepid I created another 4GB swap partition, I found that after reinstalling Intrepid a couple of times that the swap partition for intrepid was never being used, it was using the swap I setup for hardy, so when I installed apha 2 I didn't create a swap partiton. I've been running with only the one swap partition for about a month now and haven't had any problems.

Jim

---

### Post by cake_or_death on 2008-07-29
> **eightmillion said:**
> You have to have a swap file at least the size of physical memory to be able to hibernate a laptop.


Vista has a page file that is not a separate partition.

Could you post the contents of your **/etc/fstab** please


sorry, how do I go about getting to the contents of /etc/fstab?  is there a terminal command?

---

### Post by PmDematagoda on 2008-07-29
> **cake_or_death said:**
> sorry, how do I go about getting to the contents of /etc/fstab?  is there a terminal command?

```
cat /etc/fstab
```

---

### Post by cake_or_death on 2008-07-29
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2d47ca63-480a-446b-809b-7630eedaa837 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=860feed7-f9b1-4f17-b91b-113830d64485 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

does that help?

---

### Post by eightmillion on 2008-07-29
Yeah, that helps. There's only one swap partition listed in you fstab. So, while you have two swap partitions, they aren't both enabled at the same time. You can safely get rid of /dev/sda5.

---

### Post by cake_or_death on 2008-07-29
The partition editor won't allow me to delete the partition.  An error messages tells me to unmount any logical partitions with a number higher than 5 (I'm guessing it means sda6 and sda7).  Can I just resize the partition down to the minimum size, which partition editor tells me is 8 MB, or would it be best to figure out another way to delete it?

---

