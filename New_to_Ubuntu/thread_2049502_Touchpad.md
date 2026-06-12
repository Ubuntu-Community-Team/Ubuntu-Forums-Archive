---
title: "Touchpad"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-08-28
I have two users. One that is originaly created by Ubuntu and another that i have created. Recently while working in the user 1 my Touch pad suddenly stopped working. But if i attach a usb mouse it works well. Where as there is no such problem with user 2.

Can any one suggest what could be going wrong !

.

---

### Post by lechien73 on 2012-08-28
I've experienced problems before when the "Disable touchpad while typing" checkbox is checked in **System Settings -> Mouse and Touchpad**

You could try unchecking this box to see if it works. You could also try opening a terminal window (Ctrl+Alt+T if you need a shortcut) and typing:

```
synclient TouchpadOff=0
```

This might re-enable your touchpad.

---

