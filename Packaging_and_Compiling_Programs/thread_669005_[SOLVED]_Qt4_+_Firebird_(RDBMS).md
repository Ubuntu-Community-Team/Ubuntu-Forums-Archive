---
title: "[SOLVED] Qt4 + Firebird (RDBMS)"
date: 2008-01-16
forum: Packaging and Compiling Programs
---

### Post by dschulz on 2008-01-16
Hi all,

I'm developing a toy in C++ using Trolltech's Qt4 library, just a small GUI for altering rows of a few tables.

My toy is working properly using QSQLITE driver (Sqlite3), QMYSQL (MySQL 5) and QPSQL (PostgreSQL 8.x), absolutely no problems with those RDBMS, but..

This week I looked at Firebird2 and decided to give it a try. In a few minutes I discovered that the package **libqt4-sql** (the one that provides support for accessing databases from Qt4 apps) comes with just a few drivers enabled (coincidentally the ones that I mentioned above). Firebird is NOT enabled by default. 

I've noticed that OpenSUSE provides independent packages, as plugins, for each RDBMS, for example *"libqt4-sql-drivernamehere"*, while Ubuntu (probably Debian also) provides only one package that enables support for three RDBMSs. I guess if Suse's way of solving this is more convenient...

I've found posts in some mailing lists suggesting to recompile the **libqt4-sql** package in order to enable the QIBASE driver (for Fbird support), but I don't know exactly how to do this.

Any ideas, suggestions, thoughts ?

TIA

note: you may have noticed that I'm not so fluent in English, excuse me :)

---

### Post by dschulz on 2008-01-16
from **libqt4-sql** package description:

> 
Qt 4 SQL database module 
Qt is a cross-platform C++ application framework.  Qt's primary feature
is its rich set of widgets that provide standard GUI functionality.

This package contains the SQL module for Qt. [U] It includes support for
PostgreSQL, MySQL, and SQLite databases.[/U]  If you wish to to use the SQL
module for development, you should install the libqt4-dev package.

---

### Post by dschulz on 2008-01-18
Well, finally I was able to successfully create usable deb packages with Firebird (and Borland Interbase) support enabled. What I did was:




0. Enable  deb-src lines in /etc/apt/sources.list && aptitude update
Then read [this page]("http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/") first if you need help on building deb packages.


1. Create an empty directory, lets say, ~/rebuild then change into it

 ```
 mkdir ~/rebuild && cd ~/rebuild
```

2. Fetch qt4-x11 sources from repository:

```
  apt-get source libqt4-sql
```

3. Install required build dependencies:

```
 sudo apt-get build-dep libqt4-sql  
```

4. Install another new dependencies, since now we need to link against libfbclient also. This should do it:

```
 sudo aptitude install firebird2.0-super firebird2.0-dev libfbclient2
```

I think the **firebird2.0-super** package is not really necessary, but I installed anyways.

5. Unpack the sources. Maybe this is not required, to be sure run

```
 dpkg-source -x qt4-x11_4.3.2-0ubuntu3.1.dsc
```

Note that version numbers may differ. Today is 4.3.2-0ubuntu3.1.

6. Change to the directory where the sources tarball was unpacked

```
 cd qt4-x11-4.3.2/
```

7. Edit **debian/rules** file and add the line 

```

-qt-sql-ibase \

```
 
as another option for **./configure** (line ~44) to make it look like this

```

                    ...
                    -qt-sql-psql \
                    -qt-sql-mysql \
                    -qt-sql-ibase \
                    -qt-sql-sqlite \
                    -system-sqlite \
                    -qt-sql-sqlite2 \
                    ...

```


8. Edit  **config.tests/unix/ibase/ibase.pro** and replace

```
LIBS += -lgds

by

LIBS += -lfbclient
```

9. Edit **src/plugins/sqldrivers/ibase/ibase.pro** and replace

