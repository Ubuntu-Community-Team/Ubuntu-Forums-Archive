---
title: "Segfault in Pmw.dialog"
date: 2009-01-28
forum: Programming Talk
---

### Post by dld on 2009-01-28
Has anyone found a workaround or fix for segment fault when activating a Pmw Dialog?
   DLD

---

### Post by Zugzwang on 2009-01-29
Dear OP, when using abbreviations that are uncommon in this forum, please always explain them. Also state the context of your question, for example to which toolkit/programming language you refer to.

---

### Post by dld on 2009-01-29
Ok, Thanks.  Pwm is Python MIcrowidgets.  Dialog is one of the widgets it provides.  With the latest releases of Ubuntu (8.10), Python, Pmw and Tkinter, Pmw.Dialog segment faults when calling activate() on it.  This may be a problem in Ubuntu (probably not), Python (probably not), Pmw (perhaps) or Tkinter (also possible).

---

### Post by stevescripts on 2009-02-04
Did you get this issue resolved?  If not, can you post a simple example that causes the segfault? 

Steve
(meant to get around to this earlier ...)

---

### Post by dld on 2009-02-05
Not resolved!  As an example execute:
   /usr/share/doc/python-pmw-doc/examples/Dialog.py
This is from the python-pmw-doc package.

If it would be helpful, I can cut that example down to fewer lines.

---

### Post by stevescripts on 2009-02-05
Yes, cut it down a bit please.

Does this work for you?

```

#!/usr/local/bin/python2.5

import Tkinter
root = Tkinter.Tk()
import Pmw
Pmw.initialise(root)

dialog = Pmw.Dialog(
        title = 'Pmw dialog',
        buttons = ('Yes', 'No'))

root.mainloop()

```

Steve

---

### Post by dld on 2009-02-05
Yes, it does work:  2 small windows, the dialog with 2 buttons and an empty main window.  But the dialog doesn't hold focus and prevent the top window from displaying.   Put    "dialog.activate()"    before  "root.mainloop()"   and see the segfault.

---

### Post by dld on 2009-02-06
I have traced the problem to a call to _busy_hold() [line 1259 in file PmwBase.py] in calling showbusycursor [line 1110] in def activate() [line 1102].  _busy_hold is a global name; I don't have any idea yet where function _busy_hold() might be defined.  Hope this helps.

---

### Post by dld on 2009-02-06
I have traced the problem to a call to _busy_hold() [line 1259 in file PmwBase.py] in calling showbusycursor [line 1110] in def activate() [line 1102].  _busy_hold is a global name; I don't have any idea yet where function _busy_hold() might be defined.  Hope this helps.

One more step. The definition of busy_hold() is in file PmwBlt.py beginning on line 54.  The segment fault happens on line 57:

 window.tk.call(_busyCommand, 'hold', window._w)

This takes us into tk, so it is the end of the line for me.  Anybody understand tkinter?

---

