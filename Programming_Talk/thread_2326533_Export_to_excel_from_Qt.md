---
title: "Export to excel from Qt"
date: 2016-06-01
forum: Programming Talk
---

### Post by thietnguu on 2016-06-01
Hi alls! i create project " export to excell" form Qt creator. it work on windows7 but on ubuntu not work. help me please!

----
```
QSqlDatabase db = QSqlDatabase::addDatabase("QODBC", "excelexport");
    if(!db.isValid())
    {
        qDebug() << "ExportExcelObject::export2Excel failed: QODBC not supported.";
        return -2;
    }
    // set the dsn string
    QString dsn = QString("DRIVER={Microsoft Excel Driver (*.xls)};DSN='';FIRSTROWHASNAMES=1;READONLY=FALSE;CREATE_DB=\"%1\";DBQ=%2").
                  arg(excelFilePath).arg(excelFilePath);
    db.setDatabaseName(dsn);
    if(!db.open())
```

----

---

### Post by thietnguu on 2016-06-08
Help me please!!!!!!!!!!

---

### Post by howefield on 2016-06-08
Thread moved to the "*Programming Talk*" for want of a better forum than originally posted.

---

### Post by spjackson on 2016-06-08
[LIST]
[*]Where did you get an Excel ODBC driver for Linux?
[*]How did you install it?
[*]What happens when you run your program? Please be more explicit than "on ubuntu not work".
[*]What Qt version are you using?
[/LIST]

---

### Post by thietnguu on 2016-06-08
ok

---

### Post by T.J. on 2016-06-08
> **thietnguu said:**
> Hi alls! i create project " export to excell" form Qt creator. it work on windows7 but on ubuntu not work. help me please!

----
```
QSqlDatabase db = QSqlDatabase::addDatabase("QODBC", "excelexport");
    if(!db.isValid())
    {
        qDebug() << "ExportExcelObject::export2Excel failed: QODBC not supported.";
        return -2;
    }
    // set the dsn string
    QString dsn = QString("DRIVER={Microsoft Excel Driver (*.xls)};DSN='';FIRSTROWHASNAMES=1;READONLY=FALSE;CREATE_DB=\"%1\";DBQ=%2").
                  arg(excelFilePath).arg(excelFilePath);
    db.setDatabaseName(dsn);
    if(!db.open())

```
----


That looks like a Windows specific DSN to me.  While there are ODBC libraries for Linux, in my opinion -  you are better off not using them, because then you are using Microsoft's programming model, which really only works well for Windows.  Everyone else outside of Microsoft has better sense and is interested in cross-platform.  I'd use a more universal format such as ODT, which is more portable and can be opened easily by Excel on Windows and LibreOffice on Linux, Windows and Mac.  Another alternative would be to simply use a CSV - comma separated text file. Excel should be able to read those with no difficulty. Yet another possibility and a favorite of mine is SQLite.

 Plus, as a bonus, by not using Microsoft's native format, you don't have to worry if you are violating someone's patent.  Yes, I know - Microsoft opened the Office format, but has been said that the standard is poorly defined in places. I admit, I haven't looked at it personally, but the fact that LibreOffice seems to refine the filters every so often might be saying something about how clear the Office standard actually is.

---

