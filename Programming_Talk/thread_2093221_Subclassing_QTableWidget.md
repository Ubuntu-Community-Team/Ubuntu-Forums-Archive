---
title: "Subclassing QTableWidget"
date: 2012-12-10
forum: Programming Talk
---

### Post by Woody1987 on 2012-12-10
I have subclassed QTableWidget and I am trying to populate it. But setItem doesnt seem to work, nothing is displayed when I run it. What am I doing wrong?

```
#include <QTableWidget>

class MyTableWidget : public QTableWidget
{
    Q_OBJECT
public:
    MyTableWidget (QWidget *parent = 0);
    void refresh();

private:
    int currentRow;
};
```

```
#include "MyTableWidget .h"

MyTableWidget ::MyTableWidget (QWidget *parent) : QTableWidget(parent)
{
    refresh();
}

void MyTableWidget ::refresh()
{
    setRowCount(1);
    setItem(0, 0, new QTableWidgetItem("test"));
}
```

---

### Post by muteXe on 2012-12-10
This might be a silly question, but you are definitely new'ing up your specialised class instead of the base now?

---

### Post by Woody1987 on 2012-12-10
In qtcreator I have a qtablewidget which I have promoted to my custom one. I know that refresh is being called because when I run it, the table displays an empty row, without the qTableWidgetItem.

---

### Post by Woody1987 on 2012-12-10
Solved, Items weren't showing up because I had defined the columns for my custom table in the designer. Once I removed them and set them up within the constructor, it all worked.

---

