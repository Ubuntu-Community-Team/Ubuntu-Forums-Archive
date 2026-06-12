---
title: "ubuntu/vista"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by omes on 2008-05-12
i have ended with ubuntu as the sole os and i want to download vista next to it can someone tell me how?

---

### Post by tamoneya on 2008-05-12
you need to buy vista and get the disk. Then the installation is very similar to how ubuntu worked however you first need to free up some partition space.  The best way to do this is by putting in the ubuntu install disk (hard drives will not get mounted) and then run ```
sudo gparted
```Then shrink the ext3 partition so that you have as much space as you like for windows.  Then you can reboot and put the windows disk in.  Tell it to use the remaining space for windows.  

This installs windows but will mess with the MBR and linux will no longer be bootable.  The simplest way to solve this is to use supergrub and reinstall grub into you MBR.  This will detect both windows and ubuntu and make them both bootable.

---

### Post by amaroKer on 2008-05-12
Uhhh, Vista is available from any major computer retailer.  You're not gonna find a (legal) download for it.  I don't think it'll cost too much...

If your computer didn't come with Vista, I'd make sure that you have pretty good specs on your machine before purchasing it, or risk being VERY disappointed.

---

### Post by omes on 2008-05-12
hi there i am new to ubuntu and new to the net first time posting anything...
the other day i install ubuntu and made an erorr ended losing all my data and my old os as there a way to ritrive it or at list to instal vista next to ubuntu

---

### Post by tamoneya on 2008-05-12
you will get a better response from the forum if you keep your question on one thread.

---

### Post by Inxsible on 2008-05-12
If you wrote over the old install, it will be extremely difficult to get the data back.

You can however use the following links to install a dual boot of Vista and Ubuntu. You will need the Vista install CD and it is recommended to install Vista before you install Ubuntu. Once you have done that use these guides for a dual boot.

[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")    [Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by zenwalker on 2008-05-12
Yes, Vista needs a much higher machine req than what Gnu/Linux (Ubuntu in this case) needs to do same kinda operations. So make sure u meet vista req before buying it.

---

### Post by ugm6hr on 2008-05-12
> **omes said:**
> i have ended with ubuntu as the sole os and i want to download vista next to it can someone tell me how?

Can you confirm whether you have a Vista CD / reinstallation CD to use?

If not, this question is obviously going to lead nowhere.

If Vista came on your HD, and you didn't receive a reinstallation CD, you may have a recovery partition.

Post the output from:```
sudo fdisk -l
```

---

