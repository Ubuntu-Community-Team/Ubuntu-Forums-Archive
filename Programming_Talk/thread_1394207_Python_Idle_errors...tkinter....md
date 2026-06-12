---
title: "Python Idle errors...tkinter..."
date: 2010-01-30
forum: Programming Talk
---

### Post by LumbeeNDN on 2010-01-30
...whats the fix for this? I've poked around on google and can't seem to find a straight forward answer.

---

### Post by stevescripts on 2010-01-30
Can you be more specific?  An example would probably prove useful...

Steve

---

### Post by LumbeeNDN on 2010-01-30
sure thing...for instance when I call a function I get this at the shell...

>>> Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 1417, in __call__
    return self.func(*args)
  File "/usr/lib/python2.5/idlelib/MultiCall.py", line 151, in handler
    r = l[i](event)
  File "/usr/lib/python2.5/idlelib/CallTips.py", line 55, in try_open_calltip_event
    self.open_calltip(False)
  File "/usr/lib/python2.5/idlelib/CallTips.py", line 79, in open_calltip
    self.calltip.showtip(arg_text, sur_paren[0], sur_paren[1])
  File "/usr/lib/python2.5/idlelib/CallTipWindow.py", line 66, in showtip
    self.position_window()
  File "/usr/lib/python2.5/idlelib/CallTipWindow.py", line 35, in position_window
    self.parencol))
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 2860, in bbox
    self.tk.call((self._w, 'bbox') + args)) or None
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 1033, in _getints
    return tuple(map(getint, self.tk.splitlist(string)))
ValueError: invalid literal for int() with base 10: '(63,'
fib(

...I also get a blank window with "idle" as the title. Additionally in my edit window I can't highlight anything, or use the mouse. Idle has always been this way for me in Ubuntu. I have a clean install of 9.10. I also reinstalled python which did nothing.

---

### Post by LumbeeNDN on 2010-02-07
...heres a screen shot. I'm open to ANY ideas...throw me a bone and I'll try it...

---

