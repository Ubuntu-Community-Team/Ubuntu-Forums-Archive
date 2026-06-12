---
title: "Need to unpartition my machine, keep linux"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Spoken on 2008-09-28
Right now my computer is dual booted with Vista and Ubuntu, and for reasons not needed to be spoken of, i need to remove vista and give ubuntu the entire hard drive.  what steps are needed to take?

---

### Post by Elfy on 2008-09-28
It would help to have a bit more informationfor more specific answers, but generally - boot the livecd, delete the vista partition and resize the ubuntu partition.

IF you want a more specific answer please run

```
sudo fdisk -l
df -h
```

---

### Post by bumanie on 2008-09-28
There will be various ways of doing this. If I were you, I'd use gparted to delete the vista partition and then if you wish, you can resize (extend) the ubuntu partition. You will probably have to reinstall grub, otherwise you will likely get a grub error of some kind (probably grub error 22). As long as you reinstall grub, ubuntu should work as before.

---

### Post by kansasnoob on 2008-09-28
I would think you could just boot any Ubuntu Live CD (choose try without changes to computer from the boot menu), then once you're in the live desktop go to System > Administration > Partition Editor (that's Gparted):

[ATTACH]86672[/ATTACH]

You see I've right clicked my windows partition and I could just select to delete it. Then I'd be able to resize all my other partitions.

If you want more detailed instructions I'd recommend posting a screenshot of your gparted. You could do that before booting into the Live CD but you'll probably need to install gparted:

```
sudo apt-get install gparted
```

Just be aware that you can't complete the repartitioning process without being booted into the Live CD.

And we should know if you're using the grub bootloader and if Ubuntu is the default boot.

---

### Post by Excalibre on 2008-09-29
> **bumanie said:**
> There will be various ways of doing this. If I were you, I'd use gparted to delete the vista partition and then if you wish, you can resize (extend) the ubuntu partition. You will probably have to reinstall grub, otherwise you will likely get a grub error of some kind (probably grub error 22). As long as you reinstall grub, ubuntu should work as before.
Correct me if I'm wrong, but won't this also change the drive numbering (i.e. if Ubuntu's partition was sda2 before, it's sda1 now) so won't /etc/fstab at least also need to change?

---

### Post by bumanie on 2008-09-29
As far as I know, reinstalling grub will be reflected in /etc/fstab.

---

### Post by Excalibre on 2008-09-29
> **bumanie said:**
> As far as I know, reinstalling grub will be reflected in /etc/fstab.
You think that reinstalling Grub will automatically make the necessary changes in /etc/fstab? It didn't for me. I did a much more wide-ranging screwing-around with my partition tables, and maybe that's why I had more trouble, but I had to do a lot more stuff to clean up afterwards.

---

