---
title: "Using two hard drives"
date: 2017-12-13
forum: New to Ubuntu
---

### Post by btown7654 on 2017-12-13
I'm installing ubuntu on a 32g Emmc, and I also have a ssd on a sata 3. I have only worked with Windows. Can someone send me a link or push me in the right direction on how to install the os on the emmc and use the ssd for data. I have already installed the os on the emmc. Not sure how to set up the ssd for data. Any help would be much appreciated. Hope I didn't already mess up.

---

### Post by QIII on 2017-12-13
Hello!

Is the eMMC something that came with a notebook?  

In general, it is best to have the OS run on the fastest media, with storage on the slowest.  SSDs are far faster than eMMC and have much more sophisticated wear-leveling and TRIM.  Also, the amount of storage available on eMMCs is significantly less than a typical SSD -- in your case 32GB.

How large is your SSD?  I would say you would be much better served installing your OS on a portion of your SSD, with a large partition set aside and dedicated to data.

We can help you with that, too, of course!

---

### Post by oldrocker99 on 2017-12-13
I always use the "Something Else" option during installation, and install the root /  on a 50GB partition, and use the rest for a Steam folder. You'll want to get a bigger SSD or a large HD for /home. Your /home partition, I have found, can never be too big.

---

