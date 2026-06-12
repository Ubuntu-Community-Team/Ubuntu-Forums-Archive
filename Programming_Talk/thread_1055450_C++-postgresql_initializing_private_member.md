---
title: "C++-postgresql initializing private member"
date: 2009-01-30
forum: Programming Talk
---

### Post by bo01 on 2009-01-30
Hi again guys and I'm sorry for opening many threads but I need some help.

Here is a simple program:

```
#include <pqxx/pqxx>

using namespace std;
using namespace pqxx;

class test {
private:
connection conn;

public:
void foo(){conn=connection("dbname=temp");
}

};


int main() {

test t;
t.foo();

return 0;
}


```

And when I'm trying to compile it with:

```
g++ -o test.o test.cpp -lpqxx
```

I get the following output.


```
/usr/local/include/pqxx/connection_base.hxx: In copy constructor ‘pqxx::basic_connection<pqxx::connect_direct>::basic_connection(const pqxx::basic_connection<pqxx::connect_direct>&)’:
/usr/local/include/pqxx/connection_base.hxx:904: error: ‘pqxx::connection_base::connection_base(const pqxx::connection_base&)’ is private
/usr/local/include/pqxx/basic_connection.hxx:50: error: within this context
test.cpp: In member function ‘void test::foo()’:
test.cpp:11: note: synthesized method ‘pqxx::basic_connection<pqxx::connect_direct>::basic_connection(const pqxx::basic_connection<pqxx::connect_direct>&)’ first required here 
/usr/local/include/pqxx/connection_base.hxx: In member function ‘pqxx::basic_connection<pqxx::connect_direct>& pqxx::basic_connection<pqxx::connect_direct>::operator=(const pqxx::basic_connection<pqxx::connect_direct>&)’:
/usr/local/include/pqxx/connection_base.hxx:905: error: ‘pqxx::connection_base& pqxx::connection_base::operator=(const pqxx::connection_base&)’ is private
/usr/local/include/pqxx/basic_connection.hxx:50: error: within this context
test.cpp: In member function ‘void test::foo()’:
test.cpp:11: note: synthesized method ‘pqxx::basic_connection<pqxx::connect_direct>& pqxx::basic_connection<pqxx::connect_direct>::operator=(const pqxx::basic_connection<pqxx::connect_direct>&)’ first required here 
```

I realize obviously that the problem is when I'm trying to call the constructor connection() to the private member conn.

But how can I initialize this object (conn)?

As far as I know, libpqxx has not any function like PQconnectdb() that libpq (for C) has. For this purpose, it is used the constructor connection(), that I cannot use above.

I would be glad if someone can help me.

Thanks in advance.

---

### Post by snova on 2009-01-30
> **bo01 said:**
> ```

class test {
private:
connection conn;

public:
void foo(){conn=connection("dbname=temp");
}

};

```

You could store **conn** as a pointer:

[PHP]
class Test
{
    private:
        connection* conn;
    public:
        void foo()
        {
            conn = new connection("dbname=temp");
        }
};
[/PHP]

Just remember to delete it later on when you're done with it... a destructor or something, depending on the class.

---

### Post by bo01 on 2009-01-31
Thank you snova, but later on if I want to send some queries to the conn object how I am going to do that?

The changed code doesn't work:


```
#include <pqxx/pqxx>

using namespace std;
using namespace pqxx;

class test {
private:
connection* conn;

public:
void foo(){
    conn=new connection("dbname=temp");
}


result boo()  {
    work trans(conn, "Demo");

    result res=trans.exec("select * from profile;");

    trans.commit();

    return res;
}


};


int main() {

test t;
t.foo();


result r;
r=t.boo();



return 0;
}
```


And the compile output:

