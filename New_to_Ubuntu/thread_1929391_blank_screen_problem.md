---
title: "blank screen problem"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by amreshravi on 2012-02-21
hello,  i have hp pavilion g6 laptop. hardware confgs are 3420apu, dual graphic amd hd7450 and 6520, 4gb ram. i tried every way to run ubuntu 11.10 (live boot and also tried to install inside windows), i am getting the same problem after grub menu i get blank screen. i tried to boot by changing quite and splash to no splash and also tried adding radeon.modeset=0. nothing works. i need help, i m new to Linux.

---

### Post by Krytarik on 2012-02-22
> **amreshravi said:**
> i tried to boot by changing quite and splash to no splash and also tried adding radeon.modeset=0. nothing works.
How about "nomodeset"!?:

[http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Hope that helps.

---

### Post by Bucky Ball on 2012-02-22
> **Krytarik said:**
> How about "nomodeset"!?:



Yep, add that to the kernel line when you edit the kernel line in the opening grub menu.

---

