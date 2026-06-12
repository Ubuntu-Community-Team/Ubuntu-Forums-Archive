---
title: "Brightness settings not working"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by StardustLuna on 2012-08-29
I have a Hp Pavilion dv7 with 12.04 on it. My brightness keys or the slider in the system settings do nothing in changing the brightness. Is there something or other that I need to install? It'd really help because this bright screen is draining my battery.

---

### Post by Raphicerus on 2012-08-29
> **StardustLuna said:**
> I have a Hp Pavilion dv7 with 12.04 on it. My brightness keys or the slider in the system settings do nothing in changing the brightness. Is there something or other that I need to install? It'd really help because this bright screen is draining my battery.

I had the same situation on a Sony laptop, that I solved by installing the control panel for the proprietary display hardware (called "NVIDIA X Server Settings"). The brightness keys still didn't work, but the graphic interface allowed me to turn the brightness down.

---

### Post by Mark Phelps on 2012-08-29
Such "special keys" generally do not work because (1) they require special drivers (that only come through the OEM for MS Windows), and (2) there is no way to install those drivers in Linux.

However, as mentioned, if you have an AMD or Nvidia video chipset, you may then be able to install restricted drivers -- which then might provide the option to control screen brightness.

To see what video chipset you have, open a terminal and enter "lspci" -- and look for the line containing "VGA".

---

### Post by StardustLuna on 2012-08-29
Here's the line that you requested. 

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

---

### Post by NikTh on 2012-08-29
Hi , 
try the workaround with kernel boot options. See here on how to set : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I suggest **acpi_osi= **
and **acpi_backlight=vendor**

Thank you

---

### Post by StardustLuna on 2012-08-29
> **NikTh said:**
> Hi , 
try the workaround with kernel boot options. See here on how to set : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I suggest **acpi_osi= **
and **acpi_backlight=vendor**

Thank you

Just want to make sure before I try it. This won't turn off my fans will it? I saw it mentioned in the other thread. Because I'm pretty sure that I need them. :?

---

### Post by NikTh on 2012-08-29
> **StardustLuna said:**
> Just want to make sure before I try it. This won't turn off my fans will it? I saw it mentioned in the other thread. Because I'm pretty sure that I need them. :?

No , 
acpi=**off** is the dangerous parameter. 

Thanks

---

