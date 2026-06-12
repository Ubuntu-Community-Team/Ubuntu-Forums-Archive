---
title: "PyQT4 pulling data from QTableWidget to QLineEdit"
date: 2011-04-09
forum: Programming Talk
---

### Post by slooksterpsv on 2011-04-09
Hi all, I'm having a weird issue where I can't pull data from a table that I populated via mysql. Here's the thing:

1. I have a QTableWidget that has 8 columns (1 unused for now)
2. I click on load and it queries and loads the data into my QTableWidget via MySQL
[php]
try:
            conn = mdb.connect('192.168.x.x', 'xxxxxxxx', 'xxxxxxxx', 'computerrepair')
            cursor = conn.cursor()
            
            cursor.execute("SELECT * FROM comprep WHERE date='"+str(self.calendarWidget.selectedDate().toString("MM/dd/yyyy"))+"'")
              
            rows = cursor.fetchall()
            
            for row in rows:
                self.tableWidget.insertRow(self.tableWidget.rowCount())
                itm1 = QtGui.QTableWidgetItem(str(row[0]), 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 1, itm1)
                itm2 = QtGui.QTableWidgetItem(row[1], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 2, itm2)
                itm2 = QtGui.QTableWidgetItem(row[2], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 3, itm2)
                itm2 = QtGui.QTableWidgetItem(row[3], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 4, itm2)
                itm2 = QtGui.QTableWidgetItem(row[4], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 5, itm2)
                itm2 = QtGui.QTableWidgetItem(row[5], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 6, itm2)
                itm2 = QtGui.QTableWidgetItem(row[6], 0)
                self.tableWidget.setItem(self.tableWidget.rowCount()-1, 7, itm2)
                self.tableWidget.update()
                
            cursor.close()
            conn.close()
[/php]
3. I click on a cell to get the row (which works, the row # changes) and try to load that value into a cell via:
[php]
def pullToFields(self):
        print "PULL TO FIELDS"
        if self.tableWidget.rowCount() > 0:
            #self.crName.setText(self.tableWidget.)
            item = self.tableWidget.itemAt(self.tableWidget.currentRow(), 1)
            #self.crName.setText(item.text())
            print item
        else:
            print "Load Data First"
[/php]
I tried doing self.tableWidget.itemAt(self.tableWidget.currentRow(), 1).text() and .toString()

But it comes back as NONE.

What am I missing?

---

### Post by benson444 on 2011-04-09
itemAt() expects the x, y coordinates of the mouse cursor. You want the item() method.

```
itemText = self.tableWidget.item(self.tableWidget.currentRow(), 1).text()
```

---

### Post by slooksterpsv on 2011-04-09
Thank you that worked perfectly! I'm really liking PyQt4 it's awesome!

:KS:KS:KS:KS:KS

---

### Post by paraxhitman on 2012-09-24
[FONT=Tahoma]My problem is that I want to join MySQL data base with Widgets in PyQt4, and, I want to be able for editing, deleting and adding of information on it and show them on this widgets.
May I ask you, if possible, send to me the related codes and some examples.[/FONT]

---

