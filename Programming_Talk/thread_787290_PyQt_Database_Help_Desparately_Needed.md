---
title: "PyQt Database Help Desparately Needed"
date: 2008-05-08
forum: Programming Talk
---

### Post by peterbrewer on 2008-05-08
I am currently doing a project for a bakery database as part of my first year at university.  The usual procedure is to use Microsoft Access, though I requested the opportunity to look at other options and ended up using Python, QT and SQLite to create a system.

I have a large part of the system working including most forms and some reports.  My main problem is my more complex reports are a bit awkward.

What I have is a table called Stock which references some information from two other tables, specifically a table called Customers and another called Ingredients.  The issue I am having in the form is acquiring data from fields within the system using ID's for these tables.  Also when I have the two relationship queries in the same form it doesn't seem to be able to cope with parsing more than the relationship.  Below is a copy of my code for this class:

```
import sys
from PyQt4.QtCore import *
from PyQt4.QtGui import *
from PyQt4.QtSql import *
import qrc_bakery_rc
import ui_stockdetails
import ui_main
import suppliergui
import titleid
import supplierdetails

STOCKID, STOCKSUPPLIERID, STOCKCOMPNAME, STOCKPHONE, STOCKEMAIL, STOCKINGREDIENTID  = range(6) 

class StockGui(QDialog,
		ui_stockdetails.Ui_StockDetails):
	FIRST, PREV, NEXT, LAST = range(4)
	
	def __init__(self, parent=None):
		super(StockGui, self).__init__(parent)
		self.__index = 0
		self.setupUi(self)

		self.stockModel = QSqlRelationalTableModel(self)
		self.stockModel.setTable("stock")
		self.stockModel.setRelation(STOCKSUPPLIERID,
			QSqlRelation("suppliers", "supplierId", "companyName, contactPhone, contactEmail"))

		self.stockModel.setSort(STOCKID, Qt.AscendingOrder)
		self.stockModel.select()
		self.stockMapper = QDataWidgetMapper(self)
		self.stockMapper.setSubmitPolicy(QDataWidgetMapper.ManualSubmit)
		self.stockMapper.setModel(self.stockModel)
		self.stockMapper.setItemDelegate(QSqlRelationalDelegate(self))
		self.stockMapper.addMapping(self.stockSupplierContactNameEdit, STOCKCOMPNAME)

		stockRelationModel = self.stockModel.relationModel(STOCKSUPPLIERID)
		self.stockSupplierNameComboxBox.setModel(stockRelationModel)
		self.stockSupplierNameComboxBox.setModelColumn(
			stockRelationModel.fieldIndex("companyName"))
		self.stockMapper.addMapping(self.stockSupplierNameComboxBox, STOCKSUPPLIERID)
		#self.stockSupplierContactNameEdit.setModel(stockRelationModel)
		#self.stockSupplierContactNameEdit.setModelColumn(
			#stockRelationalModel.fieldIndex("contactForename"))
			
		self.stockModel.setRelation(STOCKINGREDIENTID,
			QSqlRelation("ingredient", "ingredientId", "name, unitMinQuantity, unitDescriptorId"))
		stockIngredientRelationModel = self.stockModel.relationModel (STOCKINGREDIENTID)
		self.stockIngredientTypeComboBox.setModel(stockIngredientRelationModel)
		self.stockIngredientTypeComboBox.setModelColumn(
			stockIngredientRelationModel.fieldIndex("name"))
		self.stockMapper.addMapping(self.stockIngredientTypeComboBox, STOCKINGREDIENTID)
		self.stockMapper.toFirst()


		#self.connect(self.stockViewButton, SIGNAL("clicked()"), supplierdetails.run2(STOCKSUPPLIERID))
		#self.connect(self.supplierEditTitlesButton, SIGNAL("clicked()"), titleid.run)
		self.connect(self.stockFirstRecordButton, SIGNAL("clicked()"),
			lambda: self.saveStockRecord(StockGui.FIRST))
		self.connect(self.stockPreviousRecordButton, SIGNAL("clicked()"),
			lambda: self.saveStockRecord(StockGui.PREV))
		self.connect(self.stockNextRecordButton, SIGNAL("clicked()"),
			lambda: self.saveStockRecord(StockGui.NEXT))
		self.connect(self.stockLastRecordButton, SIGNAL("clicked()"),
			lambda: self.saveStockRecord(StockGui.LAST))
		self.connect(self.stockNewRecordButton, SIGNAL("clicked()"), self.addStockRecord)
		#self.connect(self.stockDeleteRecordButton, SIGNAL("clicked()"),
		#	self.deleteSupplierRecord)
		self.connect(self.stockQuitButton, SIGNAL("clicked()"), self.done)
	def done(self, result=None):
		self.stockMapper.submit()
		QDialog.done(self, True)
	def addStockRecord(self):
		row = self.stockModel.rowCount()
		self.stockMapper.submit()
		self.stockModel.insertRow(row)
		self.stockMapper.setCurrentIndex(row)
		#now = QDateTime.currentDateTime()
		#self.startDateTime.setDateTime(now)
		##self.endDateTime.setDateTime(now)
		#self.supplierTitleComboBox.setCurrentIndex(
			#self.spplierTitleComboBox.findText("Other"))
		self.stockSupplierNameComboxBox.setFocus()
		self.stockModel.submitAll()
	def deleteSupplierRecord(self):
		#companyName = self.supplierCompanyNameEdit.text()
		#if QMessageBox.question(self,
			#QString("Delete"),
			#QString("Delete reference to supplier: <br>%1") \
				#.arg(companyName),
				#QMessageBox.Yes|QMessageBox.No) == QMessageBox.No:
			#return
		#row = self.supplierMapper.currentIndex()
		#self.suppliersModel.removeRow(row)
		#self.suppliersModel.submitAll()
		#if row + 1 >= self.suppliersModel.rowCount():
			#row = self.suppliersModel.rowCount() - 1
		#self.supplierMapper.setCurrentIndex(row)


		def saveStockRecord(self, where):
			row = self.stockMapper.currentIndex()
			self.stockMapper.submit()
			if where == StockGui.FIRST:
				row = 0
			elif where == StockGui.PREV:
				row = 0 if row <= 1 else row - 1
			elif where == StockGui.NEXT:
				row += 1
				if row >= self.stockModel.rowCount():
					row = self.stockModel.rowCount() - 1
			elif where == StockGui.LAST:
				row = self.stockModel.rowCount() - 1
			self.stockMapper.setCurrentIndex(row)
		


#Stock Items Tab

		#self.connect(quitButton, SIGNAL("clicked()"), self.done)
#Customers Tab

		#self.connect(quitButton, SIGNAL("clicked()"), self.done)
#Batches Tab
		#self.connect(quitButton, SIGNAL("clicked()"), self.done)

#def start():
	#form = MainWindow()
	#form.show()
def run():
	form = StockGui()
	form.show()


```

