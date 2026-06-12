---
title: "No splash screen on HP mini 110-3000"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by darksidedude on 2012-07-10
hey all, after a stint of being away I have returned with my netbook in tow. durring the boot from the live USB the plymouth splash screen worked sort of, the resolution was a bit off. after install was complete I noticed that nothing shows up at all. just the "grub is loading" and then a blank screen for 10-15 seconds. I have done a few mods to system and I will list them don't know if it will affect any tips.

mods

Linux kernel 3.4.4
installed LXDE

no proprietary drivers are in use on this system.

thanks for the help, as always your the best =)

---

### Post by NikTh on 2012-07-10
> **darksidedude said:**
> 
mods

Linux kernel 3.4.4
installed LXDE

Yes , the mod of kernel 3.4.4 maybe affects the splash. 
Try this
```

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all
```

---

### Post by darksidedude on 2012-07-10
I booted in to the generic kernel that came with 12.04 just to be sure if it worked. and it did not. same black screen, and if memory serves it never worked right after I started booting from the HDD. I tried ```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u -k all
```

and I got ```
joe@joe-HP-Mini-110-3000:~$ sudo update-alternatives --config default.plymouth
[sudo] password for joe: 
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/lubuntu-logo/lubuntu-logo.plymouth
Nothing to configure.
joe@joe-HP-Mini-110-3000:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-3.4.4
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
joe@joe-HP-Mini-110-3000:~$ 

```

to no avail. is it plymouth not playing nice with the Intel graphics driver? and if it is. I would settle for a verbose style boot like debian or old fedora. just want to see something on the screen so I know its not hanging

---

### Post by bodhi.zazen on 2012-07-10
What graphics card is it ?

---

### Post by darksidedude on 2012-07-10
its an intel x3150, I don't know the chipset off hand, sorry

---

### Post by NikTh on 2012-07-11
> **darksidedude said:**
> its an intel x3150, I don't know the chipset off hand, sorry
With my intel i have no problems . To see more info about your card open a terminal and ```
lspci -nnk | grep -iA2 vga
``` 

For verbosity try to remove "quiet splash" parms from /etc/default/grub . 
```
gksudo gedit /etc/default/grub
``` find the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and make it
GRUB_CMDLINE_LINUX_DEFAULT=""
then 
```
sudo update-grub
``` 
reboot to see.

---

### Post by darksidedude on 2012-07-11
here is the output of ```
joe@joe-HP-Mini-110-3000:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: Hewlett-Packard Company Device [103c:148a]
	Kernel modules: i915

```

---

