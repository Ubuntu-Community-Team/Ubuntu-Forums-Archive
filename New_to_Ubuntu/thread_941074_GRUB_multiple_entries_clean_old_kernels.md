---
title: "GRUB multiple entries: clean old kernels?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by gfern on 2008-10-07
Hello everyone! 

I installed Ubuntu as my first ever Linux system around 4 months ago and kept windows, just in case, even though I really never needed it again. Everything works fine with GRUB, but as time goes on there seems to appear more and more entries of available Ubuntu bootable options. After reading some posts online, I figured that these are Ubuntu entries for old Kernels, as I must have updated the kernel a few times through the updating tool.

So now what do I do to clean up those entries? Should I edit the menu.lst file under Grub, or should I remove the old Kernels through Synaptics, or should I do something entirely different? ; ) Can anyone help? 

Thanks!

---

### Post by shifty_powers on 2008-10-07
could use boot up manager...

```
sudo apt-get install bum
```

---

### Post by philinux on 2008-10-07
Also startupmanager works a treat to.

I like to keep the odd kernel around just in case an update causes a problem.

---

### Post by PocketDog on 2008-10-07
I just comment out the old kernel options (#) in menu.lst rather than delete the entries. You never know if you'll need them one day...

---

### Post by gfern on 2008-10-07
Thanks guys! Startupmanager actually has an option to limit the number of kernels on start-up. Should work fine!

---

### Post by Ptero-4 on 2008-10-07
in the /boot/grub/menu.lst file look for the entry "howmany" and change whatever is next to the = sign to 2. That way you'll only have one kernel besides the current one, in case a particularly bad kernel update breaks your X11, blows your ndiswrapper (like I had happen one too many times) or just completelly bricks your system. You always have the old one to fall back on.

---

### Post by drs305 on 2008-10-07
See the link in my signature about StartUp-Manager and all the things it can do for you via a gui app - including limiting the number of kernels displayed...

---

### Post by shifty_powers on 2008-10-07
heh, yeah, startup manager is probably betterlooking at it :D

---

