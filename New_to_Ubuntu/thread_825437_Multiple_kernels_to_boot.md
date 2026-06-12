---
title: "Multiple kernels to boot"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Jensss on 2008-06-11
Since I've installed Hardy there were 2 kernel updates.
So I'd started with kernel -16 and when I updated to -17 and a little time later to -18, everytime their came a new Ubuntu option in the GRUB bootloader and also a recoverymode.

Now I have:
- Ubuntu 8.04 -18
- Ubuntu 8.04 -18 Recovery mode
- Ubuntu 8.04 -17
- Ubuntu 8.04 -17 Recovery mode
- Ubuntu 8.04 -16
- Ubuntu 8.04 -16 Recovery mode
- Vista

How can it be that it happened? And how can I change it back to normal?

---

### Post by sam_delta on 2008-06-11
that happens, because if the new kernel causes problems to your system, you can always boot to the old working one, but since you made sure that the new one is working, you can remove them from the boot menu now.

you will have to comment/delete out some lines of the file /boot/grub/menu.lst

post the output of the command ```
cat /boot/grub/menu.lst
```

EDIT-- Better delete them using synaptic as suggested below
sam

---

### Post by iaculallad on 2008-06-11
Everytime you upgrade your kernel, grub automatically add the newer kernel to your /boot/grub/menu.lst file without deleting older boot kernels.
You can edit menu.lst and remove older kernel options and use Synaptics to delete this (unused) kernel files permanently.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by inportb on 2008-06-11
I would instead suggest that you remove them through the apt-get system, since it's much cleaner that way. The kernels should be called linux-image-*; make sure you don't remove the one you're currently using.

---

### Post by Oldsoldier2003 on 2008-06-11
> **inportb said:**
> I would instead suggest that you remove them through the apt-get system, since it's much cleaner that way. The kernels should be called linux-image-*; make sure you don't remove the one you're currently using.

agreed. for a new user its probably easier to use synaptic. open synaptic and search for "linux-image" then mark the images you no longer need "mark for complete removal".

This will completely remove the extra kernels and the symlinks associated to them and update your grub menu.lst.

---

### Post by Jensss on 2008-06-11
Thanks guys!
I just thought it was strange because I use ubuntu now for more then a year and 7.10 didn't do that.

---

### Post by kansasnoob on 2008-06-11
I prefer just installing startupmanager (which will then show up under System>Administartion>Start Up Manager) from synaptic and under the advanced tab you can simply change "number of kernels to keep" to 1.

---

### Post by Oldsoldier2003 on 2008-06-11
> **kansasnoob said:**
> I prefer just installing startupmanager (which will then show up under System>Administartion>Start Up Manager) from synaptic and under the advanced tab you can simply change "number of kernels to keep" to 1.

i would set it to "2' to be honest. I suppose its because im just a wee bit paranoid and like to keep a backup kernel.

---

