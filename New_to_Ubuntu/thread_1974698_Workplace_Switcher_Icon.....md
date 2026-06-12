---
title: "Workplace Switcher Icon...."
date: 2012-05-06
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-06
Hey guys, somehow my workspace switcher icon got replaced with the icon of a regular folder and I'd like to get the default icon back...I have no idea how it happened as I don't believe I touched anything related to icons after installing 12.04 (apart from installing the default gnome 3 theme) and it showed the correct icon all my previous boots but now its showing this:

[IMG]http://i.imgur.com/tVjo0.png[/IMG]

Does anyone know how I can get the default icon back?

---

### Post by philinux on 2012-05-06
> **d4m1r said:**
> Hey guys, somehow my workspace switcher icon got replaced with the icon of a regular folder and I'd like to get the default icon back...I have no idea how it happened as I don't believe I touched anything related to icons after installing 12.04 (apart from installing the default gnome 3 theme) and it showed the correct icon all my previous boots but now its showing this:

[IMG]http://i.imgur.com/tVjo0.png[/IMG]

Does anyone know how I can get the default icon back?

Change the theme back to ambiance as a first attempt.

---

### Post by rajplay on 2012-05-06
> **philinux said:**
> Change the theme back to ambiance as a first attempt.

I have a similar problem and I never changed my theme from ambiance. Its been ambiance for ever.

---

### Post by philinux on 2012-05-06
```
unity --reset
```

This will lose you any customisations and revert unity to the installed state.

---

### Post by d4m1r on 2012-05-08
> **philinux said:**
> Change the theme back to ambiance as a first attempt.


Well you were right....Changing it back to ambiance fixes it. Does this mean Gnome doesn't have a similar icon for the workplace switcher and is therefor just default to a basic folder icon? :confused: Is there a way for me to change just that icon manually?

Thanks in advance guys!

---

