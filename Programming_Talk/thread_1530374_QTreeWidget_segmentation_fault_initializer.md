---
title: "QTreeWidget segmentation fault initializer"
date: 2010-07-13
forum: Programming Talk
---

### Post by matmatmat on 2010-07-13
Hi everybody, I'm trying to make a simple to do list program with QSql and a QTreeWidget. I am trying to add a row to the tree:
[php] void MainWindow::loadTree(){
QTreeWidgetItem* item=new QTreeWidgetItem(ui->treeWidget);
item->setText(0, tr("Hello, world"));
ui->treeWidget->addTopLevelItem(item);
}
[/php]


But when I run this I get a segmentation fault from the first line of the function, why does this happen?

Backtrace:
```


Thread 1 (Thread 0xb7fd6710 (LWP 5955)):
#0  0x0086f8fd in QAbstractItemView::model() const () from /usr/lib/libQtGui.so.4
#1  0x00902a5c in QTreeWidgetItem::QTreeWidgetItem(QTreeWidget*, int) () from /usr/lib/libQtGui.so.4
#2  0x0804bc3e in MainWindow::loadTree (this=0xbffff7fc) at ../tasker/mainwindow.cpp:52
#3  0x0804bbad in MainWindow::connect (this=0xbffff7fc) at ../tasker/mainwindow.cpp:48
#4  0x0804b664 in MainWindow (this=0xbffff7fc, parent=0x0) at ../tasker/mainwindow.cpp:8
#5  0x0804b3f5 in main (argc=1, argv=0xbffff8e4) at ../tasker/main.cpp:7

```

---

