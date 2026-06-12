---
title: "QT: How to tell whether Shift or Ctrl are being pressed down"
date: 2010-02-07
forum: Programming Talk
---

### Post by Zorgoth on 2010-02-07
Basically what the subject says.  I can't figure out how to determine this and it is really annoying because I have to design my own selection procedure for a special case in QTextEdit (where we are selecting select strings rather than characters and selection doesn't go away when you click something else) and I want to bind ctrl-A, ctrl-shift-A, and shift-click to various functions.  What do I do?

---

### Post by Zorgoth on 2010-02-10
I found the solution on another forum; what you need to do is, if event is a pointer to a QMouseEvent or a QKeyEvent, use one of the booleans event->modifers().testFlag(Qt::ShiftModifier) or event->modifers().testFlag(Qt::ControlModifier)

---

