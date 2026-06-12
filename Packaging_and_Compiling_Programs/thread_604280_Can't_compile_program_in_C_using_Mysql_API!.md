---
title: "Can't compile program in C using Mysql API!"
date: 2007-11-05
forum: Packaging and Compiling Programs
---

### Post by Khao on 2007-11-05
Hey there,
I'm having a hard time trying to figure out how to compile a small C program that can make Mysql queries! I'm on a fresh install of Ubuntu Server 7.10 with mysql installed and operationnal. Here's the source code of the program, found in a tutorial :
```
#include <stdio.h>
#include <mysql/mysql.h>

main() {
   MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = “MYSERVER”;
   char *user = “MYUSER”;
   char *password = “MYPASSWORD”; /* set me first */
   char *database = “MYDATABASE”;

   conn = mysql_init(NULL);

   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 3306, NULL, 0)) {
      fprintf(stderr, “%s\n“, mysql_error(conn));
      exit(1);
   }

   /* send SQL query */
   if (mysql_query(conn, “show tables”)) {
      fprintf(stderr, “%s\n“, mysql_error(conn));
      exit(1);
   }

   res = mysql_use_result(conn);

   /* output table name */
   printf(“MySQL Tables in mysql database:\n“);
   while ((row = mysql_fetch_row(res)) != NULL)
      printf(“%s \n“, row[0]);

   /* close connection */
   mysql_free_result(res);
   mysql_close(conn);
}
```

I have tryed many ways to compile with gcc and none of them worked, most of the time having this error :
Mysql.c:1:50: error: /usr/local/mysql/include/mysql/mysql.h: No such file or directory
followed by tons of error : stray 223 in program MYSQL undeclared (first use) .. blah blah. 
I'm kind of a noob with this so please help me!
Thank you!

---

### Post by sonofusion82 on 2007-11-06
you might need to install mysql development files.
please see this thread: [http://ubuntuforums.org/showthread.php?t=123162](http://ubuntuforums.org/showthread.php?t=123162)

---

