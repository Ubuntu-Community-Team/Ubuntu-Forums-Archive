---
title: "Install windows XP after Ubuntu (without lose ubuntu)"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by betoe on 2008-07-14
Hi to all you

This is my first post on this forum. I have already searched about this topic but didn't find something helpful.

I have installed ubuntu on my laptop. I have free space ready to do partitions and install win XP. I really need XP because i need some software for school like matlab and labview. And vista was a big thrash.

I will format the free space as fat32 in order to write/read it from ubuntu. But i think that when i finished my xp installation, MBR will be overwrited and grub will not load my ubuntu installation; I had win vista until yesterday, right now im using grub to choose the ubuntu installation.

How can i avoid to damage MBR (If possible)? or how i must restore grub to load XP and ubuntu?


Greetings

---

### Post by overdrank on 2008-07-14
> **betoe said:**
> Hi to all you

This is my first post on this forum. I have already searched about this topic but didn't find something helpful.

I have installed ubuntu on my laptop. I have free space ready to do partitions and install win XP. I really need XP because i need some software for school like matlab and labview. And vista was a big thrash.

I will format the free space as fat32 in order to write/read it from ubuntu. But i think that when i finished my xp installation, MBR will be overwrited and grub will not load my ubuntu installation; I had win vista until yesterday, right now im using grub to choose the ubuntu installation.

How can i avoid to damage MBR (If possible)? or how i must restore grub to load XP and ubuntu?


Greetings
HI and welcome
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Also have you thought of using a virtual machine.

---

### Post by balaknair on 2008-07-14
The page Overdrank linked to above should be able to help you recovering your Ubuntu grub(it's pretty comprehensive with a great many options). 
I would however suggest you format your Windows partition as NTFS instead of FAT32. All the newer versions of Ubuntu can read/write to NTFS quite well, and NTFS is better than FAT32 in that it is more stable, offers more file permissions settings and also resists fragmentation better. Performance is also supposed to be better. If you have trouble with NTFS in Ubuntu(if you're using an older version of Ubuntu) just install ntfs-3g(sudo apt-get install ntfs-3g). You can also install fs-driver in Windows to be able to access the Ubuntu ext partitions from Windows.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

So what I use(my personal choice) on my laptop 120GB drive
NTFS partition- Windows XP(15 GB)
NTFS partition- A bunch of Windows programs and games(mainly games)(25 GB)
Ext3fs partition- Ubuntu mount point / (15 GB)
Linux Swap- 3 GB
Ext3fs partition- /home folder and shared stuff (rest of the drive space)


This is just my personal preference, of course your tastes may differ.

And as Overdrank suggests you can also try using a virtual machine, though they have their limitations. I'd recommend Virtualbox. You can install it from the repositories(Open Source Edition), or you can download the .deb binaries from the second link below(closed source version with USB support).
 [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) 
 [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by betoe on 2008-07-15
Thanks by your answers and the welcome. Good links, its what i need.

So i will install XP on NTFS partition, i will do it some minutes more.

About emulate win programs, i want to do it soon but i cant get the risk of have only ubuntu because this laptop is just for school and i need to do some programming. I will try Virtualbox on the weekend.


Greetings and i will post in the next days my advances.

---

### Post by betoe on 2008-07-18
Problem solved 2 days ago, thank you!

Now i will start to learn about ubuntu, hope i can adapt it to use it for school too.


Greetings

---

