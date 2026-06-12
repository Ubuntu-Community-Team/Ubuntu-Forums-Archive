---
title: "UBUNTU disable auto brighness"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by tux-world on 2013-06-28
im using latest version of ubuntu and using KDE, after changing brighness in `Screen Brighness` from kde battery settings after 10~15 second automatically change that without any delay.

detail: Samsung Laptop 300e5x a0j

shell command:

```
    xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto 
```

result:
```

    tux-world@tux-world ~ $ xrandr --output LVDS --set BACKLIGHT 102 --set BACKLIGHT_CONTROL legacy --output VGA --auto
    warning: output LVDS not found; ignoring
    warning: output VGA not found; ignoring
    X Error of failed request:  BadRROutput (invalid Output parameter)
      Major opcode of failed request:  140 (RANDR)
      Minor opcode of failed request:  15 (RRGetOutputProperty)
      Serial number of failed request:  30
      Current serial number in output stream:  30
```

shell command:

```
    tux-world@tux-world ~ $ cat /sys/class/backlight/samsung/brightness 
```

result:

```
    6
```

after change:

```
    tux-world@tux-world ~ $ cat /sys/class/backlight/samsung/brightness 
```

result:

```
    2
```

after 10~15 second automatically change:
result:

```
    6
```

---

