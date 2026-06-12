---
title: "[SOLVED] Dual boot with XP question"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by spocksbeard on 2008-10-11
Hi, I previously had Ubuntu setup using Wubi and decided that I liked it and would like to have it permanentaly dual-booting on my laptop with XP.

I have found a guide [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1") that shows installation of Ubuntu alongside XP without having to re-install XP, and creating a shared partition which both OSes can access. 

I would like to know if I can use ntfs for the shared partition as I read somewhere that Hardy can read and write to ntfs by default, and fat32 has issues with some of my DVD iso files. 

Also, just to double check, would I need the system rescue CD the guide mentioned aswell as the Hardy Live CD (which I already have waiting to burn to disc).

Finally, what size partitions would you recommend for the XP and Ubuntu partitions? My total HDD size is 106GB.

Thanks in Advance

---

### Post by ashmew2 on 2008-10-11
I think that guide is okay...

You have a 106 GB HD...How about ..

10 GB = XP 
10 GB = Ubuntu root
10 GB = /home
Max 2 GB = Swap
74 GB for storage ( You can easily partition according to your needs)

This is just my opinion...You can do what you want with the partition table :)

Plus..Whenever ive installed Ubuntu..I didnt really have a Rescue Disc on me..But its better to be safe than sorry...Always backup Valuable Data and Rescue CD could come in handy....

Be sure to check the md5sum of the .iso of Hardy you may be having..Also check the Integrity of the CD after burning... :)

NTFS wont hurt as the filesystem..But if you are planning on Using Linux heavily and keeping XP to a minimum like Yahoo Messenger and stuff...You can consider Ext3 also..

---

### Post by bumanie on 2008-10-11
> I previously had Ubuntu setup using Wubi and decided that I liked it and would like to have it permanentaly dual-booting on my laptop with XP.There is a way to change a wubi installation to its own partition - unfortunately, I'm at work and can't remember the link.
> I would like to know if I can use ntfs for the shared partition as I read somewhere that Hardy can read and write to ntfs by default, and fat32 has issues with some of my DVD iso files. Ubuntu 8.04 definitely does have read/write ability to ntfs, which is very stable - you don't need a FAT32 share.

---

### Post by spocksbeard on 2008-10-11
> **ashmew2 said:**
> 
Be sure to check the md5sum of the .iso of Hardy you may be having.


Sorry to sound stupid but how would I do this?

---

### Post by bodhi.zazen on 2008-10-11
> **bumanie said:**
> There is a way to change a wubi installation to its own partition - unfortunately, I'm at work and can't remember the link.


[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

To be honest, I would advise you wait a short time and install 8.10 (the standard way) when it is released.

---

### Post by bodhi.zazen on 2008-10-11
> **spocksbeard said:**
> Sorry to sound stupid but how would I do this?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by spocksbeard on 2008-10-11
Thanks for all the help! I shall have to do a bit more reading methinks

---

