---
title: "Remove win partition"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Wray on 2013-01-02
What is the best way to remove the win partition from a dual boot ubuntu drive, and leave the entire drive available to ubuntu?  Can i just repartition the drive without damaging/blowing away the ubuntu partition ?
Toshiba laptop.

---

### Post by docshawnc on 2013-01-02
It's probably safer to delete the windows partition and then resize the ubuntu one to use the whole disk.

---

### Post by COMECON on 2013-01-02
First, install **GParted**:
```
$ sudo apt-get install gparted
```Once it's installed, run it. Select the Windows partition (usually it's the **ntfs** filesystem), right click on it, and select **Delete**. Don't worry, anything will be done until you apply the changes!
After deleting it, you'll have some unallocated (free) space. Just select the Ubuntu partition, right click, select **Resize / Move partition**, and, using the sliders, append all the free space to it. Then just click Apply and wait!
I recommend you updating GRUB after that, then Windows won't be shown on the GRUB:
```
$ sudo update-grub2
```Note: If you have multiple Linux partitions (e.g., one for /home, one for /), you have to move them for having the free space next to the one where you want to add the space. For example, if you have:
```
 
--- Free Space
--- /dev/sda1 (/home)
--- /dev/sda2 (/)

```If you want to add the space to **/dev/sda2**, just select /dev/sda1, click on **Resize / Move partition** (right click) and move to have the free space **after** it. So you will have:
```

--- /dev/sda1 (/home)
--- Free space
--- /dev/sda2 (/)

```Now just add the space to /dev/sda2.

Catbuntu

---

### Post by Wray on 2013-01-02
> **COMECON said:**
> First, install **GParted**:
```
$ sudo apt-get install gparted
```Once it's installed, run it. Select the Windows partition (usually it's the **ntfs** filesystem), right click on it, and select **Delete**. Don't worry, anything will be done until you apply the changes!
After deleting it, you'll have some unallocated (free) space. Just select the Ubuntu partition, right click, select **Resize / Move partition**, and, using the sliders, append all the free space to it. Then just click Apply and wait!
I recommend you updating GRUB after that, then Windows won't be shown on the GRUB:
```
$ sudo update-grub2
```Note: If you have multiple Linux partitions (e.g., one for /home, one for /), you have to move them for having the free space next to the one where you want to add the space. For example, if you have:
```
 
--- Free Space
--- /dev/sda1 (/home)
--- /dev/sda2 (/)

```If you want to add the space to **/dev/sda2**, just select /dev/sda1, click on **Resize / Move partition** (right click) and move to have the free space **after** it. So you will have:
```

--- /dev/sda1 (/home)
--- Free space
--- /dev/sda2 (/)

```Now just add the space to /dev/sda2.

Catbuntu

Thanks COMECON My problem now is don't know which partition is which: both are ntfs
i assume that sda2 is the linux partition since it is second on the boot list at startup.
How can i know for sure?

---

### Post by Mark Phelps on 2013-01-02
> **Wray said:**
> Thanks COMECON My problem now is don't know which partition is which: both are ntfs
i assume that sda2 is the linux partition since it is second on the boot list at startup.
How can i know for sure?

If they really ARE both NTFS -- that means you installed using Wubi -- in which case, your Ubuntu install is a virtual file INSIDE one of the NTFS partitions.

If you remove MS Windows, you will lose access to Ubuntu.

---

### Post by Wray on 2013-01-02
> **Mark Phelps said:**
> If they really ARE both NTFS -- that means you installed using Wubi -- in which case, your Ubuntu install is a virtual file INSIDE one of the NTFS partitions.

If you remove MS Windows, you will lose access to Ubuntu.

Thanks mark, it seems you are correct.
Since both partitions are clean installs i really have no problem blowing both away and starting over.  My thought now is to download a copy of ubuntu to a DVD, then use it to blow everything away and load a clean ubuntu. i assume that is doable, ie. repartition reformat from the DVD ?  What partition structure would you recommend for the new install.  This laptop has only 250 gb...

---

