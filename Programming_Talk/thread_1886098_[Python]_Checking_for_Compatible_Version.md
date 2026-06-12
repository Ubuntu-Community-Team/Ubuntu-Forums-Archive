---
title: "[Python] Checking for Compatible Version"
date: 2011-11-24
forum: Programming Talk
---

### Post by dodle on 2011-11-24
I think I've come up with a way to check that some version within a range is being used. I've been testing it and seems to work. But if someone sees an issue would you please point it out. This isn't specifically meant to be used to get the python version, but that is what I am doing in this example.

[php]import sys

min = (2, 5, 0)
max = (2, 7, -1)
try:
    version = sys.version_info[:3]
except AttributeError:
    sys.exit('Python interpreter version too old')


def MinVersion():
    val = 1
    x = 0
    while (x < 3):
        if (val != 1):
            return val
        if (version[x] >= min[x]):
            if (version[x] > min[x]):
                val = 2
        else:
            val = 0
        x += 1
    return val

def MaxVersion():
    val = 1
    x = 0
    while (x < 3):
        if (max[x] < 0):
            return 1
        if (val != 1):
            return val
        if (version[x] <= max[x]):
            if (version[x] < max[x]):
                val = 2
        else:
            val = 0
        x += 1
    return val

def MinMaxVersion():
    return ((MinVersion() > 0) == (MaxVersion() > 0))[/php]

If someone knows of a better way to do this please let me know. I know that [color=red]sys.hexversion[/color] can be used to check for the python version.

```
>>> print hex(sys.hexversion)
0x20701f0
>>> print sys.hexversion >= 0x20700f0
True
```

Though I'm not sure why the 'f0' has to be included.

---

### Post by crdlb on 2011-11-24
```

if not ((2,5) <= (2,7,2) < (3,0)):
    throw ...

```

I normally wouldn't bother checking the python version, but that's how I'd do it.

---

### Post by dodle on 2011-11-25
Thanks, that is helpful. I had tried that before but it wasn't working. I must have done something wrong.

```
>>> print ((0, 7, 2) > (0, 7, 1))
True
```

---

