---
title: "Different swap partition for a different distro on a different partition?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Brushstroke on 2011-10-15
Quick question. If I were to install another Ubuntu version alongside the one I already have or another distro alongside the one I already have, would that partition needs its own swap partition or would just one swap be used for all Linux partitions on the drive?

---

### Post by wildmanne39 on 2011-10-15
Hi, you can set it to use the same swap from what I have read but I have never done it myself.
Thank you

---

### Post by Brushstroke on 2011-10-15
Wait, so I have to set it to do this? How do I go about that?

---

### Post by wildmanne39 on 2011-10-15
Hi,
> use the same swap from what I have read but I have never done it myself.

I believe when you manually set up your partitions you can tell it to use the same swap but I am not sure that is the method used, I googled it but I did not find the answer.
Thank you

---

### Post by mcduck on 2011-10-15
Different distros can share the same swap without any problems, only limitation being that you can't hibernate one distro and boot to another, as hibernation stores the data from memory into swap.

Setting it up is easy, just use the manual partitioning during the install and set your current swap partition's mount point as swap.

Edit: actually, you probably don't have to do anything... I just realized that when I made a fresh install of 11.10 yesterday I only defined my root and storage partitions and did nothing for the swap partition that I had on my hard drive. It seems that Ubuntu's installer automatically detected the existing swap partition and used it. The installer is clearly smarter than I am... :D

---

### Post by wildmanne39 on 2011-10-15
Hi, thank you mcduck for helping us out there, that is what I thought but I am glad someone confirmed it for the OP.

---

