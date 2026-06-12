---
title: "Have to hold button at boot up(Ibex)"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by rojodojo on 2008-11-01
I've installed both amd64 version of Ubuntu & Xubuntu 8.1, but when it gets the the load screen loading up, I have to push a button on my keyboard for the progress bar to progress. I've tried installing it by live usb and cd-rom, but I still get the same problem.
Is this a new problem in Intrepid Ibex?

---

### Post by rojodojo on 2008-11-02
Edit - It seems this problem only happens on my laptop. I had gOS on previously, but I removed it with gParted.
Does anyone know why it would be forcing me to push on the keyboard to continue loading?

---

### Post by JJ85 on 2008-12-09
I'm experiencing the same problem on a laptop with a 64 bit processor and I have ibex 32 bit installed. Can some one please help?

---

### Post by phidia on 2008-12-09
Hi, Just want to validate that I've seen this behavior-I use 64 bit also.
Searching this...

Try > acpi=noirq as a boot option and check out [this]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops") Ubuntu/HP laptop blog for more.

Added) To make that edit if you want to try that open a terminal and do this (copied from another thread):
> gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq


---

