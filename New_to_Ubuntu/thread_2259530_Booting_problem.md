---
title: "Booting problem"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by vasanthabojan on 2015-01-05
I am getting the following error if my ubuntu boots automatically without choosing any options but it worked fine before

"Gave up waiting for root device.common problems

    -Boot args (cat /proc/cmdline)  
    -Check root delay =(did the system wait long enough?)  
    -check root=(did the system wait for right device?)
    -missing modules (cat /proc/module;ls /dev)  
 ALERT! /dev/mapper/LTSP--vg-root does not exist.Dropping to shell !
 Busy box v1.18.5(ubuntu 1:1.18.5-1 ubuntu 2.1)built in shell /ash)

  Enter help for a list of commands

  (initramfs)"

But if i hold the shift key when booting and choose previous linux version and a image in that it works fine.

Can anyone please suggest any idea to solve this problem??

---

### Post by yancek on 2015-01-05
> ALERT! /dev/mapper/LTSP--vg-root does not exist.Dropping to shell !

That would indicate an LVM install and a problem finding the root filesystem.  I don't use LVM or have any knowledge so I would suggest you get the bootrepair from the link below and select the option to Create a Bootinfo Summary to post here.  Someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

