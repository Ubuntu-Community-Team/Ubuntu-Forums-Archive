---
title: "kernel 2.6.24-16 vs 2.6.22-14: wireless"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by brodiesel on 2008-09-11
Hey everybody, a question about Hardy...

When I installed gutsy, at the boot screen i would get the choice of gutsy or windows (not counting the memcheck, etc.). when i installed hardy, however, i have two versions of the linux kernel to choose from: 2.6.24-16 and 2.6.22-14. 

i havent noticed any difference between the two except for the very important difference that in 2.6.24-16 i have no wireless networks. none. i have tried to manually configure, and that hasn't done it either. its as iff wireless doesnt exist as an option. 

in 2.6.22-14 the wireless has worked flawlessly from the start. 

so my questions:

why doesnt wireless work in the other version, and if it doesnt, can i erase that version? why would i need it? right now its at the top of the boot order, and its a little bit of a pain.

---

### Post by adam_kimber on 2008-09-12
The version stated is the Kernel version. So when they update the kernel, the number gets revised. The problem with this is if something is specifically programmed to use that kernel, such as proprietary video drivers etc. The driver is looking for kernel x and it finds y and therefore does not load. The differences between x and y and probably not so great to stop the driver from working, it just doesn't in case it breaks something. 

I expect this is what is happening to you in the later version. If you go the restricted drivers manager in the older and newer versions are there any differences? 

I can help with this but I need to know what type of wireless card are you using?

---

### Post by brodiesel on 2008-09-13
Aaah, it seems that none of the restricted drivers are in use in the other kernel (2.6.24-16). In this kernel (2.6.22-14) both of my Atheros drivers are working, but the ATI Fire Gl driver is not. The wireless card is Atheros 102.11.

So why are the drivers working on one and not another (for that matter, why doesnt the fire gl driver work on either)? As far as how to deal with the issue, should I 
a) fix the drivers in the first kernel
b) remove that kernel, i dont need it
c) change the boot order so that it automatically boots from the kernel that works.

i should explain that i dont know how to do any of the above things...

---

### Post by unutbu on 2008-09-13
When you boot with the 2.6.22-14 kernel, you are using the kernel you had used with Gutsy.
Only when you boot with the 2.6.24-16 are you using the Hardy kernel. 

Take a look at /lib/modules. You will see directories whose names are something like
2.6.22-14-generic and 2.6.24-16-generic. Inside these directories are modules that the kernel uses... except that the 2.6.22-14 kernel only looks inside /lib/modules/2.6.22-14-generic and the 2.6.24-16 kernel only looks inside /lib/modules/2.6.24-16-generic.

Since you upgraded to Hardy, you probably want to install the Atheros drivers while booted with the 2.6.24-16 kernel. That way the drivers will get installed into /lib/modules/2.6.24-16-generic.

Unfortunately, I am not familiar with how to install wireless drivers for Atheros cards. 
Perhaps start a new thread asking this question.

---

### Post by adam_kimber on 2008-09-13
When you boot the 16 kernel and go to the restricted drivers (my bad its called Hardware Drivers now, sorry) do you get a box which lists the atheros and the ati drivers? Or are they listed at all? 

I have attached what mine looks like as i use the Nvidia drivers. It says in use and enabled. Usually you have to restart when you enable. 

If you don't have anything listed try going to synaptic or a command line and installing the following package. 

linux-restricted-modules-2.6.24-16-generic

Short of that its into other methods. However the restricted driver / modules should have updated with the new kernel. :confused:

---

