---
title: "Newb with installation question"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by gars943 on 2012-02-15
After searching and even using the " " marks around query, still can't find the information I'm looking for, so if someone could point me in the right direction, I'd appreciate the help.
When installing Ubuntu in Windows 7, a window pops up during installation saying that "no os was detected on this drive if you allow, all files will be lost" or something similar to that. My question is, will the files in Windows 7 be lost or just the ones in the virtual drive? I should add that I'm trying to run Ubuntu parallel with my Windows 7 os using "Virtualbox". I hope this isn't to confusing to understand.
I'm on a Dell laptop Intel Core 2Duo CPU T6500 @ 2.10GHz
4.oo RAM
64-Bit Operationg system 
Thanks,
Gary

---

### Post by winh8r on 2012-02-15
have a read through this and if you need any more assistance, just ask


[http://www.psychocats.net/ubuntu/virtualbox]("http://www.psychocats.net/ubuntu/virtualbox")


EDIT** with regard to the installation of ubuntu, it is perfectly safe to install it in the virtual box drive, as this is literally a "virtual filesystem" and is not a "real" part of your Windows drive.
Ubuntu will always tell you if there is something else on the drive it is about to partition and will not overwrite a wWindows installation unless you explicitly tell it to do so.

It is always advisable to have your data backed up anyway whatever you are doing on any OS.

---

### Post by Simple Name on 2012-02-15
It is more than safe to proceed - virtual hard disk is not a real partition and therefore can not damage your operating system.

---

### Post by 3rdalbum on 2012-02-15
Perfectly safe as the others have mentioned. Notice that your hard disk is listed in Ubuntu by the size of the virtual disk, not by the size of the actual physical disk. Also, Ubuntu lists the manufacturer as "Virtualbox", not as the physical disk's manufacturer.

So yes, what you describe is normal and you will not lose data on your real hard disk. Guest operating systems are stuck inside their virtual hard disk.

---

