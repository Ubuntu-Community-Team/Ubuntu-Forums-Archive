---
title: "access"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by navaleshubham10 on 2011-11-27
how can i open other volumes? is there any kind of settings or some kind of code

---

### Post by spiky001 on 2011-11-27
Maybe you can explain some more, In Nautlus there are other partitions in the side pane

---

### Post by CryptAck on 2011-11-27
By volumes, do you mean hard drive partitions? 

You'd need to mount ([http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)) them onto your file system.


Sorry for the link, attempted to map word 'mount' to ref, but Insert Link option was not working on the interface.

---

### Post by navaleshubham10 on 2011-11-27
actually, i have windows xp professional in c drive and ubuntu in e drive but i want to access other volumes like d and f but there is no option to open

---

### Post by CryptAck on 2011-11-27
> **navaleshubham10 said:**
> actually, i have windows xp professional in c drive and ubuntu in e drive but i want to access other volumes like d and f but there is no option to open

Ahh, okay!

In that case, you'll need to use a tool (driver) to read the Linux file systems from Windows. Windows doesn't have native read support for Linux file systems. 

Do you know what file system you used during install? I'm assuming Ext3 or Ext4?

If so, I believe the Ext2 IFS still works, [http://www.fs-driver.org/](http://www.fs-driver.org/) 

There was another tool I used years ago, but I cannot recall at this time.

---

### Post by CryptAck on 2011-11-27
Going off the information from this web-posting ([http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/))

I would say that Ext2IFS will not work with Ext4, and the other tool listed is a better choice. 

Best of luck!

---

### Post by navaleshubham10 on 2011-11-27
can i open folders of other volumes in Ubuntu

---

### Post by grahammechanical on 2011-11-27
A Linux distribution like Ubuntu can read Windows formatted drives and access the folders and files on those drives. A Windows operating system is not usually able to read a Ubuntu partition.

In Linux a disk partition is called a partition. In Windows a partition is called a drive.

You do not tell us what version of Ubuntu you are using. We may have to give you different directions for different versions.

Open the File Manager. On the left hand side is a panel or pane. Under **Computer** you get access to some folders on the Ubuntu partition. File System is where the operating system files are stored. That may even be on its own partition but it is just called File System.

Under **Devices** you will see other partitions (called drives in Windows) They are also called File Systems if they have an operating system on them. You will also see the size of the partition. You will not see a drive letter such as C: D: E: F: Linux does not use the same names that Windows uses.

I do not have Windows on my machine but I do have more than one Linux operating system. I am describing what I ama seeing in my File Manager.

Regards.

---

### Post by CryptAck on 2011-11-27
> **navaleshubham10 said:**
> can i open folders of other volumes in Ubuntu

From Ubuntu, you *should* be able to access any Windows drives by default, yes. 

From Windows, you'll need additional software (as I posted above) to access Ubuntu/Linux data.

---

