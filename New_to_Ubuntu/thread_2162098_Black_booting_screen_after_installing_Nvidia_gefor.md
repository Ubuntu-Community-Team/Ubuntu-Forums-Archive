---
title: "Black booting screen after installing Nvidia geforce driver."
date: 2013-07-13
forum: New to Ubuntu
---

### Post by arnav803 on 2013-07-13
Hi.I have Ubuntu 12.10 32 bit and I recently installed nvidia driver in my desktop.I am facing no issues just that the Ubuntu booting screen doesn't come and instead of a black screen is shown and then I am directly at the log-in screen.I just want to know why is this happening and is there any solution to it.[IMG]http://handytutorial.com/wp-content/uploads/2012/10/ubuntu-logo.png[/IMG]
 I want this screen back instead of a black screen or this one-->
[IMG]http://i.stack.imgur.com/U39zl.jpg[/IMG]

---

### Post by coldcritter64 on 2013-07-13
> **arnav803 said:**
> Hi.I have Ubuntu 12.10 32 bit and I recently installed nvidia driver in my desktop.I am facing no issues just that the Ubuntu booting screen doesn't come and instead of a black screen is shown and then I am directly at the log-in screen.I just want to know why is this happening and is there any solution to it.<snipped image>
 I want this screen back instead of a black screen or this one-->
<snipped image>

I had similar occurring after installing the nvidia restricted drivers with this install of 12.04. I was using it for a while and noticed it corrected itself after I used some commands when altering the grub menu. I ran update-grub and update-initramfs, I suspected at the time my use of update-initramfs may have updated the information in the initramfs  for the Plymouth screens.

I'd suggest you try the code below in a terminal,
```
sudo update-initramfs -u
```
then when the code finishes, close the terminal and reboot the machine. You may not note the end Plymouth screen changing until subsequent reboots even if the code works; if it doesn't change try another reboot immediately to note if it has worked fully.

**If the code does fix the screens and you have more than one kernel installed**, to update-initramfs for all your kernels installed, run the code below,
```
sudo update-initramfs -u -k all
```

---

### Post by dannyboy79 on 2013-07-13
what does your grub boot file look like? if you removed splash from the boot line then you won't see a splash screen anymore

---

### Post by coldcritter64 on 2013-07-13
> **dannyboy79 said:**
> what does your grub boot file look like? if you removed splash from the boot line then you won't see a splash screen anymore

+1 good idea to check that OP. An easy way to check is with terminal,
```
cat /etc/default/grub | grep GRUB_CMDLINE_LINUX
``` this should return 2 entries the one with _DEAULT on the end here shows the splash entry. From my install
> :~$ cat /etc/default/grub | grep GRUB_CMDLINE_LINUX
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by arnav803 on 2013-07-13
Thanks guys that helped me and i also found an excellent guide to do this --->[http://jechem.blogspot.be/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html](http://jechem.blogspot.be/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html) . Thanks again!!:P

---

