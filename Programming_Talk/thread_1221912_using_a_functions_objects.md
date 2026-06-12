---
title: "using a functions objects"
date: 2009-07-24
forum: Programming Talk
---

### Post by slaiyer on 2009-07-24
The function below connects to a database, now i want to use it in other functions of classes so as to call the connection and use the variable **query** and **conn**. But i keep getting an out of scope error when compiling

```
void database_connect(){
      Connection conn(false);
        if(!conn.connect("DB NAME", "localhost", "DB USER", "DB PASS")){
            cout << "Sorry, could not connect to the database";
        }else{

      static  Query query = conn.query();

        }
}
```


so, is there a way of returning the two variables **query** and **conn** to the function that calls this function?

NB:

I have tried using static, but i also keep getting the same error.

---

### Post by slaiyer on 2009-07-25
anyone got any ideas?

---

### Post by pepperphd on 2009-07-25
You can declare them globally.

---

### Post by smartbei on 2009-07-25
One option would be to create a struct DBData or something:
```

struct DBData {
    Query * query;
    Connection * conn;
}DBData;

```
And then you could allocate query and conn and the struct dynamically, stick them in the struct, and return it.

Another option is to return conn (allocating it dynamically of course) and let the caller do query = conn.query();

The reason you need to allocate dynamically is that otherwise the object is on the stack, meaning that when the function exits it will be destroyed. Of course, if the function returns an object of a certain type, and the copy constructor (I am assuming C++) is implemented, then you do not need to allocate dynamically as everything will work transparently.

---

### Post by jpkotta on 2009-07-25
The standard ways to return multiple values in C (or C++) are:

Return a struct:
```

typedef struct {
   int foo;
   int bar;
} foobar_t;

foobar_t func(void)
{
    foobar_t ret;
    ret.foo = 1;
    ret.bar = 2;
    return ret;
}

```

Pass a pointer to a writable object:
```

void func(int *foo, int *bar)
{
    *foo = 1;
    *bar = 2;
}

```

---

### Post by dwhitney67 on 2009-07-25
slaiyer -

Since it appears that you are writing code in C++ and using MySQL++, try to think in terms of object oriented programming, and not functional programming (as is done in C).

Define an object that manages the database connection, and the connection object, and also permits a caller to issue a query, and receive the results.

Consider the following (incomplete code):
```

#include <mysql++.h>
#include <string>

struct DatabaseLoginInfo
{
   std::string database;
   std::string hostname;
   std::string username;
   std::string password;
};

class DatabaseManager
{
public:
   DatabaseManager(const DatabaseLoginInfo& loginInfo);

   mysqlpp::StoreQueryResult issueQuery(const std::string& query);

   ...

private:
   mysqlpp::Connection dbConn;
};


DatabaseManager::DatabaseManager(const DatabaseLoginInfo& loginInfo)
{
   try {
      dbConn.connect(loginInfo.database.c_str(),
                     loginInfo.hostname.c_str(),
                     loginInfo.username.c_str(),
                     loginInfo.password.c_str());
   }
   catch (mysqlpp::ConnectionFailed& e) {
   }
}

mysqlpp::StoreQueryResult
DatabaseManager::issueQuery(const std::string& query)
{
   mysqlpp::StoreQueryResult dbResult;

   try {
      mysqlpp::Query dbQuery = dbConn.query();
      dbResult = dbQuery.store(query.c_str());
   }
   catch (mysqlpp::BadConversion& e) {
   }
   catch (mysqlpp::BadFieldName& e) {
   }
   //...
   catch (mysqlpp::TypeLookupFailed& e) {
   }

   return dbResult;
}

```
As I stated, the code is incomplete, especially with respect to handling any exceptions that are thrown.

You would probably would also want to ensure there is a DB connection before attempting to issue a query.  The MySQL++ Connection object provides a connection() method that can be called to determine if the connection is (still) valid.

P.S.  I wrote code similar to the above several years ago.  As for the code above, I have not tested it, much compiled it.

---

### Post by Sockerdrickan on 2009-07-29
> **pepperphd said:**
> You can declare them globally.
Using the global scope for variables is bad software design. Try to keep it clean from start to finished product.

---

### Post by slaiyer on 2009-07-29
i decided to go with dwhitney67 class method, and its working great for me so far, though still have some functionality to modify in it. but will do that later, its nice to finally move from a stagnant position.

---

