---
title: "Cross-compiling C libs for Windows 7"
date: 2011-07-13
forum: Packaging and Compiling Programs
---

### Post by DangerOnTheRanger on 2011-07-13
Long story short: I know Windows 7 isn't binary compatible with previous versions of  Windows, so can MinGW cross-compile for Windows 7? If so, how, if it's not done automatically?

---

### Post by sakishrist on 2011-07-15
What do you mean by 7 is not binary compatible? Can't Windows 7 run XP programs? I am sure it can. Except if you mean something else, then, my fault.

---

### Post by DangerOnTheRanger on 2011-07-16
Well, I tried loading a DLL compiled with Windows XP in Windows 7, and it failed to load. I made sure all the DLLs dependencies were satisfied, and it still failed to load, so I assumed Windows 7 wasn't binary (ABI) compatible with Windows XP.

---

