---
title: "unable to access windows files after installing lubuntu"
date: 2018-02-28
forum: New to Ubuntu
---

### Post by dilipkumarthota on 2018-02-28
Hi friends i have installed lubuntu along side windows 7 but after installation i couldn't access my windows files. As i went through couple of threads here i found that the file system is different because of which i couldn't  access. 

Request you all to help me friends. I have valuable data in that.  

i tried
```
 sudo mount /dev/sda5 /home/newd -t ntfs-3g 
```   but not working!!! below is the details of the partitioned disk.  

[HTML]Device     Boot     Start       End   Sectors   Size Id Type 
/dev/sda1  *         2048 382908699 382906652 182.6G 8e Linux LVM 
/dev/sda2       382910462 625141759 242231298 115.5G  5 Extended 
/dev/sda5       382910464 625141759 242231296 115.5G 83 Linux[/HTML]

---

### Post by Autodave on 2018-02-28
Did you shut off "fast boot" in the BIOS?

---

### Post by Rex Bouwense on 2018-02-28
Going one step further, have you opened PCMan and mounted the partition that you have your Windows files on?  All you should have to do is right click the partition and select mount.  I am guessing that it is sda2.

---

### Post by Mark Phelps on 2018-03-01
From your details about sda, there is no Windows partition -- anymore.

My guess is that you made the mistake of using the Ubuntu installer without first manually creating some free space in Windows, and, in the process, overwrote the Windows partition(s).

---

### Post by dilipkumarthota on 2018-03-01
thanks for the response.. But as i remember i haven't touched the option 'fast boot'

---

### Post by dilipkumarthota on 2018-03-11
> **Mark Phelps said:**
> From your details about sda, there is no Windows partition -- anymore.

My guess is that you made the mistake of using the Ubuntu installer without first manually creating some free space in Windows, and, in the process, overwrote the Windows partition(s).

Thanks for the response!!! i admit that i have done that mistake .. but does it mean that it has wiped my data or do i have still chance to get the data back... Request to help.

---

### Post by dilipkumarthota on 2018-03-11
> **Rex Bouwense said:**
> Going one step further, have you opened PCMan and mounted the partition that you have your Windows files on?  All you should have to do is right click the partition and select mount.  I am guessing that it is sda2.

i have tried this but couldn't install pcman on ubuntu as it says after unpacking command not found. Any other alternate software which you can suggest me

---

### Post by yancek on 2018-03-11
During your installation, you chose to use LVM (definitely not the default) and this options overwrites the disk.  The longer you use the computer, the less chance you will have of recovering data which you might be able to do to a certain extent with TestDisk/Photorec.  You can use the Ubuntu install media to download and run it.  There is a Step-by-Step guide at the download site at the link below.

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

