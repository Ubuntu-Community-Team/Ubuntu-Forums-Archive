---
title: "Reading ext3 from network on windows"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by impaler on 2008-06-16
Hello I am wanting to access a folder from a ubuntu machine that has the ext3 format, will I be able to access it from a windows machine on the same network?

I saw these programs to read ext3 partitions from windows on the local machine;
[http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows")

Does anyone have any advice or guides I cant seem to find any. I will give it a go soon and see how it goes, it may just work. I would just like to know about what is going on more.

---

### Post by Cadmus on 2008-06-16
You need to share the folder (like a windows shared folder) there's wizards and the like in Ubuntu. But first take a quick read around of the program that shares from linux to windows, Samba.

---

### Post by drs305 on 2008-06-16
Added: Posts are correct that this is not necessary for network use. Time to wake up with some coffee.

There is a freeware app named ext2fs which will allow you to view ext2/ext2 linux partitions from windows. Here is a link:
[Ext2 Installable File System For Windows]("http://www.fs-driver.org/index.html")

Once you have read about it you can click on the "Download" tab at the top of the page to get the freeware.

Added: Posts are correct that this is not necessary for network use.

---

### Post by AndyCooll on 2008-06-16
Yes, you'll be able to share files and folders across your network

Cadmus points you in the generally accepted way to go ...Samba. 

Here are a couple of starting points:
[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")
[ HowTo: Easiest way to share files & printers with Windows]("http://ubuntuforums.org/showthread.php?t=806699")

:cool:

---

### Post by ChameleonDave on 2008-06-16
You can install ext3 drivers on Windows, but I don't actually think they are necessary over a network.

---

