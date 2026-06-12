---
title: "C++ Qt Segfault onclick?"
date: 2015-02-21
forum: Programming Talk
---

### Post by fallenshadow on 2015-02-21
Hey all,

Having this annoying issue, getting a segfault when I click. Anything out of order here?

_MainWindow.h_
//Public
```
PaintWidget* getCurrentWidget();
```

_MainWindow.cpp_

```
PaintWidget* MainWindow::getCurrentWidget()
{
    PaintWidget *widget = static_cast<PaintWidget *>(ui->tabWidget->currentWidget()); //FAILS HERE
    return widget;
}
```

//Private
_ColourPicker.h_
```
MainWindow *main;
```

_ColourPicker.cpp_

```
void ColourPickerTool::onMousePress(const QPoint &pos, Qt::MouseButton button)
{
    Q_UNUSED(button);

    d->lastPos = pos;
    d->mouseButton = button;
    qDebug() << "Hello world." << pos.x() << " " << pos.y();

    PaintWidget *currentWidget = main->getCurrentWidget();

}
```

Any help or advice greatly appreciated.

---

### Post by spjackson on 2015-02-21
I would suspect that you are dereferencing a null pointer (or an otherwise invalid one). Is main null? or main->ui? or main->ui->tabWidget?

---

### Post by fallenshadow on 2015-02-22
I changed it up to using a QImage return type because really its the QImage I need access to but I'm not doing something quite right. Wouldn't be surprised if its something silly, as im just trying to get back into some OOP. Sent you a PM as its probably easier to just have a look at it directly.

---

### Post by fallenshadow on 2015-02-23
If you don't want to hands on help me or don't have time its okay btw. I may figure it out if I get more time to spend on it next weekend.

---

### Post by spjackson on 2015-02-23
_mainwindow.h_
```

QImage* MainWindow::getCurrentWidget();

```
I don't think you should be returning a pointer to the image since in the implementation you are getting a copy of a QImage object. Hence:
```

QImage MainWindow::getCurrentWidget();

```

and change mainwindow.cpp accordingly.

However, the above is **not** the cause of the crash. This is simply that ColourPickerTool's private member "main" is never initialised. So when you do:
```

QImage currentImage = main->getCurrentWidget();

```
you are de-referencing an invalid pointer. Somewhere you need to set main to the address of your MainWindow object.

---

### Post by fallenshadow on 2015-02-23
Thanks, I'll see what I can come up with as a solution.

---

