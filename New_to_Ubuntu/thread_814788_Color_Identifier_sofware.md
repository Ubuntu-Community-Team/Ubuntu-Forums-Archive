---
title: "Color Identifier sofware"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by bovus on 2008-06-01
Hey, I had this nifty free program for windows that would tell me the RGB values and the color name of whatever pixel the cursor was over, is there such a thing for linux?  It would really help because im color blind.

---

### Post by sayakb on 2008-06-01
Did you try installing it with Wine?
```
sudo apt-get install wine
```

---

### Post by sayakb on 2008-06-01
You might also try grabc:
```
sudo apt-get install grabc
```
And run it from terminal:
```
grabc
```

It gives Hex value of color.

---

### Post by mcduck on 2008-06-01
Try GColor, or Agave, both are in repositories. (GColor is simpler one, giving you eyedropper tool that you can use to get color from anywhere on the display. Agave is bit more advanced, offering color scheme generator as well as similar eyedropper tool).

---

