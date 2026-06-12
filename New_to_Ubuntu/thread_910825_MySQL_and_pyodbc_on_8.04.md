---
title: "MySQL and pyodbc on 8.04"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Jukey91 on 2008-09-04
Has anybody managed to install the MySQL 5.1.5 ODBC connector on 8.04?  I see that Synaptic has libmyodbc, but this version is 3.51.  I'd like to use 5.1.5.  I didn't see a built version of this, for Ubuntu, on the MySQL site.  I did download the source, but I can't find any documentation on what to do to make it build on Ubuntu.  The MySQL INSTALL document, that came with the source code, says just to "build it".  Well, what all does that mean?  If anybody has done this, I'd appreciate any advice.

How about pyodbc?  I did manage to build that one.  In order to compile pyodbc, I had to install g++, as well as the header files for unixodbc (unixodbc-dev).  Once I did this, it built and installed.  A quick check in python (pyodbc.version) showed that I was running 2.0.58...the latest version.  Has anybody else installed pyodbc on Ubuntu?  Do my steps match up with what you did?

---

### Post by Jukey91 on 2008-09-05
I was able to get it to work after a few hours of trying different things.  Now I am able to communicate with a MySQL server on another PC through the pyodbc module in Python, using Hardy Heron.  If anybody ever wants to use pyodbc to talk to MySQL, here is how to set it up...


1. MySQL connector:

- From Synaptic, install unixodbc.  You will also need to install unixodbc-dev (this is needed to build pyodbc).

- Download the MySQL 5.1.5 non-rpm odbc connector

- From the downloaded contents: 'cp -d ./lib/* /usr/local/lib'

- I initially tried to run ./bin/myodbc-installer.  I had a lot of hassle trying to get this to work.  Different packages were required to run this command, and those packages had to be built, which required other packages.  The end result is that myodbc-installer does the same thing as editing /etc/odbcinst.ini and /etc/odbc.ini.  If you want to avoid this hassle, then DON'T BOTHER WITH MYODBC-INSTALLER and just manually edit these other two files.  Trying to use myodbc-installer was where the lion's share of my time was wasted.  ](*,)

- Edit /etc/odbcinst.ini to say:
[MySQL]
Description     = MySQL ODBC 5.1 Driver (this can be an arbitrary name)
Driver          = /usr/local/lib/libmyodbc5.so
Setup           = /usr/local/lib/libmyodbc3S.so
UsageCount      = 1

- This is not necessary, but if you want to configure a DSN, you can add this to /etc/odbc.ini.  The Driver line must match the section name you provided in odbcinst.ini, which was [MySQL]:
[MySQL-test]
Description     = MySQL test database (this can be an arbitrary name)
Trace           = Off
TraceFile       = stderr
Driver          = MySQL
SERVER          = 192.168.1.26
USER            = user
PASSWORD        = password
PORT            = 3306
DATABASE        = test


2. pyodbc

- download the pyodbc source files

- unixodbc-dev was already installed, from above.  These header files are needed for pyodbc compilation.

- You also need to install the headers for your current Python version.  This was available in Synaptic as python2.5-dev.

- Now go to the pyodbc source folder and 'python setup.py install'.  This will build pyodbc and put it in the right place.


3. Testing

- Now that you have done the first two steps, open a python shell and type the following:
>>> import pyodbc
>>> pyodbc.connect('DRIVER={MySQL};SERVER=192.168.1.4;DATABASE=test;UID=username;PWD=password')

- You should see a pyodbc connection object was returned.  This means that you are connected and can use the rest of pyodbc to do what you need to do on MySQL.  You're done!  \\:D/ Note that I typed in the connection string into pyodbc.connect().  I did this because I did not put anything in /etc/odbc.ini.  Of course, you can put something in /etc/odbc.ini and then your function call would look like this:
>>> pyodbc.connect("DSN=MySQL")


If somebody else comes across this usage of pyodbc and MySQL, then I hope these instructions will help you save the hours of frustration that I went through to get to the end result.


Here are a couple of websites which were helpful:
[http://www.unixodbc.org/odbcinst.html](http://www.unixodbc.org/odbcinst.html)
[http://pyodbc.sourceforge.net/docs.html](http://pyodbc.sourceforge.net/docs.html)

---

### Post by rinoco on 2008-09-24
Thanks for your info. This is really helpful.
However, MySQL ODBC Connector 5.1.15 seems to have some problems with UTF-8
encoding. I had to downgrade to 3.51 to solve the encoding problem.

Hope this will help someone, too.

---

### Post by Jukey91 on 2008-09-24
I found the following reply regarding UTF-8 and MySQL ODBC.  Maybe this is the problem you are having.

-----------------------------------
How are you retrieving the data? If you are using SQL_C_CHAR, you will
get data in the latin1 character set. For Unicode data, you need to use
SQL_C_WCHAR. There is no portable way to get Unicode data as UTF-8 data
directly using ODBC.

Jim Winstead
MySQL Inc. 
-----------------------------------


[http://www.nabble.com/Utf8-errors-when-using-mysql-odbc-5.1-connector-td15225026.html]("http://www.nabble.com/Utf8-errors-when-using-mysql-odbc-5.1-connector-td15225026.html")

---

### Post by rinoco on 2008-11-15
I specified CHARSET=utf8 in the connect function parameter.
It solves my problem.

Hope it will help.

---

