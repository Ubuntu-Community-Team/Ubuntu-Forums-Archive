---
title: "gedit error gedit:2128"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by Xpdin on 2015-06-20
I am a beginner Linux user
I use Lubuntu Core...


I have been trying to add 


    ```
echo 9 > /sys/class/backlight/acpi_video0/brightness

```

to ```
/etc/rc.local
``` and every time when I change something in rr.local appears in the terminal:


    ```
(gedit:2198): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files



```And still the ```
echo 9 > /sys/class/backlight/acpi_video0/brightness
``` doesn't work how it should after the restart.


Thank you.

---

### Post by dino99 on 2015-06-20
[http://ubuntuforums.org/showthread.php?t=2088043](http://ubuntuforums.org/showthread.php?t=2088043)  (glance at the latest post)

---

### Post by GrouchyGaijin on 2015-06-21
> **Xpdin said:**
> I am a beginner Linux user
  ```
/etc/rc.local
``` 

Just a guess by I *think* files in /etc/ have to be modified as root.
Have you tried editing the file by launching ```
sudo gedit
``` ?

---

