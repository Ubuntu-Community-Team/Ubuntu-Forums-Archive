---
title: "Unable to change Laptop LCD Backlight Brightness"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by abc617 on 2013-03-30
I just got Ubuntu on my laptop as my first Linux OS. I got everything set up as I like it, but now theres a problem where I can't set/change the LCD backlight brightness on my laptop.

My computer is an Acer V3-551. I'm using the fglrx AMD display drivers. I had to fiddle around with it in order to get a dual monitor display working. But every since I installed the whole Catalyst Control panel, I can't adjust the screen brightness. I tried adjusting the brightness slider in the settings and the FN-brightness control keys on my laptop. Brightness does not change. When I do change the brightness, I clearly see the brightness level-indicator change, but the laptop brightness does not clearly change. 

I've tried changing the following in my " /etc/default/grub" and ran "updated-grub" after make the changes
-Changed "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" --> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux"
-Changed "GRUB_CMDLINE_LINUX="" to ---> "GRUB_CMDLINE_LINUX="acpi_backlight=vendor"" 

If anyone has a possible solution, it would be appreciated if you could share it, because I've yet to find someone with a problem similar to mine with a working solution!

---

