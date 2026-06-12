---
title: "Help with a USB Tool"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by metacognition on 2008-09-24
Hey guys, so I have this USB foot pedal that I use for work and it came with an installation CD. Unfortunately, it's only for Windows. I've tried wine, but it disappears on the actual install. (Last of DirectX 8, some other prog, and Codec)
```
Backtrace:
=>1 0x004452e5 in _ins5576._mp (+0x452e5) (0x0033ec9c)
  2 0x00445218 in _ins5576._mp (+0x45218) (0x0033ecd8)
  3 0x00443e54 in _ins5576._mp (+0x43e54) (0x0033ecf8)
  4 0x00442cad in _ins5576._mp (+0x42cad) (0x0033ed0c)
  5 0x0044c24b in _ins5576._mp (+0x4c24b) (0x0033ee28)
  6 0x0044b473 in _ins5576._mp (+0x4b473) (0x0033ef50)
  7 0x0041d8d4 in _ins5576._mp (+0x1d8d4) (0x0033fd90)
  8 0x00421273 in _ins5576._mp (+0x21273) (0x0033fdc8)
  9 0x00421db9 in _ins5576._mp (+0x21db9) (0x0033fddc)
  10 0x0043ce71 in _ins5576._mp (+0x3ce71) (0x0033fdf4)
  11 0x0043d165 in _ins5576._mp (+0x3d165) (0x0033fe0c)
  12 0x00437457 in _ins5576._mp (+0x37457) (0x0033fe4c)
  13 0x004379bd in _ins5576._mp (+0x379bd) (0x0033fe7c)
  14 0x004769af in _ins5576._mp (+0x769af) (0x0033ff08)
  15 0x7b8773a7 in kernel32 (+0x573a7) (0x0033ffe8)
  16 0xb7e0f9e7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```
Any help?

---

### Post by Pro-reason on 2008-09-24
Unless you have any particular reason for thinking that these Windows drivers will work via Wine, look for Linux drivers.

---

