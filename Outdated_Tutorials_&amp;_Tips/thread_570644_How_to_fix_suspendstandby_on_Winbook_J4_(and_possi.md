---
title: "How to: fix suspend/standby on Winbook J4 (and possibly other laptops)"
date: 2007-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by M4cb0y on 2007-10-08
After lots of searching I finally found out how to fix suspend on this laptop. I thought I'd share it in case it's useful for anyone else, it was really helpful for me..

First, open up the terminal and edit the file /etc/default/acpi-support
```
sudo nano /etc/default/acpi-support
```

Scroll down to the entry that says
 ```
ACPI_SLEEP_MODE=mem
```
and change it to:
```
# ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby
```
Close the file and execute :
```
sudo /etc/init.d/acpid restart
```
Then try out suspend and see if it works.

This is probably really obvious but it took me forever to find out that this was all I had to do. I searched forever and tried a bunch of workarounds, but nothing worked until I just did this. Hopefully someone else will find this useful too :)

---

