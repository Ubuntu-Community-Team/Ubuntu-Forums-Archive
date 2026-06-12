---
title: "Big Desktop Feature Problem!"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Anjue on 2008-11-27
I tried to enable the Big Desktop via Catalyst Control Center. It's seems okay but After Login It's become to dual head!

I use Laptop ACER Aspire 5551AWXMi with ATi Mobility RadeonX1300

---

### Post by pastalavista on 2008-11-27
> **Anjue said:**
> I tried to enable the Big Desktop via Catalyst Control Center. It's seems okay but After Login It's become to dual head!

I use Laptop ACER Aspire 5551AWXMi with ATi Mobility RadeonX1300

I'm not sure what you mean by "...After Login It's become to dual head"

...it now offers a choice of monitors? Do you physically have more than one video port (XVGA, HDMI, Svideo etc.) ?

---

### Post by Anjue on 2008-11-27
In the login screen I can use both of screen as big desktop features (I can move the mouse across the screen)  but after login the second monitor change to dual monitor!

---

### Post by pastalavista on 2008-11-28
you may need to configure xserver too... I'm not sure

```
sudo dpkg-reconfigure xserver-xorg
```

---

