---
title: "ubuntu overwrites the whole partition?"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by brainzz on 2012-11-17
Hello,
Machine: **Windows 7**
Ubuntu Version to be installed: **12.10**
Drive selected for installation: **D Drive**
Is Drive Empty?: **No, Drive D has data in it.**
Drive Size: **100 GB**
Drive Free Space: **39 GB**
Additional Info: **See Image**


[IMG]http://i46.tinypic.com/risqrd.png[/IMG]


My Question: **Would Ubuntu wipe out my already existing data in D Drive?**

Thank you guys,
~ aki

---

### Post by Basher101 on 2012-11-17
looks like you try to install via Wubi. Wubi installs only creates a virtual partition inside Windows. This is for people that want to try out Ubuntu to an extent that a Live CD session cannot provide. So in other words, a Wubi install is not a real ubuntu insallation. To make a full installation you would need to boot from a Live Cd, create a new ext4 filesystem partition where Ubuntu would be installed to. 

And, to answer your original question, no, it would not simply erase your partition, but instead, take some space and create a virtual partition.


The advantage of a wubi install is that you can easily uninstall it if you do not like Ubuntu. The drawback is that if you can't boot into windows, you also have no access to Ubuntu.

Hope this helps

regards

---

### Post by Gone fishing on 2012-11-17
Even if you did a non-Wubi install Ubuntu although needing its own partitions (non-Wubi), can resize the Windows partitions to make room for itself.

---

### Post by brainzz on 2012-11-18
Thank you "Basher101" and "Gone Fishing".
Yes, i wanted to put down a new installation of Ubuntu, and not something virtual that i can try out.

So, Wubi goes out the window for my purposes as of now.

And even if it is a non-Wubi installation, all I have to do is burn the ISO and boot from that drive, and Ubuntu will help me create/resize the partitions to make room for itself.

I hope I am right in understanding the both of you.

Thanks a lot,
~aki

---

### Post by pkadeel on 2012-11-18
Yes if you burn ISO to CD and boot from it then it will provide you 2 options
Try or Install
If you choose install then it will guide you through the whole process which includes the option for partitioning the drive.

---

