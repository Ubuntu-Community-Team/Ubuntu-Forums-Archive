---
title: "problem shutting down"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-20
the shut-down and restart options do not work on my system running ubuntu8.10.when i try doing so,it starts shutting down,but does not,since my screen,CPU,etc. remain on.how do i fix this?

---

### Post by dracayr on 2008-11-20
I had that problem for a long time, but it went away with the upgrade to ibex.. never found a way to fix it, apart from shutting down with 
Alt+Printscreen+R+E+I+S+U+O

dracayr

---

### Post by stonecoldjha on 2008-11-20
doing that everytime would be weird........right.

---

### Post by dracayr on 2008-11-20
well of course you don't have to have all the buttons pressed at once^^ only have alt and printscreen pressed and then press the others one at a time (but without long pauses between them). If you've done it for a few times, it actually is quite fast...

dracayr

---

### Post by Keen101 on 2008-11-20
try doing this in a terminal

it might help you see an error message or figure out where it is freezing

```
sudo shutdown -h +0
```

you can also edit your grub menu.lst file to show you what it is doing on bootup ans shutdown by removing the word "quiet" before the word "splash" on the kernel you use. But, that's something for another discussion i guess.

---

### Post by kngunn on 2008-11-20
Please post your hardware configuration --  I've previously had problems with Dell Optiplex systems that required tossing a switch to the kernel at boot do to ACPI problems (I think that was the problem -- it's been awhile).

---

### Post by philinux on 2008-11-20
> **stonecoldjha said:**
> the shut-down and restart options do not work on my system running ubuntu8.10.when i try doing so,it starts shutting down,but does not,since my screen,CPU,etc. remain on.how do i fix this?

If it's a pre 2000 bios it might need acpi=force adding to the boot stanza in grub.

---

