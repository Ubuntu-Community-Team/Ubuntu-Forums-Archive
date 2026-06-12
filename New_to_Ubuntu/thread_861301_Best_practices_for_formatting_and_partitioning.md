---
title: "Best practices for formatting and partitioning?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by litlfrog on 2008-07-16
Hi,

I'm doing a fresh install of Ubuntu 8 on a computer at work. We need to reformat the single hard drive before install. Is reformatting the same thing as deleting a partition? I have a co-worker with a lot of tech experience but virtually no experience in Linux, and he wants to watch me do the install. I've got some experience using Ubuntu at home, which is why the boss asked me to redo this computer. I'd rather do the partitioning manually--do I understand correctly that I should have separate partitions for /swap, /etc, and /home? Thanks in advance--I want to look suave and savvy when working on the computer. :guitar:

---

### Post by dracayr on 2008-07-16
formatting is installing a filesystem on a partition (and thus creating it). It's quite the opposite thing of deleting a partition. Since a new filesystem is empty, all the data is lost while formatting, which is why many people (mostly window$ users) think it's deleting

dracayr

---

### Post by Elfy on 2008-07-16
Personally I only use / , /home and swap. I don't have seperate boot, etc, var partitions

I would also do the partitioning seperately in a partition editor then do the install, but that's just preference again

---

### Post by kestrel1 on 2008-07-16
Formatting is not the same as deleting a partition. If you delete a partition you have to re-create it before it can be formated.
Formating makes the drive recognisable by the OS, be it Windows, MAC OS, Linux etc. So when you format you are giving the drive a type of file system to use, NTFS, Fat32, EXT3 the list goes on.
Basically I would say your best bet would be to start the install & let Ubuntu use the whole drive & not worry about partitioning the drive before hand. That way you won't get in a mess if you are not sure what you are doing.

---

### Post by jimv on 2008-07-16
> **kestrel1 said:**
> Formatting is not the same as deleting a partition. If you delete a partition you have to re-create it before it can be formated.
Formating makes the drive recognisable by the OS, be it Windows, MAC OS, Linux etc. So when you format you are giving the drive a type of file system to use, NTFS, Fat32, EXT3 the list goes on.
Basically I would say your best bet would be to start the install & let Ubuntu use the whole drive & not worry about partitioning the drive before hand. That way you won't get in a mess if you are not sure what you are doing.

Agreed.  Just hit the "Use entire drive" option.  That will give you a / and a swap partition, and you just hit the button once, so you'll look like a pro.

---

### Post by o.besner on 2008-07-16
Hey there,

There are many ways of partitioning your drive, and there is virtually no bad way of doing it. Here's how I was taught to do it, by a Gentoo-using-picky-power-user-friend :P. My computer has a SATA hard-drive, so it shows up as /dev/sda. if you have an IDE, it's gonna be /dev/hda. Same thing.

/dev/sda1   ext2  /boot    (64MB)
/dev/sda2   swap  swap      (2300 MB)
/dev/sda3   jfs   /         (10000 MB)
/dev/sda4   jfs   /home      (480 000 MB)


Explanation : what you should have on your drive is 4 partitions : /boot (for the kernel), swap, / (root), and /home (all your stuff)

If your kernel one day becomes FUBAR, all you have to do is repair the /boot partition without touching the rest of the system. Pretty useful. 

My swap is huge, and it's because I hibernate/suspend my computer, and I need to copy my RAM (2 GB) on the hard drive. If you don't plan on suspending, you don't need such a big swap. 256 or 512 MB will be enough.

My root partition is 10 000 MB, because my /tmp is often crammed with wavs and parts of dvds. How many programs you will install is the big factor there. 10 000 is probably overkill for many, but I had plenty of space on my drive to spare.

Your home partition should use the remaining place on your HD. The boot partition is always in ext2, and swap is in swap. I use JFS because I noticed it is faster than ext3 when it comes to showing the content of large folders like /usr/bin, and my drive seems to spin less often (thus quieter). However, ext3 has extensive support and is rock solid (as in incredibly stable, and data recovery is pretty easy). ReiserFS is what my Gentoo friend is using, and is considered very fast for small files, but I've never tried it.

Good luck ! have a look at  [http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=4)  if you need to know more.

---

