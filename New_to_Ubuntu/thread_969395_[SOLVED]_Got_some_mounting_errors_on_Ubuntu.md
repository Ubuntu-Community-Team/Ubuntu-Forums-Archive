---
title: "[SOLVED] Got some mounting errors on Ubuntu"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by tehforum on 2008-11-03
Hi,

I have some mounting errors when I try and click on my Windows XP partition,81.9GB Volume.

I have a screenshot of this.

[http://www.filehive.com/files/081103/Screenshot.png](http://www.filehive.com/files/081103/Screenshot.png)

Is there any alternative ways of fixing this problem, instead of the ones displayed in the error message?


Thanks.

---

### Post by bumanie on 2008-11-03
You can boot into windows and do a clean shutdown. You can also install ntfsprogs and do an ntfsfix to ensure the ntfs filesystem is checked on its next boot. > sudo apt-get install ntfsprogs > ntfsfix /dev/sdxx (replacing xx with your drive and partition number)

---

### Post by oldos2er on 2008-11-03
> **tehforum said:**
> Hi,

I have some mounting errors when I try and click on my Windows XP partition,81.9GB Volume.

I have a screenshot of this.

[http://www.filehive.com/files/081103/Screenshot.png](http://www.filehive.com/files/081103/Screenshot.png)

Is there any alternative ways of fixing this problem, instead of the ones displayed in the error message?


 What bumanie said.

 Ubuntu attempts to preserve your data by refusing to mount a "dirty" NTFS partition. I think you can also fix the problem by running Windows' "chkdsk /f" command on the partition.

---

### Post by Oberiko on 2008-11-03
The default error message for this is pretty poor.

I would request that to give a more "graceful failure", Ubuntu should give the error in a pop-up, along with an option to run the ntsfix program for you.

---

### Post by kansasnoob on 2008-11-03
> **bumanie said:**
> You can boot into windows and do a clean shutdown. You can also install ntfsprogs and do an ntfsfix to ensure the ntfs filesystem is checked on its next boot.

+1

ntfsprogs will let you mount Win partitions and even files that you shouldn't unless you really, really know what you're doing!

It's in the repos!

---

### Post by tehforum on 2008-11-28
Thank you all.

Booting into Windows, and doing a shutdown worked perfectly. :)

---

