---
title: "How can I enable a swap partition?"
date: 2018-09-04
forum: New to Ubuntu
---

### Post by rocco.martinello on 2018-09-04
My hard drive is partitioned as follows:
[IMG]http://www.roccomartinello.it/disk_partitioning.jpg[/IMG]
All partitions are primary partitions.
I have Windows 10 and Ubuntu 18.04.1 LTS dual boot.
I deleted Ubuntu swap file because I want use swap partition (that is listed above), but I don't know how to enable it (using free -m command I see that Ubuntu doesn't use the swap partition that I created).
How can I do to enable this swap partition?
If I use cat /etc/fstab on terminal the result is the following:
[IMG]http://www.roccomartinello.it/fstab.png[/IMG]
Thank you in advance for your answers!!!

---

### Post by sporksrule on 2018-09-04
Try this tutorial, it is what I use to turn enable a swap partition: [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-18-04)

---

### Post by wildmanne39 on 2018-09-04
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by Impavidus on 2018-09-05
First find the UUID of the swap partition:```
sudo blkid | grep 'TYPE="swap"'
```Then modify your /etc/fstab and replace /swapfile with UUID=xxx, using the UUID you got from the command above. The line that now has /swapfile must then look something like```
UUID=01234567-89ab-cdef-0123-456789abcdef none            swap    sw              0       0
```
The swap partition will be used after a reboot or running```
sudo swapon -a
```

---

### Post by rocco.martinello on 2018-09-05
Hi Impavidus, thank you very much for your answer!
I used /dev/sda5 instead of [COLOR=#000000][FONT=&quot]UUID and it works!
Is it ok anyway to use [/FONT][/COLOR]/dev/sda5 instead of [COLOR=#000000][FONT=&quot]UUID?[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2018-09-05
Depends on if you have other drives installed. What might be sda today may be sdb the net time you reboot. Uuids never change.

---

