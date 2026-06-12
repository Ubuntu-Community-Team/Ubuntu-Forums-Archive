---
title: "upgraded to 8.04 now no wireless"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by imakeart on 2008-04-25
I've been reading a few different approaches to this problem, and its just sending me in circles. Someone out there please help!? :)

I upgraded from 7.10 to 8.04 - everything appeared to go smoothly, but now the wireless isn't working (Atheros). When I plug in a Belkin USB wireless it does work, albeit slowly.

I checked the Synaptic and the package that handles Madwifi is installed and when I do 'lspci' it is detecting the Atheros Wireless card. I honestly can't see why its not working. :confused:

I read in one post about using the Gutsy kernel instead - is this an option? and if so how do I revert back? or should I just get rid of 8.04 and reinstall 7.10?


Thanks,
Amanda

---

### Post by superprash2003 on 2008-04-25
> When I plug in a Belkin USB wireless it does work, albeit slowly.

Does this mean that internet works?

---

### Post by spiderbatdad on 2008-04-25
Do you get a grub menu at boot, from which to select different operating systems? If you only boot one OS it may be hidden. Press escape just after start up and prior to boot to display the grub menu, or take a look at the file /boot/grub/menu.lst  scroll way down to the section under ####END DEFAULT OPTIONS####
Your kernels will be listed there. Look for kernel 2.6.22-14

Here's mine:```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

```

See there are two normal kernels and two (recovery mode)

---

