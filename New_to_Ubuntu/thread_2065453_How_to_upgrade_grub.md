---
title: "How to upgrade grub"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by tumerictj on 2012-10-01
Hey all---

I'm using Ubuntu 12.04 as the sole OS on my old dell laptop.  Things are generally working well, but today during while installing the daily updates, I got a message about upgrading the bootloading package grub-pc.  Here is the gist of it:

I must choose a drive for which I'd like grub-install to be automatically run for.  There is a note that if I'm not sure what drive is designated as boot drive by my BIOS, it might be a good idea to install grub to all of them.

On the other hand, it claims that some partition boot records are listed as well, and it is generally not a good idea to install grub here.

My options are (1) /dev/sda, (2) -/dev/sda1.  

After a bit of research, I tried to select only option (1).  Then I got a message saying I hadn't selected any drives.  

Thanks in advance for any advice,

TJJ

---

### Post by Hadaka on 2012-10-01
Hi, this should help
[http://ubuntuforums.org/showthread.php?t=1972331](http://ubuntuforums.org/showthread.php?t=1972331)

#read post 5 and 6

---

### Post by oldfred on 2012-10-02
Space-bar to select?

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Bashing-om on 2012-10-02
tumerictj; Hi ! welcome to the forum.

On today's grub update, I did not get any dialog; It just updated.
To address your issue: terminal commands:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub

``` Will out put grub's location on your system.
I show on my system version 1.99-21ubuntu.34 (latest version).

In the event you require to update grub I suggest the following.
```
sudo update-grub
``` just to ensure all is kosher at this point.
then update your packages; from terminal:
```
sudo apt-get update
sudo apt-get upgrade
```I expect this to be all that will be required.
[INDENT]kind regards <==BDQ

[/INDENT]

---

