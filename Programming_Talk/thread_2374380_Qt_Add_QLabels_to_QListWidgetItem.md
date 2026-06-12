---
title: "Qt: Add QLabels to QListWidgetItem?"
date: 2017-10-15
forum: Programming Talk
---

### Post by fallenshadow on 2017-10-15
Hi all,

Spent nearly 2 hours just trying to add some QLabels to a QListWidgetItem. Only text would succeed in being added to it. No QLabel or QPushButton could be added. 

Is it possible or not?

---

### Post by norobro on 2017-10-15
> **fallenshadow said:**
> Is it possible or not?
Sure. See here: [http://doc.qt.io/qt-5/qlistwidget.html#setItemWidget](http://doc.qt.io/qt-5/qlistwidget.html#setItemWidget)

---

### Post by fallenshadow on 2017-10-16
All I ever see is the QListWidgetItem but not the QLabel:

```

QLabel *label = new QLabel();
    label->setText("test");

    QListWidgetItem *item = new QListWidgetItem();
    item->setText("lol");

    QHBoxLayout *layout = new QHBoxLayout();
    layout->addWidget(label);

    QWidget *widget = new QWidget();
    widget->setLayout(layout);

    ui->listWidget->setItemWidget(item,widget);
    ui->listWidget->addItem(item);

```

Any ideas? Is it the order of what im doing here? I thought this would be more straight forward.

---

### Post by norobro on 2017-10-16
[SIZE=2]Apparently the widget is too large to fit on the row. I got it to show by supplying a size hint for the QListWidgetItem. The docs say that if no size hint is set one will be computed but it doesn't seem to work. [http://doc.qt.io/qt-5/qlistwidgetitem.html#setSizeHint](http://doc.qt.io/qt-5/qlistwidgetitem.html#setSizeHint)

Here's what worked for me:```
...
    widget->setLayout(layout);

    qDebug() << item->sizeHint();  // returns QSize(-1, -1)
    
    item->setSizeHint(QSize(0, 30));

    ui->listWidget->addItem(item);

    ui->listWidget->setItemWidget(item,widget);
...
```[/SIZE]

---

### Post by fallenshadow on 2017-10-17
Thanks, that worked great! Just having an issue setting the background colour of the QLabel now but that is a separate issue.

---

### Post by norobro on 2017-10-18
Are you using setStyleSheet()? 
[http://doc.qt.io/qt-5/qwidget.html#styleSheet-prop](http://doc.qt.io/qt-5/qwidget.html#styleSheet-prop)
[http://doc.qt.io/qt-5/stylesheet-reference.html](http://doc.qt.io/qt-5/stylesheet-reference.html)

Should be a matter of one statement. For example:```
label->setStyleSheet("color: white; background: red;");
```

---

### Post by fallenshadow on 2017-10-18
Thanks, I was trying to use QPalette which worked before for setting the background colour but not in this case. SetStylesheet worked better for me.

---

