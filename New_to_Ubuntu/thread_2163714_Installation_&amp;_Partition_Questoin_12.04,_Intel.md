---
title: "Installation &amp; Partition Questoin 12.04, Intel Mac"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by jimdixon on 2013-07-19
Hi,

I haver a Mac (osx 10.5.8, Intel Core 2 Duo) with a Windows 7 Partition that I set up in Boot Camp. I would like to completely Replace the Windows partition with Ubuntu 12.04 (64 bit, i think). I have installed rEFIt. My question:

Can I boot Ubuntu from a CD in my Windows Partition, and just install Ubuntu in its place? or do I need to wipe the Windows partition and do some sort of reformatting first?

Thanks for considering.

---

### Post by newb85 on 2013-07-19
Disclaimer: I'm not familiar with Boot Camp.  (Is it a virtual HD sort of setup?)

Ubuntu will not install on a NTFS partition.  The Ubuntu installation media includes Gparted, a tool for creating the EXT4 partition Ubuntu needs for installation.  Don't boot from within Windows.

Addendum: You should see the instructions at [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick).

---

### Post by jimdixon on 2013-07-19
Thanks,

I'll go ahead and delete Windows and then use Gparted.

Edit: Boot camp isn't a virtual HD. Its prepackaged with osx to create a partition that is ideal for dual booting Windows.

---

