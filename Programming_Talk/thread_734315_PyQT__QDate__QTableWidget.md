---
title: "PyQT / QDate / QTableWidget"
date: 2008-03-24
forum: Programming Talk
---

### Post by wrightee on 2008-03-24
Hi, new at PyQT but not coding.. I'm stumbling with QDate and
QTableWidget using PyQT and would appreciate some guidance:

My server gives me a string y[0]: "20080327", which I convert to a
QDateTime object using:

x=QDateTime.fromString(y[0],"yyyymmdd")

Printing x.toString("dd-mm-yyyy") gives me what I would expect -
27-03-2008

What I'm trying to do though is add this to a QTableWidget item to
create a date sortable column; I'm using this:

if type(y)==QDateTime:
                        item=QTableWidgetItem()
                        item.setData(Qt.DisplayRole,QVariant(y))

BUT.. I'm adding 90 dates going back from today and getting values
that look like this:

27/01/2007 00:12
28/01/2007 00:12
29/01/2007 00:12
30/01/2007 00:12
31/01/2007 00:12
01/01/2008 00:01
01/01/2008 00:02
01/01/2008 00:03

etc

I tried using QDate but couldn't seem to be able to get
QDate.fromString to create an object at all.

Could someone please advise where I'm going wrong, the end result
should be a column in my QTableWidget formatted dd/mm/yyyy that can be
sorted as dates, not strings, and originate from data formatted
"YYYYMMDD"

Thank you very much in advance!

---

