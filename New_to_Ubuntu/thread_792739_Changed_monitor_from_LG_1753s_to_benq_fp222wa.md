---
title: "Changed monitor from LG 1753s to benq fp222wa"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by markotitel on 2008-05-13
Hi,

I changed my monitor and wanted to setup new one manually.
Whe I tried to do it I couldnt find it under supported monitor types.

Then tried uninstalling vga driver Administration > Hardware Drivers > Disable , restarted ubuntu, enabled Hardware Drivers and it setup  correctly.

With exact monitor type. Where from monitor driver is loaded?

---

### Post by andrewski on 2008-06-11
My guess is that your /etc/X11/xorg.conf (the file that drives most of your graphical configuration) would need to be reset. You can do that via ```
sudo dpkg-reconfigure --default-priority xserver-xorg
```. This will automatically make a backup of your xorg.conf as xorg.conf_backup_date. Then reboot and see if your new monitor works correctly.

In this case, the driver will just change the video card, not the monitor/display.

---

