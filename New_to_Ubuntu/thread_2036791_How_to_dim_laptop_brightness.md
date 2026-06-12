---
title: "How to dim laptop brightness"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by dimension123 on 2012-08-02
I am wondering on how to dim my screen on my laptop? I am currently using ubuntu. I went to system settings , brightness but it does not have a way to change the brightness. Does anyone know how ??

---

### Post by Haltron on 2012-08-02
Hi, i solved this by firstly installing xbacklight. Then i placed  acpi_backlight=vendor at the end of every line beginning with linux in my grub.cfg located at /boot/grub/grub.cfg using gedit.

Then i created an xbacklight.desktop file to initiate my desired backlight levels at bootup


hope this helps

---

### Post by dwhite on 2012-08-02
i'm not sure what version of Ubuntu you are using, if 12.04 just go to system settings -->open "brightness and lock" and change brightness from there, see screen shot.

---

### Post by dimension123 on 2012-08-05
Wow, thank you very much Dwight! I never saw the scroll bar , its hard to see it. They should change the color to make it appear more. Thanks again!

---

