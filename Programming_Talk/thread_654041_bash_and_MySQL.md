---
title: "bash and MySQL"
date: 2007-12-30
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-30
I found [http://lists.mysql.com/mysql/179169](http://lists.mysql.com/mysql/179169), which points to [http://www.edlsystems.com/shellsql/overview.html](http://www.edlsystems.com/shellsql/overview.html) and I tried installing it and I got a whole bunch of errors (below).  Unfortunately, I am using 5.0 of MySQL and this was tested with 4.1, so obviously that could be a problem.  Has anybody used this bash tool before or know of something similar?

Thanks!

```

gcc -g -c shmysql.c -I/usr/include/mysql -Wall
shmysql.c:32:19: error: stdio.h: No such file or directory
shmysql.c:33:23: error: sys/types.h: No such file or directory
shmysql.c:34:20: error: unistd.h: No such file or directory
shmysql.c:35:19: error: mysql.h: No such file or directory
shmysql.c:36:20: error: signal.h: No such file or directory
shmysql.c:37:19: error: ctype.h: No such file or directory
shmysql.c:38:19: error: fcntl.h: No such file or directory
shmysql.c:40:21: error: strings.h: No such file or directory
shmysql.c:41:20: error: string.h: No such file or directory
In file included from shmysql.c:44:
string.h:37:20: error: stdlib.h: No such file or directory
In file included from shmysql.c:45:
message.h:38:21: error: sys/ipc.h: No such file or directory
message.h:39:21: error: sys/msg.h: No such file or directory
In file included from shmysql.c:45:
message.h:63: error: expected specifier-qualifier-list before ‘key_t’
shmysql.c:63: error: expected ‘)’ before ‘*’ token
shmysql.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
shmysql.c: In function ‘main’:
shmysql.c:104: error: ‘MYSQL’ undeclared (first use in this function)
shmysql.c:104: error: (Each undeclared identifier is reported only once
shmysql.c:104: error: for each function it appears in.)
shmysql.c:104: error: ‘tdb’ undeclared (first use in this function)
shmysql.c:108: warning: implicit declaration of function ‘fprintf’
shmysql.c:108: warning: incompatible implicit declaration of built-in function ‘fprintf’
shmysql.c:108: error: ‘stderr’ undeclared (first use in this function)
shmysql.c:109: warning: implicit declaration of function ‘exit’
shmysql.c:109: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:112: error: ‘NULL’ undeclared (first use in this function)
shmysql.c:114: warning: incompatible implicit declaration of built-in function ‘fprintf’
shmysql.c:115: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:122: warning: implicit declaration of function ‘fork’
shmysql.c:126: warning: incompatible implicit declaration of built-in function ‘fprintf’
shmysql.c:127: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:146: warning: incompatible implicit declaration of built-in function ‘fprintf’
shmysql.c:150: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:154: warning: implicit declaration of function ‘printf’
shmysql.c:154: warning: incompatible implicit declaration of built-in function ‘printf’
shmysql.c:157: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:174: warning: implicit declaration of function ‘setsid’
shmysql.c:175: warning: incompatible implicit declaration of built-in function ‘exit’
shmysql.c:176: warning: implicit declaration of function ‘close’
shmysql.c:193: warning: implicit declaration of function ‘strncasecmp’
shmysql.c:211: warning: implicit declaration of function ‘atoi’
shmysql.c:212: warning: implicit declaration of function ‘atol’
shmysql.c:215: error: ‘sqldb’ undeclared (first use in this function)
shmysql.c:215: warning: implicit declaration of function ‘mysql_init’
shmysql.c:224: warning: implicit declaration of function ‘mysql_real_connect’
shmysql.c:234: warning: implicit declaration of function ‘snprintf’
shmysql.c:234: warning: incompatible implicit declaration of built-in function ‘snprintf’
shmysql.c:234: warning: implicit declaration of function ‘mysql_error’
shmysql.c:234: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
shmysql.c:237: warning: implicit declaration of function ‘mysql_close’
shmysql.c: In function ‘mainloop’:
shmysql.c:275: error: ‘NULL’ undeclared (first use in this function)
shmysql.c:277: error: ‘MYSQL_RES’ undeclared (first use in this function)
shmysql.c:277: error: ‘res’ undeclared (first use in this function)
shmysql.c:288: warning: implicit declaration of function ‘signal’
shmysql.c:288: error: ‘SIGINT’ undeclared (first use in this function)
shmysql.c:289: error: ‘SIGTERM’ undeclared (first use in this function)
shmysql.c:305: warning: implicit declaration of function ‘mysql_query’
shmysql.c:305: error: ‘sqldb’ undeclared (first use in this function)
shmysql.c:314: warning: implicit declaration of function ‘mysql_store_result’
shmysql.c:316: warning: implicit declaration of function ‘mysql_field_count’
shmysql.c:323: warning: implicit declaration of function ‘dolines’
shmysql.c:324: warning: implicit declaration of function ‘mysql_free_result’
shmysql.c: At top level:
shmysql.c:334: error: expected ‘)’ before ‘*’ token
make: *** [shmysql.o] Error 1
cp: cannot stat `shmysql': No such file or directory
gcc -g -c shsql.c -Wall
shsql.c:38:19: error: stdio.h: No such file or directory
In file included from shsql.c:40:
string.h:37:20: error: stdlib.h: No such file or directory
string.h:38:20: error: string.h: No such file or directory
In file included from shsql.c:41:
message.h:37:23: error: sys/types.h: No such file or directory
message.h:38:21: error: sys/ipc.h: No such file or directory
message.h:39:21: error: sys/msg.h: No such file or directory
message.h:47:20: error: unistd.h: No such file or directory
message.h:48:20: error: signal.h: No such file or directory
message.h:49:19: error: ctype.h: No such file or directory
In file included from shsql.c:41:
message.h:63: error: expected specifier-qualifier-list before ‘key_t’
shsql.c: In function ‘main’:
shsql.c:61: warning: implicit declaration of function ‘fprintf’
shsql.c:61: warning: incompatible implicit declaration of built-in function ‘fprintf’
shsql.c:61: error: ‘stderr’ undeclared (first use in this function)
shsql.c:61: error: (Each undeclared identifier is reported only once
shsql.c:61: error: for each function it appears in.)
shsql.c:62: warning: implicit declaration of function ‘exit’
shsql.c:62: warning: incompatible implicit declaration of built-in function ‘exit’
shsql.c:65: warning: implicit declaration of function ‘strtol’
shsql.c:69: warning: incompatible implicit declaration of built-in function ‘fprintf’
shsql.c:70: warning: incompatible implicit declaration of built-in function ‘exit’
shsql.c:73: error: ‘NULL’ undeclared (first use in this function)
shsql.c:75: warning: incompatible implicit declaration of built-in function ‘fprintf’
shsql.c:76: warning: incompatible implicit declaration of built-in function ‘exit’
shsql.c:93: warning: implicit declaration of function ‘strcmp’
shsql.c:130: warning: implicit declaration of function ‘getchar’
shsql.c:130: error: ‘EOF’ undeclared (first use in this function)
shsql.c:155: warning: incompatible implicit declaration of built-in function ‘fprintf’
shsql.c:157: warning: incompatible implicit declaration of built-in function ‘exit’
shsql.c:172: warning: incompatible implicit declaration of built-in function ‘fprintf’
shsql.c:174: warning: incompatible implicit declaration of built-in function ‘exit’
shsql.c:179: warning: implicit declaration of function ‘fputs’
shsql.c:179: error: ‘stdout’ undeclared (first use in this function)
shsql.c:189: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [shsql.o] Error 1
cp: cannot stat `shsqlstart': No such file or directory
cp: cannot stat `shsqlend': No such file or directory
cp: cannot stat `shsql': No such file or directory
cp: cannot stat `shsqlline': No such file or directory
cp: cannot stat `shsqlesc': No such file or directory


```

---

### Post by geirha on 2007-12-30
Try installing build-essential and libmysqlclient-dev
```
sudo aptitude install build-essential libmysqlclient-dev
```

---

### Post by DouglasAWh on 2008-01-01
I've gone another direction, looking at [http://lists.mysql.com/mysql/179205](http://lists.mysql.com/mysql/179205), though I did install the packages suggested above.

I am running 

```

	echo "select * from widgets where colour = 'red';" > /tmp/query

	$RESULT=`mysql -u user -ppassword widget_sales < /tmp/query`

```

but with my stuff, and I am getting errors or no output:

```

whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ mysql -u root -p gifts < /tmp/query
Enter password: 
whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ $RESULT=`mysql -u root -p gifts < /tmp/query`|echo $RESULT

Enter password: 
bash: =: command not found
whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ $RESULT='mysql -u root -p gifts < /tmp/query'|echo $RESULT

bash: =mysql -u root -p gifts < /tmp/query: No such file or directory
whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ echo mysql -u root -p gifts < /tmp/query
mysql -u root -p gifts
whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ echo 'mysql -u root -p gifts < /tmp/query'
mysql -u root -p gifts < /tmp/query
whitdoug@linux-laptop:~/Link to Class/668/portfolio3$ echo `mysql -u root -p gifts < /tmp/query`
Enter password: 

```

---

### Post by geirha on 2008-01-02
to set a variable you must not prefix it with the $, so
```
RESULT=`mysql ...`
```

---

### Post by DouglasAWh on 2008-01-03
my code now looks like

[php]
#!/bin/bash

echo "SELECT bought, name, pic, link, description FROM wishlist;" > /tmp/query

RESULT=`mysql -u root -p gifts < /tmp/query`

echo $RESULT
[/php]

but, I still get no output

The MySQL looks like

```

mysql> use gifts;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> describe wishlist;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| id          | int(10)      | NO   | PRI | NULL    | auto_increment | 
| name        | varchar(100) | YES  |     | NULL    |                | 
| link        | text         | YES  |     | NULL    |                | 
| pic         | varchar(100) | YES  |     | NULL    |                | 
| price       | int(11)      | YES  |     | NULL    |                | 
| bought      | int(11)      | YES  |     | 0       |                | 
| type        | varchar(20)  | YES  |     | NULL    |                | 
| description | text         | YES  |     | NULL    |                | 
+-------------+--------------+------+-----+---------+----------------+
8 rows in set (0.36 sec)

```

The query file is made correctly, with no extra white space.


**EDIT**: Ok, I'm an idiot...I don't have any data in my database.  I do on the production database, but not on the test one yet...oops.

---

### Post by geirha on 2008-01-03
That sounds plausible, because that sure looks correct ;)

I would have changed the script a little bit however. A query is usually just a line or two, while the output could be hundreds of lines. It would make more sense to store the query in a variable, and the output in a file...

Something like this perhaps
```

query='SELECT bought,name,pic,link,description FROM wishlist;'
tmpfile=`mktemp`

echo "$query" | mysql -u root -p gifts >$tmpfile
cat $tmpfile

rm $tmpfile

```

---

