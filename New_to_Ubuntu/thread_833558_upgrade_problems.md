---
title: "upgrade problems"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Bix in Austin on 2008-06-18
file:///home/administrator/Desktop/Screenshot-synaptic-1.png

I hope this comes out as an image of the error message that I got. I f it didn't show correctly here is the text of the error message:
E:/var/chache/apt/archeves/linux-image-2.6.24-19-generic-2/6/24-19.33-i386.deb: short read in buffer_copy (backend dpkg-during `./boot/vmlinuz-2.6.24-19-generic)
I received this while I was checking the error message that showed up when I put my cursor on the update icon. I went tho the package manager as directed and tried to reinstall the problem packages and kept getting the same message.
I tried to use sudo rm /var/cache/apt/archives/linux-image* and
sudo apt-get update then
sudo apt-get upgrade as I was instructed a few days ago with a problem with xulrunner install. That one worked but this time I get a long list of folders that can't be removed starting with Desktop. Is this going to happen every time I try to download the listed updates and upgrades. I am new to linux, I am running version 8.4 as my first install and this recurring problem is beyond my knowledge of Ubuntu Linux. When I tried to send an error report it did go through but gave me another error message.
How can I put these problems behind me and enjoy using Ubuntu Linux?

---

### Post by avtolle on 2008-06-18
Just wondering; is your /boot partition full? From terminal```
df -h
```post the results.

---

### Post by YaroMan86 on 2008-06-18
What I usually do is rewrite the next version on a DVD-RW and fresh install. Of course, it helps that I have a seperate home partition.

---

