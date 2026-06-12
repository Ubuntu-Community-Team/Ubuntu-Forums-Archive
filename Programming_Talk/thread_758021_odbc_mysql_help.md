---
title: "odbc mysql help"
date: 2008-04-17
forum: Programming Talk
---

### Post by pacofvf on 2008-04-17
I cant connect to my database with the Full conection example program here :
[http://www.easysoft.com/developer/languages/c/odbc_tutorial.html#connect_simple](http://www.easysoft.com/developer/languages/c/odbc_tutorial.html#connect_simple)

when i type this :$ odbcinst -s -q
[client]
[mysqld_safe]
[mysqld]
[mysqldump]
[isamchk]

ok, i guess i have the odbc drivers to connect to mysql....
but when i compile that program or any example... i get this:
IM002:1:0:[unixODBC][Driver Manager]Data source name not found, and no default driver specified
:confused:,yes i'm new to odbc...lol
ohh and this is how i compile:
gcc foo.c -lodbc -o foo

---

### Post by pacofvf on 2008-04-19
> **pacofvf said:**
> I cant connect to my database with the Full conection example program here :
[http://www.easysoft.com/developer/languages/c/odbc_tutorial.html#connect_simple](http://www.easysoft.com/developer/languages/c/odbc_tutorial.html#connect_simple)

when i type this :$ odbcinst -s -q
[client]
[mysqld_safe]
[mysqld]
[mysqldump]
[isamchk]

ok, i guess i have the odbc drivers to connect to mysql....
but when i compile that program or any example... i get this:
IM002:1:0:[unixODBC][Driver Manager]Data source name not found, and no default driver specified
:confused:,yes i'm new to odbc...lol
ohh and this is how i compile:
gcc foo.c -lodbc -o foo

somebody?? :(

---

### Post by johnmark54 on 2009-12-23
**Here's how I set up unixODBC for mySQL to work with the pyodbc module**
The ubuntu package to install, is naturally

libmyodbc

and I think you need these too, to compile pyodbc:

libmysqlclient-dev

libmysqld-dev

pyodbc-2.1.6.zip is best sourced from

[http://code.google.com/p/pyodbc/](http://code.google.com/p/pyodbc/)

where some documentation and advice can also be found.

Once unzipped, installation includes a compile step

[FONT="Courier New"]% python setup.py build

% python setup.py install[/FONT]

And the module will import!

You'll need to know the socket, for the connection string. The socket can be found in the config file [FONT="Courier New"]/etc/mysql/my.cnf,[/FONT] on ubuntu:
[FONT="Courier New"]
socket = /var/run/mysqld/mysqld.sock[/FONT]

Or to see it just run
[FONT="Courier New"]
% mysqladmin -u root -p version[/FONT]

as mentioned in [http://code.google.com/p/pyodbc/wiki/ConnectionStrings](http://code.google.com/p/pyodbc/wiki/ConnectionStrings)

But the connection string suggested there won't work. And the documentation at [http://www.unixodbc.org/](http://www.unixodbc.org/) is spotty. You'll get this error until you create the odbc config files:

[FONT="Courier New"]IM002:1:0:[unixODBC][Driver Manager]Data source name not found, and no default driver specified[/FONT]

For system DSNs you'll need these files.

_____________________

[FONT="Courier New"]/etc/odbc.ini

[myDSN]

Description = myodbc_driver

Driver = myodbc_driver

Server =

Database =

Port =

Socket =

Option =

Stmt =[/FONT]

___________________

[FONT="Courier New"]/etc/odbcinst.ini

[myodbc_driver]

Description =

Driver = /usr/lib/odbc/libmyodbc.so

Driver64 = /usr/lib

Setup = /usr/lib/odbc/libodbcmyS.so

Setup64 = /usr/lib

UsageCount = 1

CPTimeout =

CPReuse =[/FONT]

(Doing this with the conventional ODBCConfig graphical tool offers nothing more than a form-based editor, with little guidance for what to do.)

Finally you should be able to use this connection string:

[FONT="Courier New"]cn = pyodbc.connect('DRIVER={myodbc_driver};DATABASE=my_db;UID=my_user;PWD=my_pw;SOCKET=/var/run/mysqld/mysqld.sock')[/FONT]

Arguably by filling out the DSN details in odbc.ini the connection string need only refer to the DSN by name, but I haven't tried it.

---

### Post by saimanoj on 2011-12-02
@johnmark54
Thank you very much. It helped me a lot i am suffering from the same problem since 2 days by searching the internet tried several things without use.
But your simple solution helped me out.
Many many thanks  again and again.
My doubt is why this is not yet included in pyodbc documentation.

---

### Post by lucyliue00 on 2012-07-30
> **johnmark54 said:**
> **Here's how I set up unixODBC for mySQL to work with the pyodbc module**
The ubuntu package to install, is naturally

libmyodbc

and I think you need these too, to compile pyodbc:

libmysqlclient-dev

libmysqld-dev

pyodbc-2.1.6.zip is best sourced from

[http://code.google.com/p/pyodbc/](http://code.google.com/p/pyodbc/)

where some documentation and advice can also be found.

Once unzipped, installation includes a compile step

[FONT="Courier New"]% python setup.py build

% python setup.py install[/FONT]

And the module will import!

You'll need to know the socket, for the connection string. The socket can be found in the config file [FONT="Courier New"]/etc/mysql/my.cnf,[/FONT] on ubuntu:
[FONT="Courier New"]
socket = /var/run/mysqld/mysqld.sock[/FONT]

Or to see it just run
[FONT="Courier New"]
% mysqladmin -u root -p version[/FONT]

as mentioned in [http://code.google.com/p/pyodbc/wiki/ConnectionStrings](http://code.google.com/p/pyodbc/wiki/ConnectionStrings)

But the connection string suggested there won't work. And the documentation at [http://www.unixodbc.org/](http://www.unixodbc.org/) is spotty. You'll get this error until you create the odbc config files:

[FONT="Courier New"]IM002:1:0:[unixODBC][Driver Manager]Data source name not found, and no default driver specified[/FONT]

For system DSNs you'll need these files.

_____________________

[FONT="Courier New"]/etc/odbc.ini

[myDSN]

Description = myodbc_driver

Driver = myodbc_driver

Server =

Database =

Port =

Socket =

Option =

Stmt =[/FONT]

___________________

[FONT="Courier New"]/etc/odbcinst.ini

[myodbc_driver]

Description =

Driver = /usr/lib/odbc/libmyodbc.so

Driver64 = /usr/lib

Setup = /usr/lib/odbc/libodbcmyS.so

Setup64 = /usr/lib

UsageCount = 1

CPTimeout =

CPReuse =[/FONT]

(Doing this with the conventional ODBCConfig graphical tool offers nothing more than a form-based editor, with little guidance for what to do.)

Finally you should be able to use this connection string:

[FONT="Courier New"]cn = pyodbc.connect('DRIVER={myodbc_driver};DATABASE=my_db;UID=my_user;PWD=my_pw;SOCKET=/var/run/mysqld/mysqld.sock')[/FONT]

Arguably by filling out the DSN details in odbc.ini the connection string need only refer to the DSN by name, but I haven't tried it.
I am getting an error while using pyodbc. I have installed 'Microsoft  Access Driver (.mdb)' and it is not able to connect to the database in  localhost. Please note my system is not configured as server. I did all  possible check but unable to get over this issue.  Please help.
-L
Log:
>>> import os, sys, pyodbc, pg
>>> DBfile = '/media/Cruzer/NMOC94-11/database/HRNMOC94-11_Access2003.mdb'
>>> conn = pyodbc.connect('DRIVER={Microsoft Access Driver (*.mdb)};DSN=localhost;DBQ='+DBfile)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
pyodbc.Error: ('08001', '[08001] [unixODBC]Could not find Database parameter (1) (SQLDriverConnect)')
>>>

---

