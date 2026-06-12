---
title: "No keyboard/mouse installing with Live CD (8.04)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by kbubuntu on 2008-09-15
I installed Ubuntu 8.04 on my son's Dell Vostro in a VMWare virtual machine in a snap and loved it. Now I'm trying to set up my 5 yr old Pentium 4 as dual boot with WinXP (now at SP3).

If I recall, all of my Pentium's USB ports were 1.1 at time of purchase but were upgraded to 2.0 with a driver upgrade. It came with 6 PCI slots 2 in front 4 in back. These are all listed in device mgr as Intel 82801EB USB Universal Host Controller. 

When I boot from Live CD, keyboard works for BIOS enter/setup, and for selecting keyboard type from initial menu in Ubuntu installer. Also works for selecting Fx keys (F4, F6) and arrow keys in installation menu. But installer will not accept <Enter> key so I can't select "Install Ubuntu", which I would really, really like to do.

Searched Google + Ubuntu forums, found suggestions re: enabling USB legacy support in BIOS. Tried that, and tried plugging keyboard/mouse into front and back USB connectors. Ie, tried front connectors with/without USB legacy support, and then back connectors with and without.

Suspecting the Intel hardware/updated with USB2.0 driver was not entirely up to full USB 2.0 spec I bought a VIA USB 2.0 PCI card and installed that. Works fine in Windows, but same result when attempting to install Ubuntu with/without USB legacy support enabled in the BIOS. 

Does anybody have any tips/pointers/suggestions as to how I might get around this? The goal is to set this up for dual boot and, unless I'm mistaken, I need to use the Live CD to accomplish this...

---

### Post by arch0njw on 2008-09-16
I hate to recommend this, but have you tried installing through Windows using wubi?  Personally, I don't like how wubi works, but I know a lot of people who have had luck with it.  So I guess I can probably go suck an egg, eh?

---

### Post by scorchgeek on 2008-09-16
Have you tried text-mode installation? Sometimes the Live CD just doesn't work.

---

### Post by Therion on 2008-09-16
Have had this problem... Lol... What a PITA, huh?

Solution:  Beg, borrow or steal a PS2 connector keyboard.  Install and update Ubuntu fully.  Install USB keyboard and you're good to go.

---

### Post by scorchgeek on 2008-09-16
I haven't tried, but it's possible a USB-to-PS2 adapter would also work. You can probably find one at a garage sale or from a friend with a few spare computer parts. They're really cheap, too, so not much loss if it doesn't help. Like the person above said, USB should work fine once installed.

---

