---
title: "grub menu items"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by zxc318 on 2008-08-07
I just installed Ubuntu 7.04.  Am in there now....

Why do I need all those boot options? 
What would I use Ubuntu, kernel 2.6.20-17-generic (recovery mode) for?
What would I use Ubuntu, memtest86+ for?
Since installing the 260 updates, now I have more boot options.  Seems to be doubles of everything Ubuntu except the memtest86+ entry....

---

### Post by tamoneya on 2008-08-07
you can edit the menu by looking at the bottom of /boot/grub/menu.lst.  You will need root privileges to edit it though so hit alt-F2 and run:```
gksudo gedit /boot/grub/menu.lst
```
Just put a "#" before the sections you dont want to see.  This comments them out and the computer ignores them.  

I would keep the latest "normal" ubuntu and the latest "recovery" ubuntu.  Recovery ubuntu drops you to a root shell and is useful if you really screw up your install and lock yourself out.

---

### Post by appi2012 on 2008-08-07
When you update the linux kernel (the base of ubuntu), it saves the old one in case the new one doesn't work. You can set how many you want to keep by downloading [Start Up Manager]("apt:startupmanager") (click to install) (It installs in the Administration tab) From there, you can set how many kernels you want to display in your menu.

---

### Post by cdtech on 2008-08-07
> **zxc318 said:**
> I just installed Ubuntu 7.04.  Am in there now....
Why do I need all those boot options? 
By default kernel upgrades will not remove the pre existing kernel images, as mentioned above "in case the new one doesn't work" then you can just boot with the old kernel image.

> **zxc318 said:**
> What would I use Ubuntu, kernel 2.6.20-17-generic (recovery mode) for?
This is to boot into Linux without loading any GUI configurations during boot and puts you into a terminal. If you can't boot into the GUI this could be useful.

> **zxc318 said:**
> What would I use Ubuntu, memtest86+ for?
Since installing the 260 updates, now I have more boot options.  Seems to be doubles of everything Ubuntu except the memtest86+ entry....
This is to test your installed RAM. If you feel you have issues running Linux or not using all your RAM, you can test using this option.

**P.S.**
Once you do a Kernel upgrade and find everything to be working correctly you can just remove the old kernel images using "Synaptic Package Manager"

---

### Post by drs305 on 2008-08-07
I have a tutorial on StartUp-Manager - see my signature for the link. SUM is an easy and safe way to edit grub's menu.lst  I originally wrote it in response to the many posts about seeing so many kernels listed on the menu. StartUp-Manager CAN limit the number of kernels displayed but there is actually a more efficient method to change this. 

Changing the number of kernels displayed in SUM only hides the menu items but leaves the old kernels on the machine. Generally you only need your current kernel and one working backup. If you use synaptic to remove old kernels, it not only frees up a bit of space on your computer (more important if you have a small /boot partition) but will also automatically remove those entries from the menu list. In synaptic, look for hardy kernels by finding the packages named "linux-image-2.6.24-*XXX*" and remove the ones you don't want.

You can see the kernel you are currently using with:
```
uname -r
```

---

