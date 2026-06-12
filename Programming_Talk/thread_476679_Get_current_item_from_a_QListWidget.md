---
title: "Get current item from a QListWidget?"
date: 2007-06-17
forum: Programming Talk
---

### Post by Kimm on 2007-06-17
I cant seem to find any reference on how to grab the current item in a QListWidget (Qt4) (as text).

Any help anyone? :/

---

### Post by msumurph on 2007-06-17
I think it is: 

```
widget->currnetitem()->text()
```

currentitem returns a QListWidgetItem, which has a method text(), which returns a QString.

I have not tried this, just read the documentation entry in QT Assistant.  Hope this helps. ;)

---

### Post by Kimm on 2007-06-18
> **msumurph said:**
> I think it is: 

```
widget->currnetitem()->text()
```

currentitem returns a QListWidgetItem, which has a method text(), which returns a QString.

I have not tried this, just read the documentation entry in QT Assistant.  Hope this helps. ;)

I found the same solution in a discussion regarding KDE4. But it was not evident from the online [documentation](http://doc.trolltech.com/4.1/qlistwidget.html)

QT Assistant eh? Sounds like a good thing to have! :D Need to get it... :D

---

