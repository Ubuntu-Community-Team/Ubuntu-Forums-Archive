---
title: "Qt, help!"
date: 2010-11-27
forum: Programming Talk
---

### Post by SchindlerShadow on 2010-11-27
ok i got a really stupid question. 
i just finished learning c++, and just started Qt, its a bit over whelming. no real straight forward book.
ok so i got a label and a line edit in mainwindow.
i want to assign whatever is in the line edit to x
and assign label = to x
label is called label
line edit is lineEdit

i try this:
in MainWindow.cpp:

[codebox]
#include "mainwindow.h"
#include "ui_mainwindow.h"
#include <string>

MainWindow::MainWindow(QWidget *parent) :
    QMainWindow(parent),
    ui(new Ui::MainWindow)
{
    ui->setupUi(this);
    string x; //normal string dosent work for some reason even with <string>
    x = "Hello World";
    x = ui->lineEdit->textChanged();
    ui->label->text() = x;
}
MainWindow::~MainWindow()
{
    delete ui;
}
[/codebox]

and i get some crazy errors like

'string' was not declared in this scope line 10 //wtf?
expected ';' before 'x' line 10 //i did that, dident i?
invalid use of member (did you forget the '&' ?) line 11 // why do i need &?
no matching function for call to 'QlineEdit::textChanged()' line 12
no match for 'operator=' in 'QLabel::text() const() = ((MainWindow*)this)->QWidget::x' line 13 //wtf?

maybe im not putting it in the right place? thanks for any help!

---

### Post by Tcressy on 2010-11-27
First things first, please include your code in a code box please, no one wants to read it as provided.

And after a quick glance, when dealing with a qt application it is important to note that QString should be used.

---

### Post by Tcressy on 2010-11-27
Also, if you are wishing to stick with just a regular string, you forgot to include a namespace. 

So either globally declare "using namespace std;" or explicitly std::string x = "Hello World;";

Should work

---

### Post by spjackson on 2010-11-27
When you write "string", I take it that you mean std::string.  However, you are better off using QString because this is what you need for interfacing with Qt.

So you want:
```

QString x = "Hello World";

ui->lineEdit->setText(x);
     x = ui->lineEdit->text();
      
```

textChanged() is a signal (returning void) so you cannot assign its value to x. If you want to respond to textChanged() you need to create a slot and connect your signal to it. (See examples.)

The official tutorials are good and the examples are excellent. [http://doc.trolltech.com/4.6/examples.html](http://doc.trolltech.com/4.6/examples.html)

The definitive book is C++ GUI programming with Qt 4 by Jasmin Blanchette & Mark Summerfield.

---

### Post by SchindlerShadow on 2010-11-27
> **spjackson said:**
> When you write "string", I take it that you mean std::string.  However, you are better off using QString because this is what you need for interfacing with Qt.

So you want:
```

QString x = "Hello World";

ui->lineEdit->setText(x);
     x = ui->lineEdit->text();
      
```

textChanged() is a signal (returning void) so you cannot assign its value to x. If you want to respond to textChanged() you need to create a slot and connect your signal to it. (See examples.)

The official tutorials are good and the examples are excellent. [http://doc.trolltech.com/4.6/examples.html](http://doc.trolltech.com/4.6/examples.html)

The definitive book is C++ GUI programming with Qt 4 by Jasmin Blanchette & Mark Summerfield.

thx lol, sorry forgot the namespace. SOLVED

---

