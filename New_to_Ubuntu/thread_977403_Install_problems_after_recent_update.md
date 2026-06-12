---
title: "Install problems after recent update"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by CAMEMBEAR on 2008-11-10
When booting up computer following an update yesterday,  X-windows has failed and we get the following message "Install problem! The configuration defaults for GNOME Power Manager have not been installed correctly please contact your system administrator" we then get similar messages regarding other applications etc, but we can access the desktop packages eg Thunderbird Open Office Spreadsheet, but there is no wallpaper - just black background and no toolbars at top or bottom of screen. What do we do?

---

### Post by drs305 on 2008-11-10
I've done some researching on this and haven't found a definitive answer. The following things worked for some users but not all:

Reinstall gnome-power-manager.
```
sudo aptitude reinstall gnome-power-manager
```

Re-enable your video card via System, Admin, Hardware Drivers.

or:
```

sudo dpkg --configure -a
sudo apt-get -f install

```

These may be long shots but won't hurt your system should they not solve the problem.

---

### Post by CAMEMBEAR on 2008-11-10
Thanks for that - but I'm afraid it didn't work. Any other ideas?

---

