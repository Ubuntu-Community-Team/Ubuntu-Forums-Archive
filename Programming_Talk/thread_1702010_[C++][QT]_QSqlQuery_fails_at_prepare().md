---
title: "[C++][QT] QSqlQuery fails at prepare()"
date: 2011-03-07
forum: Programming Talk
---

### Post by dawwin on 2011-03-07
I've got following code:
```

    QString dbFile;
    QSqlDatabase db;

    dbFile = "./NCDatabase.db";
    db = QSqlDatabase::addDatabase("QSQLITE");
    db.setDatabaseName(dbFile);
    if (db.open() == false) {
        QMessageBox::critical(0, "Error", "Error");
        return;
    }

    QSqlQuery query;
    if (query.prepare("create table :table (option varchar(255), df varchar(255))") == false) {
        QMessageBox::critical(0, "Error", "Error2");
    }

```Does anyone know, why prepare() fails here?
QSqlQuery::lastError() returns 'near "?": syntax error Unable to execute statement'

---

### Post by Some Penguin on 2011-03-07
Not an SQLLite user (more PostgreSQL and some MySQL), but it looks to me like you're either trying to create a table named 'table' (unlikely to work since it's going to be a reserved keyword) or create a prepared statement with a placeholder for a table name (also unlikely to work, because a prepared statement is meant to be something optimized for repeated calls with just a bit of interpolation -- and changing the table completely defeats the purpose of that, because a different table means you get to call the query optimizer all over again for a completely different schema).

---

### Post by dawwin on 2011-03-07
I didn't even call bindValue() to replace ':table' because it doesn't have sense if prepare() fails.
I tried to use SELECT in MySQL and I have the same error
```

    QSqlDatabase db;

    db = QSqlDatabase::addDatabase("QMYSQL");
    db.setHostName("localhost");
    db.setDatabaseName("abcd");
    db.setUserName("root");
    db.setPassword("password");
    if (db.open() == false) {
        QMessageBox::critical(0, "Error", "Error");
        return;
    }

    QSqlQuery query;
    if (query.prepare("select * from :tabname") == false) { // <<<< it returns false
        QMessageBox::critical(0, "Error", "Error2"); 
    }

```

---

### Post by Some Penguin on 2011-03-07
As I wrote earlier, don't expect to be able to use a placeholder for a table name.

---

### Post by dawwin on 2011-03-07
I didn't read it at the first time, thanks for help

---

