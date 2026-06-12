---
title: "GCC compiling error related to MySQL header file and references in the header file"
date: 2014-06-06
forum: Packaging and Compiling Programs
---

### Post by cercig on 2014-06-06
Hi,

I need an urgent answer. [COLOR=#000000][FONT=Arial]I am trying to write a C code with embedded MySQL server and client options. The compiler is gcc.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I added the location of the header file manually in the code; like: #include "/usr/include/mysql/mysql.h"
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have the necessary library installed: _libmysqld-dev_ which includes MySQL embedded development libraries.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
When I compile my code very simply like: "gcc test.c" I get errors like this:

[/FONT][/COLOR]```

prov.c:(.text+[COLOR=#800000]0x1b[/COLOR]): [COLOR=#00008B]undefined[/COLOR] reference to [COLOR=#800000]`mysql_server_init'
prov.c:(.text+0x25): undefined reference to `[/COLOR]mysql_init[COLOR=#800000]'
prov.c: (.text+0x45): undefined reference to `mysql_options'[/COLOR]
prov.c: (.text+[COLOR=#800000]0x5e[/COLOR]): [COLOR=#00008B]undefined[/COLOR] reference to [COLOR=#800000]`mysql_options'
prov.c: (.text+0x99): undefined reference to `[/COLOR]mysql_real_connect[COLOR=#800000]'
prov.c: (.text+0xad): undefined reference to `mysql_query'[/COLOR]
prov.c: (.text+[COLOR=#800000]0xbc[/COLOR]): [COLOR=#00008B]undefined[/COLOR] reference to [COLOR=#800000]`mysql_store_result'
prov.c: (.text+0x101): undefined reference to `[/COLOR]mysql_fetch_row[COLOR=#800000]'
prov.c: (.text+0x123): undefined reference to `mysql_free_result'[/COLOR]
prov.c: (.text+[COLOR=#800000]0x132[/COLOR]): [COLOR=#00008B]undefined[/COLOR] reference to [COLOR=#800000]`mysql_close'
prov.c: (.text+0x137): undefined reference to `[/COLOR]mysql_server_end[COLOR=#800000]'[/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

My code is below:

[/FONT][/COLOR]```

[COLOR=#808080]#include[/COLOR] [COLOR=#800000]<stdio.h>[/COLOR]
[COLOR=#808080]#include[/COLOR] [COLOR=#800000]<stdlib.h>[/COLOR]
[COLOR=#808080]#include[/COLOR] [COLOR=#800000]<stdarg.h>[/COLOR]
[COLOR=#808080]#include[/COLOR] [COLOR=#800000]"/usr/include/mysql/mysql.h"[/COLOR]

MYSQL *mysql;
MYSQL_RES *results;
MYSQL_ROW record;

[COLOR=#00008B]static[/COLOR] [COLOR=#00008B]char[/COLOR] *server_options[] = { [COLOR=#800000]"prov"[/COLOR], [COLOR=#800000]"--defaults-file=my.cnf"[/COLOR] };
[COLOR=#00008B]int[/COLOR] num_elements = [COLOR=#00008B]sizeof[/COLOR](server_options)/ [COLOR=#00008B]sizeof[/COLOR]([COLOR=#00008B]char[/COLOR] *);

[COLOR=#00008B]static[/COLOR] [COLOR=#00008B]char[/COLOR] *server_groups[] = { [COLOR=#800000]"libmysqld_server"[/COLOR], [COLOR=#800000]"libmysqld_client"[/COLOR] };

[COLOR=#00008B]int[/COLOR] main([COLOR=#00008B]void[/COLOR])
{
    mysql_server_init(num_elements, server_options, server_groups);
    mysql = mysql_init(NULL);
    mysql_options(mysql, MYSQL_READ_DEFAULT_GROUP, [COLOR=#800000]"libmysqld_client"[/COLOR]);
    mysql_options(mysql, MYSQL_OPT_USE_EMBEDDED_CONNECTION, NULL);


    mysql_real_connect(mysql, NULL,NULL,NULL, [COLOR=#800000]"data"[/COLOR], [COLOR=#800000]0[/COLOR],NULL,[COLOR=#800000]0[/COLOR]);

    mysql_query(mysql, [COLOR=#800000]"SELECT data_id, from the data series"[/COLOR]);

    results = mysql_store_result(mysql);

   [COLOR=#00008B]    while[/COLOR]((record = mysql_fetch_row(results))) {
        printf([COLOR=#800000]"%s - %s \n"[/COLOR], record[[COLOR=#800000]0[/COLOR]], record[[COLOR=#800000]1[/COLOR]]);
    }

    mysql_free_result(results);
    mysql_close(mysql);
    mysql_server_end();

   [COLOR=#00008B]    return[/COLOR] [COLOR=#800000]0[/COLOR];
}[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by steeldriver on 2014-06-06
Hello and welcome to the forums - *I have added CODE tags to your post to make it easier to read - please use them when you post code or terminal output*

The errors you are getting are from the link phase, rather than the compile phase - so they are related to missing libraries not missing header files. As far as I know the mysql.h header is provided by the libmysqclient-dev package and once it's installed you should be able to just do

```

#include <mysql/mysql.h>
.
.
.

```

and then to compile and link the actual library

```

gcc test.c **-lmysqlclient**

```

(I would add a **-o test** ans well,  else the resulting executable gets built as a.out)

Hope this helps.

---

### Post by cercig on 2014-06-06
Thanks steeldriver,

I am completely new, and I needed urgent answer. Thanks a lot for every helping.

It compiles without error now with -lmysqlclient

However, now I am getting:

"Segmentation fault (core dump)"

I guess maybe I didn't prescribe correctly for the data file "data.csv".

Can't my code open and read csv file directly? I saw on internet like:
LOAD DATA LOCAL INFILE 'data.csv' INTO TABLE test [COLOR=#000000][FONT=Consolas]FIELDS TERMINATED [/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]BY[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#800000][FONT=Consolas]','[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] lines terminated [/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]by[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#800000][FONT=Consolas]'\n'[/FONT][/COLOR][COLOR=#000000][FONT=Consolas];

However, I am not sure how to add this structure into my code.

Any (hopefully) last recommendation?

Thanks.

[/FONT][/COLOR]

---

### Post by steeldriver on 2014-06-06
I don't have any experience in mysql client programming - sorry

Hopefully someone else will be able to help, although you may have better luck on a mysql or developer forum (since this isn't really an Ubuntu specific question)

EDIT: FWIW you code actually runs for me if I replace the connection and query strings with something appropriate for my environment i.e.

```

mysql_real_connect(mysql, NULL,"root","*my_mysql_root_pw*", "mysql", 0,NULL,0);

mysql_query(mysql, "SELECT Host,User FROM user");
```

then
```

$ gcc -O0 -g -o test test.c -lmysqlclient
$ ./test
127.0.0.1 - root
::1 - root
lap-t61p -
lap-t61p - root
localhost -
localhost - debian-sys-maint
localhost - root
```

---

### Post by cercig on 2014-06-06
Thanks again,

My main problem might be the CSV data file. How to desribe it in C and how to import it in the mysql line. I don NOT think it works if I only write "mysql.csv" as data file in the line below.

mysql_real_connect(mysql, NULL,"root","*my_mysql_root_pw*", "mysql", 0,NULL,0);

---

### Post by steeldriver on 2014-06-06
What is your end goal exactly? Do you actually need to write a C program - or do you just need a way to import data from a CSV file into a mysql database?

---

### Post by cercig on 2014-06-06
Importing that "data.csv" data to MySQL,
Then creating a server, and also a client with visual interface.
When I search a criteria through the client, the client will communicate with the server and the client will display the result.
And everything must be in C code :)

---

