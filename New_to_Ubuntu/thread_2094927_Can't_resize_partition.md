---
title: "Can't resize partition?"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by zeating on 2012-12-15
I have particion sda1 which is 100mb system reserved for windows
sda 2 which is 118gb NTFS Music particion
sda 3 790gb windows 7 particion
and 22gb unallocated space

No matter what I do it won't allow me to resize SDA2, whats the problem? i've tried gparted live cd and booting into windows but i still cant do it

---

### Post by GreatDanton on 2012-12-15
That's because sda2 is between sda1 and sda3. If you would like to resize it, you have to shrink (or remove) sda3 resize your partition (sda2) and make new sda3. IMO instead of doing all of the above, just make new partition on unallocated place. 

Just a warning. Whenever you would like to resize partitions (or shrink them) and you would like to use it with Windows, always use Windows tools. Gparted is not suitable in this case.

Regards.

---

### Post by zeating on 2012-12-15
If I made a new partition out of the unallocated space how do I add it to my music partition?

---

### Post by Mark Phelps on 2012-12-15
> **zeating said:**
> If I made a new partition out of the unallocated space how do I add it to my music partition?

You can't -- because there is a partition in the way.  Partitions have to be contiguous space -- they can't jump around other partitions.

---

### Post by zeating on 2012-12-15
Is there any way to add the unallocated space to my music drive without deleting data?

---

### Post by Cheesemill on 2012-12-15
If you can post a screenshot of gparted it will let us know ***exactly*** how your partitions are set up. We can then give you more accurate advice.

---

### Post by zeating on 2012-12-15
Okay, picture attached. I'm on Windows 7 atm

---

### Post by Cheesemill on 2012-12-15
To increase the size of sda2 you need to have the free space next to it, you can do this with gparted but it will take a long time.

First make sure you have a backup and then boot the gparted CD.

Then you can move sda3 all the way to the right and then resize sda2 to take up the free space next to it.

---

### Post by Mark Phelps on 2012-12-15
To merge spaces, you would first need to copy the stuff you want to save from the last partition onto an external drive.  That will allow you to remove that partition without losing anything.

You can then remove that partition using GParted.

You can now move the Win7 OS partition to the right -- but do NOT use Linux utilities or apps to do this.  Doing so risks corrupting the Win7 OS partition.

Instead,  Google for, download, and burn a CD of Minitool Partition Wizard Boot CD.  This is a Windows app that knows how to manage Windows partitions.  You can use this to move the Win7 OS partition to the right -- to put the free space next to the partition you want to expand.

But, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will give you the means to restore the Win7 boot loader, should it become damaged during the partition move.

NOW, boot from the Minitool CD and use the wizard to move the Win7 OS partition to the right.

Once that is done, you can use the same tool to expand the Music partition.  Do NOT add another partition in here as that will change the partition index of your Win7 OS partition and GRUB is likely then NOT to work when booting Win7.

---

### Post by zeating on 2012-12-17
Is that the only way to do it? I don't have an external drive or anything, so theres no way to just merge the 20gb without deleting partitions and stuff?

part of me says it'd be easier to just buy another hard drive :roll:

---

### Post by Mark Phelps on 2012-12-17
> **zeating said:**
> Is that the only way to do it? I don't have an external drive or anything, so theres no way to just merge the 20gb without deleting partitions and stuff?

part of me says it'd be easier to just buy another hard drive :roll:

I understand that this can be frustrating -- but you keep asking essentially the same question over and over -- and the answer is always going to be NO -- you can not merge two spaces that have a partition between them.

---

### Post by Cheesemill on 2012-12-17
I've explained how to achieve what you're asking in post #8.

---

### Post by N3XU5 on 2012-12-17
Why are you using the windows parition editor for linux filesystems?

Use disk utility, or gparted. They can usualy move partitions to the right, or to the left

---

