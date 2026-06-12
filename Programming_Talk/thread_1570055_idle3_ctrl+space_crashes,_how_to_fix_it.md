---
title: "idle3 ctrl+space crashes, how to fix it?"
date: 2010-09-07
forum: Programming Talk
---

### Post by zubaran on 2010-09-07
Hi

I am learning python 3.
When I try to ctrl+space to call code assist idle3 crashes with traceback:
```

Traceback (most recent call last):
  File "/usr/bin/idle3", line 5, in <module>
    main()
  File "/usr/lib/python3.1/idlelib/PyShell.py", line 1420, in main
    root.mainloop()
  File "/usr/lib/python3.1/tkinter/__init__.py", line 1012, in mainloop
    self.tk.mainloop(n)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 0-1: illegal encoding

```Does anybody know how to fix it? Some workaround?

Ubuntu 10.04.

---

### Post by hakermania on 2010-09-08
i don't know python but see the output. "Unknown encoding".
Have you tried to change the encoding of your program from utf8 to something more common?

---

### Post by zubaran on 2010-09-08
More common you say:o
utf8 is pretty much common for me.
Entire OS is using utf8 why should I put torment on me to change encoding.
Thanks anyway. At leat you tried):P

By the way. idle for python 2.7 is running ok. Without ctrl+space problems.

---

