---
title: "undefined reference to mysql_init??"
date: 2011-01-13
forum: Programming Talk
---

### Post by i4ba1 on 2011-01-13
hai all,

I have an error when i compile my code using mysql c API
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <string.h>
#include <stdio.h>
#include <mysql.h>
#include <stdlib.h> 

#include <config.h>


/*
 * Standard gettext macros.
 */
#ifdef ENABLE_NLS
#  include <libintl.h>
#  undef _
#  define _(String) dgettext (PACKAGE, String)
#  ifdef gettext_noop
#    define N_(String) gettext_noop (String)
#  else
#    define N_(String) (String)
#  endif
#else
#  define textdomain(String) (String)
#  define gettext(String) (String)
#  define dgettext(Domain,Message) (Message)
#  define dcgettext(Domain,Message,Type) (Message)
#  define bindtextdomain(Domain,Directory) (Domain)
#  define _(String) (String)
#  define N_(String) (String)
#endif





int main (int argc, char *argv[])
{
     MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = "127.0.01";
   char *user = "root";
   char *password = "123abcd"; /* set me first */
   char *database = "mysql";

   conn = mysql_init(NULL);

   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

   /* send SQL query */
   if (mysql_query(conn, "show tables")) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

   res = mysql_use_result(conn);

   /* output table name */
   printf("MySQL Tables in mysql database:\n");
   while ((row = mysql_fetch_row(res)) != NULL)
      printf("%s \n", row[0]);

   /* close connection */
   mysql_free_result(res);
   mysql_close(conn);
    return 0;
}
when compile that code the error show:
/home/iqbalkhan/testsql/src/main.cc:66: undefined reference to `mysql_init'
/home/iqbalkhan/testsql/src/main.cc:69: undefined reference to `mysql_real_connect'
/home/iqbalkhan/testsql/src/main.cc:71: undefined reference to `mysql_error'
/home/iqbalkhan/testsql/src/main.cc:76: undefined reference to `mysql_query'
/home/iqbalkhan/testsql/src/main.cc:77: undefined reference to `mysql_error'
/home/iqbalkhan/testsql/src/main.cc:81: undefined reference to `mysql_use_result'
/home/iqbalkhan/testsql/src/main.cc:85: undefined reference to `mysql_fetch_row'
/home/iqbalkhan/testsql/src/main.cc:89: undefined reference to `mysql_free_result'
/home/iqbalkhan/testsql/src/main.cc:90: undefined reference to `mysql_close'

i try to googling and found the answer. the answer is: 
compile your app with the command bellow  gcc -o test  -L/usr/lib/mysql -lmysqlclient test.c

But, in my /usr/lib/ directory there is no mysql directory, i'm confused
with this problem. can ou help me to solve this problem, please!!.

Best Regards

---

### Post by dwhitney67 on 2011-01-13
This is wrong:
```

...
#include </usr/include/mysql/mysql.h>
#include </usr/include/mysql/my_global.h>
...

```
This should be:
```

...
#include <mysql.h>
#include <my_global.h>
...

```

Then, when it comes to this step:
```

gcc -o test -L/usr/lib/mysql -lmysqlclient test.c

```
do this instead:
```

gcc -o test test.c `mysql_config --cflags --libs`

```

-------------

EDIT:

I just realized that your C program is using a header file for C++, and is also using a Gtkmm header file.  Choose the language you wish to use, for C and C++ are NOT the same language.  As for the Gtkmm, why is this even included???

If you go with C++, then include <cstdio>, and in lieu of using "gcc", use "g++".  The following headers should work for C:
```

//#include <iostream>     // not needed; only for C++
#include <stdio.h>        // for printf() and fprintf()
#include <stdlib.h>       // for exit()

#include <mysql.h>
//#include <my_global.h>  // not needed
...

```

P.S.  It is not very wise to name your executable as "test"; another application with the same name resides in /usr/bin.

---

### Post by i4ba1 on 2011-01-13
if i used:
#include <mysql.h>
#include <my_global.h>
the erro message show;
/home/iqbalkhan/testsql/src/main.cc:22: fatal error: mysql.h: No such file or directory
/home/iqbalkhan/testsql/src/main.cc:22: fatal error: my_global.h: No such file or directory

My project is c language not c++ [dwhitney67]("http://ubuntuforums.org/member.php?u=322753").

---

### Post by dwhitney67 on 2011-01-13
> **i4ba1 said:**
> if i used:
#include <mysql.h>
#include <my_global.h>
the erro message show;
/home/iqbalkhan/testsql/src/main.cc:22: fatal error: mysql.h: No such file or directory
/home/iqbalkhan/testsql/src/main.cc:22: fatal error: my_global.h: No such file or directory

My project is c language not c++ [dwhitney67]("http://ubuntuforums.org/member.php?u=322753").

Please re-read my entire post, specifically for this:
```

gcc -o test test.c `mysql_config --cflags --libs`

```

---

### Post by i4ba1 on 2011-01-13
this command executed from terminal?.
gcc -o test test.c `mysql_config --cflags --libs

[dwhitney67]("http://ubuntuforums.org/member.php?u=322753") for information i use Anjuta IDE to compile and run the program. and the mysq.h still error: /home/iqbalkhan/testsql/src/main.cc:22: fatal error: mysql.h: No such file or directory.

