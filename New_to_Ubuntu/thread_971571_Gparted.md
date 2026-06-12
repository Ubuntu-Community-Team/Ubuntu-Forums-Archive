---
title: "Gparted"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-11-05
i've installed Partition Editor. when running it, it can't displays my harddisk partitions. it shows unallocated.

my hdd is partitioned in three. 1 partition is ntfs, 1 is for swap, and the 3rd one contain ubuntu OS.

why is it so? 

plus is there a way for me to access partition editor from grub?

---

### Post by Separ on 2008-11-05
Could you try posting the output of ```
sudo fdisk -l
```
Also, are you running the partition editor as root?

---

### Post by mapes12 on 2008-11-05
In my experience the best way to run GParted is from a live cd which can be burnt from here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Running the application whilst inside Linux can cause problems because the HDD is not only running the application but also the OS. The live CD just loads in the application with minimal Linux Kernel into memory freeing up the partions to work on them.

BTW good practice is alway to keep /home on a seperate partion. See here:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Doing this enables you to mess around with different versions of Ubuntu in the /(root) partition without screwing up your files, personal settings, bookmarks and the rest.

---

### Post by RajaAjmal on 2008-11-05
thanks for our reply Separ.
Right now i'm not using my computer. when reaching home i'll tr the 'sudo fdisk -l'

how to run the partition editor as root? 

i've 2 hdd in my pc. my pc boot from the hdd which contain ubuntu. when running partition editor i can view + make modification to the 2nd hdd, but not with the one consisting the ubuntu.

---

### Post by Separ on 2008-11-05
You can run it as root by hitting alt+f2 and typing ```
gksudo gparted
```

---

### Post by RajaAjmal on 2008-11-05
thanks for ur advice mapes12

---

### Post by RajaAjmal on 2008-11-05
i'll try the 'gksudo gparted' n let u know

---

