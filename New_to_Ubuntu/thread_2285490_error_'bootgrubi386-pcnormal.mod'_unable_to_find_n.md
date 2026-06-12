---
title: "error: 'boot/grub/i386-pc/normal.mod' unable to find normal.mod"
date: 2015-07-06
forum: New to Ubuntu
---

### Post by Vinod_Sharma on 2015-07-06
Dear All,

 my OS (Ubuntu) is not booting it is giving error: 'boot/grub/i386-pc/normal.mod' unable to find normal.mod

link is give below. Will you please help me.

[Http://paste.ubuntu.com/11830468/](Http://paste.ubuntu.com/11830468/)

Thanks,
Vinod

---

### Post by yancek on 2015-07-06
Your posted output does not show any sign of Grub other than indicating the core.img file is present.  There is not grub.cfg file which is the boot menu file and other files generally needed are not shown.  It does not appear the installation was successful for whatever reason but I see you are using software RAID which I have no experience with.  You might try booting the install medium and mounting sda1 to see if any of the /boot/grub files are actually there.

---

### Post by nerdtron on 2015-07-06
We'll need details on your RAID config since raid devices are showing on the boot info script. Also note that the /boot partition which is on the /dev/sda on your setup cannot be on RAID5 or RAID0.

/boot can only be on RAID10 or RAID1 setups if you are using RAID.

---

