---
title: "[ C++ and MySQL ] How to compile ?"
date: 2010-01-02
forum: Programming Talk
---

### Post by The Secret on 2010-01-02
```
#include <iostream>
#include <mysql.h>

using namespace std;

int main(int argc, char *argv[])
{
    MySQL *Connection;
    Connection = mysql_init(NULL);
    mysql_real_connect(Connection, "localhost", "root", "password", "test", 0, NULL, 0);
    return 0;
}

```

```
g++ main.cpp -o main -L/usr/include/mysql-lmysqlclient -I/usr/include/mysql
[COLOR=Red]main.cpp: In function ‘int main(int, char**)’:
main.cpp:8: error: ‘MySQL’ was not declared in this scope
main.cpp:8: error: ‘Connection’ was not declared in this scope[/COLOR]
```

What I'm doing wrong ?

[COLOR=Gray]** Don't blame me for the source code and/or commands I've used - I'm learning and all this stuff comes from a tutorial.[/COLOR]

---

### Post by Arndt on 2010-01-02
> **The Secret said:**
> ```
#include <iostream>
#include <mysql.h>

using namespace std;

int main(int argc, char *argv[])
{
    MySQL *Connection;
    Connection = mysql_init(NULL);
    mysql_real_connect(Connection, "localhost", "root", "password", "test", 0, NULL, 0);
    return 0;
}

```

```
g++ main.cpp -o main -L/usr/include/mysql-lmysqlclient -I/usr/include/mysql
[COLOR=Red]main.cpp: In function ‘int main(int, char**)’:
main.cpp:8: error: ‘MySQL’ was not declared in this scope
main.cpp:8: error: ‘Connection’ was not declared in this scope[/COLOR]
```

What I'm doing wrong ?

[COLOR=Gray]** Don't blame me for the source code and/or commands I've used - I'm learning and all this stuff comes from a tutorial.[/COLOR]

I looked into mysql.h and found a struct there, typedefed as "MYSQL". I guess that's what you want, not "MySQL".

---

### Post by The Secret on 2010-01-02
```
[COLOR=Red]/tmp/ccG0CdLt.o: In function `main':
main.cpp:(.text+0x11): undefined reference to `mysql_init'
main.cpp:(.text+0x59): undefined reference to `mysql_real_connect'
collect2: ld returned 1 exit status[/COLOR]

```

Something is still wrong.

---

### Post by Arndt on 2010-01-02
> **The Secret said:**
> ```
[COLOR=Red]/tmp/ccG0CdLt.o: In function `main':
main.cpp:(.text+0x11): undefined reference to `mysql_init'
main.cpp:(.text+0x59): undefined reference to `mysql_real_connect'
collect2: ld returned 1 exit status[/COLOR]

```

Something is still wrong.

Does the tutorial really contain that compilation/linking command? It specifies where to find the mysql library (but strangely so - libraries are not in /usr/include), but then doesn't actually link with it.

---

### Post by caelestis2 on 2010-01-02
Since you are using C++ I would suggest using

[http://tangentsoft.net/mysql++/](http://tangentsoft.net/mysql++/)

Life would be easier for you.

---

### Post by dwhitney67 on 2010-01-02
Try:
```

g++ -I/usr/include/mysql main.cpp -o main -L/usr/lib/mysql -lmysqlclient

```

P.S.  Btw, since you are doing C++ development, you should really consider using the MySQL++ library, not the regular/wimpy MySQL C library.
```

sudo apt-get install libmysql++-dev

```

---

### Post by The Secret on 2010-01-03
> **dwhitney67 said:**
> Try:
```

g++ -I/usr/include/mysql main.cpp -o main -L/usr/lib/mysql -lmysqlclient

```P.S.  Btw, since you are doing C++ development, you should really consider using the MySQL++ library, not the regular/wimpy MySQL C library.
```

sudo apt-get install libmysql++-dev

```

Still the same error and the mysql++ dev package is already installed.

---

### Post by Arndt on 2010-01-03
> **The Secret said:**
> Still the same error and the mysql++ dev package is already installed.

I don't know why there is a difference, but I can link the program without errors.

---

### Post by LKjell on 2010-01-03
If you use ```
#include <mysql/mysql.h>
``` Then you do not need the long path include. But you still need the library linking.

---

### Post by dwhitney67 on 2010-01-03
> **The Secret said:**
> Still the same error
Have you checked to verify that you have a 'mysqlclient' library installed on your system?  Check the results of this command:
```

ls -l /usr/lib/mysql/libmysqlclient*

```
Do you perhaps need mysqld or perhaps libndbclient?

> 
... and the mysql++ dev package is already installed.
But you are not using it!

---

### Post by The Secret on 2010-01-04
> **LKjell said:**
> If you use ```
#include <mysql/mysql.h>
``` Then you do not need the long path include. But you still need the library linking.

Thank you.

> **dwhitney67 said:**
> Have you checked to verify that you have a 'mysqlclient' library installed on your system?  Check the results of this command:
```

ls -l /usr/lib/mysql/libmysqlclient*

```Do you perhaps need mysqld or perhaps libndbclient?

If I would know what I need, this thread wouldn't be here :D Basically, I figured out that I don't have the mysqlclient libraries, tough after installing them, I receive the same error as without them.

> **dwhitney67 said:**
> But you are not using it!

Because I don't know how ( if this isn't the way it should be used ).

