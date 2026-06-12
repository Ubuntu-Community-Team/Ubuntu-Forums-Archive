---
title: "Partition clean up"
date: 2017-05-10
forum: New to Ubuntu
---

### Post by lemuel1112 on 2017-05-10
Hi folks, I am wanting to clean up my partitions, as the computer seems to be slowing down since I loaded Ubuntu 17.04. I have dual boot with Win 10 and sda6 is Linux Mint which I don't use anymore. I also don't know what sda1 ext4 is. I want to make sure that I do everything correctly without causing problems for Ubuntu or Windows. Attached is my GParted display.  [ATTACH=CONFIG]275033[/ATTACH]

---

### Post by yancek on 2017-05-10
sda1 is by far the largest partition on the drive (150+GB) so you need to mount that partition to take a look at it.  From GParted, it shows as empty, no data and also shows a red icon on the left which usually means problems?  You may need to do a filesystem check on that partition but it might just be empty. 

If you ran GParted from an installed Ubuntu, then sda7 is Ubuntu shown with the "/" symbol in GParted.  If you delete the Mint partition which you say is sda6, your sda7 will change to sda6 as it is a logical partition and you might have problems booting Ubuntu if it is on sda7.  You could just format sda6 and use it for data.

---

### Post by lemuel1112 on 2017-05-15
How do I mount the partition?

---

