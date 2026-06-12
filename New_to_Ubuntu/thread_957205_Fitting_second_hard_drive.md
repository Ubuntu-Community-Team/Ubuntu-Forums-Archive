---
title: "Fitting second hard drive"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-10-24
I wasn't sure if this or the hardware board was the right one, but I am, above all else, an absolute beginner.

I have reason to need some access to Windows on a regular basis so for now, dual booting seems the answer. However, how I would like to do is fit a second hard drive and have Ubuntu on one and Windows on the other, with my existing drive (the Ubuntu one), as the default drive and the new one for Windows when I choose. How easy would this be to set up and are there any points I need to be aware of?

---

### Post by indytim on 2008-10-24
It's easy.

If you had checked the stickies at the top of the forum, you would have found resources for what you are looking for.  Here's a link to a pretty good source of info regarding various aspects of starting off in Linux.

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

IndyTim

---

### Post by nhasian on 2008-10-24
yes you can have windows on one drive, and ubuntu on another and dual boot.  alternatively if you have enough space, you can have both operating system on the same drive by resizing the original partition to make room for a new partition for the 2nd operating system.

also you know while you are in linux you can access your data on the windows partition right?  :)

---

### Post by bumanie on 2008-10-24
The potential problem you will have is that windows does not like booting from a secondary hard drive. Also there will be no grub reference on the windows drive. It is preferable to have windows installed on the first hard drive and ubuntu installed on the other hard drive, installing ubuntu after windows. You will have to edit your /boot/grub/menu.lst and to add windows to it and probably also use a map command on the /boot/grub/menu.lst which might trick grub into booting windows once you have added windows to the list. You will also have to reinstall grub via the live cd after that. I fear you may have issues that you will give you headaches unless you install windows first. Any way you can try and post back if you have problems. Good luck. It is not impossible doing it the way you plan to, but it is usually more difficult.

---

### Post by starcannon on 2008-10-24
And for the love of the holy data on your windows drive, back it up before you do any installing of other operating systems, partitioning, formatting, or any other thing that a "woops" moment could destroy.

Recovering data is possible, but its painful, scary, tedious, and limited in its results. Back up your data before doing anything on the order of setting up a dual boot system. Search the forums for things like "ubuntu destroyed my files" and variations on the search term and read a long list of wont and woe at those who didn't back up data, then clicked along without reading each and every screen with comprehension. Ubuntu installs won't do anything that they are not told to do, but mistakes happen, don't let a mistake lead to a life of binge drinking. Back up your data.

Okay ```
Option     "BackupSermon"     "Off"
```GL and above all have fun.

---

