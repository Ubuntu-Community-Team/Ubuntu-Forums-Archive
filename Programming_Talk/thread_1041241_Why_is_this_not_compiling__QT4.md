---
title: "Why is this not compiling?  QT4"
date: 2009-01-16
forum: Programming Talk
---

### Post by TheOrangePeanut on 2009-01-16
I'm following this tutorial:

[http://doc.trolltech.com/4.4/tutorials-tutorial-t6.html](http://doc.trolltech.com/4.4/tutorials-tutorial-t6.html)

This is the relevant section of code that isn't compiling.

```
MyWidget::MyWidget(QWidget *parent) : QWidget(parent)
{
    QPushButton *quit = new QPushButton("Quit");
    quit->setFont(QFont("Times", 18, QFont::Bold));
    connect(quit, SIGNAL(clicked()), qApp, SLOT(quit()));
    
    QGridLayout *grid = new QGridLayout;
    for(int row = 0; row < 3; ++row)
    {
        for(int col = 0; col < 3; ++col)
        {
            LCDRange *lcdRange = new LCDRange;
            grid->addWidget(lcdRange, row, col);
        }
    }
    
    QVBoxLayout *layout = new QVBoxLayout;
    layout->addWidget(quit);
    layout->addWidget(grid);  //error here
    setLayout(layout);
}
```

Here is the error message I'm recieving

```
lcdrange.cpp: In constructor &#8216;MyWidget::MyWidget(QWidget*)&#8217;:
lcdrange.cpp:56: error: no matching function for call to &#8216;QVBoxLayout::addWidget(QGridLayout*&)&#8217;
/usr/include/QtGui/qboxlayout.h:81: note: candidates are: void QBoxLayout::addWidget(QWidget*, int, Qt::Alignment)

```

If I comment out adding grid to layout, the program compiles and runs (albeit only as a quit button on a window).  grid is declared in exactly the same fashion, though populated differently, as quit so I'm not sure why I'm getting throw this error message.  Likewise, it seems to match the tutorial's code... unless I'm missing something, which is very possible.  Can anyone point out what I'm doing wrong?


Edit:  I should have been calling addLayout instead of addWidget.  Duh.  If a mod sees this, delete it.  Thanks.

---

### Post by Zugzwang on 2009-01-16
> **TheOrangePeanut said:**
> If a mod sees this, delete it.  Thanks.

Then please mark this thread as being solved on your own.

---

