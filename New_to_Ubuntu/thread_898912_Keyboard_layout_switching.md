---
title: "Keyboard layout switching"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by PunkLV on 2008-08-23
Hello. The problem is: after every reboot I have to manually remove and re-add RU layout, so it would work. I belive this happens due to nvidia's xorg.conf, or something is not written properly there. 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Any help, hint, guess would be much appreciated

---

### Post by unutbu on 2008-08-23
Manually set the keyboard as you want it, then type
```

grep -n -A10 'Identifier.*Keyboard' /etc/X11/xorg.conf
xprop -root | grep XKB

```
Please post the output.

---

### Post by PunkLV on 2008-08-23
grep -n -A10 'Identifier.*Keyboard' /etc/X11/xorg.conf

38:    Identifier     "Keyboard0"
39-    Driver         "keyboard"
40-EndSection
41-
42-Section "Monitor"
43-    Identifier     "Monitor0"
44-    VendorName     "Unknown"
45-    ModelName      "Unknown"
46-    HorizSync       30.0 - 110.0
47-    VertRefresh     50.0 - 150.0
48-    Option         "DPMS"

xprop -root | grep XKB

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "logiultrax", "us,ru", ",winkeys", "grp:alt_shift_toggle"

---

### Post by unutbu on 2008-08-23
Log out. (So neither GNOME or Xorg is touching xorg.conf)
Press Ctrl-Alt-F2.
Log in.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20080823
sudo nano /etc/X11/xorg.conf
```
Edit Line 38--40 to look like this:
```

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "logiultrax"
    Option         "XkbLayout" "us,ru"
    Option         "XkbVariant" ",winkeys"
    Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

```
Save, exit.
Ctrl-Alt-F7. Login and see if it works.

If that does not work, press Ctrl-Alt-F2 to get back to the text terminal. 
```

sudo nano /etc/X11/xorg.conf
```
Try
```

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "logiultrax"
    Option         "XkbLayout" "us,ru"
    Option         "XkbVariant" ",winkeys"
    Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

```
Save, exit.
Ctrl-Alt-F7. Login and see if it works.

If that also does not work, then to return to your original settings:
Ctrl-Alt-F2.
```
sudo cp /etc/X11/xorg.conf-20080823 /etc/X11/xorg.conf 
cp ~/.xsession-errors ~/errors
```

Ctrl-Alt-F7. Login and post ~/errors.

---

### Post by PunkLV on 2008-08-23
Holy Cra.. worked like a charm.. 

some crazy linux-magics..

Thank You indeed.

---

