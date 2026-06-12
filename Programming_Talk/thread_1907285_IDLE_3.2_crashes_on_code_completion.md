---
title: "IDLE 3.2 crashes on code completion"
date: 2012-01-11
forum: Programming Talk
---

### Post by ffalka on 2012-01-11
Hi,

I have just installed IDLE 3.2 on Ubuntu 11.10.
Its version is:
Python 3.2.2 (default, Sep  5 2011, 21:17:14) 
[GCC 4.6.1] on linux2

When I start IDLE , and press ctrl+Space it crashes
Traceback (most recent call last):
  File "/usr/bin/idle-python3.2", line 5, in <module>
    main()
  File "/usr/lib/python3.2/idlelib/PyShell.py", line 1416, in main
    root.mainloop()
  File "/usr/lib/python3.2/tkinter/__init__.py", line 1012, in mainloop
    self.tk.mainloop(n)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xc0 in position 0: invalid start byte

Could anybody help me?

---

