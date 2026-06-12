---
title: "[Python] [PyQt] TableView doesn't display like I'd expect"
date: 2012-11-18
forum: Programming Talk
---

### Post by Erik1984 on 2012-11-18
Ok there I am again with another Python question :P I have a few problems with a TableView widget in my PyQt program. I succeed in setting a table model and display that but the layout is not as I would expect (as can be seen in the attached image).

Basically there are three problems:
1. Checkboxes on each cell, how to get rid of them?
2. The text in the columns is not vertically aligned, could that be because one contains a number and the other a string?
3. The columns don't fill the whole table width.

Any ideas how to get that right?

Here is the code responsible for drawing the inteface:
```

    def initUI(self):   
        self.setGeometry(300, 300, 350, 300)
        self.setWindowTitle('Table Test')              
        
        button = QtGui.QPushButton('Test Button', self)
        button.clicked.connect(self.buttonClicked)
        self.dateEdit = QtGui.QDateTimeEdit(QtCore.QDate.currentDate())
        self.dateEdit.setMinimumDate(QtCore.QDate.currentDate().addDays(-365))
        self.dateEdit.setMaximumDate(QtCore.QDate.currentDate().addDays(365))
        self.dateEdit.setDisplayFormat("yyyy.MM.dd");
        
        self.groupbox = QtGui.QGroupBox("Entry")
        self.groupboxLayout = QtGui.QVBoxLayout(self)
        self.groupboxLayout.addWidget(self.dateEdit)
        self.groupboxLayout.addWidget(button)
        self.groupbox.setLayout(self.groupboxLayout)
        
        self.tableModel = MyTableModel(self.database)
        self.tableView = QtGui.QTableView()
        self.tableView.setModel(self.tableModel)

        layout = QtGui.QVBoxLayout(self)
        layout.addWidget(self.tableView)
        layout.addWidget(self.groupbox)
        self.setLayout(layout)
                
        self.show()

```

If you need more pieces of the code I can of course provide them but pasting the entire source might be distracting.

---

### Post by oldfred on 2012-11-18
I am not a python programmer, but am experimenting. :)

Do you have a data model with roles to define the data? 

I converted to using QT designer so my gui is separate from my code. But I wanted my model to display data from many tables so I do not do it what I think is correct in the sense you are to define each column and the roles you want for that columns.

My ui.tableView is from my designer python file.

```
    def loadtbl(self, tbl2):
        #test ='self.ui.' + tblview
        print ("tbl2, tbl: ", tbl2, tbl)
        self.model = Model(self, tbl2)
        self.center()
        self.ui.tableView.setModel(self.model)
        self.ui.tableView.showColumn(1)
        # set column width to fit contents
        self.ui.tableView.resizeColumnsToContents()
        self.ui.tableView.verticalHeader().setVisible(False)
        self.loadtotals(tbl2)
        self.statusBar().showMessage(tbl2)

```

Then in my data model it define the data formatting Note a lot of commented lines where I was testing something or the other.

```
class Model(QSqlTableModel):
    def __init__(self, parent, tblm, *args):
        #QSqlTableModel.__init__(self, parent, *args)
        super(Model, self).__init__(parent)
        self.setEditStrategy(QSqlTableModel.OnRowChange)
        print ("Model tblm: ", tblm)
        self.setTable(tblm)
        self.select()

    def data(self, index, role):
        if not index.isValid():
            return QSqlTableModel.data(self, index, role)
        column = index.column()
        row = index.row()
        #text = index.sibling(index.row(), column).data()
        ValInt = QSqlTableModel.data(self, index).toInt()[0]
        ValFloat = QSqlTableModel.data(self, index).toFloat()[0]
        ValString = QSqlTableModel.data(self, index).toString()
        #testval = ValString.isalpha()
        #print ("text: ", ValInt, ValFloat, ValString)
        if (role == Qt.DisplayRole):
            #print ("text: ", ValInt, ValFloat, ValString)
            if (column > 4 and (ValFloat <> 0)):
                # make sure to convert special classes (otherwise it is user type in QVariant)
                #ff1 = "float: ",float(ValString)
                #ff2 =  '{0:,d}'.format(ValFloat)
                #ff2 = '20:.2'.format(ValFloat)
                #ff3 = format(Decimal('1234567.89'), '.2f')
                #yy= 18446744073709551616.0
                #ff3 = '{:20,.2f}'.format(yy)
                #print(format(ValFloat,"10.2f"))
                return '%0.2f' %ValFloat
                #return "{2:10.2f}".format(ValString)
                #pass
            return QSqlTableModel.data(self, index, role)

        elif (role == Qt.ForegroundRole):
            if (column > 1):
                if ValFloat < 0:
                    return QBrush(Qt.red)
            elif (column == 1):
                return QBrush(Qt.blue)

        elif (role == Qt.TextAlignmentRole):
            if (ValFloat <> 0):
                return int(Qt.AlignRight|Qt.AlignVCenter)
            return int(Qt.AlignLeft|Qt.AlignVCenter)

        return QSqlTableModel.data(self, index, role)

```

---

### Post by Erik1984 on 2012-11-18
Thanks oldfred, roles could be the problem, Currently my code only handles the Qt.DisplayRole case. Guess I didn't get the concept behind those Qt roles yet. I also see that you inherit the TableModel from QSqlTableModel while I base it off QAbstractTableModel. 

This is what I have now:
```

class MyTableModel(QtCore.QAbstractTableModel):
    def __init__(self,database):
        QtCore.QAbstractTableModel.__init__(self)
        self.database = database
        self.model = self.database.getTable("weekly")
        self.header = self.database.getTableColumnNames("weekly")
        print self.header
        print self.model
        
    def data(self,index,role):        
        return self.model[index.row()][index.column()]
        
    def rowCount(self,parent):
        return len(self.model)
        
    def columnCount(self,parent):
        if len(self.header) > 0:
            return len(self.header)
        else:
            return 0
   
    def headerData(self, col, orientation, role):
        if role != QtCore.Qt.DisplayRole:
            return QtCore.QVariant()
        if orientation == QtCore.Qt.Horizontal:
            return self.header[col]
        return QtCore.QVariant()
    
    def getNewData(self):
        print "dataChanged."
        self.emit(QtCore.SIGNAL("LayoutAboutToBeChanged()"))
        self.model = self.database.getTable("weekly")
        self.emit(QtCore.SIGNAL("LayoutChanged()"))
        self.dataChanged.emit(self.createIndex(0, 0),\        
                              self.createIndex(self.rowCount(0),\
                              self.columnCount(0)))
        self.emit(QtCore.SIGNAL("DataChanged(QModelIndex,QModelIndex)"),
                  self.createIndex(0, 0), \
                  self.createIndex(self.rowCount(0), \
                  self.columnCount(0)))

```

---