```
tre.cpp: In member function &#8216;pqxx::result test::boo()&#8217;:
tre.cpp:17: error: no matching function for call to &#8216;pqxx::transaction<read_committed>::transaction(pqxx::connection*&, const char [5])&#8217;
/usr/local/include/pqxx/transaction.hxx:98: note: candidates are: pqxx::transaction<ISOLATIONLEVEL>::transaction(pqxx::connection_base&) [with pqxx::isolation_level ISOLATIONLEVEL = read_committed]
/usr/local/include/pqxx/transaction.hxx:93: note:                 pqxx::transaction<ISOLATIONLEVEL>::transaction(pqxx::connection_base&, const std::string&) [with pqxx::isolation_level ISOLATIONLEVEL = read_committed]
/usr/local/include/pqxx/transaction.hxx:83: note:                 pqxx::transaction<read_committed>::transaction(const pqxx::transaction<read_committed>&)

```


Thanks again.

---

### Post by dwhitney67 on 2009-01-31
Try specifying a const reference to the connection object.  Strangely though, one must strip away the const-ness before using the connection.

I would recommend that you use a different DB with a better C++ library (e.g. MySql++).

Here's some code that will assist you with your Postgresql testing:
```

#include <pqxx/pqxx>

using namespace pqxx;

class DataBase
{
  public:
    DataBase()
      : m_conn(connection("dbname"))
    {
    }

    result doQuery(const std::string query)
    {
      work action(const_cast<connection&>(m_conn), "Demo");

      result res = action.exec(query);

      action.commit();

      return res;
    }

  private:
    const connection& m_conn;
};

int main()
{
  DataBase db;
  result res = db.doQuery("select * from foo");
}

```

---

### Post by bo01 on 2009-01-31
Thanks for your answer dwhitney67, but that's not exactly what I want to do. 
Plus your code doesn't compile. It gives me this:

```
/usr/local/include/pqxx/connection_base.hxx: In copy constructor ‘pqxx::basic_connection<pqxx::connect_direct>::basic_connection(const pqxx::basic_connection<pqxx::connect_direct>&)’:
/usr/local/include/pqxx/connection_base.hxx:904: error: ‘pqxx::connection_base::connection_base(const pqxx::connection_base&)’ is private
/usr/local/include/pqxx/basic_connection.hxx:50: error: within this context
DataBase.cpp: In constructor ‘DataBase::DataBase()’:
DataBase.cpp:9: note: synthesized method ‘pqxx::basic_connection<pqxx::connect_direct>::basic_connection(const pqxx::basic_connection<pqxx::connect_direct>&)’ first required here 
```


I would like to do what this program does but not with the C library, but the C++ one.

```
#include </usr/include/postgresql/libpq-fe.h>
#include <string>

using namespace std;

class db {
private:
PGconn* conn;

public:

void create_connection(string settings) {
   const char* c=settings.c_str();
   conn = PQconnectdb(c);
}

PGresult* send_query(string query) {
   const char* c=query.c_str();
   PGresult* res;
   res=PQexec(conn,c);
}

};

int main() {
   db data;
   data.create_connection("dbname=test");
   PGresult* r;
   r=data.send_query("select * from something");

   return 0;
}



```

---

### Post by dwhitney67 on 2009-01-31
The code I posted earlier does compile/link; otherwise I would not have posted it.

I was able to compile it using the following statement:
```

g++ -Wall -pedantic test.cpp -lpqxx

```
My system (Fedora 9) has lib pqxx version 2.6.8 installed on it; I obtained it from Fedora's repos.

As for your latest code code, it appears that you have changed APIs.

Figure out what you want to do, and stick to it.

---

### Post by bo01 on 2009-01-31
I use the same statement for g++ and it doesn't compile (libpqxx--->2.6.9 version). Anyway.

I posted the last piece of code in order to show you what I have managed to do with other API that I want to do with the c++ library for postgres (libpqxx).

Briefly, what I want to do is to have a basic class (let test), that uses a connection object as a private member and then create other classes, that can create test objects and call a test's method to initialize the connection object. That is why I posted the code that uses libpq-fe.h (c library). My project is on c++/postgres and I have to use libpqxx.

