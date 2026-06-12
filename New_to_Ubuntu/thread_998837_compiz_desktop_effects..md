---
title: "compiz desktop effects."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-12-01
hi,
 i have compiz configuration manager installed in my ubuntu. when i minimize a window, i want to get the "fire" like animation..i guess u understand what i am talkin about( i mean, the window should go to ashes when i minimize it), but i dont know where to enable that animation and change the settings in compiz configuration manager.

please help
thanks

---

### Post by fr.theo on 2008-12-01
Hi,

Just a few questions have you enabled visual effects from System>> Preferences>> Appearance, under the tab Visual effects and selected Extras?

and are you also requiring themes on your desktop?


if you have done all that then goto Systems>> Preferences>> Advanced Desktop Effects Settings, it should bring up the compiz configuration manager windows and from there you should be able to modify the effects you want.

---

### Post by __Ryan__ on 2008-12-01
I find it easiest to use the simple CCSM, it gives you a more intuitive interface for configuring compiz.

```
sudo aptitude install simple-ccsm
```

Once installed go to Animations, enable extra animations, then select the burn animation for whatever window action you wish.

---

### Post by tjwoosta on 2008-12-01
> I find it easiest to use the simple CCSM, it gives you a more intuitive interface for configuring compiz.


simple-ccsm works great for most of the configuration of compiz, but if you are really serious about customizing your desktop to its fullest extent, i would go with the regular CCSM


you should be able to find it in the add/remove programs list under the applications menu

simply set it to search for "all available applications" and find CCSM (compiz config settings manager)

---

