---
title: "Ubuntu 13.10 in Dell Inspiron N5010 freezes when brightness is changed"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by uslochana on 2013-12-29
I have installed Ubuntu 13.10. My computer freezes when brightness is  changed. Therefore everytime this happens I had to force shutdown my  laptop. 
I somehow managed to fix the brightness issue in 12.04 by modifyng the  line in grub as GRUB_CMDLINE_LINUX="acpi_backlight=vendor". But this  doesn't work on 13.10.. 
Please help!!
Thanks

---

### Post by Toz on 2013-12-29
Can you provide some more detailed information?

1. Info about your kernel boot parameters:
```
cat /proc/cmdline
```

2. Info about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. Info about your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

As for a wild, off-the-cuff guess, if GRUB_CMDLINE_LINUX="acpi_backlight=vendor" worked in 12.04, you can try:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
...in 13.10.

---

