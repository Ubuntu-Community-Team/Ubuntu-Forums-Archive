---
title: "More space"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by saloomi2012 on 2013-03-02
So when I first installed Ubuntu from wubi I gave it 18 GB, I am almost out of GB's now and want to give Ubuntu more, anyone know how?(running **Ubuntu 12.10 ** with **Windows 7 dual boot**):confused:

---

### Post by cwsnyder on 2013-03-02
First, if you are installed from Wubi, you are running a virtual Ubuntu install inside your Windows partition, you are not dual-boot, it only seems like it to you.

Second, [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) contains instructions for one method and a link to another method for re-sizing your WUBI virtual Ubuntu install.

---

### Post by Karlchen on 2013-03-02
Thumbs up for the second part of the reply post. Correct and to the point.=D>
> **cwsnyder said:**
>  Second, [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) contains instructions for one method and a link to another method for re-sizing your WUBI virtual Ubuntu install.

Thumbs down for the first part. This is neither correct, nor helpful. ](*,)
> **cwsnyder said:**
> First, if you are installed from Wubi, you are  running a virtual Ubuntu install inside your Windows partition, you are  not dual-boot, it only seems like it to you.
A Ubuntu Wubi installation is a full Ubuntu installation. Its filesystem is located in a large container file. The container file is located on a Windows NTFS partition. One downside of this container file is that the size of the container file is limited to 30 GB. Another downside is that Ubuntu depends on the health of the underlying NTFS filesystem. During the past 3 years, however, this has never proven to be any problem at all on my office notebook. although it is being used 8 hours a day, 5 days a week (minimum usage).
During the boot phase you have to decide whether you want to boot Windows or Ubuntu much in the same way that you would have to do in case Windows and Ubuntu lived on separate disk partitions. So this is a dual boot situation. You either run Windows, or you run Ubuntu, never both at the same time.

Karl

---

### Post by saloomi2012 on 2013-03-02
Thank you guys!

---

