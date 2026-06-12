---
title: "Installation strange"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by WesternRyno on 2013-03-01
Well, at least strange to me.  

To make a long story short...., 

after installing bumblebee and restarting I was locked out of Ubuntu 12.04 and was greeted with either the black or purple screen of nothingness.  

Booted up on the flashdrive and ran boot repair.  

Was then booted into a previous version of Ubuntu that I thought I had wiped in a fresh install?  In fact, sure I wiped.  

Now I have three versions of Ubuntu on my Lenovo with a 750GB harddrive and 24GB SSD drive, both of which Ubuntu on them.

**Question**:  How can I erase/format/delete the whole shebang so I can have fresh empty drives to put a clean, fresh 12.04 on?  Thanks to anyone who can help me out of this vortex of doom....really would love to make this work as I love Ubuntu on my older machines.

PS Could this be happening because this is such a new Notebook with UEFI?

---

### Post by Gone fishing on 2013-03-01
If you just want to start over, boot up on a live Ubuntu CD or a parted magic CD back up any data and run gparted you will then be able to delete the existing partitions.

---

### Post by UltimateCat on 2013-03-02
>  Could this be happening because this is such a new Notebook with UEFI? 				


That's possible but if you do what Gone fishing suggest's your Lenovo should boot just fine-

If not the way around the Win's 8 UEFI is to disable the Secure Boot- -
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)

How to install Linux and Win's 8
[http://www.zdnet.com/search?q=how+to+install+linux+and+windows+8](http://www.zdnet.com/search?q=how+to+install+linux+and+windows+8)

Hope this helps; Good luck;-)

---

### Post by WesternRyno on 2013-03-02
Thanks for your help guys, I formatted both drives and put a fresh install on.  System stable now.

---

