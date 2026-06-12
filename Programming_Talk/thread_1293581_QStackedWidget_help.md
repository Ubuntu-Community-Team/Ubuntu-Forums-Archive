---
title: "QStackedWidget help"
date: 2009-10-17
forum: Programming Talk
---

### Post by abhinandh on 2009-10-17
can someone tell me whats wrong with this code
```
QSplitter splitter(Qt::Horizontal);

        QTableWidget *left=new QTableWidget;
        QTableWidget *right=new QTableWidget;
        
        left->setRowCount(5);
        left->setColumnCount(5);
        left->setItem(0,0, &QTableWidgetItem("test"));
        splitter.addWidget(left);
        splitter.addWidget(right);

        ui->stackedWidget->insertWidget(1,&splitter);
        
        ui->stackedWidget->setCurrentIndex(1);
```
the stacked widget is already in the layout( used QtDesigner )
the two table widgets dont show up :(

---

