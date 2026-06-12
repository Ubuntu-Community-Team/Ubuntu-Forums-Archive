---
title: "Coding in Qt 3, need help with weird bug"
date: 2009-10-16
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-10-16
Hey everyone,

So I'm fairly new with Qt and I need some help figuring out the origin of a certain bug of mine. So I subclassed QTable and QTableItem to display a bunch of information. The information is illustrated as a color which takes up a cell. New information is constantly being filled in / updated onto the table. The table starts with a size of 0,0 and grows. So does the following bugs ring a bell to anyone?

> X Error: BadLength (poly request too large or internal Xlib length error) 16
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3600038
X Error: BadLength (poly request too large or internal Xlib length error) 16
  Major opcode:  3
  Minor opcode:  0
  Resource id:  0x3600038
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x360017d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x360017d

---

