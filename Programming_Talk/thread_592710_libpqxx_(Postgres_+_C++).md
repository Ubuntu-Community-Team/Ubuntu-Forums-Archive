---
title: "libpqxx (Postgres + C++)"
date: 2007-10-26
forum: Programming Talk
---

### Post by borland-c on 2007-10-26
I have install libpqxx-2.6.9 and libpqxx-dev
I download examles from page [http://pqxx.org/development/libpqxx/](http://pqxx.org/development/libpqxx/)
and 

I get options from makefile, but with option *-lpq /usr/local/pqxx/lib/libpqxx.a* i reseived error that file .../libpqxx.a not found
so while compile with g++ I use options
```
-I/usr/include/postgresql -I/usr/local/pgsql/include -I/usr/local/pqxx/include -Wall -pedantic -O -L/usr/local/pgsql/lib
```

but while compiling everyone from examles I receive errers
for sample1.cxx```
sample1.cxx:19: error: &#8216;class pqxx::Transaction&#8217; has no member named &#8216;Exec&#8217;
sample1.cxx:42: error: &#8216;class pqxx::Transaction&#8217; has no member named &#8216;Commit&#8217;
```for sample2.cxx```
sample2.cxx:33: error: &#8216;class pqxx::Transaction&#8217; has no member named &#8216;Exec&#8217;
/usr/local/include/pqxx/cursor.h: In constructor &#8216;pqxx::Cursor::Cursor(TRANSACTION&, const char*, const std::string&, long int) [with TRANSACTION = pqxx::Transaction]&#8217;:
sample2.cxx:38:   instantiated from here
/usr/local/include/pqxx/cursor.h:115: error: no matching function for call to &#8216;pqxx::Cursor::error_permitted_isolation_level(pqxx::isolation_traits<read_committed>)&#8217;
/usr/local/include/pqxx/cursor.h:276: note: candidates are: static void pqxx::Cursor::error_permitted_isolation_level(pqxx::isolation_traits<serializable>)
```
so what's wrong ? or I can use smth else for using Postgres from C++ ?

---

### Post by dumbsnake on 2007-10-26
I use almost exclusively C++ for programming and almost exclusively PostGres for databasing, but I use the C postgres library and headers.  I didn't find a C++ library out there that really did what I wanted it to do.  

After you install the postgres-dev package, you will want to add:
```
#include "postgresql/libpq-fe.h"

```


to the top of any files that need to use the C interface.  Also you will need to link with the postgres client library which is called libpq and is probably in your /usr/lib directory if you have installed the postgres-dev package.

Congratulations on picking postgres.  So many people go with MySQL with its inferior feature set, slower performance, lesser stability and worse licensing terms.  Goodluck in your programming endeavors.

---

