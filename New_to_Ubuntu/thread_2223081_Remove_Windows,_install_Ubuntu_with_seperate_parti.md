---
title: "Remove Windows, install Ubuntu with seperate partitions for root, swap and home"
date: 2014-05-09
forum: New to Ubuntu
---

### Post by Misconstruction on 2014-05-09
I'm reviving an old laptop, that can barely run Ubuntu or Windows 7, by installing Lubuntu. 

Currently it has Windows 7 installed. I have already run Lubuntu 14.04 from a USB stick and everything works out of the box.

Is there a guide around for doing the following:
1) Erase Windows are reformat entire harddrive
2) Install Lubuntu 14.04 with seperate partitions for root, home and swap?

thanks i advance for any help!

---

### Post by BBQdave on 2014-05-09
> **Misconstruction said:**
> 1) Erase Windows are reformat entire harddrive
2) Install Lubuntu 14.04 with seperate partitions for root, home and swap?

The Ubuntu installer (Lubuntu) will automatically wipe HD and set correct partitions, if you choose that :)

Or if you want your own custom partition scheme, you can choose that too.

---

### Post by Misconstruction on 2014-05-09
Thank you for your response!

So using the remove windows option will allow me to specify a partition scheme - or does it simply create three seperate partions for root, swap and home?

---

### Post by jdeca57 on 2014-05-09
> **BBQdave said:**
> 
Or if you want your own custom partition scheme, you can choose that too.

It's strange that using an entire disk means exactly that: one partition and one swap. Of course, the advantage is that you don't have to worry about the size to allocate to home and root. But if you want to reinstall a separate home is a luxury. That doesn't mean you can forget  to back-up, of course.
Anyhow,
[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu#Advanced_partitioning](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu#Advanced_partitioning)
is more or less what you can expect.

---

### Post by Rex Bouwense on 2014-05-09
You can have only four primary partitions and you are going to only put one OS on your computer. You could let the installer format and partition for you and you will end up with two,   / and swap,   but as jdeca57 has stated it will not have a separate   /home.  (That is where all of your stuff is stored).  As he stated it is a luxuary if you want to re-install.  However, since every good Linux user will tell you to back up your data          (/home/user), before you upgrade, I believe a separate /home becomes unnecessary.  Others swear by it.  It is just a matter of preference.  If you want a separate /home, then you will need three partitions.  You must choose "do something else" when installing and then size them yourself.

---

### Post by cmcanulty on 2014-05-09
I prefer to select something else and put 20GB in / (plenty of space for tons of apps), /home with rest except for leaving enough for a 3rd swap partition at least as lg as your ram so you can hibernate. Ex with my 4 GB ram on a 500GB drive I have /ext4 20GB, /home 475GB ext4, linux swap 5gb. if your hd is small make / less large

---

### Post by pfeiffep on 2014-05-09
> **Misconstruction said:**
> Thank you for your response!

So using the remove windows option will allow me to specify a partition scheme - or does it simply create three seperate partions for root, swap and home?You should select something else in order to designate your own partition sizes

---

