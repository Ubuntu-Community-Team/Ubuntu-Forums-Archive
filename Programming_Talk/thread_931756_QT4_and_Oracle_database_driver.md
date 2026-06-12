---
title: "QT4 and Oracle database driver"
date: 2008-09-27
forum: Programming Talk
---

### Post by BitRogue on 2008-09-27
Anyone here using QT4 on (K)Ubuntu to program projects for Oracle databases? I could be missing something but it seems the QT4 package in Ubuntu's repos has not been compiled with the QOCI driver.

Running this code :
```
#include <QtGui>
#include <QtSql>

int main(int argc, char **argv)
{
  QApplication a(argc,argv);
  QMainWindow mainwin;

  QSqlDatabase db;
  db.addDatabase("QOCI");
  db.setDatabaseName("XE");
  db.setUserName("system");
  db.setPassword("anypass");

  mainwin.show();
  return a.exec();
}
```

produces this output:
```
QSqlDatabase: QOCI driver not loaded
QSqlDatabase: available drivers: QPSQL7 QPSQL QMYSQL3 QMYSQL QSQLITE QSQLITE2
```

The QT Assistant docs expressly state that it IS included, so now Im wondering if the Ubuntu developers have deliberately left it out due to some licencing issue and now I have to recompile QT from scratch in order to get included? Or am I missing something?

---

### Post by mikiek on 2009-01-28
I have the same problem trying to connect to oracle. How can I get to libqt4-sql-qoci plugin?
Thanks
Milos

---

### Post by ice.simx on 2009-05-15
i was also having same problem, when running code from QtCreator. then tried it run from terminal - it run perfectly

i only add following line to /etc/ld.so.conf
/opt/qtsdk-2009.02/qt/lib

where /opt/qtsdk-2009.02/qt is my QT install PATH or QTDIR

be sure that libqsqloci.so file exist at $QTDIR/plugins/sqldrivers/

---

### Post by samjh on 2009-05-15
You need libraries from Oracle client in order to compile the Oracle driver for Qt.  Since Oracle client is neither libre or open, I doubt that Debian or Ubuntu maintainers for Qt would be able to compile the driver for it.

I don't know if there is a way to access Oracle databases via Qt's ODBC driver.  Worth experimenting?

---

