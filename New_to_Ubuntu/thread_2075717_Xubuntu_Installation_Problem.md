---
title: "Xubuntu Installation Problem"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Lord Zamy on 2012-10-24
I am trying to install xubuntu on my computer which is already running windows 7. There are 2 main problems during the installation. When I click on continue after the part saying - "For best results, please ensure blah blah blah......", a dialog box pops up saying - "The installer has detected that the following disks have mounted partitions:
/dev/sda
Do you want the installer to try to unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partions there."

Then it gives me the options yes or no. My first question is which one i should choose. I have two hard drives in my computer. The C:/ or the /dev/sda drive is of 160gb and is partitioned into two with the smaller partition being 100mb (maybe it was created by windows). This one conatins the windows OS files. The second hard drive, I use for all my data. So I would like to install xubuntu on C:/ only. 

Now when I choose the option install alongside windows, only my other hard drive is being shown. I can't choose the 160gb one. So how should I install it now? 
P.S. I don't want to install using wubi.

---

### Post by Merrattic on 2012-10-24
1. Boot up Windows 7 and use Computer Management to resize your Windows 7 partition (not the 100mb one) to create sufficient unallocated space for your Xubuntu installation, say @ 20GB.

2. Boot Xubuntu CD, follow the install options, Xubuntu should offer to install to the unallocated space, assist with partitioning, setting up swap etc. You can use the wizard or do this manually.

This is a brief howto, there are much better / more complete guides on the forum or in ubuntuland

---

