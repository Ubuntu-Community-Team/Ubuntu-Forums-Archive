---
title: "[SOLVED] Webcam issues - Third thread :) Keep on truckin!"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-22
Hey, 
So this is my third thread about webcams, Same problem, but i'm wiser for it. ( or so i comfort myself)
Anyway, I've been digging around looking for a driver for my MSI Starcam 370i usb webcam 
With help i was able to load both gspca and ov511, and then the cam worked.... once.
Since then nothing. I've also come across the Generic Microdia-SN9CXXX Video4Linux1 & Video4Linux2 driver. 
Which can be found here:

[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

But tis both for a previous version of Ubuntu and is i386. I use AMD64. I half heartedly attempted forcing architecture but I didn't really expect it to work and it didn't.

So! any obscure (stable) drivers that you have a link to ? any patches for gspca or ov511 ? Any ideas on turning my pretty lil webcam into a wonderful desktop ornament that both enhances the lighting and lends depth to this little corner of my room ?

Any posts welcome.

Thanks guys....

---

### Post by Amarsingh0793 on 2008-07-23
There are many tools in synaptic to help with webcams, like cheese and Webcam monitor.

Good Luck :)

---

### Post by BGFG on 2008-07-24
> **Amarsingh0793 said:**
> There are many tools in synaptic to help with webcams, like cheese and Webcam monitor.

Good Luck :)

Thanks man,
But i think my problem is at the driver level, i have cheese installed and all i get is static. Also Ekiga and Skype, no webcam functionality.
I just upgraded to kernel 20 and now in cheese i see the little gnome foot doing the toe thing so some hope....

---

### Post by philinux on 2008-07-24
[http://www.ebuyer.com/product/119159](http://www.ebuyer.com/product/119159)

This works out the box.

Nearly all webcams have an issue with the mic though.

Or this might help.
[http://www.linux-drivers.org/usb_webcams.html](http://www.linux-drivers.org/usb_webcams.html)

---

### Post by BGFG on 2008-07-24
So many projects. Talented programmers using time that could otherwise be spent on the main OS architecture. Why won't these hardware manufacturers just give us linux ready drivers ?

---

### Post by BGFG on 2008-07-28
Thanks for all the suggestions and help, I installed camorama and now it works. Image is quite dark though. but at least i know it works now.

---

