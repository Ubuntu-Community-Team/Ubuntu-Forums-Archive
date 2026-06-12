---
title: "mysql++ compilation errors"
date: 2013-10-08
forum: Programming Talk
---

### Post by thms2 on 2013-10-08
I'm trying to write a C++ program that will connect to a MySQL database but I can't get it to compile with mysql++.

So, starting with a vanila 12.04 machine I've installed the following packages:
```
sudo apt-get install g++ 
sudo apt-get install mysql-server mysql-client
sudo apt-get install libmysqlclient-dev libmysql++-dev libmysqlcppconn-dev
```

and writen a small test program:
```
#include <iostream>#include <string>
#include <mysql++/mysql++.h>
#include <mysql++/connection.h>
#include <mysql/mysql.h>

using namespace std;

mysqlpp::Connection conn(false);

int main(int argc,char** argv)
{
    string database("...");
    string server("...");
    string user("...");
    string pass("...");
    
    if(!conn.connect(database.c_str(),server.c_str(),user.c_str(),pass.c_str()))
    {
                cerr<<"Couldnt connect to database."<<endl;
                return 1;        
    }
    return 0;
}
```

but when I try compiling it
```
g++ -I/usr/include/mysql -I/usr/include/mysql++  -L/usr/lib -lmysqlpp -lmysqlclient connect.cpp
```
BOOM
```
/tmp/cczYyYGQ.o: In function `main':connect.cpp:(.text+0x119): undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
/tmp/cczYyYGQ.o: In function `__static_initialization_and_destruction_0(int, int)':
connect.cpp:(.text+0x26c): undefined reference to `mysqlpp::Connection::Connection(bool)'
connect.cpp:(.text+0x271): undefined reference to `mysqlpp::Connection::~Connection()'
collect2: ld returned 1 exit status
```


I've tried everything I could find on the web but nothing worked. Any help finding what I'm doing wrong would be much appreciated...

---

### Post by steeldriver on 2013-10-08
link order matters - you need your dependent libs to go AFTER the .cpp file on the g++ command line

---

### Post by spjackson on 2013-10-08
> **thms2 said:**
> 
```
g++ -I/usr/include/mysql -I/usr/include/mysql++  -L/usr/lib -lmysqlpp -lmysqlclient connect.cpp
```
.
Try listing the libraries after your own code:
```

g++ -I/usr/include/mysql -I/usr/include/mysql++  -L/usr/lib connect.cpp -lmysqlpp -lmysqlclient 

```

---

### Post by thms2 on 2013-10-08
Yes it does. Thanks a lot!

---

