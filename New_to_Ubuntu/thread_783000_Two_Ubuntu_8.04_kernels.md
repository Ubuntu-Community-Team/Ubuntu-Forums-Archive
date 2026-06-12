---
title: "Two Ubuntu 8.04 kernels???"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by deerewright on 2008-05-05
I upgraded to 8.04 from 7.10.  Now I have two different kernels in my grub menu:

Ubuntu 8.04, kernel 2.6.24-16-generic

Ubuntu 8.04, kernel 2.6.22-14-generic

1.) What is the difference/Why do I have two kernels?

2.) Can I remove one of them (not from the grub menu, but from the hard                   drive? If so, how?

---

### Post by NullHead on 2008-05-05
> **deerewright said:**
> I upgraded to 8.04 from 7.10.  Now I have two different kernels in my grub menu:

Ubuntu 8.04, kernel 2.6.24-16-generic

Ubuntu 8.04, kernel 2.6.22-14-generic

1.) What is the difference/Why do I have two kernels?

2.) Can I remove one of them (not from the grub menu, but from the hard                   drive? If so, how?

I would simply uninstall the one with the lowest version number; e.g 2.6.22-14, the old gutsy kernel. Use synaptic to accomplish this.

The lower version number is the old kernel brought over from your upgrade. You don't need it anymore and it'll only take up space on your hard drive.

---

### Post by SunnyRabbiera on 2008-05-05
This is normal, as Ubutu usually gives a primary kernel and a backup one...
Plus you updated from gutsy so that is also normal.
I would not worry about having two kernels, it really doesn't take up any extra space and its good to have around just in case something goes wrong.

---

### Post by deerewright on 2008-05-05
> **NullHead said:**
> I would simply uninstall the one with the lowest version number; e.g 2.6.22-14, the old gutsy kernel. Use synaptic to accomplish this.


How do I use synaptic to remove the old kernel?

Also, I see two gzip files in my boot directory and two backup files:

initrd.img-2.6.22-14-generic.gzip and .bak

initrd.img-2.6.22-16-generic.gzip and .bak

Can I delete these?

---

### Post by NullHead on 2008-05-05
well what I would do is open synaptic and search for "linux" and remove linux-image-2.6.22-14-generic, linux-headers-2.6.22-14-generic and linux-restricted-modules-2.6.22-14-generic. The names on those might be a little bit off, but like SunnyRabbiera said; it doesn't really matter. You can leave all those and it won't bother you. Just as long as you're booting into the kernel with the highest version number.

---

