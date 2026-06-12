---
title: "brightness function"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by cody14 on 2014-09-01
So I have a Asus g750jm laptop with the Intel i7 and a nvidia 860m. My problem is the function keys for the back light don't work. I have tried every fix google has supplied whether it be from editing grub with the backlight vendor commands or making a config file for the Intel_backlight. Ive tried everything. Works for everyone else's rig but mine. Bios allows the brightness keys but Ubuntu does not.

---

### Post by cody14 on 2014-09-01
no one has a asus like mine?

---

### Post by Frantic_Earthling on 2014-09-17
> **cody14 said:**
> no one has a asus like mine?

I have.
But I do not have the solution.
I did the same on my G750JZ and tried everything in terms of editing grub with the backlight vendor commands or making a xorg config file, to no avail.

---

### Post by Frantic_Earthling on 2014-09-17
This worked!

[http://ubuntuforums.org/showthread.php?t=2208852&highlight=brightness+asus](http://ubuntuforums.org/showthread.php?t=2208852&highlight=brightness+asus)

Add "acpi_osi" at the end of GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in  /etc/default/grub

which gives

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Then save and update grub.

---

### Post by rolkin on 2014-09-17
Glad you found a solution. I also have to add "acpi_osi=" to the grub config and i have an Asus Zenbook UX302LA. This is actually really common for the newer Asus'.

---

