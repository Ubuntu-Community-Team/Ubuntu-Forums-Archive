---
title: "Debugger won't break at breakpoints in qt creator"
date: 2013-04-12
forum: Programming Talk
---

### Post by JeyPeyy on 2013-04-12
I have imported a project to Qt Creator (latest gedit from git) and I have now managed to make it run, but I'm still not able to debug it since it won't break at my breakpoints. The gdb output shows this:
> &"warning: GDB: Failed to set controlling terminal: Inappropriate ioctl for device\n"
no loadable sections found in added symbol-file system-supplied DSO at 0x7ffff7ffa000

The second line is shown when debugging from the terminal too, but not the first one. Breaking works well from the terminal (but I prefer putting my breakpoints graphically).

---

