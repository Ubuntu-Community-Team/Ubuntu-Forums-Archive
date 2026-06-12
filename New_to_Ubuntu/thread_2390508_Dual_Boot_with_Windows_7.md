---
title: "Dual Boot with Windows 7"
date: 2018-04-29
forum: New to Ubuntu
---

### Post by dshrimankar on 2018-04-29
Hello All,

I just installed Ubuntu on my laptop that has Win 7. I re-partitioned the HD and installed Ubuntu on one of the partitions. I was curious whether I could access Ubuntu while I am in Windows mode and vice-a-versa?

Thanks
D

---

### Post by oldfred on 2018-04-29
No, not with dual boot.
You can create a shared data partition, NTFS to share data.

Or you can install inside a VM if you have lots of RAM to share installs.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box](http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box)

---

### Post by yancek on 2018-04-29
What do you mean by access?  The default for windows is no, not unless you install additonal drivers/software to allow access to a Linux system.
You should be able to access read/write windows files from Ubuntu.  You would need to have ntfs-3g installed.  I'm not sure if it in a default install.
Creating a separate data partition as suggested (ntfs) is best and don't try to write to system files on windows from Linux or vice versa, just use a data partition.

---

### Post by junaidahmed2 on 2018-04-29
You can shrare any number of FAT32/NTFS partition between Ubuntu and Windows. But never access any shared partition or Windows system partition from Ubuntu while Windows on hibernation. 
You can also access ext4 partitions from Windows using [Linux Reader]("https://www.diskinternals.com/linux-reader/") . But do not access Ubuntu system partition from Windows while Ubuntu is hibernated. 
So as long as Ubuntu or Windows is not sleeping in cave, you can access one from the other.

---

### Post by joegry on 2018-04-30
Another setup you may wish to try would be to install virtualbox on windows and then install ubuntu within virtualbox [https://www.virtualbox.org/](https://www.virtualbox.org/) . I believe Virtualbox would allow you to share directories between the two operating systems.  I hope this hlps.

---

### Post by hier-kommt-luis on 2018-05-08
> **joegry said:**
> Another setup you may wish to try would be to install virtualbox on windows and then install ubuntu within virtualbox [https://www.virtualbox.org/](https://www.virtualbox.org/) . I believe Virtualbox would allow you to share directories between the two operating systems.  I hope this hlps.

It would be better option to use VMWare if with 18.04, at least it's way more stable [https://www.vmware.com/products/workstation-pro.html](https://www.vmware.com/products/workstation-pro.html)

---

