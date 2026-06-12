---
title: "Cannot boot into main HDD"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by KyleRickards on 2012-02-05
Hi all

I know there are many threads about this but I cannot get any solution to work.

I have a laptop which dual boots XP and Ubuntu 11.10.  However I switched it on before and only got a Grub Rescue prompt. After fiddling and thinking I was reinstalling Grub, I now just have a Grub prompt and can't do anything.

I don't have a live CD with me at the moment but do have an external drive which I can boot with (also with Ubuntu 11.10 on it). Can I fix things by using my external drive to get an OS or do I need a live disk?

Sorry for length of question!

K.

PS) I have also run the boot script.sh file and got the results of that if it helps?

---

### Post by wolfen69 on 2012-02-05
[This]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") may help. I believe you can use the external drive to restore grub.

---

### Post by KyleRickards on 2012-02-05
Thanks Wolfen, I tried Boot Repair but it seems to keep wanting to fix SDC (which is my external drive) rather than SDA which is where my dual boot is...

---

### Post by Bodsda on 2012-02-05
Sure, the procedure for fixing a borked boot loader from a live cd is exactly the same as fixing one from another form of bootable media.

Theres loads of info about this kinda thing.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If Boot Repair didnt work, then just use the terminal way on that link (Ignore the fact it assumed youve booted from cd, the procedure is identical)

Hope this helps,
Bodsda

---

### Post by KyleRickards on 2012-02-05
Thanks Bodsda, I have have messed something up big time as when I get into the partition where the OS was, it's empty (using file manager on my external drive). I will just reinstall when I get chance with another CD, luckily I had no data to keep on the installation.

Many thanks
Kyle

---

