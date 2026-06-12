---
title: "Help!!"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by onac255 on 2008-05-25
Ok so I finally updated ubuntu with like 89 file downloads and downloaded the two drivers one for the ATI chip and the other for the Broadcom Wireless card.

Well I restarted the system and now after about a second of the "ubuntu" load screen it goes to  a black screen stating the following

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

What in the heck do I do now? I did try 'help' and tried typing in some commands but nothing works.

---

### Post by Prospero2006 on 2008-05-25
Ok, the grub boot loader is not picking up the correct kernel. 
There are a couple of things you can do:

First, when you first turn on the computer, get to the grub boot loader options screen and choose an earlier kernel.

Second, boot a live cd and take a look at your /boot/grub/menu.lst 
file.

---

### Post by jemate18 on 2008-05-26
> **onac255 said:**
> Ok so I finally updated ubuntu with like 89 file downloads and downloaded the two drivers one for the ATI chip and the other for the Broadcom Wireless card.

Well I restarted the system and now after about a second of the "ubuntu" load screen it goes to  a black screen stating the following

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

What in the heck do I do now? I did try 'help' and tried typing in some commands but nothing works.

Can you please tell what version of ubuntu you use?
I have experienced this in compiling a new kernel. 
In some ways, it has not been able to detect your harddrive and that it
wasn't able to mount your root partition, therefore, it boots that way.

In my case, I just choose my first kernel in the grub menu selection of kernel,

---

### Post by onac255 on 2008-05-26
how do I get to the grub options screen?

---

### Post by shifty_powers on 2008-05-26
> **onac255 said:**
> how do I get to the grub options screen?
press escape when you boot ;)

---

### Post by onac255 on 2008-05-26
None of the kernels work...

---

### Post by Duck2006 on 2008-05-26
> **onac255 said:**
> None of the kernels work...

Can you login with recovery mode?

---

### Post by grandours on 2008-05-26
I'm having the same problem as onac255.  The only way I can get up and running is by choosing the older kernel (-16 instead of -17) from the GRUB boot loader menu.

---

