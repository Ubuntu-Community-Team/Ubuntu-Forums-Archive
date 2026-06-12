---
title: "Change Cursor in PyQt4"
date: 2009-03-25
forum: Programming Talk
---

### Post by sjbaugh on 2009-03-25
I am just starting with QT4 in Python. Iam trying to change the cursor for a Widget to the CrossCursor (cross hairs) but I cannot find how to define the cursor in python. I am trying to use setCursor().

Any help will be appreciated.

Steve

---

### Post by sjbaugh on 2009-03-26
After lots of trial and error I have found how to do it:

```
self.setCursor(QtGui.QCursor(QtCore.Qt.CrossCursor))
```

---