I don't know if this is clear. Sorry for the inconvenience and thanks again!

---

### Post by WitchCraft on 2009-02-07
> **dwhitney67 said:**
> 
The code I posted earlier does compile/link; otherwise I would not have posted it.

Correct, and your code works on Debian, too. 
But add a return value to an int main function...

> **dwhitney67 said:**
> 
My system (Fedora 9) has lib pqxx version 2.6.8 installed on it; I obtained it from Fedora's repos.


On Debian, recently installed, and upgraded & dist-upgraded:
> 
pkg-config --modversion libpqxx
2.6.9
> **bo01 said:**
> 
I use the same statement for g++ and it doesn't compile (libpqxx--->2.6.9 version). Anyway.


dwhitney67's code compiles on debian, too:


> **dwhitney67 said:**
> 
I was able to compile it using the following statement:
```

g++ -Wall -pedantic test.cpp -lpqxx

```
I don't know why this directive works for you two, since you both don't include the header files...
> 
all:~/Desktop# pkg-config --cflags --libs libpqxx
-I/usr/include/postgresql  -lpqxx 
g++  -Wall -pedantic `pkg-config --cflags --libs libpqxx` plsql.cpp -o plsq

plsql.cpp:
```

#include <pqxx/pqxx>
#include <iostream>
#include <cstdlib>


// libpqxx-dev
// Description: C++ library to connect to PostgreSQL (development files)
// libpqxx - a C++ API to the PostgreSQL database management system.
// This package contains header files for linking against libpqxx.
// Obsoletes the libpqpp-dev package.
// apt-get install libpqxx-dev
// pkg-config --cflags --libs libpqxx



//using namespace std;
//using namespace pqxx;


class DataBase
{
public:
    DataBase()
            : m_conn(pqxx::connection("dbname"))
    {
    }

    pqxx::result doQuery(const std::string query)
    {
        pqxx::work action(const_cast<pqxx::connection&>(m_conn), "Demo");

        pqxx::result res = action.exec(query);

        action.commit();

        return res;
    }

private:
    const pqxx::connection& m_conn;
};


int main()
{
    DataBase db;
    pqxx::result res = db.doQuery("select * from foo");
    return EXIT_SUCCESS ;
}

```


PS: Add error checking, since it is possible that the database doesn't exist and that plsql is not installed...!
> 
 ./plsq
terminate called after throwing an instance of 'pqxx::broken_connection'
  what():  missing "=" after "dbname" in connection info string

Aborted


---

### Post by dwhitney67 on 2009-02-07
> **WitchCraft said:**
> ... 
But add a return value to an int main function...

Specifying a return value for the main() function is optional; please refer to the C/C++ programming standards for more details (I forgot the particular section).  If one fails to provide a return value, then a value of 0 is returned by default.



> **WitchCraft said:**
> 
...
```

int main()
{
    DataBase db;
    pqxx::result res = db.doQuery("select * from foo");
    return EXIT_SUCCESS ;
}

```


PS: Add error checking, since it is possible that the database doesn't exist and that plsql is not installed...!
+1.

From the error that you posted, it would appear that an exception was thrown, and obviously it was not handled.  Sorry about that.

The main() function could probably be written like:
```

int main()
{
  try
  {
    DataBase db;
    pqxx::result res = db.doQuery("select * from foo");
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << std::endl;
    return -1;
  }
}

```

---

### Post by WitchCraft on 2009-02-07
> **dwhitney67 said:**
> 
The main() function could probably be written like:
```

int main()
{
  try
  {
    DataBase db;
    pqxx::result res = db.doQuery("select * from foo");
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << std::endl;
    return -1;
  }
}

```

Much better now!
+1

I'd still do a 
#include <cstdlib>
return EXIT_FAILURE
instead of return -1

but that's optional

---

