---
title: "UI code from Qt 4 Designer"
date: 2010-12-08
forum: Programming Talk
---

### Post by Colin@oxford on 2010-12-08
I am trying to get to know QT4 and have started with the GUI creator QT 4 designer.  I am puzzled at the output that it produces, because it does not appear to create classes derived from the QT ones.  For example, a blank "Main window" design gives this as the output after passing through UIC (excluding the headers and namespaces):
```

class Ui_MainWindow
{
public:
    QWidget *centralwidget;
    QMenuBar *menubar;
    QStatusBar *statusbar;

    void setupUi(QMainWindow *MainWindow)
    {
        if (MainWindow->objectName().isEmpty())
            MainWindow->setObjectName(QString::fromUtf8("MainWindow"));
        MainWindow->resize(800, 600);
        centralwidget = new QWidget(MainWindow);
        centralwidget->setObjectName(QString::fromUtf8("centralwidget"));
        MainWindow->setCentralWidget(centralwidget);
        menubar = new QMenuBar(MainWindow);
        menubar->setObjectName(QString::fromUtf8("menubar"));
        menubar->setGeometry(QRect(0, 0, 800, 23));
        MainWindow->setMenuBar(menubar);
        statusbar = new QStatusBar(MainWindow);
        statusbar->setObjectName(QString::fromUtf8("statusbar"));
        MainWindow->setStatusBar(statusbar);

        retranslateUi(MainWindow);

        QMetaObject::connectSlotsByName(MainWindow);
    } // setupUi

    void retranslateUi(QMainWindow *MainWindow)
    {
        MainWindow->setWindowTitle(QApplication::translate("MainWindow", "MainWindow", 0, QApplication::UnicodeUTF8));
    } // retranslateUi

};

namespace Ui {
    class MainWindow: public Ui_MainWindow {};
} // namespace Ui

```

I would have expected that Ui_MainWindow to have been derived from QMainWindow and have a Q_OBJECT as its first item.  As it stands, I cannot see how to display the window (and moc does nothing with this file).

 An example of what I am expecting is in: [http://doc.trolltech.com/4.6/mainwindows-application-mainwindow-h.html]("http://doc.trolltech.com/4.6/mainwindows-application-mainwindow-h.html")

What have I done wrong?

---

### Post by Vaphell on 2010-12-08
and when you type the basic derivative class by hand, does it work? I am currently learning Qt (I skipped Qt convenience tools entirely because real men don't use such stuff) and have no real problem with creating my own classes with Q_OBJECT inside (using codeblocks ide, though i had to hack makefiles a bit).

---

### Post by pelle.k on 2010-12-08
> **Colin@oxford said:**
> What have I done wrong?
[http://doc.qt.nokia.com/4.5/designer-using-a-ui-file.html](http://doc.qt.nokia.com/4.5/designer-using-a-ui-file.html)
Specifically, something much like this should get you going;
```
 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);
     QWidget *widget = new QWidget;
     Ui::CalculatorForm ui;
     ui.setupUi(widget);

     widget->show();
     return app.exec();
 }
```

---

### Post by Colin@oxford on 2010-12-09
Ah, I think I understand.  I was confused because the old (QT3) way provided a class derived from QWidget and put in the Q_OBJECT macro.
Now I have to make that derivation myself.

---

