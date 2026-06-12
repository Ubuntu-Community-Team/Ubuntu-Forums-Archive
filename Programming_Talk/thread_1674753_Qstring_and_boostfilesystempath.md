---
title: "Qstring and boost::filesystem::path"
date: 2011-01-24
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2011-01-24
I am totally new to Qt and boost. But not new to C++. I am having a bit of a trouble. 

I am using Qt and boost::filesystem:: path on Windows under mingw 4.5.2. My system contains non-english paths. I want, as a simple case, to open an "open file" dialog(QFileDialog) and let the user choose a single file. Then I want to pass the path of the file to boost::filesystem:: path. But it doesn't work if the path contains non-english characters. I can extract the path from the QFileDialog as a QString and display it **correctly** on a QMessageBox.

What kind of character encoding does boost::filesystem:: path expect? I use on my QString on of these member functions: **toLocal8Bit().data()**, **toutf8.data()**, and **toStdString** and it doesn't work. Infact if I use the output of the above functions and display it in a QMessageBox the path is garbled where the non-english character occur.

Obviously this is a character encoding issue and I don't know how to correctly convert the contents of the QString to something that boost::filesystem:: path expects.

PS: I was going to provide a simple program that shows this behavior but I can't even find a simple "hello world" tutorial for Qt that doesn't involve QtCreator. (and they say Qt has awesome support, Gtkmm FTW! :twisted:). Currently I use the source of another program(qbittorrent) that displays this behavior and compile it again and again. Can someone provide a program that displays a simple window with a simple button that opens a QFileDialog in a signal handler?

---

### Post by benson444 on 2011-01-24
I've never used boost and haven't used Windows for years so I can't really help with the encoding issue but here's a little Qt program to help you test.

dialog.h
```
#include <QDialog>

class QLineEdit;

class Dialog : public QDialog
{
    Q_OBJECT
public:
    Dialog(QWidget *parent = 0);
public slots:
    void openFile();
private:
    QLineEdit *lineEdit;
};
```

dialog.cpp
```
#include <QtGui>
#include "dialog.h"

Dialog::Dialog(QWidget *parent)
    : QDialog(parent)
{
    lineEdit = new QLineEdit();
    lineEdit->setReadOnly(true);
    QPushButton *button = new QPushButton("Open a file");
    connect(button, SIGNAL(clicked()), SLOT(openFile()));
    QVBoxLayout *layout = new QVBoxLayout();
    layout->addWidget(lineEdit);
    layout->addWidget(button);
    setLayout(layout);
    resize(500, 0);
}

void Dialog::openFile()
{
    QString filename = QFileDialog::getOpenFileName(
            this, "Select a file", QDir::homePath());
    lineEdit->setText(filename);
}
```

main.cpp
```
#include <QApplication>
#include "dialog.h"

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);

    Dialog *dlg = new Dialog();
    dlg->show();

    return app.exec();
}
```

To compile on Linux you can put the 3 files in the same directory and then run

```
qmake -project
qmake
make
```

---

### Post by SledgeHammer_999 on 2011-01-24
I just finished dissecting and chopping(:twisted:) an example program shown on the qt site and got it to do the basic stuff that I wanted.

Nevertheless, I just tried your program and I like it more.

One innocent mistake in main.cpp. It should be:
```
QApplication app(argc, argv);
```

Thank you benson444

---

### Post by benson444 on 2011-01-24
Darn, I didn't edit quickly enough :D

---

