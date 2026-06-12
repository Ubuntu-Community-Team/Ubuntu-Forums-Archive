---
title: "Installation problems on new Core 2 Quad"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by billvb on 2008-10-20
EDIT: Fixed one problem, now a second occured (similar to the first)


Hello Everyone,

I just got a new dell today and I'm immediately putting Ubuntu on it.

I downloaded ubuntu-8.04.1-desktop-amd64.iso.  Is this the correct file, it seemed like all the others were for 32 bit machines?

When i boot from the CD, it gives the usual ubuntu startup bar, but then puts a debian shell up on the screen and does not boot to gnome.

It seems like I have very limited options at this point, as many of the commands do nothing.

Any help would be greatly appreciated, thank you!

---

### Post by tgunner on 2008-10-20
How much RAM, and what video card do you have?

---

### Post by billvb on 2008-10-20
4 GB ram, integrated intel video card.

The shell is 'initramfs'  I've found a few other posts dealing with this but none seem to help.  Should I try 8.10?

---

### Post by billvb on 2008-10-20
Also, I'm planning to wipe out windows and use all the space for ubuntu.

---

### Post by tgunner on 2008-10-20
What point does the command line screen stop at? Have you tried the "Safe graphics" mode start-up option?

---

### Post by billvb on 2008-10-20
Well, i got it to install by adding the lines (hit F6 in the first screen after booting from the CD):



all_generic_ide_flopp=off irqpoll pci=nomsi


However, I rebooted and then it was taking several minutes.  After a few minutes it DUMPED ME BACK TO THE BUSYBOX!!


Any ideas now?!

---

### Post by Nepherte on 2008-10-21
So you have it installed? If so, press 'e' when you see the grub menu where you have to choose what you want to boot (if you don't get this grub menu, press 'esc' first). Then go to the kernel line and add:
```
all_generic_ide_flopp=off irqpoll pci=nomsi
```

*If* that works, you will have to do it again when you're in ubuntu to make it persistent. Open /boot/grub/menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Find the lines:
```
title    Ubuntu xxxx
root     xxxxxx
kernel   xxxxxx **all_generic_ide_flopp=off irqpoll pci=nomsi**
initrd   xxxxxx

```
and add the part in bold to it.

---

