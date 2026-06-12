---
title: "opening windows files in ubuntu"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by ignorant fool on 2008-06-21
I have a problem.
i don't want to completely move to Ubuntu. i want to use it next to windows vista. which means I will sometimes use vista and sometimes use Ubuntu. so i want to access files from vista. word documents especialy, and i use open office in vista too, although i save them as word 2003 files to be compatable on other computers (does this matter??). so i don't want to copy them, because then if i make changes in ubuntu they wont be changed in vista, and it takes more disk space, which i dont have enough of.
is this possible?

---

### Post by akiratheoni on 2008-06-21
What's your question? Ubuntu can read NTFS partitions so if you open your Word documents from the Vista partition in Ubuntu and edit it and save it, Vista should still be able to open your modified version fine.

---

### Post by ignorant fool on 2008-06-21
i dont know what u mean. i dont know about partitions. and i tried to open my vista map but it said that i cant acces the acer something.

---

### Post by gianluca.colucci on 2008-06-21
Hi there,

yes, it is possible.

First of all, you need to create a dual boot system, you have to install first Windows Vista and after Ubuntu. The two systems will be installed in two different partitions on your harddisk. 

There are few ways to read a ext2/ext3 partition from Windows. 
I would suggest you to do some search in Google and to have a look at this website: [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html")

From the other way around, Linux supports Windows partitions (fat16, fat32, etc.), so with a mount you should be able to access your "Microsoft" partition from Linux.

I have just found this other article:
[Share Partitions Between Linux and Windows HOWTO]("http://www.geocities.com/epark/linux/partition-share-HOWTO.html")

Informations are not always up to date and/or related to Ubuntu Linux, but there is a lot to read, which can be, at the very least, of some help.

Cheers,
Gianluca

---

### Post by housam on 2008-06-21
Here is how to make a dual boot windows / ubuntu : [[COLOR="Red"]_http://www.psychocats.net/ubuntu/installing_[/COLOR]]("http://www.psychocats.net/ubuntu/installing")

---

