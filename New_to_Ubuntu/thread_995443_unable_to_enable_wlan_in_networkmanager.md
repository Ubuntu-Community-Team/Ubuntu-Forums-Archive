---
title: "unable to enable wlan in networkmanager"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by mormor on 2008-11-27
Thats basicly my problem.
Networkmanager wont let me enable wlan.
Happened after a failed attempt to replace networkmanager with wicd. (intrepid 64x on acer travelmate 6291)

---

### Post by Michael.Godawski on 2008-11-28
So do you have a working network configuration tool installed now? Wicd is not working? Network manager is reinstalled successfully?

What is your wlan card?

Please post the result of these commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by nachomania on 2008-11-28
Uh... In Network Tools, unlock the menu and set wireless back to roaming mode. In edit/properties, I believe

---

