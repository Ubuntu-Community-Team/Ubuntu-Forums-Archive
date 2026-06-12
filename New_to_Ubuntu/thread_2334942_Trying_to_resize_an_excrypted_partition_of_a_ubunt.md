---
title: "Trying to resize an excrypted partition of a ubuntu VM failed"
date: 2016-08-24
forum: New to Ubuntu
---

### Post by danielhk1 on 2016-08-24
Dear all,

Trying to enlarge a encrypted partition of the ubuntu VM by livecd following this link: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)



root@ubuntu:~# lvresize -L+10G /dev/ubuntu-vg/root
 Extending logical volume root to 18.75GiB
 Insufficient free space: 2560 extents needed, but only 0 available

root@ubuntu:~# pvdisplay 
 --- Physical volume ---
PV Name  /dev/mapper/crypt1
VG Name ubuntu-vg
PV Size 9.76 GiB / not usable 3.00 MiB
Allocation yes(but full)
PE Size 4.00 Mib
Total PE 2497
Free PE 0
Allocate PE 2497


I am not sure whats wrong. The VM is running under Virtual Box, VM file type is vdi and is currently have Dynamic storage allocation, so it is having 20G size but actually size is 9.9G. Would you please help and advise if the Dynamic storage allocation is the cause of the problem? 

Thanks
Daniel

---

### Post by TheFu on 2016-08-24
Please post **sudo parted -l** output and **sudo lvdisplay**, **sudo vgdisplay** outputs.

Use *code tags* for the results so things line up too, please.

---

### Post by danielhk1 on 2016-08-25
> **TheFu said:**
> Please post **sudo parted -l** output and **sudo lvdisplay**, **sudo vgdisplay** outputs.

Use *code tags* for the results so things line up too, please.

Thanks for your reponse, i use screenshot this time and hope it is clear, thanks
[ATTACH=CONFIG]270851[/ATTACH][ATTACH=CONFIG]270852[/ATTACH][ATTACH=CONFIG]270853[/ATTACH]

---

