---
title: "Qt - Get background colour from QLabel?"
date: 2017-08-22
forum: Programming Talk
---

### Post by fallenshadow on 2017-08-22
How would I get the colour of a Label so I can store it in the settings and restore it later?

Using Qt and C++.

---

### Post by ajgreeny on 2017-08-22
I use Xubuntu and there is a gtk app to find colours called gcolor, see screenshot. I can not find a similar app for qt but you may be able to search and find one which works, or you could see how much of gtk library is needed for that gcolor to work for you as well.

---

### Post by norobro on 2017-08-22
You have to call palette() on your label. For the various colors see here: [http://doc.qt.io/qt-5/qpalette.html#ColorRole-enum](http://doc.qt.io/qt-5/qpalette.html#ColorRole-enum)

To get the background color:```

[COLOR=#008000]QColor [/COLOR][COLOR=#008000]background [/COLOR][COLOR=#008000]= [/COLOR][COLOR=#008000]your_label.palette().color(QPalette::Window);[/COLOR]
```

---

### Post by fallenshadow on 2017-08-24
@norobro - Thanks, this is exactly what I needed. You can also use the following to get a hex which is better for storing to a settings file:

```

background.name()

```

---

