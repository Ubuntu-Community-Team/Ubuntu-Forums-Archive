---
title: "OBDC support for Qt4."
date: 2007-12-29
forum: Programming Talk
---

### Post by Peter__v on 2007-12-29
How can you install this? the standard Qt4-sql package does not contain QOBDC.

```
QSqlDatabase: available drivers: QPSQL7 QPSQL QMYSQL3 QMYSQL QSQLITE QSQLITE2
```

 Fedora has packages for it:

[http://download.fedora.redhat.com/pub/fedora/linux/extras/6/i386/repoview/qt4-odbc.html](http://download.fedora.redhat.com/pub/fedora/linux/extras/6/i386/repoview/qt4-odbc.html)

I tried installing the rpm with alien, it installed but no luck on actually getting it to work.

I know you can install from source and ./configure, but I have kubuntu, so a lot of packages rely on Qt.Id rather not have 2 different Qt4 installations , that complicates things. Makes sense?

Any ideas?

---

### Post by Peter__v on 2007-12-29
*spelling mistake; should have been ODBC.But theres no .debs for it. I think its strange i dont see much posts about this.

---