---

### Post by Arndt on 2010-01-04
> **The Secret said:**
> 

If I would know what I need, this thread wouldn't be here :D Basically, I figured out that I don't have the mysqlclient libraries, tough after installing them, I receive the same error as without them.



So what was the result of this?

```
ls -l /usr/lib/mysql/libmysqlclient*
```

---

### Post by The Secret on 2010-01-04
> **Arndt said:**
> So what was the result of this?

```
ls -l /usr/lib/mysql/libmysqlclient*
```

```
ls: cannot access /usr/lib/mysql/libmysqlclient*: No such file or directory
```

```
i   libmysqlclient-dev              - MySQL database development files          
c   libmysqlclient15-dev            - MySQL database development files          
i A libmysqlclient15off             - MySQL database client library             
i   libmysqlclient16                - MySQL database client library             
p   libmysqlclient16-dev            - MySQL database development files - empty t
```

libmysqld-dev and libmysql++-dev are installed, too.

---

### Post by dwhitney67 on 2010-01-04
> **The Secret said:**
> 
Because I don't know how ( if this isn't the way it should be used ).
This is the golden-question you should have asked from the start.

In your opening post, it appears as if you a merely attempting to establish a connection to the database.  Here's a simple example, using your parameters, and the MySQL++ interface:
```

#include <mysql++.h>
#include <iostream>

int main()
{
   using namespace mysqlpp;
   using namespace std;

   try
   {
      Connection conn("test", "localhost", "root", "password");
   }
   catch (ConnectionFailed& e)
   {
      cerr << "Exception: " << e.what() << endl;
   }
}

```
To compile/link this code:
```

g++ -Wall -pedantic -Wno-long-long -O2 `mysql_config --include` -I/usr/include/mysql++ -c sql++.cpp
g++ sql++.o `mysql_config --libs` -lmysqlpp -o sql++_test

```
Naturally, the example above is not very OO-ish.  Also, repeatedly typing in the build commands is a pain; a Makefile would be much desired.

---

### Post by Arndt on 2010-01-04
> **The Secret said:**
> ```
ls: cannot access /usr/lib/mysql/libmysqlclient*: No such file or directory
```

```
i   libmysqlclient-dev              - MySQL database development files          
c   libmysqlclient15-dev            - MySQL database development files          
i A libmysqlclient15off             - MySQL database client library             
i   libmysqlclient16                - MySQL database client library             
p   libmysqlclient16-dev            - MySQL database development files - empty t
```

libmysqld-dev and libmysql++-dev are installed, too.

I don't know what those letters mean. But mine is in /usr/lib, actually. In /usr/lib/mysql, I have libmysqld.a, among other things.

---

### Post by dwhitney67 on 2010-01-04
> **Arndt said:**
> I don't know what those letters mean. But mine is in /usr/lib, actually. In /usr/lib/mysql, I have libmysqld.a, among other things.
I totally forgot the other day (yesterday?) that the 'mysql_config' utility can be used to obtain the proper CFLAGS and LDFLAGS settings for the mysql library.

I suppose the OP should/could have used a g++ statement as:
```

g++ main.cpp -o main `mysql_config --include --libs`

```

---

