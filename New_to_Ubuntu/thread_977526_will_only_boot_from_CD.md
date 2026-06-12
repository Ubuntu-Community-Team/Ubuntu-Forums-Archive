---
title: "will only boot from CD"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by dazwest on 2008-11-10
Hi,
Complete newbie here....
Have just installed Ubuntu onto an existing Vista PC. Seemed to work fine but if i reboot with no CD in the drive then it just boots straight to windows with no boot option menu.
If I leave the CD in then it boots to Ubuntu.
How can i get it to give me a menu to choose which to boot into and also to choose which I want as the default OS?

thanks!

---

### Post by Elfy on 2008-11-10
If you haven't actually hit the install icon on the desktop then you have just been using the livecd.

So if you take the cd out and reboot you only get windows

---

### Post by meindian523 on 2008-11-10
or maybe you should press Esc(keep pressing) after the BIOS finishes it's POST.

---

### Post by dazwest on 2008-11-10
> **forestpixie said:**
> If you haven't actually hit the install icon on the desktop then you have just been using the livecd.

So if you take the cd out and reboot you only get windows

Yeah I went through the whole installation process, chose partitions and sizes etc. The partitions show as being there when booted but just no way of booting from the HD...

---

### Post by Elfy on 2008-11-10
Boot the livecd again and run this command from a terminal

```
sudo fdisk -l
```

You'll get a list similar to 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2675    21486906   83  Linux
/dev/sda2            2676        9889    57946455    5  Extended
/dev/sda3            9890       10011      979965   82  Linux swap / Solaris

One will be Linux - use that device in the next to replace sdxy

```
sudo mkdir /mnt/recovery
sudo mount - t ext3 /dev/sdxy /mnt/recovery
```

Now please run these and paste the outputs here for us please and also the output from the fdsik -l command

```
cat /mnt/recovery/boot/grub/menu.lst
ls /mnt/recovery/boot/grub
```

---

