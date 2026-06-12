---
title: "folder redirect help"
date: 2020-03-12
forum: New to Ubuntu
---

### Post by zelandroid009 on 2020-03-12
Hi. I installed Ubunto 18.04 LTS this morning. In preparation of this I created a separate partition and copied to it all of my Documents, Downloads, Pictures, Videos and Music to be shared between Windows and Ubuntu. The partition is called Home. Following instructions on How-To Geek I was able to mount this partition as /media/storage and it appears on my Ubuntu desktop. I then followed those same instruction to access the user-dirs.dirs file in the .config folder and changed setting for my Documents, Downloads, Pictures, Music and Video links point them to /media/storage/...After saving the changes I rebooted the system.

However, when I click on Documents I am not taken to the folder with that name on /media/storage.

What have I done wrong?

Please help

John

---

### Post by deadflowr on 2020-03-12
It helps to know what guide you followed.

---

### Post by zelandroid009 on 2020-03-12
> **deadflowr said:**
> It helps to know what guide you followed.


This guide. It's for Ubuntu and Win 7 but it seemed straight forward.

[https://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](https://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by oldfred on 2020-03-12
I prefer links.
And I mount my data partition(s) in /mnt not /media, so not shown in Nautilus. You could just mount in / (root) also.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)


If still issues post details.
mount
cat /etc/fstab
cat .config/user-dirs.dirs

---

### Post by zelandroid009 on 2020-03-12
Than you. I appreciate your kind assistance. I'll post a follow-up with my results

---

### Post by TheFu on 2020-03-12
Put those settings back they way they were, change the directories in the user's HOME to point to the /media/ .... locations using symbolic links.  I hope you don't care anything about security, since vFAT and NTFS provide none.

BTW, labeling a non-Linux disk as "home", "Home", "HOME" or any other combination is a poor choice and will cause confusion when you understand more.

---

