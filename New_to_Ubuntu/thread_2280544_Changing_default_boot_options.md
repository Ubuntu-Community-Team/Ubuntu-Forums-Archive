---
title: "Changing default boot options"
date: 2015-05-31
forum: New to Ubuntu
---

### Post by james139 on 2015-05-31
Hi, I want to change the order of the OS list in grub. Ubuntu comes first and I could do with changing it to Win7 for other users on the PC. I googled it but thought I might have more success first time on here.

---

### Post by yancek on 2015-05-31
If you want to set the windows entry to boot as default, you can do that by editing as root user the /etc/default/grub file, the line below:

> 
GRUB_DEFAULT=0

You would first go to the /boot/grub/grub/cfg file and count the menuentry lines to the one for windows then enter it in the above file.  Remember the count begins with zero not one so if windows were the fifth menuentry, you would put the number 4 in the file.  Run sudo update-grub after making the change.

---

### Post by Elfy on 2015-05-31
The files in /etc/grub.d/ get read and then used to build the grub.cfg file in /boot/grub

If you go to /etc/grub.d/ you'll see something like

```
00_header        10_linux      20_memtest86+  30_uefi-firmware  41_custom
05_debian_theme  20_linux_xen  30_os-prober   40_custom         README
```

Change the name of the os-prober one to 09 and it should read first and then be at the top of the grub list. 

```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
```

run update-grub

```
sudo update-grub
```

This is the part of grub.cfg directly after the 05_debian theme section before changing the file name as above

> ### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###

Once I changed 30_ to 09_

> ### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/09_os-prober ###

And the OS I have showing up as other OS's are now at the top of the grub list.

---

