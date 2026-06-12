---
title: "Unity 3D Dock Doesn't appear"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by rgreener25 on 2012-01-30
In unity 3d my dock doesn't appear when i push it to the side of the screen i first have to type <ALT><F2> then ```
unity --reset-icons
``` is there a way i can make it permenant

---

### Post by rgreener25 on 2012-01-30
Does anyone know what i can do

---

### Post by Grenage on 2012-01-30
I don't have Unity to test, but if this does not work:

```
unity --reset
```

Then you can try resetting the settings to default with the following commands:

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
unity --reset
```

I have not personally used gconftool to reset things.

---

