---
title: "mysql.h"
date: 2006-04-26
forum: Programming Talk
---

### Post by mokojin on 2006-04-26
Hi all

I'm trying to run a simple example that i have found in google to connect a C application to MySQL. But the system doesn reconize mysql.h, and i have MySQL installed.

Anyone knows a solution?


PS

First time trying to program in linux.

---

### Post by ruzle0 on 2006-04-26
do you have the mysql.h file on your computer, if not then you probably need to install the source to mysql, 
look for pakages in synaptic ending with dev. i don't know what package you want for sure but try libmysqlclientXX.dev once installed you can look at the files it contains in synaptic.
if this doesn't fix you give some more information on what you've done and the errors you get

---

### Post by vijayanand_sodadasi on 2006-04-26
[QUOTE=mokojin]Hi all
I'm trying to run a simple example that i have found in google to connect a C application to MySQL. But the system doesn reconize mysql.h, and i have MySQL installed.
[/QUOTE]

Check if you have mysql.h on your system.  Hopefully it will be present in /usr/include/mysql/mysql.h as you said you have MYSQL installed.  If it is not there at that location, then do a complete search by entering this command at the command prompt. ```
find / -name "mysql.h" -print
```  Also while compiling your c program specify the include path; something like this:  ```
gcc myprog.c -I /usr/include/mysql 
```

---

### Post by mokojin on 2006-04-27
I have found it and included as:

#include "/usr/include/mysql/mysql.h"

the full code is:

```
#include <stdio.h>
#include "/usr/include/mysql/mysql.h"

int main() {
	
   MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = "localhost";
   char *user = "me";
   char *password = "password";
   char *database = "mydatabase";
   
   conn = mysql_init(NULL);
   
   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(0);
   }

   /* send SQL query */
   if (mysql_query(conn, "SELECT * FROM games")) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(0);
   }

   res = mysql_use_result(conn);
   
   /* output fields 1 and 2 of each row */
   while ((row = mysql_fetch_row(res)) != NULL)
      printf("%s %s\n", row[1], row[2]);

   /* Release memory used to store results and close connection */
   mysql_free_result(res);
   mysql_close(conn);
}
```

and it's giving me the following errors:

```
mysql.c: In function ‘main’:
mysql.c:21: warning: incompatible implicit declaration of built-in function ‘exit’
mysql.c:27: warning: incompatible implicit declaration of built-in function ‘exit’
/tmp/ccinQBp8.o: In function `main':
mysql.c:(.text+0x3e): undefined reference to `mysql_init'
mysql.c:(.text+0x5e): undefined reference to `mysql_real_connect'
mysql.c:(.text+0x70): undefined reference to `mysql_error'
mysql.c:(.text+0xa5): undefined reference to `mysql_query'
mysql.c:(.text+0xb7): undefined reference to `mysql_error'
mysql.c:(.text+0xe7): undefined reference to `mysql_use_result'
mysql.c:(.text+0x11c): undefined reference to `mysql_fetch_row'
mysql.c:(.text+0x133): undefined reference to `mysql_free_result'
mysql.c:(.text+0x141): undefined reference to `mysql_close'
collect2: ld returned 1 exit status
```


It appears that is not reconigzing the functions. Any idea?

---

### Post by RafG on 2006-04-27
[QUOTE=mokojin]I have found it and included as:

#include "/usr/include/mysql/mysql.h"[/QUOTE]

#include <mysql/mysql.h> should work as well, methinks...

```
mysql.c: In function ‘main’:
mysql.c:21: warning: incompatible implicit declaration of built-in function ‘exit’
mysql.c:27: warning: incompatible implicit declaration of built-in function ‘exit’
```

You should include stdlib.h for exit(). Since this code is in main(), you might just as well return, by the way.

```
/tmp/ccinQBp8.o: In function `main':
mysql.c:(.text+0x3e): undefined reference to `mysql_init'
mysql.c:(.text+0x5e): undefined reference to `mysql_real_connect'
mysql.c:(.text+0x70): undefined reference to `mysql_error'
mysql.c:(.text+0xa5): undefined reference to `mysql_query'
mysql.c:(.text+0xb7): undefined reference to `mysql_error'
mysql.c:(.text+0xe7): undefined reference to `mysql_use_result'
mysql.c:(.text+0x11c): undefined reference to `mysql_fetch_row'
mysql.c:(.text+0x133): undefined reference to `mysql_free_result'
mysql.c:(.text+0x141): undefined reference to `mysql_close'
collect2: ld returned 1 exit status
```

ld sometimes needs to be told a bit more explicitly what libraries it should use. Try compiling with something like

gcc -lmysqlclient -o mysqlapp mysql.c

If you still get linking errors, read [http://mysqld.active-venture.com/Link_errors.html](http://mysqld.active-venture.com/Link_errors.html)

---

