---
title: "[Python] Hex color 0xFFFF00 to RGB color (255, 255, 0), HOW??"
date: 2008-10-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-04
I got yellow in hex color, 0xFFFF00. But how to convert it to RGB color, (255, 255, 0)?

---

### Post by mike_g on 2008-10-04
I'm not completely sure if this is the correct python syntax, but it should at least give you an idea of how to extract the colour elements from a number. I basically involves bitshifting and masking using the binary AND operator:
```
def getRed(col):
    return (col >> 16) and 255

def getGreen(col):
    return (col >> 8) and 255

def getBlue(col):
    return col and 255

```

---

### Post by Pyro.699 on 2008-10-04
```

def rgb(h): 



    n = eval('0x'+h[1:])
    return (n>>16)&0xff, (n>>8)&0xff, n&0xff

```

Not sure if that works or not, i just wrote it quickly

---

### Post by Wybiral on 2008-10-05
Pythons 'int' function has an optional base argument...

```

def rgb(c):
    split = (c[0:2], c[2:4], c[4:6])
    return [int(x, 16) for x in split]

```

---

