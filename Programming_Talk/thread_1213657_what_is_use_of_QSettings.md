---
title: "what is use of QSettings??"
date: 2009-07-15
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-15
what exactly is use of QSettings, i understood like it overall represents various independent platform apps settings. 
Why should we use this?? also it just hides totally after application program is run, i din't quiet understand this:( 

```

void MainWindow::readSettings()
{
    QSettings settings("Trolltech", "MDI Example");
    QPoint pos = settings.value("pos", QPoint(200, 200)).toPoint();
    QSize size = settings.value("size", QSize(400, 400)).toSize();
    move(pos);
    resize(size);
}
```
hope you will clarify this??

---

