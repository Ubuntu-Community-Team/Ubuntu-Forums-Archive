---
title: "Making second hard drive /home"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by TaintedBllack on 2008-07-04
How could I set my entire secondary hard drive to serve as /home?

---

### Post by bumanie on 2008-07-04
If already installed, follow this [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) If yet to install, click on the link in that article.

---

### Post by nitro_n2o on 2008-07-04
You can do this while installing ubuntu by formating your second hard drive and choose the mount point to be /home
if you wanna move the current home directory to your second drive, then make sure you back up your data first. Then use gparted
sudo apt-get install gparted 
which will give you a graphical way of partitioning the drive
check out this link [http://linuxplanet.com/linuxplanet/tutorials/4269/1/](http://linuxplanet.com/linuxplanet/tutorials/4269/1/) or this one [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

---

### Post by TaintedBllack on 2008-07-04
Okay well.. I did a fresh install of Kubuntu on my primary HD and created a /home partition on my secondary HD.. But when I login it is not using the /home parition that I created it is using one from root. How can I redirect it to use the one I created?

---

### Post by TaintedBllack on 2008-07-04
Still looking for help with this.. Please

---

### Post by logos34 on 2008-07-04
You have to point the installer to the separate /home. like this:

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)
(>second screen)

---

