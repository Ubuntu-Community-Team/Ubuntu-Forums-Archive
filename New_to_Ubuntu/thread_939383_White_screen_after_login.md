---
title: "White screen after login"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by larry Price on 2008-10-05
OK, I've been struggling with the white screen after login and used this fix, ALT F2 metacity --replace 
This worked and I got my desktop back. However if I reboot, the same thing happens again. How do I make this fix permanent? Thanks....

---

### Post by Forbees on 2008-10-05
you need to turn off all desktop effects

this happened to me when i installed all effects b4 my graphics card drivers

either you need to get the drivers, or you just can't handle the effects

---

### Post by larry Price on 2008-10-05
Forbees, I'm not sure what effects you are talking about. This is a fresh install of Hardy. As far as I know, I've not added anything... Thanks..

---

### Post by kabotage on 2008-10-05
```
dpkg-reconfigure xserver-xorg
```

---

### Post by larry Price on 2008-10-05
> **kabotage said:**
> ```
dpkg-reconfigure xserver-xorg
```
Kabotage,
I did try this previously, no effect. But metacity --replace did work. Thanks

---

