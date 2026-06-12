---
title: "What is the default color of Ubuntu text?"
date: 2011-01-08
forum: Programming Talk
---

### Post by leon.vitanos on 2011-01-08
I am setting a label with this... 
```
ui->imagesLabel_2->setStyleSheet("* { color: white }");
```

But if i set it to black it will be different from the other text's default ( which is black-grey ).. 

So what is the default color of ubuntu text? 

I am using Qt Creator....

---

### Post by Zugzwang on 2011-01-09
Browsing the documentation, it seems as if you can do what you want by getting the QPalette object for your application (returned by QApplication:: palette()) and reading the text color from it.

See: [http://doc.qt.nokia.com/4.6/qpalette.html#details](http://doc.qt.nokia.com/4.6/qpalette.html#details)

---

### Post by leon.vitanos on 2011-01-09
> **Zugzwang said:**
> Browsing the documentation, it seems as if you can do what you want by getting the QPalette object for your application (returned by QApplication:: palette()) and reading the text color from it.

See: [http://doc.qt.nokia.com/4.6/qpalette.html#details](http://doc.qt.nokia.com/4.6/qpalette.html#details)
I basically had found a solution.. it is something like setStyleSheet(stylesheet); 

Something like that.. i do not remember exactly now.. Anyway thanks.. :)

---

