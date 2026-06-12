---
title: "linking sql libraries, C++"
date: 2009-05-18
forum: Programming Talk
---

### Post by Alcareru on 2009-05-18
I've done a very simple program to try out db interaction with c++. I've set up a mysql server and created a database there and I am now trying to connect to it from my c++ application. The problem is that I don't know what libraries to add for the linker? I'm running ubuntu 8.10.

I've included headers:
sql.h, sqlext.h and sqltypes.h

P.S. The endproduct will be running on windows and is going to interact with a very old solid db so if you have any advices for that I'd apreciate it.

---

### Post by dwhitney67 on 2009-05-18
In the past, I have relied on something similar to the following, in a Makefile; let me know if you do not understand it.

```

EXE        = myapp
SRCS       = foo.cpp

MYSQL_INC := $(shell mysql_config --include)
MYSQL_LIB := $(shell mysql_config --libs)

INCLUDES   = $(MYSQL_INC) \
             -I/usr/include/mysql++

OBJS       = $(SRCS:.cpp=.o)

CXXFLAGS   = -Wall -pedantic -Wno-long-long -O2
LDFLAGS    = $(MYSQL_LIB) -lmysqlpp

all : $(EXE)

$(EXE): $(OBJS)
        $(CXX) $^ $(LDFLAGS) -o $@

.cpp.o :
        $(CXX) $(CXXFLAGS) $(INCLUDES) -c $<

```

---

### Post by Alcareru on 2009-05-18
> **dwhitney67 said:**
> LDFLAGS    = $(MYSQL_LIB) -lmysqlpp


Says cannot find -lmysqlpp. I suppose I have to install that.. I was hoping to get away with a minimum of additional dependencies, but if I must. :) It should work just the same on windows as well, shouldn't it?

---

### Post by dwhitney67 on 2009-05-18
If you are not using the MySQL++ library, then there is no need to install it.

I figured that since you are programming in C++, that you would rely on the MySQL++ API for your programming needs.  As for the Makefile, you would need to edit the entries for INCLUDES and LDFLAGS.

---

### Post by Alcareru on 2009-05-18
> **dwhitney67 said:**
> If you are not using the MySQL++ library, then there is no need to install it.
The mysql database was just something I'm using on my own for learing purposes, but the end product is going to be interacting with a rather old solid database so mysql++ is probably not going to be very usefull at that point.

So to be more precise I would like to be able to use mysql 5 with merely the funktionalities declared by these headers:
sql.h, sqlext.h and sqltypes.h

That is probably how I'll have to do it in the end anyways. But now I get error at linking:
undefined reference to 'SQLGetInfo'
undefined reference to 'SQLAllocConnect'
... and so on...

So I believe there's some libraries that I should link to the application, but I don't know what.

---

### Post by dwhitney67 on 2009-05-18
Can you please provide the following:

1.  The command and/or Makefile that you are using the build your application.

2.  A sample application that calls the functions you mentioned.  That way I can attempt to duplicate the problem on my system to further investigate the issue.

EDIT:  Examining the MySQL C API, I did not come across the functions that you are attempting to call.  Please confirm that you are indeed calling legit MySQL functions.  Here's a synopsis of the [MySql API]("http://dev.mysql.com/doc/refman/5.0/en/c-api-function-overview.html").

---

### Post by Alcareru on 2009-05-18
SQLGetInfo is declared in the sql.h header file on line 721:

```

SQLRETURN  SQL_API SQLGetInfo(SQLHDBC ConnectionHandle,
                                  SQLUSMALLINT InfoType, SQLPOINTER InfoValue,
                                  SQLSMALLINT BufferLength, SQLSMALLINT *StringLength);

```

Here's my header:
```
#ifndef _SQL_INTERFACE_H
#define	_SQL_INTERFACE_H

#include <sqltypes.h>

class SQL_Interface {
public:
    SQL_Interface();
    SQL_Interface(const SQL_Interface& orig);

    void connect();
    void printInfo();
    void executeQuery();

    virtual ~SQL_Interface();
private:
    HENV environmentHandle;
    HDBC dbConnectionHandle;
    HSTMT statementHandle;
    SDWORD returnCode;
    static int STRING_LENGTH;
    //UCHAR info[STRING_LENGTH];
    UCHAR info[30];
};

#endif	/* _SQL_INTERFACE_H */

```

