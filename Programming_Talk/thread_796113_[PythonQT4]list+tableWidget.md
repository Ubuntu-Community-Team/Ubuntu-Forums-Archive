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

### Post by tsic on 2008-05-16
I modified my code like this:
```

while i<= (len(self.l)-1):
	self.ui.table_cmd_rep.setRowCount(c+1)
	print "c= ", c
	txt = "commande %d" % (c+1)
	self.ui.table_cmd_rep.setVerticalHeaderItem((c), QtGui.QTableWidgetItem(txt))
	self.ui.table_cmd_rep.setItem(i, 0, QtGui.QTableWidgetItem(str(self.l[i])))
	self.ui.table_cmd_rep.setItem(i, 1, QtGui.QTableWidgetItem(str(self.l[i+1])))
			
	i=i+2
	c=c+2
	print "c= ", c

```

The list appear in the tableWidget but there is an extra line:

---

