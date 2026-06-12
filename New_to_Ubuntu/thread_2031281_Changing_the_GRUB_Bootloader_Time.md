---
title: "Changing the GRUB Bootloader Time"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-07-21
How can I change the number of seconds for the GRUB bootloader to automatically boot? Also, how do I set it to automatically boot Windows instead of Ubuntu?

---

### Post by anewguy on 2012-07-21
Please see [this]("http://linuxpoison.blogspot.com/2010/11/how-to-change-grub-2-default-timeout.html") - it tells all (it's simple also).

OOPPPSSS - missed that you're running 10.04 - in that case please see [this]("http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/") it explains how to do this for the old grub (also simple).  Changing the default boot is also simple - just take a loot at that file and if you can't figure it out post back.

---

### Post by NikTh on 2012-07-21
Hi  , 

Ubuntu 10.04 uses grub 2 . Not grub legacy. 

An other option is to install grub-customizer and change from there anything you want. 

open a  terminal (Ctrl+alt+t) and copy paste below commands , one at time. 

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer
```Then find and open grub-customizer (it will be at administration section) and change time or boot order or picture ...
See a tutorial here : [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Regards

---

### Post by anewguy on 2012-07-21
None the less the first line of my post contains the link to the how-to for grub2. It's been a long time since I used 10.Exxon so if I was wrong about it usinggrub so be it. I was thinking grub2 didn't show up until 11.04 but I realized after I posted that was unity (after the old netbook stuff).  None the less everything is contained in my original post.

---

