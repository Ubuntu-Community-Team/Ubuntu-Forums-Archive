---
title: "Should I have wubi install to a separate drive?"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by acidqueen on 2013-02-24
All,

I'm posting from work, so I'm not in front of my home PC right now--but I do have a wubi question (since I'm about to try using wubi to install Ubuntu on a computer here at work (that computer has no optical drive and I have no thumb drive to hand, thus the need for wubi), and depending on outcome I'll try it at home):

Specifically, should I devote a separate drive to Ubuntu, or should I just go ahead and let wubi to install it to its own partition on the system drive?

Thanks in advance :D

---

### Post by kartikrajkanna on 2013-02-24
If you REALLY want it right now, just install ubuntu with Wubi and migrate it to a new partition .....

[https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")

I don't fancy Wubi that much, because it messed up my laptop, so been having new specific partition for Ubuntu all along.

Hope I helped

---

### Post by acidqueen on 2013-02-24
> **kartikrajkanna said:**
> If you REALLY want it right now, just install ubuntu with Wubi and migrate it to a new partition .....

[https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")

I don't fancy Wubi that much, because it messed up my laptop, so been having new specific partition for Ubuntu all along.

Hope I helped

Right, but what I am asking is:

Should I let it make a partition on a drive that already has an OS on it?

OR

Should I take a drive that has nothing on it, and devote that drive solely to Ubuntu?

---

### Post by fantab on 2013-02-24
If you have two HDD, then I recommend that you install Ubuntu directly (Not Wubi) on a separate HDD. Assuming that the other OS is Windows, if you install ubuntu on a sparate HDD then you can have the Windows Boot-loader intact and the Ubuntu Boot-Loader, GRUB on its own HDD. If you want Ubuntu to be your default boot then just change default HDD order from the BIOS.

I would also recommend that you do the manual partitioning of your HDD, they way you like it, rater than using the installer to do the partitioning for you.

Use Gparted, which is there in your Ubuntu LiveCD/USB to do your partition ing.

Good Luck..

---

### Post by acidqueen on 2013-02-24
> **fantab said:**
> If you have two HDD, then I recommend that you install Ubuntu directly (Not Wubi) on a separate HDD. Assuming that the other OS is Windows, if you install ubuntu on a sparate HDD then you can have the Windows Boot-loader intact and the Ubuntu Boot-Loader, GRUB on its own HDD. If you want Ubuntu to be your default boot then just change default HDD order from the BIOS.

I would also recommend that you do the manual partitioning of your HDD, they way you like it, rater than using the installer to do the partitioning for you.

Use Gparted, which is there in your Ubuntu LiveCD/USB to do your partition ing.

Good Luck..

Right, I can do that for my home computer no problem. But as I have already said:

> [the work computer] has no optical drive and I have no thumb drive to hand, thus the need for wubi

But you did answer my question as to how to implement wubi on the work machine--again, because wubi is the ONLY way that I can implement Ubuntu on that computer.

Thanks.

---

### Post by fantab on 2013-02-24
Unless you are badly pressed for it, I will not recommend Wubi install. You can search this forum for more wubi related answers. **[Read More]("https://wiki.ubuntu.com/WubiGuide")**.

---

### Post by acidqueen on 2013-02-24
> **fantab said:**
> Unless you are badly pressed for it, I will not recommend Wubi install. You can search this forum for more wubi related answers. **[Read More]("https://wiki.ubuntu.com/WubiGuide")**.

Well yes, but again, wubi is my **only** alternative in this case.

---

### Post by Cheesemill on 2013-02-24
A Wubi installation doesn't need a separate drive or a separate partition, it just installs Ubuntu into a folder on whichever disk you point it at, usually just your current C: drive.

The whole point of Wubi is to give you a way to install Ubuntu without having to alter partitions.

---

### Post by acidqueen on 2013-02-24
> **Cheesemill said:**
> A Wubi installation doesn't need a separate drive or a separate partition, it just installs Ubuntu into a folder on whichever disk you point it at, usually just your current C: drive.

The whole point of Wubi is to give you a way to install Ubuntu without having to alter partitions.

That's cool--I wound up throwing it on a devoted drive anyway, just to make it easier for my co-workers that want to play with Ubuntu. :)

---

