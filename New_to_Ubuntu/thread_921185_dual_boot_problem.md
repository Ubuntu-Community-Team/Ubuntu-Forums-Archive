---
title: "dual boot problem"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by santhust on 2008-09-16
hi. 
i was having ubuntu on my dell inspiron 1525 notebook. now i had also installed windows vista on a seperate partition(80 GB for windows vista; while 150 GB left for ubuntu), using gparted through ubuntu itself. the windows was installed successfully, but now when i start my laptop it doesn't show me the dual boot options. instead the windows vista gets started; hence i am not being able to start ubuntu.

please help. where could i have gone wrong or missed some thing?

---

### Post by kjohansen on 2008-09-16
you should be able to follow the last few steps here to reconfigure the boot loader:


[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Harisz750 on 2008-09-16
Try booting your Live CD, open a terminal, and do:
Code:

sudo grub
grub> find /boot/grub/stage1

That should return your Ubuntu partition in the form of (hdX,Y), use that:

Code:

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

if you have one disk.. the X = 0  & Y = 1 (meaning grub is at the second partition)

now it will show the grub at boot.. tell us if you can choose to boot in windows.. or we will have to edit grub/menu.lst

---

### Post by santhust on 2008-09-17
> **kjohansen said:**
> you should be able to follow the last few steps here to reconfigure the boot loader:


[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
oh i tried, but it didn't worked. i had to delete ubuntu partition and reinstall it! any way thanks. i got to learn from the problem. it would have certainly been better if i could have found a way so as not to reinstall ubuntu (this appears like a brute force method) but some way that could have given me my previous "captured" ubuntu! any way didn't like such a capture from vista...:(

---

