---
title: "[Qt5] QWindow dnd"
date: 2014-11-25
forum: Programming Talk
---

### Post by kangaba on 2014-11-25
Hi,
Is it possible to have DND on a QWindow or a non-extended QWidget?

The docs say one should extend the QWidget and override the drag functions, but my QWidget is created by Qt so i can't extend it:
QWidget *wrapper = QWidget::createWindowContainer(view, window); // view is a QWindow

So what are my options?


EDIT: I had to wait for Qt 5.4 and use QOpenGLWidget.

---

