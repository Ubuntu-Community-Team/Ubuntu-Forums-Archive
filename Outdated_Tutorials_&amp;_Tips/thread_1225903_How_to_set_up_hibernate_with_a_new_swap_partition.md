---
title: "How to set up hibernate with a new swap partition"
date: 2009-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by ~Las~ on 2009-07-29
After I created a new swap partition i couldnt Hibernate and this is how i got to fix it(after googling)


1)created a swap with gpated(= or bigger than installed amount of ram)
2)from information tab in gparted on that swap or by command "blkid" in terminal get UUID of new swap partition
3)copy that UUID (only part after UUID= & without "")
4)in terminal become root by "sudo su" & providing password
5)edit resume file by "gedit /etc/initramfs-tools/conf.d/resume"
6)replace UUID in that with the one you copied earlyer (new swap files one) & save,close
7)edit fstab by "gedit /etc/fstab"
8)replace UUID of the line whih is for swap (the line includes word swap) & save,close
   eg:-UUID=b382fab8-fa15-471f-a397-f96ad10bfc11 none swap sw 0 0
9)update initramfs by "update-initramfs -u -k all"
10)update grub (update-grub)
11)reboot & should work:P

---

