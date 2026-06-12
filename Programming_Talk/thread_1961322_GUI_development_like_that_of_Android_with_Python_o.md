---
title: "GUI development like that of Android with Python on PC?"
date: 2012-04-19
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2012-04-19
So, recently I was playing around with Python for Android and learned that the GUI development on Android is very easy. 
For example
```

import android

app = android.Android()
app.dialogCreateAlert("An example")
app.dialogSetSingleChoiceItems(['Awesome', 'Cool', 'Woah'])
app.dialogSetPositiveButtonText("Select")
app.dialogSetNegativeButtonText("Quit")
app.dialogShow()
resp = app.dialogGetResponse().result

```This would create a small dialogue asking you to choose one of the options. This on a computer would take alot more code. Is there something similar for PC? with Python? (sorry if the question is stupid :|)

---

### Post by dniMretsaM on 2012-04-19
> **cyb3r_sn4k3 said:**
> So, recently I was playing around with Python for Android and learned that the GUI development on Android is very easy. 
For example
```

import android

app = android.Android()
app.dialogCreateAlert("An example")
app.dialogSetSingleChoiceItems(['Awesome', 'Cool', 'Woah'])
app.dialogSetPositiveButtonText("Select")
app.dialogSetNegativeButtonText("Quit")
app.dialogShow()
resp = app.dialogGetResponse().result

```This would create a small dialogue asking you to choose one of the options. This on a computer would take alot more code. Is there something similar for PC? with Python? (sorry if the question is stupid :|)

That shouldn't be too hard. How about a picture of what it looks like. One of the easier (yet still fairly powerful) graphical toolkit for Python is Tkinter. I personally prefer Qt, though. And some use GTK.

---

### Post by digrejzo on 2012-04-19
maybe this is off topic, but dniMretsaM can you please suggest a few Tkinter/Qt tutorials/e-books?

thanks!

---

### Post by memilanuk on 2012-04-19
Zetcode.com has a bunch of tutorials on tkinter, wxpython, pyqt/pyside, python, sqlite, and much more.

---

### Post by digrejzo on 2012-04-19
that's a great resource, thanks a lot ;)

---

### Post by dniMretsaM on 2012-04-19
> **memilanuk said:**
> Zetcode.com has a bunch of tutorials on tkinter, wxpython, pyqt/pyside, python, sqlite, and much more.

That's where I'm learning from. I actually have one of there Qt tutorials open now. Yeah, great resource.

---

### Post by cyb3r_sn4k3 on 2012-04-19
> **memilanuk said:**
> Zetcode.com has a bunch of tutorials on tkinter, wxpython, pyqt/pyside, python, sqlite, and much more.

Thats a great site.

---

