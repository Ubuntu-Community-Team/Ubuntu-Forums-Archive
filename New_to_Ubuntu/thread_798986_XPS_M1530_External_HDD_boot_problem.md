---
title: "XPS M1530 External HDD boot problem"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by venky80 on 2008-05-18
I have a new DELL xps M1530 
I am trying to boot ubuntu which is loaded in my external USB HDD, I also have grub installed in the external HDD.
I have changed the boot sequence and trying to boot off the external USB HDD but i just see a flash of the grub and the computer boots into the grub installed in my laptops internal HDD.
How can I make the laptop stop doing it.
Also I was using the external HDD ubuntu in my old toshiba laptop and it could easily boot off it.
I have A08 firmware.

---

### Post by garyedwardjohnston on 2008-05-18
Just a pure guess...try turning off USB high speed (2.0) from BIOS.

There are known issues with high speed USB devices in the kernel.

---

