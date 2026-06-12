---
title: "[SOLVED] USB drive size reduced after trying to install Ubuntu Hardy"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Google Spider on 2008-06-30
Hi, I was trying to install Ubuntu Hardy on my 4 GB USB drive using [[COLOR="Red"]this guide[/COLOR]]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") and screwed it. :(

While installing I made two partitions exactly as suggested in that guide. I was not able to boot with the pendrive however, as it froze at the Ubuntu splash screen. So I booted into Mint(my primary os) and deleted the two partitions and made a new one with starting cylinder 1 (default) and end cylinder 3841 (deault).

But now the drive properties say its only a 715 MB volume :confused:

Here is a screenshot


[http://i32.tinypic.com/2yzeihs.png](http://i32.tinypic.com/2yzeihs.png)

I will appreciate all the help. Thanks.

---

### Post by aquavitae on 2008-07-03
I don't know the exact answer to your problem, but there are a couple of notes:

There is also a discrepancy between file system types; fdisk shows /dev/sdb1 to be linux, and the properties window shows it as msdos. Are you sure they do actually refer to the same device?  Could you post the output of ```
sudo fdisk -l
``` so we can see all the drives?

Slightly off-topic, I notice you used "sudo su" followed by "fdisk /dev/sdb". sudo su is not recommended by ubuntu for security reasons (there are plenty of blogs, wikis and, um... arguments about this all over the web if you're interested in the reasons for this). For a simple command like that, its better to just prefix it with sudo:
```
sudo fdisk /dev/sdb
```
If you have a lot of commands to run as root and need to log into a root shell (which is what you did with sudo su), its preferable to use "sudo -i".

---

### Post by Google Spider on 2008-07-03
Hey thanks for the reply. Where did you dig up this thread from? I should have marked this thread as solved. I already fixed it using Gparted. :)

---

### Post by aquavitae on 2008-07-03
Only two days old... :) I was looking through oldish posts that hadn't been answered. I know how irritating it can be not getting a reply to a problem. Glad you're sorted out.

---

