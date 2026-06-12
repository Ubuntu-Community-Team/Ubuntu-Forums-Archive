---
title: "QLCDNumber"
date: 2010-10-17
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-17
Learning about QT atm... and got to tutorial#6... the exercise is to initialize each widget with a random initial setting and certainly I have no problem setting the slider to a random position, but the LCD display won't update until I click and change the slider position.

[php]
#include <QApplication>
#include <QFont>
#include <QGridLayout>
#include <QLCDNumber>
#include <QPushButton>
#include <QSlider>
#include <QVBoxLayout>
#include <QWidget>

#include <stdlib.h> // srand, rand
#include <time.h> // to seed the random number sequence


struct LCDRange: QWidget {
     LCDRange(QWidget *parent = 0);
};

LCDRange::LCDRange(QWidget *parent)
     : QWidget(parent)
{
     QLCDNumber *lcd = new QLCDNumber(2);
     lcd->setSegmentStyle(QLCDNumber::Filled);

     QSlider *slider = new QSlider(Qt::Horizontal);
     slider->setRange(0, 99);
     slider->setValue(rand() % 100); // generate random initial settings
     connect(slider, SIGNAL(valueChanged(int)),
             lcd, SLOT(display(int)));

     QVBoxLayout *layout = new QVBoxLayout;
     layout->addWidget(lcd);
     layout->addWidget(slider);
     setLayout(layout);
}

struct MyWidget: QWidget {
     MyWidget(QWidget *parent = 0);
};

MyWidget::MyWidget(QWidget *parent)
     : QWidget(parent)
{
     QPushButton *quit = new QPushButton(tr("Quit"));
     quit->setFont(QFont("Times", 18, QFont::Bold));
     connect(quit, SIGNAL(clicked()), qApp, SLOT(quit()));

     QGridLayout *grid = new QGridLayout;
     for (int row = 0; row < 3; ++row) {
         for (int column = 0; column < 3; ++column) {
             LCDRange *lcdRange = new LCDRange;
             grid->addWidget(lcdRange, row, column);
         }
     }

     QVBoxLayout *layout = new QVBoxLayout;
     layout->addWidget(quit);
     layout->addLayout(grid);
     setLayout(layout);
}

int main(int argc, char *argv[]) {
	srand(time(NULL)); // seed the random number generator
     QApplication app(argc, argv);
     MyWidget widget;
     widget.show();
     return app.exec();
}
[/php]

Anyone know how to make LCDdisplay initialize to same value as it's slider ?

oh and while I'm here... um so say I wanted to derive from LCD class to display a digital clock time in format hh:mm any siggestions?

---

### Post by GeneralZod on 2010-10-18
For setting the value: it's up to you, really.  You can either move the  

```
connect(slider, SIGNAL(valueChanged(int)), 
             lcd, SLOT(display(int)));
```

up so that it occurs before the call to 

```
slider->setValue(rand() % 100);
```

or you can set it manually via 

```
lcd->display(slider->value());
```

The second way is probably the most clear and robust.

I don't think QLCDNumber is designed to be extended in the way you want, I'm afraid.

---

### Post by worksofcraft on 2010-10-18
> **GeneralZod said:**
> ...
The second way is probably the most clear and robust.

I don't think QLCDNumber is designed to be extended in the way you want, I'm afraid.

Thanks :)

Those both work well and what it also showed me is that setting the value in the code as opposed to by user action also calls the connected call-back.

One of the reasons I'm learning QT now is because I need to be able to derive custom wigets. Using Gtk I got bogged down trying to learn about extending GObject implementations in straight C :confused: However, I do see now this would not be a good test case and I need to learn a bit more about QT first.

---

### Post by GeneralZod on 2010-10-18
There's a neat tutorial here, when you're ready:

[http://www.informit.com/articles/article.aspx?p=1405227](http://www.informit.com/articles/article.aspx?p=1405227)

---

