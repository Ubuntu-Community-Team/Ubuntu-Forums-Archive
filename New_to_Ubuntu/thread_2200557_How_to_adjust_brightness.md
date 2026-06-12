---
title: "How to adjust brightness?"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by RadScorpius on 2014-01-20
My brightness appears to be on max, none of the methods i found online worked for me. my computer is Lenovo Thinkpad E540.

Please help
Thanks

---

### Post by fosterD on 2014-01-20
You may want to try this
```
sudo sh -c 'echo -n $(cat /sys/class/backlight/acpi_video0/max_brightness) > /sys/class/backlight/acpi_video0/brightness' 
```
Also, can you adjust brightness from BIOS? it was happened on my Dell laptop

---

### Post by Toz on 2014-01-20
> **RadScorpius said:**
> My brightness appears to be on max, none of the methods i found online worked for me. my computer is Lenovo Thinkpad E540.

Please help
Thanks

Which version of Ubuntu are you using?

Which methods have you tried that were unsuccessful?

Please provide some more information by running the following commands in a terminal window and posting back the results within **[noparse]```
 
```[/noparse]** tags:
1. You current kernel boot line:
```
cat /proc/cmdline
```
2. Info about your video card(s):
```
lspci -k  | grep -A2 VGA
```
3. Info about your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

