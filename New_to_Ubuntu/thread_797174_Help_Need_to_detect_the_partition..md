---
title: "Help: Need to detect the partition."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by elord on 2008-05-17
Guys i need your help for my problem.. I succesfullly install to OS in my PC..Windows XP and UBUNTU 5.01 my problem is that i can't format my remaining partition in Windows XP since the remaining partition are done in Ubuntu..

This is the details in my PC

C:\WIndows XP
d:\UBUNTU 
Uknown partitionn are done in UBUNTU and i tried using administrative tools in XP to create the remaining partion and format it.. But they are errors.. 

Is there any solution for this problems? i know XP and Ubuntu are different format.. tnxs a lot  and More power to UBUNTU and linux users..

---

### Post by ace007 on 2008-05-17
Why so old a version of Ubuntu?  

What do you mean the partitions are "done" in Ubuntu?  Do you mean that you formatted them in Ubuntu?  That you formatted them in ext3 format?  If they are in ext3 format, Windows cannot read them.  Or do you mean that there is unpartitioned space on your hard drive?

If you want us to take a look at your setup. Open a terminal in Ubuntu and enter the following code.  Then paste the results here, we'll try to help 
```

sudo fdisk -l

```

---

### Post by Apple Ink on 2008-05-17
Run Partition editor

System>Administration>Partition Editor

Then analyze your hard disk 
If you want, you can format the drive in fat32 and then use XP to reformat in either NTFS or FAT32!

P.S. If you cant find partition editor, 
System>Administration>Package Manager|
Search for gparted and install. Restart and use!


You may want to upgrade to a more newer version of ubuntu (perhaps something which is supported)

---

### Post by elord on 2008-05-20
ok tnxs .. maybe i'll upgrade my Ubuntu 5.01 to 7.10 1st and make some changes...

---

### Post by zvacet on 2008-05-20
Don´t waste your time to upgrade.Install Hardy instead.

---

### Post by hyper_ch on 2008-05-20
> **elord said:**
> ok tnxs .. maybe i'll upgrade my Ubuntu 5.01 to 7.10 1st and make some changes...

8.04 is the current release...

---

### Post by elord on 2008-05-20
> **zvacet said:**
> Don´t waste your time to upgrade.Install Hardy instead.


ok so whats the difference if i upgrade the ubuntu and if i install the hardy?

---

### Post by hyper_ch on 2008-05-20
you will have to upgrade through various versions (from 5.04 to 8.04) which will take significantlly longer than reinstall just a 8.04

---

### Post by elord on 2008-05-20
i tried to install it in my PC but there is problems since my PC is only 32bit then the Ubuntu 8.04 is 64bit.. thats why im using 7.10 instead

---

### Post by hyper_ch on 2008-05-20
there is 32- and 64-bit version

---

### Post by zvacet on 2008-05-20
> ok so whats the difference if i upgrade the ubuntu and if i install the hardy?

You can upgrade to Dapper and then directly to Hardy.Difference is that you use unsuppoted version and to upgrade from unsupported to suppported is little bit different.It is not impossible,but there is no reason to do that if you can do fresh install.

---

