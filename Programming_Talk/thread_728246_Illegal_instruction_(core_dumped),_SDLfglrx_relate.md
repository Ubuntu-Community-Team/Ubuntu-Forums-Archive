---
title: "Illegal instruction (core dumped), SDL/fglrx related?"
date: 2008-03-18
forum: Programming Talk
---

### Post by AZzKikR on 2008-03-18
I've been trying to compile and run NeHe (Gamedev) tutorial #43, which is about freetype2 and OpenGL. With that tutorial there is a SDL version too. I've compiled and tried to run it, but it exits with the message "Illegal instruction (core dumped)".

Using gdb, it seems that this is the exception:
```

Program received signal SIGILL, Illegal instruction.
0xb736707d in __glim_PopAttrib () from /usr/lib/dri/fglrx_dri.so

```

Seems it's a driver issue. I am getting the same error when running Neverwinter Nights natively on Linux, but I couldn't check if it's the same reason because it's missing debugging symbols in the executable.

Any ideas before I start installing a new fglrx driver?

Thanks.

---

