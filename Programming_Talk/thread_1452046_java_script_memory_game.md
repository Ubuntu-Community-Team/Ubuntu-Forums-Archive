---
title: "java script memory game"
date: 2010-04-11
forum: Programming Talk
---

### Post by hbarshak on 2010-04-11
Hi All,

my post not really related to ubuntu or linux but i hope someone could help me :)

i am practicing java-script and trying to build a memory game.
i am having a weird problem:
i am changing the image "src" attribute with js code and the pic wont change unless i add an alert box after the flip.
is it possible that alert is causing a refresh or something like that that is causing the image to load ??

thanks a lot!!

the problem is in the unHide function in jScript.js

Hen

---

### Post by zoff_ita on 2010-04-12
Try changing display style property after having set new src:

```
img.src = "NEW SRC";
img.style.display = "";
```

---

### Post by hbarshak on 2010-04-13
running this does help show the picture.

can you please explain what exactly it does ?


thanks!!

---

### Post by zoff_ita on 2010-04-13
> **hbarshak said:**
> running this does help show the picture.

can you please explain what exactly it does ?


thanks!!

img.style.display = ""
set the display mode (block, inline, table-cell, etc...) of the item to default value, this cause item to be re-drawn

---

