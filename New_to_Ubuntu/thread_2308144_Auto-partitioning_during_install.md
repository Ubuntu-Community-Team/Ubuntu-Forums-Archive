---
title: "Auto-partitioning during install"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by Elishasmantle on 2015-12-31
I'm a Noob! ;)

Hello,

Regarding this topic.
If a user install using the Ubuntu auto-partitioning and uses whole hdd space :
Doesn't Ubuntu set ALL partitions to auto-grow / expand as needed until disk space runs out on the hdd?

Thank You,

elishasmantle

---

### Post by slickymaster on 2015-12-31
Moved to a thread of its own and thread title edited.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by Elishasmantle on 2015-12-31
Hello,

I did  not mean to use the forum incorrectly. I don't even know what the term "hi-jack other peoples threads means, but I assume it was asking a question within a question on the original post.

Thank You,

elishasmantle

---

### Post by v3.xx on 2015-12-31
> **Elishasmantle said:**
> 
If a user install using the Ubuntu auto-partitioning and uses whole hdd space :
Doesn't Ubuntu set ALL partitions to auto-grow / expand as needed until disk space runs out on the hdd?

When you use that option, everything on the drive is erased and the ubuntu installer replaces it with only a single install of ubuntu.

---

### Post by sammiev on 2015-12-31
^^ as said.

If you want to install another OS on the same HDD you can use gparted to shrink the partition from the right. ( which is the easiest but can be done from either end )

Always a great idea to backup your data first.

---

### Post by grahammechanical on 2015-12-31
> Doesn't Ubuntu set ALL partitions to auto-grow / expand as needed until disk space runs out on the hdd?

The answer to that question is: No it does not. Resizing partitions would require user's data to be moved around and that always carries a risk of data corruption. It is a small risk but Linux does not automatically resize partitions. A partition's size remains fixed until the user uses a disk partitioning facility to resize a partition.

If we install Ubuntu using the Erase disk and install Ubuntu option, the installer will use the whole disk. If we have a motherboard with a BIOS boot system and MBR partitioning then we get a Ubuntu partition and a swap partition. If we have a motherboard with a UEFI boot system and GPT partitioning we get a efi boot partition, a Ubuntu partition and a swap partition.

Perhaps you are thinking of folders/directories which do expand until a partition is close to being filled. Then Ubuntu will start giving the user out of space warnings. Lack of space will prevent Ubuntu from updating.

Regards.

---

### Post by Herdo on 2016-01-01
No.  If you place them all on the same partition it would just fill the drive with data from wherever, but most people recommend at least creating a separate /home partition.

[COLOR=#000000]It's pretty easy to just create 3 partitions for /, /home, and swap.

[/COLOR]

---

### Post by Elishasmantle on 2016-01-01
To Grahammechanical and Herdo, Thank YOU! That was what I was looking for as far as an answer.
I may have worded things incorrectly in my original post.

I'm still a bit confused as to how newer linux systems often do the partitioning. On my Ubuntu install it created 2 partitions: ext4 / and extended for swap.
So when I used the term auto grow partitions I was referring to the old way linux would require partitioning.
E.G: would require a / , /boot , /root , /swap, etc.... but now it seems all these partitions are not being used as such and only directory names are now being used which would grow as needed where space is being used on the hdd until that partition get near capacity and user gets warnings about partition being almost full.

Thanks also GM for the extra info on the EFI installs.

I appreciate your more detailed answers and actually answering my real question.

Thank You,

elishasmantle

---

