---
title: "ubuntu using WUBI installer dont boot showing NTFS error?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by iyan90007 on 2012-03-14
Hi, I installed ubuntu using WUBI inside Windows 7 64 bit. It doesn't boot showing NTFS error. Is Dynamic disk in windows a cause?

---

### Post by Rogueninja64 on 2012-03-14
Which type of Ubuntu are you trying to install?

---

### Post by 2F4U on 2012-03-14
And what is the exact error you are getting?

---

### Post by Vinkus on 2012-03-14
Hello, do you run WUBI on a separate partition?

---

### Post by holytree on 2012-03-14
> **Vinkus said:**
> Hello, do you run WUBI on a separate partition?

No WUBI runs in the space you have given  it along side windows

By the way which version did you  install?


holytree

---

### Post by tbhatia4 on 2012-03-14
are you ale to boot in windows

---

### Post by Mark Phelps on 2012-03-14
> **iyan90007 said:**
> Hi, I installed ubuntu using WUBI inside Windows 7 64 bit. 
Wubi does not create a new partition; instead, it uses an existing NTFS partition.

>  It doesn't boot showing NTFS error. 
Would help if you told us the error details.

> Is Dynamic disk in windows a cause?
I don't think Wubi can install to a Dynamic Disk -- but you first need to see if you have them.  Since Ubuntu isn't working for you, launch the Disk Management utility in Win7 and look at the partitions (MS calls them Drives).  If any are Dynamic Disks, the information will be shown on the screen.

---

### Post by iyan90007 on 2012-03-16
> **Mark Phelps said:**
> Wubi does not create a new partition; instead, it uses an existing NTFS partition.


Would help if you told us the error details.


I don't think Wubi can install to a Dynamic Disk -- but you first need to see if you have them.  Since Ubuntu isn't working for you, launch the Disk Management utility in Win7 and look at the partitions (MS calls them Drives).  If any are Dynamic Disks, the information will be shown on the screen.

It shows only NTFS error and the screen goes black...

---

### Post by iyan90007 on 2012-03-16
> **tbhatia4 said:**
> are you ale to boot in windows

At first it didnt show any boot screen...den it showed Windows & Ubuntu in the boot menu but ubuntu don't work...Windows & boots normally...

---

### Post by iyan90007 on 2012-03-16
> **holytree said:**
> No WUBI runs in the space you have given  it along side windows

By the way which version did you  install?


holytree

ubuntu 11.10

---

### Post by Mark Phelps on 2012-03-17
> **iyan90007 said:**
> It shows only NTFS error and the screen goes black...

What -- the Win7 Disk Management utility does this?

If not, please follow the earlier instructions I gave you about using that utility and tell us what it shows.

Not providing us the details we ask for is NOT going to get your problem solved.

---

