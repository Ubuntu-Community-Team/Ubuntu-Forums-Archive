---
title: "How to make installble/exe package for client of c++ source program."
date: 2010-02-26
forum: Programming Talk
---

### Post by ibhupi on 2010-02-26
I have some program that using opencv library for iamge processing and gtk for GUI.

Please tell me how make a complete package from it. so that i can install this on any ubuntu system same architecture without installing opencv in that system.


Thanks .

---

### Post by dwhitney67 on 2010-02-26
Link the opencv library as static within your application.  Personally, I am not familiar with opencv, but let's just say for example, if it comes with a shared-object library (eg. libopencv.so) and a static library (eg. libopencv.a), you want to use the latter.

For example
```

g++ MySource.cpp -static -lopencv `pkg-config gtk+-2.0 --cflags --libs` -o MyApp

```

P.S.  Undoubtedly I have probably skipped important dependency information for the opencv library, but I'll let you sort that out, perhaps using pkg-config.  The main thing is to specify -static before the library.  This will tell the linker to use libopencv.a.

---