---

### Post by dwhitney67 on 2011-01-13
Figure out how to build your application from the terminal.  When you are fully enlightened, and only then, do I recommend that you attempt to use an IDE.

I'm sure that Anjuta offers plenty of documentation on how to configure a project to specify the correct paths to use to find header files and library files; but none of that matters unless the user (that would be you!) reads it.

---

### Post by i4ba1 on 2011-01-13
ok, mysql.h now is found i used #include<mysql/mysql.h>. but when i compile, the same error still show.

/home/iqbalkhan/gtk-mysql/src/main.c:119: undefined reference to `mysql_init'
/home/iqbalkhan/testsql/src/main.cc:69: undefined reference to `mysql_real_connect'
/home/iqbalkhan/testsql/src/main.cc:71: undefined reference to `mysql_error'
/home/iqbalkhan/testsql/src/main.cc:76: undefined reference to `mysql_query'
/home/iqbalkhan/testsql/src/main.cc:77: undefined reference to `mysql_error'
/home/iqbalkhan/testsql/src/main.cc:81: undefined reference to `mysql_use_result'
/home/iqbalkhan/testsql/src/main.cc:85: undefined reference to `mysql_fetch_row'
/home/iqbalkhan/testsql/src/main.cc:89: undefined reference to `mysql_free_result'
/home/iqbalkhan/testsql/src/main.cc:90: undefined reference to `mysql_close'

---

### Post by dwhitney67 on 2011-01-13
i4ba1, the code below compiles/links with this statement:
```

gcc -o test test.c `mysql_config --cflags --libs`

```

test.c:
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
/*
 * main.cc
 * Copyright (C) iqbalkhan 2011 <iqbalkhan@>
 *
 * TestSQL is free software: you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the
 * Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * TestSQL is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
 * See the GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License along
 * with this program. If not, see <http://www.gnu.org/licenses/>.
 */

#include <stdio.h>        // for printf() and fprintf()
#include <stdlib.h>       // for exit()
#include <mysql.h>

#ifdef ENABLE_NLS
#include <libintl.h>
#endif

int
main (int argc, char* argv[])
{
   MYSQL*     conn;
   MYSQL_RES* res;
   MYSQL_ROW  row;

   const char* server   = "127.0.0.1";
   const char* user     = "root";
   const char* password = "123abcd"; /* set me first */
   const char* database = "mysql";

   conn = mysql_init(NULL);

/* Connect to database */
   if (!mysql_real_connect(conn, server, user, password, database, 0, NULL, 0))
   {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

/* send SQL query */
   if (mysql_query(conn, "show tables"))
   {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

   res = mysql_use_result(conn);

/* output table name */
   printf("MySQL Tables in mysql database:\n");
   while ((row = mysql_fetch_row(res)) != NULL)
   {
      printf("%s \n", row[0]);
   }

/* close connection */
   mysql_free_result(res);
   mysql_close(conn);
   return 0;
}

```

---

### Post by i4ba1 on 2011-01-13
the result when i compile my code using gcc -o main main.c mysql_config --cflags --libs is:

gcc: mysql_config: No such file or directory
cc1: error: unrecognized command line option "-fcflags"
cc1: error: unrecognized command line option "-flibs"

---

### Post by dwhitney67 on 2011-01-13
Copy/paste the command I posted earlier; do not enter it by hand, because obviously you forgot to type in the single back-quotes that surround the mysql_config statement.

---

### Post by i4ba1 on 2011-01-13
> **dwhitney67 said:**
> Copy/paste the command I posted earlier; do not enter it by hand, because obviously you forgot to type in the single back-quotes that surround the mysql_config statement.

ok dwhitney67, i have try your command again. but now the result is:

main.c:20: fatal error: /usr/include/mysql/stdio.h: Permission denied
compilation terminated. :confused:.

---

### Post by dwhitney67 on 2011-01-13
I don't know what else to tell you.  I took your code, cleaned it up a bit, and compiled/linked it just fine on my system.

Please revisit this [post]("http://ubuntuforums.org/showpost.php?p=10351570&postcount=8") so that you can copy the source code and the statement used to build the application.

---

### Post by i4ba1 on 2011-01-13
> **dwhitney67 said:**
> I don't know what else to tell you.  I took your code, cleaned it up a bit, and compiled/linked it just fine on my system.

Please revisit this [post]("http://ubuntuforums.org/showpost.php?p=10351570&postcount=8") so that you can copy the source code and the statement used to build the application.

em.. You mean there is somethings wrong in my system?. so, i can't compile my code!. :(
when i compile this file using Anjuta IDE it's fine. but the mysql_init is undefined. and when i use gcc to compile the file there is an error "permission denied compilation terminated".

---

### Post by i4ba1 on 2011-01-13
Wow Wow thank you god, thank you [dwhitney67]("http://ubuntuforums.org/member.php?u=322753"). finally i succesfully run mycode without any error. :P
this is the site that help me solve this problem. [http://lists.mysql.com/mysql/200178](http://lists.mysql.com/mysql/200178). i ever try the command from that site but not success and now it success.

---

