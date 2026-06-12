---
title: "Screen Brightness - No Steps"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by roton on 2012-07-23
When I use my keyboard to change brightness on my laptop it just jumps straight from minimum to maximum (or maximum to minimum if decreasing) without stopping.

If I use the slider for brightness in Ubuntu (under settings), I can drag it, but when I let go it just slides straight to the maximum or minimum.

The only way to control brightness at a level in between maximum and minimum is to "echo ***x*** > /sys/class/backlight/acpi_video0/brightness". ***x*** = a value from 0-7.

Any ideas as to what's wrong?

edit: Using Ubuntu 12.04, 3.2 kernel.

edit 2: It was annoying so I formatted and reinstalled. This fixed the problem... until I updated. One of the updates is causing this but I don't know which one (there were well over 300 after a new install).

---

### Post by roton on 2012-07-24
Ok it seems to be the new kernel (3.2.0-27) causing the issue. But since it's an "important update" should I put up with the inconvenient brightness controls?
Is it even safe to stay on the older 3.2.0-23?

---

### Post by NikTh on 2012-07-24
Hi , 
did you try to add a parameter in grub ? 
open 
```
gksudo gedit /etc/default/grub
```find the line 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
and make it 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"**

save the document and go to terminal again and
```
sudo update-grub
```
Reboot your pc for changes take effects

If works ok , 
if not , then i assume you understand how you can undo the above change. 

Thanks

---

### Post by roton on 2012-07-24
Thanks NikTh, that sort of worked. I can now adjust the brightness using the slider under settings. However, using the keys now bumps it up to max and decreases to only 1 setting below max, it refuses to go lower no matter now much you press the key.

---

### Post by NikTh on 2012-07-24
> **roton said:**
> Thanks NikTh, that sort of worked. I can now adjust the brightness using the slider under settings. However, using the keys now bumps it up to max and decreases to only 1 setting below max, it refuses to go lower no matter now much you press the key.

Hi , 
ok maybe you want to test with one parameter.. e.g , only acpi_osi=Linux or acpi_backlight=vendor . 
You know the way how to modify the file.. so you can test one parameter at time. 

do not forger to **update-grub**

Thanks

---

### Post by roton on 2012-07-24
It finally works now using:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi="

Thanks for all your help. Have marked as solved.

edit: Yay my 50th post... finally I can modify my profile ;)

---

### Post by ronogara on 2012-07-25
> **roton said:**
> It finally works now using:

GRUB_CMDLINE_LINUX_DEFAULT="quite splash acpi_osi="


this works for me too. Must have been the kernel update. Thanks for the fix!!

---

