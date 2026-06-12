---
title: "[SOLVED]Execute commands at startup"
date: 2020-08-13
forum: New to Ubuntu
---

### Post by ionmich1 on 2020-08-13
Ubuntu 18.04

I need to modify my keyboard at startup. I put 
```
#!/bin/sh -e
# rc.local
#

xmodmap -e "keycode  68 = Home"
xmodmap -e "keycode  67 = Delete"
0
 
```

in rc.local, but that doesn't work. So where should I have it put it? Thanks in advance.

---

### Post by Holger_Gehrke on 2020-08-14
rc.local - even if it does get executed, which needs activation of the service rc-local.service and /etc/rc.local has to be executable and needs a valid shebang line - would be a bad place for these commands because it runs before the GUI is started. Put the script in some file in your home and create a desktop file in ~/.config/autostart for it. That's what I do to set my touchpad to tap-to-click, which for some reason isn't available as an option in the settings ...

Holger

---

### Post by ionmich1 on 2020-08-14
> **Holger_Gehrke said:**
> rc.local - even if it does get executed, which needs activation of the service rc-local.service and /etc/rc.local has to be executable and needs a valid shebang line - would be a bad place for these commands because it runs before the GUI is started. Put the script in some file in your home and create a desktop file in ~/.config/autostart for it. That's what I do to set my touchpad to tap-to-click, which for some reason isn't available as an option in the settings ...

Holger

Thank you for the speedy reply, and the appropriate solution.

---

