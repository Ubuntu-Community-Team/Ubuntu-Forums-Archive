---
title: "qt4 hide tab bar"
date: 2011-01-07
forum: Programming Talk
---

### Post by Woody1987 on 2011-01-07
I am creating a app using qtcreator/qtdesigner. I have the UI almost perfect, except, I do not want the tabBar of the tabwidget to show when there is only one tab.

The following code looks like it should work, but I get an error.

```

MainWindow::MainWindow(QWidget *parent) : QMainWindow(parent), ui(new Ui::MainWindow)
{
    ui->setupUi(this);
    ui->tabWidget->tabBar()->hide();
}

```

> 
/usr/include/qt4/QtGui/qtabwidget.h:167: error: ‘QTabBar* QTabWidget::tabBar() const’ is protected


In gtkmm I could use:

```

if(numTabs() <= 1)
    tabWidget.set_show_tabs(FALSE);
else
    tabWidget.set_show_tabs(TRUE);

```

Is there a similar function in qt4?

---

### Post by Woody1987 on 2011-01-09
bump

---

