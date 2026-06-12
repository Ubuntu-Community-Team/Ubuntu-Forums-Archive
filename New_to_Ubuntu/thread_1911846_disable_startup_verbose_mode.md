---
title: "disable startup verbose mode"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by cacs on 2012-01-19
Hi there.

How do I disable startup verbose mode?

ty, C.S.

---

### Post by jonobr on 2012-01-19
Hello


In the file
```
/etc/default/grub
```
you have the ability to reduce the amount of information on boot up.
Make a backup of grub before you start changing anything but what your looking for is 
GRUB_CMDLINE_LINUX_DEFAULT
entering quiet in there should work- but research the options

cheers

---

### Post by RobertUI on 2012-01-19
Yup... by default mine is set to  "**quiet splash**"

---

### Post by cacs on 2012-01-20
Thank you guys.
When I was trying to put a new bootsplash must altered something because the "quiet splash" option doesn't work... I just see a bunch of lines with OK's in the end... :(

ty, C.S.

---

