---
title: "Get the position of a QT widget?"
date: 2010-02-02
forum: Programming Talk
---

### Post by Zorgoth on 2010-02-02
How can I get the position of a QT widget?  This may not be the right way of going about this, but I want to draw a pixmap on top of a button to label it.  In any case, being able to determine the position of a widget in a window probably has other applications.  I am very new to QT so I don't really know what I'm doing.

---

### Post by OutOfReach on 2010-02-02
```

widget->pos();

```
Basically returns a QPoint that contains the widget's position.

If I understand, you want an image on the button? I believe the button widget already has a function to do that, I just can't remember it at this moment. Might want to check out [this]("http://doc.trolltech.com/4.6/qpushbutton.html") page

---

### Post by Zorgoth on 2010-02-02
Thank you!

---

