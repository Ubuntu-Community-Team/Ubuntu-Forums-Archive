---
title: "no swap partition"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by zabergan on 2008-12-02
I recently installed ubuntu as a dual-boot with vista but I had some problems with the partitioning part and ended up with no swap partition. Most of the time ubuntu runs fine but I have some problems when I go to hibernation. How can I create some swap or should I just re-install ubuntu with a swap partition.

---

### Post by theozzlives on 2008-12-02
use the live CD, go to system>aministration>partition editor and resize and create partitions there.

---

### Post by hellion0 on 2008-12-02
You could also create a swapfile, assuming you're squeamish about repartitioning. However, this can be even more complex. There's a guide for that [here](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/).

That said, I strongly suggest creating the partition instead of creating a swapfile.

---

### Post by porchrat on 2008-12-02
Agreed.  Use the LiveCD to avoid mounting the drives.  Then use partition editor (gparted) to create the swap.  Make sure that your swap partition is at least as large as your RAM so that you can hibernate.

---

### Post by Paqman on 2008-12-02
You'll need a swap partition for hibernation.

Creating the partition is easy enough. Just boot into the Live CD and go to System > Admin > Partition Editor. Make a space the same size as your RAM and format as swap.

You'll need to add an entry for your swap to the file /etc/fstab. Make a backup of the file first. I'm not at a Linux machine just now, perhaps someone who is can post the correct syntax for the swap entry in fstab.

---

### Post by bodhi.zazen on 2008-12-02
> **zabergan said:**
> I recently installed ubuntu as a dual-boot with vista but I had some problems with the partitioning part and ended up with no swap partition. Most of the time ubuntu runs fine but I have some problems when I go to hibernation. How can I create some swap or should I just re-install ubuntu with a swap partition.

What problems did you have ? You can only have 4 primary partitions so you may need to make an extended partition.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by zabergan on 2008-12-02
> **Paqman said:**
> You'll need a swap partition for hibernation.

Creating the partition is easy enough. Just boot into the Live CD and go to System > Admin > Partition Editor. Make a space the same size as your RAM and format as swap.

You'll need to add an entry for your swap to the file /etc/fstab. Make a backup of the file first. I'm not at a Linux machine just now, perhaps someone who is can post the correct syntax for the swap entry in fstab.

Thanks for the suggestion. I've just created the partition. Now all I need is the correct syntax for the swap entry in fstab. Does anyone know where I can find this?

---

### Post by Elfy on 2008-12-02
> UUID=cbd99e21-9789-4ea0-ba9a-09d365321c1d none swap sw 0 0

This is mine, run ```
sudo blkid
``` to get your UUID number

---

### Post by zabergan on 2008-12-02
> **forestpixie said:**
> This is mine, run ```
sudo blkid
``` to get your UUID number

This is what I get when I run sudo blkid

/dev/sda1: UUID="EA501D06E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="74082C86082C4986" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="adea90a3-5304-4c0f-a72e-03e631f94518" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="85a8274f-1df1-448b-ad71-d12d5ef481d3"

---

### Post by Elfy on 2008-12-02
> /dev/sda4: TYPE="swap" UUID="85a8274f-1df1-448b-ad71-d12d5ef481d3"So the corresponding swap line for you is

```
85a8274f-1df1-448b-ad71-d12d5ef481d3 none swap sw 0 0 
```

Once you've changed fstab run this

```
sudo swapon -a
```

check with free -m that it's active.

---

### Post by bodhi.zazen on 2008-12-02
Edit fstab with any editor, say gedit:

```
gksu gedit /etc/fstab
```

Add this entry :

> # Swap /dev/sda4
UUID=85a8274f-1df1-448b-ad71-d12d5ef481d3 none swap sw 0 0

You can then

```
sudo swapon /dev/sda4
```

Otherwise, with that fstab entry , swap will be active when you boot.

You can check your swap with 

```
free
```

---

