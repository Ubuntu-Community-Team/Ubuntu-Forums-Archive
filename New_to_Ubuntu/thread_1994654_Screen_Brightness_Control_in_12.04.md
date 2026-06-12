---
title: "Screen Brightness Control in 12.04"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by tony430 on 2012-06-03
Hi, I've been using Ubuntu 12.04 on my Acer Aspire 4736z for almost a month now and I like the experience. I just have a small problem: When I first installed it there was no back-light and I cannot adjust the screen brightness. So I searched the forums and I learned that typing ```
sudo setpci -s 00:02.0 F4.B=00
``` on the terminal would turn the back-light to the highest setting and that including this command to the file ```
/etc/rc.local
``` would make Ubuntu call up that command automatically when I boot up the computer. So that issue has been taken cared of but I still had no way to adjust the screen brightness using the key combinations on the laptop (Fn+Left or Right Arrow, to decrease or increase, respectively). So I found another suggestion on the internet and it says that I can modify the file ```
/etc/default/grub
``` and look for the line [COLOR="Blue"]**```
GRUB_CMDLINE_LINUX=""
```**[/COLOR] and inside the quotation marks type **[COLOR="blue"]```
acpi_backlight=vendor
```[/COLOR]** then save. Then enter the command ```
sudo update-grub
``` on the terminal then restart the PC. After this [COLOR="blue"]**[SIZE="3"]I was able to adjust the screen's brightness but the odd thing is that the key combination for increasing the brightness decreases it and the combination for decreasing the brightness increases it.[/SIZE]**[/COLOR]

Is there a way to correct this?

---

### Post by Toz on 2012-06-03
Along with acpi_backlight=vendor, try adding acpi_osi=Linux:
```
acpi_osi=Linux acpi_backlight=vendor
```



If that doesn't fix it, try this combination:
```
acpi_osi=\"Linux\" acpi_backlight=vendor
```



Or, just:
```
acpi_osi=\"Linux\"
```
...with this last one, make sure you have the right number of quotes:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
```

---

