---
title: "compiling DSSI plugins."
date: 2013-04-15
forum: Packaging and Compiling Programs
---

### Post by zizzdude on 2013-04-15
Hey everyone,

I'm learning how to create dssi plugins for understand the in and outs for making digital synthesizers for DAW's like Renoise. Seeing that there isn't any "official" documentation on making them, I'm looking through the examples provided in the dssi source files. As for compiling, I'm sorta going through a trial and error tactic to see if I'm compiling them right.

For trivial_synth, I did:
```

gcc -c -fpic trivial_synth.c
gcc -shared -o trivial_synth.so trivial_synth.o

```

which seems to work.

For karplong, I did:
```

g++ -c -fpic karplong.cpp
g++ -shared -o karplong.so karplong.o

```

and that, too, worked.

Now for less_trivial_synth, which uses QT as the gui for configurations. There are three files: less_trivial_synth.c, less_trivial_synth_qt_gui.h, and less_trivial_synth_qt_gui.cpp. 

I'm a little new on making shared libraries combining these files, so what is the correct way to do this?

---

### Post by zizzdude on 2013-04-24
bump.

---