cpp file:
```

#include "sql_interface.h"
#include <iostream>
#include <sql.h>
#include <sqlext.h>
#include <sqltypes.h>

int SQL_Interface::STRING_LENGTH = 30;

SQL_Interface::SQL_Interface() {
    this->returnCode = SQLAllocEnv(&this->environmentHandle);
}

SQL_Interface::SQL_Interface(const SQL_Interface& orig) {
}

void SQL_Interface::connect() {
    this->returnCode = SQLAllocConnect(this->environmentHandle, &this->dbConnectionHandle);
    SQLCHAR* database = (SQLCHAR*)"MYDATABASE";
    SQLCHAR* uname = (SQLCHAR*)"root";
    SQLCHAR* password = (SQLCHAR*)"mysql5314";
    this->returnCode = SQLConnect(this->dbConnectionHandle, database, SQL_NTS, uname, SQL_NTS, password, SQL_NTS);
}

void SQL_Interface::printInfo() {                                     //STRING_LENGTH
    SQLGetInfo(this->dbConnectionHandle, SQL_DBMS_VER, &this->info, 30, NULL);
            //&cbInfoValue); wtf is this?
}

```

makefile is a mod of what you proposed:
```

EXE			= application.bin
SRCS		= Main.cpp sql_interface.cpp

MYSQL_INC	:= $(shell mysql_config --include)
MYSQL_LIB	:= $(shell mysql_config --libs)

INCLUDES	= $(MYSQL_INC)# -I/usr/include/mysql++

OBJS		= $(SRCS:.cpp=.o)

CXXFLAGS	= -Wall #-pedantic -Wno-long-long -02
LDFLAGS		= $(MYSQL_LIB)# -lmysqlpp

all : $(EXE)

$(EXE) : $(OBJS)
		$(CXX) $^ $(LDFLAGS) -o $@

.cpp.o :
		$(CXX) $(CXXFLAGS) $(INCLUDES) -c $<

```

---

### Post by MadCow108 on 2009-05-18
if you are using mysql++3 (and have the dev files installed), the following command should give you the necessary compiler flags:
mysql_config --cflags --libs
(=> gcc (...) `mysql_config --cflags --libs`)

this is the output on my pc:
-I/usr/include/mysql  -DBIG_JOINS=1 -fPIC -fno-strict-aliasing
-Wl,-Bsymbolic-functions -rdynamic -L/usr/lib/mysql -lmysqlclient

---

### Post by Alcareru on 2009-05-18
> **MadCow108 said:**
> 
mysql_config --cflags --libs

This gives essentially the same output as:
mysql_config --include and mysql_config --libs

After some more research on the matter I think I've now come to realize what I'm trying to do. :) I'm trying to access the mysql database through ODBC. Which in deed is what I wanted to do, but I got a bit confused with all this..

So after installing the libmyodbc and modifying the makefile to this:
```
CC = g++
#CFLAGS = -Wall -ansi -pedantic

EXE			= application.bin
SRCS		= Main.cpp sql_interface.cpp

#MYSQL_INC	:= $(shell mysql_config --include)
#MYSQL_LIB	:= $(shell mysql_config --libs)
MYODBC_LIB	:= -L/usr/lib/odbc

INCLUDES	= /usr/include #$(MYSQL_INC)# -I/usr/include/mysql

OBJS		= $(SRCS:.cpp=.o)

CXXFLAGS	= -Wall #-pedantic -Wno-long-long -02
LDFLAGS		= $(MYODBC_LIB) -lmyodbc # -lmysqlpp

all : $(EXE)

$(EXE) : $(OBJS)
		$(CXX) $^ $(LDFLAGS) -o $@

.cpp.o :
		$(CXX) $(CXXFLAGS) $(INCLUDES) -c $<
```
I finally got it to compile. Now I finally get to beging the struggle to actually get that monster working.. thanks anyways.

---

