---
title: "How can i dublicate my hd on another hd?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by chrisme on 2008-07-13
On my hd i had installed ubuntu 8.04 desktop and setup some other software. Yesterday i lost everything and now i am installing everything from the beginning. After i finished the installation I would like to make an exact copy of my hd (including operating system and all other installations) on another hd so i would have it as backup.
Can you please tell me how to do this?

---

### Post by cariboo on 2008-07-13
There are a couple of ways to do what you want.

1. use dd:

```
sudo dd if=<current hdd> of=<hdd.iso>
```

Where <current hdd> = you hard drive <hdd.iso> you can name the resulting .iso anything you want. For further info in a terminal look at:

```
man dd
```

2. Use partimage. Partimage uses a ncurses based gui and it is pretty self evident what you need. For more info install partimage-doc.

DD is already installed, and you install partimage using Add/Remove Programs or Synaptic Package Manager.

Jim

---

### Post by bumanie on 2008-07-13
There are a number of options. Ensure the receiving drive is of equal or greater capacity to the drive being copied.
1) Gparted live cd (or use gparted off ubuntu live cd) can copy whole hard drives/partitions giving an exact copy. 2) You could use dd commands such as dd if=/dev/sda of=/dev/sdb makes a direct 1:1 copy (substituting the correct hard drive designations) To check out about dd > man dd
There are others such as partimage, ghost4linux, clonezilla, but the top two are probably the easiset IMO. Up to you which one you use.

---

### Post by chrisme on 2008-07-18
Thanks guys

I used dd if=/dev/sda of=/dev/sdb as bumanie wrote. It was very simple but for a 250GB hd it took some hours. But at least i have a full working duplicated hdd.

---

