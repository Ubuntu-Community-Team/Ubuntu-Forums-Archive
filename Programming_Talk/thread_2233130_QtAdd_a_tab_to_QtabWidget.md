---
title: "Qt:Add a tab to QtabWidget"
date: 2014-07-06
forum: Programming Talk
---

### Post by fallenshadow on 2014-07-06
I don't know why this seems so complicated. I thought that adding a tab could be done with a single param method like:   Object->addTab("New tab name");

However here I am still banging my head against this, can someone please tell me what im doing wrong?

```

void newDialog::on_buttonBox_accepted()
{
    QLabel *myLabel = new QLabel("Tab");
    uimain->tabWidget->addTab(myLabel, "Tab");
}

```

I am getting a segfault when I click this.  T_T  Also go easy on me, just started learning Qt a week or two ago. :D

---

### Post by spjackson on 2014-07-07
[FONT=arial]I don't see anything amiss in the code you have posted. Are both [COLOR=#000000]uimain and [/COLOR][COLOR=#000000]uimain->tabWidget both valid pointers at this point?[/COLOR][/FONT]

---

### Post by slooksterpsv on 2014-07-07
How are you passing uimain to the new dialog?

---

### Post by fallenshadow on 2014-07-07
In newdialog.h I am doing this:

```
#include "ui_mainwindow.h"

private:
    Ui::newDialog *ui;
    Ui::MainWindow *uimain;
};
```

I will include the code to avoid any confusion. Its a QtCreator project. Crash can be repeated by clicking New>>Ok.

---

### Post by GeneralZod on 2014-07-07
You don't appear to be initialising uimain anywhere.

---

### Post by fallenshadow on 2014-07-07
I tried this but it failed.

```
uimain(new Ui::MainWindow)
```

What do you mean?

---

### Post by slooksterpsv on 2014-07-07
Here's what I updated/changed:

```

//newdialog.h
public:
    explicit newDialog(QWidget *parent = 0, Ui::MainWindow* window = 0);

```

```

//mainwindow.cpp
void MainWindow::on_actionNew_triggered()
{
    newDialog dialog(this, ui);

```

```

//newdialog.cpp

newDialog::newDialog(QWidget *parent, Ui::MainWindow* window) :
    QDialog(parent),
    ui(new Ui::newDialog)
{
    ui->setupUi(this);

    uimain = window;

```

It works after those changes.

---

### Post by fallenshadow on 2014-07-08
Ah right, didn't realize you had to pass in those like a regular OOP method.

I thought being a Qt project it could access other forms from somewhere if I included the ui.h file.

Thanks! I shall continue my journey into Qt. :)

---

### Post by slooksterpsv on 2014-07-08
Qt is just an SDK. It's still C++ overall. So if you need to access a variable or function in a class separate from the one you're working in, you have to have a pointer to access it.

Glad it's fixed =D. If you're satisfied, please mark the thread as Solved and happy coding! =D

---

