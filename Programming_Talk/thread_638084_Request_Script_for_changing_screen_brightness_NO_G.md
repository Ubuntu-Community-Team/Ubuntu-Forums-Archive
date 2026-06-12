---
title: "Request: Script for changing screen brightness NO GUI REQUIRED"
date: 2007-12-11
forum: Programming Talk
---

### Post by Calebh on 2007-12-11
The brightness keys on my laptop do not work under ubuntu. I can change the screen brightness with the command:

sudo -s
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness
exit

100 is full brightness, 50 is half brightness, ect. These are the numbers that work:
12 25 37 50 62 75 87 100

The keys for changing the brightness is:
Brightness up: Fn+up arrow
Brightness down: Fn+down arrow
On the Dell Inspiron 1501.

Maybe someone could make a script that checks the current brightness and changes the brightness when the user uses the brightness.

---

