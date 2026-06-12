---
title: "GParted"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2014-07-31
Hi all,

I can cope with most things on my PC, but one thing I just can not do is partition a disk, I break out into a cold sweat just thinking about it, so I really need help !!!

At the moment I dual boot, Mint17 and Ubuntu 12.04, what I would like to do is remove Ubuntu and replace it without doing anything to Mint17, is this possible, if so how do I go about it.

Regards Bob

---

### Post by yancek on 2014-07-31
Boot into Ubuntu and run the df -h command shown below.  In the example below, it shows the root of the filesystem as sda5.  When you do this from Ubuntu, it will show which partition is the / partition and you can then select to format it and use it for data.

>  df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        19G   16G  2.4G  88% /


---

### Post by whitesmith on 2014-07-31
But now the OP has to deal with formatting. By far the easiest solution is to boot the gparted CD, select the Ubuntu partition and press the Del key. Then just complete the action and Ubuntu will be gone without harming Mint.

---

### Post by Impavidus on 2014-07-31
One thing though: before deleting the Ubuntu partition, make sure mint is in control of the boot process, or your computer will become unbootable (although that's easily fixed with boot-repair). To do so, reinstall grub from mint:```
sudo grub-install /dev/sda
```Assuming that's your drive. And assuming mint does it the same way as Ubuntu, but it ought to.

After removing Ubuntu, update grub from mint to remove Ubuntu from the grub menu:```
sudo update-grub
```

---

### Post by yancek on 2014-07-31
> But now the OP has to deal with formatting. By far the easiest solution  is to boot the gparted CD, select the Ubuntu partition and press the Del  key.

That would be swell if he knew which partition had Ubuntu on it but since he gave no indication that he did, the reason for my suggestion.  He can delete or format it during installation but he needs to know which partition.

---

### Post by UltimateCat on 2014-08-01
> **whitesmith said:**
> But now the OP has to deal with formatting. By far the easiest solution is to boot the gparted CD, select the Ubuntu partition and press the Del key. Then just complete the action and Ubuntu will be gone without harming Mint.

Agreed:-

Or use the new distro's partition manager to delete it and than proceed to the fresh install.

---

### Post by robert1305-gmail on 2014-08-01
Thanks for all the info guys, I must admit I was all for wiping everything and starting again, but I thought if I am going to do that I might as well bugger everything up by trying to use GP, so I did..........

I found out which partion Ubuntu was on highlighted it and then closed my eyes and clicked delete, opened them and it was just a blank partition, I then installed the new distro along side of Mint and everything works fine.

Thanks again Bob

---

### Post by sandyd on 2014-08-01
Hi, if you have found a solution, please mark this thread as solved via Thread Tools -> Mark Thread as Solved

Thanks!

---

