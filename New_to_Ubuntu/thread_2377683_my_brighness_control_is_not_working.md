---
title: "my brighness control is not working?"
date: 2017-11-15
forum: New to Ubuntu
---

### Post by napra on 2017-11-15
the brightness control is not working, why?
in my experience in windows, it need to updating the graphic driver, but i dont know how to update in ubuntu,today is my first day using ubuntu

---

### Post by Frogs Hair on 2017-11-15
What version of Ubuntu and what type of computer ? If there are drivers available for you computer they would be listed in software & updates >additional drivers.

---

### Post by napra on 2017-11-15
> **Frogs Hair said:**
> What version of Ubuntu and what type of computer ? If there are drivers available for you computer they would be listed in software & updates >additional drivers.

im use ubuntu 17 with laptop, integrated graphics card intelhd3000

---

### Post by Holger_Gehrke on 2017-11-16
Display brightness - or rather backlight intensity - is not controlled by the graphics driver bu&#359; by ACPI, the Advanced Control and Power Interface. This is a hard- and software specification most modern systems implement with varying degrees of success. ACPI on Linux is part of the kernel and control is done through udev. 

Normally this is set up on installation and just works - you hit the right (function) keys and the display goes brighter or darker. But some Laptops have their little quirks and you need to tell the system to work around them. To find out what to do. search for "Linux acpi brightness" and your laptop's manufacturer and model.

Holger

---

### Post by uragno on 2017-11-16
> **napra said:**
> im use ubuntu 17 with laptop, integrated graphics card intelhd3000

Intel HD3000 also here! You could try solutions on post#2 or post#3 here: [https://ubuntuforums.org/showthread.php?t=2377642](https://ubuntuforums.org/showthread.php?t=2377642).

If you need furher help on how-to-do-it feel free to ask.

Bye!

---

