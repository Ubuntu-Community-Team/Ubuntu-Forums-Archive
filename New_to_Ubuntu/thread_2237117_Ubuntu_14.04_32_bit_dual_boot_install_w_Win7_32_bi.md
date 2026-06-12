---
title: "Ubuntu 14.04 32 bit dual boot install w/ Win7 32 bit results in grub rescue mode"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by Marv_Downey on 2014-07-30
I've been trying to install Ubuntu 14.04 32 bit on an old Dell Inspiron 6000 laptop running Windows 7 Pro 32 bit.  Created a 55GB partiton for Ubuntu and an 8GB swap partiton and installed from DVD, keeping the Grub install pointed at the drive MBR (as I thought the instructions indicated).  When install finishes and system reboots, it responds with "error: unknown filesystem.  Entering rescue mode... grub rescue> " .  I've tried several suggestions found to try to repair, both from the terminal and using boot-repair to no avail.  I can get back to the Windows install by repairing the boot sector with a Win7 boot CD and even tried EasyBCD from within Windows, all to no avail.  Have the BootInfo URL from boot-repair - [http://paste.ubuntu.com/7909298/](http://paste.ubuntu.com/7909298/) - hope someone can help!

---

### Post by oldfred on 2014-07-30
Some older computers have BIOS that will only boot from first 137GB of a hard drive.
It does not look like you have a lot of data in your Windows sda2 partition so you could shrink it to 50GB, create a 20GB partition for / (root) and have separate /home or just use rest of drive as a NTFS data partition if booting Windows a lot (or both).
I prefer smaller system partitions anyway as then hard drive does not have to work so much in jumping around for the most used system files. Data then can be anywhere on drive as it is not used as much.
Windows does like lots of free space inside its NTFS system partition, so do not make it too small. Generally 30% free is suggested.

---

### Post by Marv_Downey on 2014-07-30
Thanks - I'll give that a try tonight!

---

### Post by oldfred on 2014-07-30
Be sure to use Windows to shrink the NTFS system partition and reboot immediately so it can run chkdsk and make repairs for its new size. Do not create partitions with Windows partition tools as it may try to convert to dynamic partitions which do not work with Linux.

---

### Post by Marv_Downey on 2014-07-31
Thanks oldfred - you were absolutely correct.  Shrank (shrunk??) the Windows partition to 100GB, put the 20GB / and 8GB swap immediately after, then used the rest for /home (since Windows use will probably be minimal - did this for a young college student friend who is really a Mac user but had special need for a dual boot Win/Linux setup), and everything worked beautifully (except the extra hour or so to find the way to get the Dell wireless working).  I guess if I had gotten involved in dual booting earlier in my career I might have known about this.  Thanks again!

---

### Post by oldfred on 2014-08-01
Glad that worked. :)

---

