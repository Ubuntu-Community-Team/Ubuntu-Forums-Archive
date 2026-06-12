---
title: "[Python/QT4]list+tableWidget"
date: 2008-05-16
forum: Programming Talk
---

### Post by tsic on 2008-05-16
Helo,
I have to put a list l in a TableWidget but the table just put the 2 first element in my list and draw the other raws empty
this is my code:

```

i=0
print len(self.l)
while i<= (len(self.l)-1):
		self.ui.table_cmd_rep.setRowCount(c+1)
		c=c+1
		self.ui.table_cmd_rep.setItem(i, 0, QtGui.QTableWidgetItem(str(self.l[i])))
		self.ui.table_cmd_rep.setItem(i, 1, QtGui.QTableWidgetItem(str(self.l[i+1])))
		i=i+2

```

My list in the beginning has:
['hello', 'salut', 'sava', 'tresbien', 'ok', 'daccord', 'jj', 'tt', 'yy', 'iii']

I have two columns.
Thank you for help

---

### Post by Verminox on 2008-05-16
```
self.ui.table_cmd_rep.setItem(i, 0, QtGui.QTableWidgetItem(str(self.l[i])))
```

Here, the value of 'row' you have given as 'i'. But 'i' is increasing at the rate of 2 per iteration. Shouldn't this value be 'c' instead as 'c' is the current row count ?

---

### Post by tsic on 2008-05-16
That's true:) thanks.
But I have some other problems that I can't find their solution:
1)when I insert a raw I use:
self.table.setVerticalHeaderItem((self.index), QtGui.QTableWidgetItem(txt))
So the problem appear when I remove the line selected the (txt) of the QTableWidgetItem don't change and the others under it for example:
raw 1                            raw 1
raw 2     => I delete raw 2 =>   raw 3 
raw 3             and raw 4      raw 4
raw 4
raw 5

how can I fix that?? 

2)I want to save the list in a file.txt but in specific way that I chose for example raw,column 
I didn't find the opposite of ligne.split(',')
and the opposite of list.append(lign.strip())

If there is an other better way ,I can use??

3)What is the Signal to use to say the selected raw for a tableWidget or the selected column
I used itemClicked(QTableWidgetItem*) but it's not what I exactly want


Thank you a lot

---

