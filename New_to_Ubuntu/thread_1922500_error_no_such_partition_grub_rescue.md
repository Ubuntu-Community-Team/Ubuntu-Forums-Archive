---
title: "error: no such partition grub rescue"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by snowman2765 on 2012-02-08
Hi all. I am pretty new here and have a bit of an issue. All help would be greatly appreciated. I have a desktop with windows 7 installed on it. I installed Ubuntu ver. 11.10 on an external hard drive. Before installation I alotted an 80gb partition for the installation. During install, I partitioned this in 4 parts: swap- 8gb, /boot- 258mb-ext2, /- 30gb-ext4, and /home ext4 - approx 42gb. Install went seamlessly, but after restart  and selecting usb to boot from, the error message came up. The computer has an internal drive of 1000gb with windows installed on it. it boots fine. my external drive is also 1000gb WD elements. I now am stuck and don't know what to do. Thanks in advance for any assistance.

---

### Post by snowman2765 on 2012-02-08
Oh, also, the internal drive is dev/ sda, and the external one is dev/ sdb. I made sure grub was installed to sdb.

---

### Post by mapes12 on 2012-02-10
This worked for me:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Very easy to use.

---