```
unix:!contains( LIBS, .*gds.* ):!contains( LIBS, .*libfb.* ):LIBS    *= -lgds

by 

unix:!contains( LIBS, .*gds.* ):!contains( LIBS, .*libfb.* ):LIBS    *= -lfbclient
```

10. Edit **src/sql/drivers/drivers.pri ** and replace
```

 unix:LIBS *= -lgds

by

 unix:LIBS *= -lfbclient

```

In general you should replace any occurence of  **-lgds** by **-lfbclient** in .pro files.
You can simply **rgrep "lgds" * | less** to find occurences.

11. Finally, compile and build the packages..

```
 dpkg-buildpackage -rfakeroot -b
```

Wait a while. This may take 20-30 minutes, depending on the hardware you are working on. At the end, freshly built deb packages should appear in **~/rebuild**

Reinstall **libqt4-sql** this way:

```
 sudo dpkg -i libqt4-sql_4.3.2-0ubuntu3.1_i386.deb
```


Support for accessing Firebird databases should be working now. 
You can check by writing a small Qt4/C++ app with the following lines:

	```
QStringList availableDrivers = QSqlDatabase::drivers ();

	foreach(QString driver , availableDrivers){
		qDebug() << "Driver: " << driver ;
	}


```

hopefully the program will print what follows:

> 
Driver:  "QPSQL7"
Driver:  "QPSQL"
Driver:  "QMYSQL3"
Driver:  "QMYSQL"
Driver:  "QSQLITE"
Driver:  "QSQLITE2"
**Driver:  "QIBASE"**


---

### Post by dschulz on 2008-01-18
I forgot to mention that you need some build tools installed in order to get this accomplished.

```
sudo aptitude install build-essential
```

Should suffice.

---

### Post by dschulz on 2008-01-18
**[COLOR="Red"]Pending issue:[/COLOR]**  the freshly built **libqt4-sql** package should depend on **libfbclient** (firebird client library). I'm not sure about how this could be solved, but I can imagine that the official maintainers of **libqt4** could simply add **libfbclient** to the list of **Build-Depends** in the **qt4-x11_4.3.2-0ubuntu3.1.dsc** file. 

anybody can point out some clue on this? I'm wrong?

---

### Post by jferrando on 2008-03-30
Now that ubuntu has added firebird2.1 to the list of supported packages, I think it is a good time to **[COLOR="Navy"][SIZE="3"]add the firebirdsql capability to the QtSql driver[/SIZE][/COLOR]**.

I usually do it by recompiling Qt from source, but of course it will be much more comfortable to have it enabled from the packaged files.

To enable firebird and mysql when recompiling Qt, this is what I do:

1) Create a symlink to the firebird library
/usr/lib$ sudo ln -s libfbclient.so.1.5.4 libgds.so

2) Configure Qt
$ ./configure -plugin-sql-mysql -plugin-sql-ibase -I/usr/include/mysql

3) Compile Qt
$ make

4) Install Qt
$ sudo make install

This installs the files in the /usr/local/Trolltech/Qt-4.3.x directory.

---

### Post by mariuz on 2008-12-10
I will submit an bug to qt developers seems they have to use the libfbclient
and not libgds

also i will try to open an launchpad bug where to add this request

---

### Post by booxter on 2008-12-27
Posted the bug: [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/311834](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/311834)

---

### Post by mariuz on 2009-01-19
I wonder why ubuntu doesn't include firebird in the main 

I will send an email to qt developers with the above patches

---

### Post by the.weavster on 2009-10-08
The QT driver for Firebird still doesn't seem to appear in the Ubuntu repository (MySQL, Postgres, ODBC and SQLite all do).

I found it at Debian's site but because the version number was very slightly different to the Ubuntu repositories version of libqt4-sql it wouldn't install.

The Firebird ODBC driver doesn't get listed in the repository either. 

It's easier for Linux users to install all they need for several other databases than it is for Firebird which is a shame.

---

