---
title: "error: no such partition. grub rescue&gt;"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by Dumindu on 2015-03-28
I have installed Ubuntu with Windows7.
I hibernated windows and after restarted the machine I got following screen.

error: no such partition
grub rescue>

Previously, before hibernating windows I was formatting some SD cards and an accidentally I saw some separate partition icon for the sd-card was created in "My computer " screen. I didn't pay much attention for that at that time and I hibernated the machine. After I restarted the machine, I got the above error screen.

  I tried to boot with my Windows recovery disk. But it was not successful. In the meanwhile I followed this link 

[http://itsfoss.com/solve-error-partition-grub-rescue-ubuntu-linux/](http://itsfoss.com/solve-error-partition-grub-rescue-ubuntu-linux/) 

but I can not mount my root partition as mentioned in the link. 

Please help!!!

---

### Post by dino99 on 2015-03-28
what kind of ubuntu installation it is ?  what do you mean by 'ubuntu with windows 7' ? is it 'alongside' or 'inside' (aka WUBI which is deprecated now)

---

### Post by Dumindu on 2015-03-28
It is alongside with Windows, no separate partitions

---

### Post by yancek on 2015-03-28
>  			 			It is alongside with Windows, no separate partitions 		

If it is installed alongside windows, then it would have to be on a separate partition.  If you are getting a Grub error then you probably have it installed somewhere.  Do you get that message when selecting Ubuntu from the boot menu, when selecting windows from the boot menu or both?  I would suggest you use the Ubuntu install medium to boot the machine, open a terminal and type the following command and post the output here:  sudo fdisk -l(Lower Case Letter L in the command)  This will list your drives/partitions and not make any changes.  You might also google "boot repair ubuntu" and go to the site download and run it selecting the option to "Create Boot Info Summary" and post that detailed info here.

---

