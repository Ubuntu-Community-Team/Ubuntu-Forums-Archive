---
title: "font problems in thunderbird"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by macvr on 2008-09-01
hi,
i had font problems in firefox and with my msttcore fonts, so when i was trying to correct the fonts,

i found this file: **_/etc/fonts/conf.d/10-autohint.conf_**
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<!--  Use the Autohinter --> 
  <match target="font">
    <edit name="autohint" mode="assign"><bool>[COLOR="Red"]true[/COLOR]</bool></edit>
  </match>
</fontconfig>
```
when i set it to [COLOR="Red"]false[/COLOR] all my other fonts get displayed properly

BUT i start having font problems in thunderbird, check attached pics[1-false, 2-true]
it gets even worse in the actual mails when all different fonts are in use!

i dont know how got this file in my config,*{my guess is probably came with the thunderbird install[installed via synaptics only], could some check this?}*

how do i correct his problem?
could i set this config to act only on thunderbird?

---

### Post by macvr on 2008-09-02
bump?

---

### Post by macvr on 2008-09-03
bump???

---

### Post by macvr on 2008-09-30
bump?

---

