---
title: "partition manager"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by alpdo on 2008-04-22
i have my 160 gb harddisk installed ;dual boot with win98 and ubuntu ;with ff partitions; 2 gb swap, 10 gb /;10 gb for win98; and  rest of the partition for /home; since /home is large enough; im wondering if i could repartition my /home partition....

---

### Post by Saint Angeles on 2008-04-22
```
sudo apt-get install gparted
```

---

### Post by alpdo on 2008-04-22
i have tried using gparted but the resize button is disable...and i cannot unmount the parttition

---

### Post by Saint Angeles on 2008-04-22
> **alpdo said:**
> i have tried using gparted but the resize button is disable...and i cannot unmount the parttition
i think you gotta unmount the partitions first... you might have better luck doing it from the live CD

---

### Post by indytim on 2008-04-22
Get the "Live" version.  

[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

IndyTim

---

### Post by alpdo on 2008-04-22
is there other program than gparted???

---

### Post by indytim on 2008-04-22
GParted is pretty much regarded as the "gold standard" of partition editing in the Lx environment (works very well on NTFS, FAT32 etc).  Is there a problem with using GParted?

IndyTim

---

### Post by billgoldberg on 2008-04-22
> **alpdo said:**
> i have my 160 gb harddisk installed ;dual boot with win98 and ubuntu ;with ff partitions; 2 gb swap, 10 gb /;10 gb for win98; and  rest of the partition for /home; since /home is large enough; im wondering if i could repartition my /home partition....

You can't repartition your /home drive when you are using ubuntu. 

You will need to unmount it, but I doubt that is possible when running the OS.

Like someone else said, download the gparted live cd, burn it and boot from it. Then you will be able to it.

I can be wrong, but I think you can also use the ubuntu live cd for it (I believe it comes with gparted).

---

### Post by alpdo on 2008-04-22
okies tanks
ill try

---

### Post by alpdo on 2008-04-22
what is makefs???

---

### Post by Xiong Chiamiov on 2008-04-22
> **alpdo said:**
> what is makefs???
It's used to make a file system.  Why do you ask?

---

### Post by alpdo on 2008-04-22
gparted works well .... tanks

:guitar:

tanks tanks tnks:popcorn:

---

### Post by alpdo on 2008-04-22
how do you use it??? makefs???

---

