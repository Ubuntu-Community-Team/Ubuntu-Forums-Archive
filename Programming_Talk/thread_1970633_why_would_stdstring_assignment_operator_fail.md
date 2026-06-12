---
title: "why would std::string assignment operator fail?"
date: 2012-05-01
forum: Programming Talk
---

### Post by korgoth28 on 2012-05-01
I call a function
```
theMap[x][y].moveUnitOn('M', c, "a merchant", UnitPointer(&(merchantList[merchantNum])));
```which looks like this
```

void Tile::moveUnitOn(char g, int c, string d, UnitPointer unit)
{
    bgGraphic = graphic;
    graphic = g;
    bgColorPair = colorPair;
    colorPair = c;
    bgDescription = description;
    description = d;
    occupyingUnit = unit;
}

```and I get a segmentation fault. gdb tells me the problem is with bgDescription = description. bgDescription is just a data member of Tile. Specifically the error is:

```
#0 0x7ffff773019a    ??() (/usr/lib/x86_64-linux-gnu/libstdc++.so.6:??)
#1 0x7ffff77315c6    std::string::assign(std::string const&) () (/usr/lib/x86_64-linux-gnu/libstdc++.so.6:??)
#2 0x4032ec    Tile::moveUnitOn(this=0x7ffffffa33c0, g=77 'M', c=5, d=..., unit=...) (/home/mike/Desktop/klepto/Tile.cpp:13)
#3 0x40263c    Player::hireMerchant(this=0x7ffffffa2e80, c=5, theMap=0x7ffffff1a300) (/home/mike/Desktop/klepto/Player.cpp:35)
#4 0x404246    main(argc=1, argv=0x7fffffffe268) (/home/mike/Desktop/klepto/main.cpp:265)

```

The code worked fine until I changed the data member occupyingUnit from type Merchant* to unitPointer. Thanks in advance.

---

### Post by movieman on 2012-05-01
Are you running off the end of your array when you index by x and y?

If bgDescription is not a properly initialised string object, anything could happen when you try to copy a string into it (e.g. it's going to try to free the old string data, which will just be a garbage pointer).

---

### Post by MadCow108 on 2012-05-01
most likely some memory corruption or overflow
what does valgrind say?

---

### Post by korgoth28 on 2012-05-01
> **movieman said:**
> Are you running off the end of your array when you index by x and y?

If bgDescription is not a properly initialised string object, anything could happen when you try to copy a string into it (e.g. it's going to try to free the old string data, which will just be a garbage pointer).

Thank you all very much, the problem was a typo in the calculation of x.

---

