---
title: "Printing from Windows XP in Virtualbox possible?"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by kramer65 on 2013-03-14
Hi People,

I've got a printer ([Dell AIO Photo 964]("http://www.dell.com/downloads/emea/products/printer/964_en.pdf")) for which there are only Windows XP or Vista drivers. Unfortunately I can't get it to work using CUPS in Ubuntu 12.04

Is it possible to run Windows XP in virtualbox in Ubuntu 12.04 and print from there? Or do I need to install a separate Windows XP next to my Ubuntu (which would be quite unhandy to constantly reboot if I would need to print something..)

All tips are welcome!

---

### Post by Paqman on 2013-03-14
If it's not working in your host OS (Ubuntu) then it won't work in the guest OS either. The guest OS doesn't have direct access to hardware, it sits on top of virtual hardware (which is really just software), and any access to peripherals comes via the host OS.

If you can plug the printer into another machine on your network and set it up as a network printer you should be able to access it that way.

---

### Post by kramer65 on 2013-03-14
I was already afraid that this would be the case. Unfortunately we've only got mac and linux computers in our network.

But I think I will make some room on one of the linux computers for a small XP installation then. I thought I had said goodbye to Windows forever.. *sights*.. :|

Thanks for your answers anyway! I wish you a beautiful day!

---

### Post by Paqman on 2013-03-14
Tbh, printers are pretty cheap these days. It might be less hassle to get one that's compatible with your computers.

---

