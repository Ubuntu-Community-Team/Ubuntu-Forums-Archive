---
title: "How to find out what sd my flash drive is?"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-15
Part of a command asks for the location of my flash drive ("of=/dev/sdx"). How do I discover which "sdx" is the flash drive? I tried "dmesg" but could not understand what was the flash drive.

---

### Post by jrb993 on 2014-01-15
Your best bet is to run:

[FONT=courier new]df -h
[/FONT]
And check out the output. One of the drives listed will be your flash drive. Under the "size" column, look for a size that's closest to your flash drive's size.[FONT=courier new]
[/FONT]

---

### Post by Jason_Gibson on 2014-01-15
There is also ```
lsblk
``` which will only show physical devices.

---

### Post by Bashing-om on 2014-01-15
bc.haynes; Hi !
In buntu there are always options:
how bout this one:
```

sudo fdisk -l

```

many paths ->
[INDENT][INDENT]lead to one end
[/INDENT][/INDENT]

---

### Post by buzzingrobot on 2014-01-15
If you have more than one USB device attached, check each time you attach a USB stick.  Things can change. I've overwritten a permanently attached backup drive when I thought I was burning an image to a stick.

---

