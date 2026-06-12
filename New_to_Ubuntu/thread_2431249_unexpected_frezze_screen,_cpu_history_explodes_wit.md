---
title: "unexpected frezze screen, cpu history explodes with no reason"
date: 2019-11-13
forum: New to Ubuntu
---

### Post by byronjev on 2019-11-13
[ATTACH=CONFIG]284398[/ATTACH]
I had my computer a that worked perfectly while being in a partitioned hard disk who had 1.5 TB for windows and more less 0.5 TB for Ubuntu.
It didn't cause me trouble and was able to perform a lot of windows at a time in my computer, never had problems. So i decided to change completely to Ubuntu. When i did this happended, it had no partitions at all, just the 2 TB completely mounted. And i know that before it had a swap partition and many other that came with the installation. Right now i have the idea that it is a problem cause by not having the swap partition. But i quite dont know. There are so many kind of solutions on the web. The picture of the cpu history was taking time after initiating the computer, with not a single one program open. I really just turned it on and started to bounce very wildly.
Any suggestions?

---

### Post by Impavidus on 2019-11-14
Even if your hard drive has only a single partition spanning entire drive, it's still a partition. Theoretically you can make a filesystem on the entire drive without partitions, but that hasn't been common since we stopped using floppy disks. So I'm quite sure you've got at least one partition on your hard drive.

Swap partitions aren't mandatory. Your screenshot shows you've got 2GB of swap, which may be a swap file. No problem there. With 7GB of memory, it's unlikely you'll ever use swap.

There are many processes running automatically after you start your computer. In particular the update manager is often busy. Can you find out which processes run exactly?

It's often recommended to use separate partitions for the operating system and for documents. That makes it easier to reinstall.

---

