---
title: "Basic compiling question"
date: 2010-03-05
forum: Packaging and Compiling Programs
---

### Post by Scooter_X on 2010-03-05
Yea, so I just went and downloaded Free Pascal so I could compile a piece of software. (obviously) I'm just dang confused, because I went there, downloaded the x86 Linux version, and got a 2mb file named Pascal. And it doesn't do anything. I've never compiled my own stuff before, and I'm likely doing something really obviously wrong, and I would appreciate it if someone would point out just what that is. Thanks. :P

---

### Post by gmargo on 2010-03-06
Free Pascal is available from the repositories; there's no need to compile it yourself.
```

$ apt-cache search free pascal | grep -i pascal
fp-compiler - Free Pascal - Compiler
fp-docs - Free Pascal - Documentation
fp-ide - Free Pascal - IDE
fp-units-base - Free Pascal - base units
fp-units-db - Free Pascal - database libraries units
fp-units-fcl - Free Pascal - Free Component Library
fp-units-fv - Free Pascal - Free Vision units
fp-units-gfx - Free Pascal - graphics libraries units
fp-units-gnome1 - Free Pascal - GNOME 1 units
fp-units-gtk - Free Pascal - GTK+ 1.2 units
fp-units-gtk2 - Free Pascal - GTK+ 2.x units
fp-units-i386 - Free Pascal - miscellaneous units
fp-units-misc - Free Pascal - miscellaneous units
fp-units-multimedia - Free Pascal - miscellaneous units
fp-units-net - Free Pascal - networking units
fp-units-rtl - Free Pascal - Runtime Library
fp-utils - Free Pascal - Utils
fpc - Free Pascal Compiler - Meta Package
fpc-source - Free Pascal Compiler - Source Code
lazarus - IDE for Free Pascal to create (graphical and console) applications
mseide-msegui - FreePascal-based GUI development library and IDE

```

---

