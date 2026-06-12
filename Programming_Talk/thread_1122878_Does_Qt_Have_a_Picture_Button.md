---
title: "Does Qt Have a Picture Button?"
date: 2009-04-11
forum: Programming Talk
---

### Post by rich1939 on 2009-04-11
I'm starting to play around with Qt and I like the Designer built into QtCreator; however, for my application I can't seem to find a picture button (i.e., one that will allow a .jpg that is 32x32 or 64x64 pixels). Am I missing something?

Thanks.

---

### Post by samjh on 2009-04-11
You can use QPushButton or QToolButton.

With QPushButton, use the [QPushButton::QPushButton ( const QIcon & icon, const QString & text, QWidget * parent = 0 )](http://doc.trolltech.com/4.4/qpushbutton.html#QPushButton-3) constructor and assign a [QIcon](http://doc.trolltech.com/4.4/qicon.html) object for the picture.

With [QToolButton](http://doc.trolltech.com/4.4/qtoolbutton.html), create the button, then set a QIcon object as the button's icon.  See the example in [QIcon](http://doc.trolltech.com/4.4/qicon.html#details)'s documentation.

---

### Post by rich1939 on 2009-04-12
> **samjh said:**
> You can use QPushButton or QToolButton.

With QPushButton, use the [QPushButton::QPushButton ( const QIcon & icon, const QString & text, QWidget * parent = 0 )](http://doc.trolltech.com/4.4/qpushbutton.html#QPushButton-3) constructor and assign a [QIcon](http://doc.trolltech.com/4.4/qicon.html) object for the picture.

With [QToolButton](http://doc.trolltech.com/4.4/qtoolbutton.html), create the button, then set a QIcon object as the button's icon.  See the example in [QIcon](http://doc.trolltech.com/4.4/qicon.html#details)'s documentation.

Thanks for the reply. I was trying to use Qt Designer to create my GUI and the QPushButton object seemed to limit the icon's size to 16x16 pixels.

I did find that QToolButton had a 32x32 pixel size choice and I might need to use that. My problem with both of these buttons is that Qt wants to use a resource as the icon, whereas Glade + Gtk+ allows me to load a filename.

I did see that I could load a file in Qt if I write the code to do so...but I really prefer to use a GUI designer for my interfaces. Is there a way to create a Qt-compatible resource file using an external program, and then refer to it in Designer?

Thanks.

---

### Post by samjh on 2009-04-12
I'm sorry I can't answer questions about Qt Designer, as I never use it.  My interfaces are hand-coded.

[http://www.qtforum.org/](http://www.qtforum.org/) might be a better place to ask, as it is dedicated to Qt programming.

---

### Post by rich1939 on 2009-04-13
[QUOTE=samjh;7061543]I'm sorry I can't answer questions about Qt Designer, as I never use it.  My interfaces are hand-coded.QUOTE]

Okay...thanks for the coding info.

---

### Post by dulouz on 2010-01-28
I know this thread is a bit old, but I was looking for an answer to the same question. Looking at the API docs for QAbstractButton, I noticed there's a setIconSize(const QSize&) slot. So if you use a QPushButton you can do something like: 

```
    QPushButton* button = new QPushButton();
    QPixmap* pixmap = new QPixmap(filename);
    QIcon icon(*pixmap);
    QSize iconSize(pixmap->width(), pixmap->height());
    button->setIconSize(iconSize);
    button->setIcon(icon);
```

---

