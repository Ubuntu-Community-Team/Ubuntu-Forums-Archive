---
title: "Installing Ubuntu on a Windows 7 laptop"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by jirico on 2012-05-23
I'm searching for the best way to install Ubuntu on my laptop. I saw that wubi is a very pratical way but since it's for work perfomance will be important.

I have a i7QM 8gb Ram laptop, do u guys think it's better to install Ubuntu on its own partition or I will not feel any perfomance difference if I use Wubi??

In the second case I will have to resize my Windows 7 partition to make space for Ubuntu,  I think it's dangerous because I never did that before, I appreciate any help,thanks.

---

### Post by dolphin194 on 2012-05-23
It is best to install Ubuntu on its own partition, however Wubi is not all that slow. It really depends on what you are doing.
[B]
The only fear of a resize operation you should have is [/B] ***power failure*.** The only thing that can cause trouble while resizing your partition is if your computer turns off. As long as your computer doesn't turn off, you should be fine. Since you are on a laptop, you shouldn't have to worry about this. Keep your computer on AC power during the resize operation. Most of the time the resize operation is smooth.

_**So here's what I would do:**_
**1.** Defragment your Windows partition.
**2.** Run chkdisk on your windows partition to make sure there are no errors
**3.** Boot from the Ubuntu install CD/USB and resize your partition, and install!

---

### Post by wilee-nilee on 2012-05-23
Windows 7 has a virtual partitioner called disk manager I believe use it to resize any windows partitions. Many windows installs come with the max amount of partitions 4 primaries on a single HD, to begin with as well, so this may mean a partition removal, and adding a extended for the Ubuntu and the swap.

Best thing you can do before anything is to backup the windows set up off the computer, even if you have a recovery partition and have a recovery or install discs in your tools set.

You might consider a wubi to begin with to make sure you like Ubuntu if you are not familiar with it. This will allow you time to decide and get updated on the partitioning needed, and the wubi can be moved to a partition in the end. There is a thread on the forums for moving that wubi to a partition as well.

---

### Post by nipunshakya on 2012-05-23
> **jirico said:**
> I'm searching for the best way to install Ubuntu on my laptop. I saw that wubi is a very pratical way but since it's for work perfomance will be important.

I have a i7QM 8gb Ram laptop, do u guys think it's better to install Ubuntu on its own partition or I will not feel any perfomance difference if I use Wubi??

In the second case I will have to resize my Windows 7 partition to make space for Ubuntu,  I think it's dangerous because I never did that before, I appreciate any help,thanks.

I think its better to have a separate dedicated partition for ubuntu. Just remember that **windows is always installed in primary partitions while ubuntu can be installed in extended partitions.** 

You can have only 4 primary partitions **or **you can have 3 primary and 1 extended(logical) partition.

Talking about resizing, u can always shrink and extend volumes in windows 7 using the **disk manager **and resizing your partitions. But remember, **always restart your machine after you have made changes to the partitions. **This will ensure that your drives are error free. (Simple and easy step.)

For dual boot guide, you can see the follwing links as well:
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Hope they help you out....

Happy Linuxing.

---

### Post by jirico on 2012-05-23
Thanks guys, I made my decision and I will install Ubuntu on the weekend. Your answers were(and will be) very useful.

---

### Post by MadmanRB on 2012-05-23
For a beginner you may want to try WUBI first as it will work like a windows install of a program instead of its own OS that would be a bit harder to remove later on.
WUBI is not the ideal choice but it is a good option if you dont feel that you can safely dualboot with little experience.

---

### Post by jirico on 2012-05-23
Thanks for the reply Madman. I already have Ubuntu on my desktop, but now I want to put on my laptop that is faster. The more perfomance I have the soon I finish my work, so I think I have no choice but to try it. I will be very careful and if I need help I know where to ask :)

---

### Post by MadmanRB on 2012-05-23
Well glad your install went well, I know what its like being a beginner so I am willing to aid.

---

### Post by nipunshakya on 2012-05-23
Glad to be at your service.

Happy Linuxing. :D

---

