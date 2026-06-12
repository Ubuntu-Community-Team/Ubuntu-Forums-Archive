---
title: "qt4 centre a window when using multiple monitors"
date: 2010-02-08
forum: Programming Talk
---

### Post by Woody1987 on 2010-02-08
I want to centre my qt4 window when my application starts. I do this by running this code:
```
QDesktopWidget *desktop = QApplication::desktop();
move((desktop->width() - this->width()) / 2, (desktop->height() - this->height()) / 2);
```

This works fine on a single monitor, but when i do it on a dual monitors setup it assumes it is one big screen. I currently use randr to setup dual monitors, not twinview or any other method. Is there a way to make it centre itself on the screen it is launched from? Or to at least centre on the primary screen?

---

### Post by Woody1987 on 2010-02-08
I have made some progress. I have managed to make it centre itself on the primary screen. But i would like it to centre on whichever screen it was launched from.

changed it to:
```
QDesktopWidget *desktop = QApplication::desktop();
move((desktop->screenGeometry().width() - this->width()) / 2, (desktop->screenGeometry().height() - this->height()) / 2);
```

---

### Post by Zugzwang on 2010-02-08
> **Woody1987 said:**
> I have made some progress. I have managed to make it centre itself on the primary screen. But i would like it to centre on whichever screen it was launched from.


Now this is tricky. Applications don't get to know from which screen they were launched. They could only have a look which process is their parent and then try to find out if there exist X11 resources belonging to that process. This is very complicated and not likely to be supported by QT.

Wouldn't it be enough to have your application remember its window position? This is supported by QT and not difficult to implement.

---

### Post by Woody1987 on 2010-02-08
> **Zugzwang said:**
> Now this is tricky. Applications don't get to know from which screen they were launched. They could only have a look which process is their parent and then try to find out if there exist X11 resources belonging to that process. This is very complicated and not likely to be supported by QT.

Wouldn't it be enough to have your application remember its window position? This is supported by QT and not difficult to implement.

It really isnt a very important feature, just something that i would like to have. I'll just leave it as it is. Thx

---

