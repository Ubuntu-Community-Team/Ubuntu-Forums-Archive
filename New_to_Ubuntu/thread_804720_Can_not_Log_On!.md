---
title: "Can not Log On!"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-23
Hi,

Pretty basic problem this one. After a fresh install of 8.04, followed by updates and adding restricted drivers, I can not logon because the logon on screen is way too big!

Any ideas?
Thanks

meta

---

### Post by hessiess on 2008-05-23
ctrl+alt+f1 -> log in -> sudo nano /etc/X11/xorg.conf -> find this section

```
SubSection "Display"
    Depth   24
    Modes           "1440x900"      "1024x768"      "800x600"
EndSubSection
```

add correct screen res -> ctrl+X, press Y then enter -> restart comp.

---

### Post by metasolaris on 2008-05-23
sudo nano /etc/X11/xorg.conf I get "command not reconised"

---

### Post by LinuxTechnology on 2008-05-23
I suggest that you click on the "auto-adjust monitor" option. That should resize/make things look the way they should be.

---

### Post by sailor2001 on 2008-05-23
boot into your recovery mode. When you get back to your sign-in  type gksudo displayconfig-stk  and scrool for your monitor and set proper resolution (higher)

---

