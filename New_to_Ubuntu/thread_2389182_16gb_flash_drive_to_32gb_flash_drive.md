---
title: "16gb flash drive to 32gb flash drive?"
date: 2018-04-12
forum: New to Ubuntu
---

### Post by leftskewed on 2018-04-12
Hi,
I was wondering if it would be possible to do a bit copy of a 16gb flash drive installation of Ubuntu 16.04 to a 32gb flash drive? If this is possible, what software would you recommend to make the clone?

Thanks

---

### Post by dino99 on 2018-04-13
no problem , use dd (see example)
[https://askubuntu.com/questions/640259/how-can-i-easily-clone-my-entire-system#640267](https://askubuntu.com/questions/640259/how-can-i-easily-clone-my-entire-system#640267)

---

### Post by sudodus on 2018-04-13
You can clone with dd, but it is risky. Many people have overwitten valuable data using it.

I would suggest cloning with [Clonezilla](http://clonezilla.org). (You find a lot of help how to use Clonezilla at its web site.)

Clonezilla is safer. It is also faster, because it is smart enough to only copy used blocks in the file systems.

---

### Post by Impavidus on 2018-04-13
Whatever tool you use for cloning, you'll find that the second half of the 32 GB drive will consist of unallocated space. After cloning, you can use the standard partitioning tools like gparted to make a new partition there or enlarge the existing partition. Expanding partitions to the right is relatively safe and fast.

---

### Post by sudodus on 2018-04-13
> **Impavidus said:**
> Whatever tool you use for cloning, you'll find that the second half of the 32 GB drive will consist of unallocated space. After cloning, you can use the standard partitioning tools like gparted to make a new partition there or enlarge the existing partition. Expanding partitions to the right is relatively safe and fast.

+1

gparted is a good tool for this purpose.

---

### Post by leftskewed on 2018-04-21
> **sudodus said:**
> You can clone with dd, but it is risky. Many people have overwitten valuable data using it.

I would suggest cloning with [Clonezilla]("http://clonezilla.org"). (You find a lot of help how to use Clonezilla at its web site.)

Clonezilla is safer. It is also faster, because it is smart enough to only copy used blocks in the file systems.

Thanks, I used Clonezilla and it worked perfectly.

---

### Post by leftskewed on 2018-04-21
> **Impavidus said:**
> Whatever tool you use for cloning, you'll find that the second half of the 32 GB drive will consist of unallocated space. After cloning, you can use the standard partitioning tools like gparted to make a new partition there or enlarge the existing partition. Expanding partitions to the right is relatively safe and fast.

Thanks, after I cloned the drive, I used gparted as you suggested and all went well.

---

### Post by leftskewed on 2018-04-21
> **dino99 said:**
> no problem , use dd (see example)
[https://askubuntu.com/questions/640259/how-can-i-easily-clone-my-entire-system#640267](https://askubuntu.com/questions/640259/how-can-i-easily-clone-my-entire-system#640267)

Thanks for your suggestion.

---

### Post by sudodus on 2018-04-22
I'm glad that thinks worked well for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