---

### Post by pmasiar on 2008-05-08
If you can, try doing it as web application. Python with Django - ORM will generate all the methods you need, and admin interface is there for free too. You want to finish it before the summer? Late start? :-)

---

### Post by peterbrewer on 2008-05-09
Thanks for the advice and I will look into it on later projects. Unfortunately one of the requirements was that it had to be a client side system.  Also I have done a significant amount of work already.

---

### Post by pmasiar on 2008-05-09
QSqlRelationalTableModel is imported from PyQt4.QtSql?

import * is discouraged, because it's hard to see where the name came from - if I want to remember it all, i can do it as well in Java :-)

Maybe your ORM mapper sucks, consider SQLObject or SQLAlchemy

---

### Post by tseliot on 2008-05-09
> **pmasiar said:**
> QSqlRelationalTableModel is imported from PyQt4.QtSql?

import * is discouraged, because it's hard to see where the name came from - if I want to remember it all, i can do it as well in Java :-)
I'm not as experienced as you and I know I can trust you, however this is used (and therefore suggested) in the book of PyQt4:

```

from PyQt4.QtCore import *
from PyQt4.QtGui import *

```

---

### Post by pmasiar on 2008-05-09
I am not **that** experienced - I can only pretend being expert on TV :-)

Even if docs suggest using it, it is still bad habit, and as such should be used with care (not for your own or other modules). Preferbale is: "from module1 import name1, nam2, name3", you can even give them shorter names for convenience in import.

I've seen once error like that: import * populates your namespace with all kinds of names, error was in defining the same name as own function - and all hell broke lose. Rather confusing. If you are **absolutely certain** then you may ignore the warning - but when you have error you again do not know where the name was defined, which module injected it.

---

### Post by tseliot on 2008-05-09
> **pmasiar said:**
> I've seen once error like that: import * populates your namespace with all kinds of names, error was in defining the same name as own function - and all hell broke lose. Rather confusing. If you are **absolutely certain** then you may ignore the warning - but when you have error you again do not know where the name was defined, which module injected it.
Ok, I see your point (and you're right) however it is also true that it would take a perverted mind to use the names which you can see in the [class reference]("http://doc.trolltech.com/4.3/classes.html") :-P

Just kidding, eh

---

### Post by pmasiar on 2008-05-09
Yup, most are longish, and all start with Q, so possibly in this case you might be almost safe. :-)

---

### Post by LaRoza on 2008-05-09
> **tseliot said:**
> I'm not as experienced as you and I know I can trust you, however this is used (and therefore suggested) in the book of PyQt4:

```

from PyQt4.QtCore import *
from PyQt4.QtGui import *

```

It seems a lot of GUI toolkits recommend that. In QT, GTK+ and Tk at least, the names usually are obviously part of that namespace because of the naming schemes. I don't like it though, and I like to use shortened names of the toolkit, ie "import PyQT4.QTCore as Core" or something. (I don't use QT, so I just used that as an example.)

---

### Post by tw55413 on 2008-09-06
You can try [http://www.conceptive.be/projects/camelot](http://www.conceptive.be/projects/camelot) to build your pyqt GUI based on sqlalchemy objects

---

