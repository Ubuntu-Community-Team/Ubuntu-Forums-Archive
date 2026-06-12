---
title: "Unbuntu 8.04 two generic kernel"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by akshaykr2 on 2008-04-27
Hi
I upgraded from ubuntu 7.10 to 8.04, and now I have two generic kernel at startup, namely generic kernel 2.6.24-16 and 2.6.22-14. Please tell me why is this so? Do I need to delete any one of these? 2.6.24-16 generic had problem like internet connectivity, but after I updated grub and initramfs it is working fine.   

I am new to all this, I don't even know what kernel, initramfs, grub etc means. Please educate me on this.

Thanks

p.s.: Mine is a dual boot, with windows as the other OS.

---

### Post by schauerlich on 2008-04-27
When you upgraded to Hardy, you got the latest version of the kernel. However, since there's the chance that the new kernel won't play nice with your hardware, Ubuntu keeps the old version around that you know works. That way, if the new kernel doesn't work, you can just start up with the old, working one, and you don't have to go through the trouble of finding and compiling the old kernel.

Also, some definitions:
GRUB: a piece of software that lets you choose what operating system (or kernel) to boot up. It also helps whichever kernel you select get loaded into RAM, so you can get on your merry little way.
kernel: the "lowest" level of software in an operating system. Its job is to talk directly to the hardware, and manage all the data that's flying around. It also does things like decide when a piece of code gets executed.
initramfs: A process that helps start up the OS.

---

### Post by akshaykr2 on 2008-04-28
Thanks

---

### Post by Oldsoldier2003 on 2008-04-28
usually its a good idea to keep the last couple kernels in case you have a problem. when the kernel list gets long you can start removing the oldest ones. Search synaptic for linux-image and mark the linux-image package for the older kernels for complete removal. this will uninstall the old kernels and update your grub menu as part of the process of removal.

---

### Post by cmcfarland21 on 2008-04-28
> **akshaykr2 said:**
> Hi
I upgraded from ubuntu 7.10 to 8.04, and now I have two generic kernel at startup, namely generic kernel 2.6.24-16 and 2.6.22-14. Please tell me why is this so? Do I need to delete any one of these? 2.6.24-16 generic had problem like internet connectivity, but after I updated grub and initramfs it is working fine.   

I am new to all this, I don't even know what kernel, initramfs, grub etc means. Please educate me on this.

Thanks

p.s.: Mine is a dual boot, with windows as the other OS.

What did you do to update your GRUB and initramfs?  2.6.24-16 is not working for me either.

---

### Post by ALex! on 2008-04-28
> **akshaykr2 said:**
> Hi
I upgraded from ubuntu 7.10 to 8.04, and now I have two generic kernel at startup, namely  and 2.6.22-14. Please tell me why is this so? Do I need to delete any one of these? 2.6.24-16 generic had problem like internet connectivity, but after I updated grub and initramfs it is working fine.   

I am new to all this, I don't even know what kernel, initramfs, grub etc means. Please educate me on this.

Thanks

p.s.: Mine is a dual boot, with windows as the other OS.

My generic kernel 2.6.24-16 doesn't even boot at all!! :cry: what should i do?! please! i'm begging for help!!!

---

### Post by bikeboy on 2008-04-28
First of all, is your system completely up to date? Were there any packages that didn't install properly?

```
sudo apt-get update && sudo apt-get upgrade
```

Second, did you ever add anything to the boot command to get your old kernel to work?

```
 cat /boot/grub/menu.lst > menu.txt 
```

Attach the menu.txt file or paste it to [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by InfinityCircuit on 2008-04-28
To update initramfs and grub:

```
sudo update-initramfs -u -k 2.6.24-16-generic
sudo update-grub
```

---

