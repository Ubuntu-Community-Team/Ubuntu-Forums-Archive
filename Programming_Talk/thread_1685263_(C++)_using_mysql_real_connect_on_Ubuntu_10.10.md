---
title: "(C++) using mysql_real_connect on Ubuntu 10.10"
date: 2011-02-10
forum: Programming Talk
---

### Post by Galactix on 2011-02-10
Hi all,

I am writing a C++ program which links to /usr/lib/libmysqlclient.so and includes from /usr/include/mysql. The code compiles without problems (g++ reports all is well). During runtime, the program halts.

I connect using:

```

.h:
#include <mysql.h>
MYSQL *mysql;

.cc:
...
mysql = mysql_init(NULL);
if(!mysql_real_connect(mysql,
                       "127.0.0.1",
                       "user",
                       "mypwd", 
                       "mydb",
                       0,
                       NULL,
                       0)){
        printf("MySQL error: Failed to connect to database: [%s],  mysql_error(mysql));
}
...

```

This returns the following error:
```

MySQL error: Failed to connect to database: [Wrong or unknown protocol]

```

Which is - according to MySQL - an Error: 2047 (CR_CONN_UNKNOW_PROTOCOL). 

Using mysql_client_test from the commandline I can connect without trouble, so I guess it must be in the mysql lib, or I am doing something severely wrong. 

The MySQL documentation is not very verbose on this error, anybody have any clues, seen this before or something?

Thanks for any reactions.

---

### Post by johnl on 2011-02-10
Just a guess based on the documentation -- try passing NULL or "localhost" as the host instead of "127.0.0.1".

The documentation says:

> 
The value of host may be either a host name or an IP address. If host is NULL or the string "localhost", a connection to the local host is assumed. ... For Unix, the client connects using a Unix socket file.


Perhaps your server is not configured to listen for TCP/IP connections, just a unix socket connection.

---

### Post by Galactix on 2011-02-16
Thanks for your input, John.

I've been trying various combinations of "localhost", "NULL", "127.0.0.1" and "" together with using a socket and explicitly stating to use the socket in /var/run/mysqld/mysqld.sock which is the one phpmyadmin uses. But no luck there.

Tried users both with and without password, including the mysql root user, and also with and without stating the database (i.e. "simres" and ""), and with and without the 'usepipe' option, all with the same results. 

I found [here]("http://wofford-ecs.org/DataAndVisualization/CGIProgramsAndDatabases/index.htm") that they include <sys/time.h>, though it does not change my situation.

Note that logging in to mysql on the commandline does work (but only for users without password???), like this:

```

$ mysql -h localhost -u sim
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 102
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

```

I am considering going into the code of mysql, and find out what "Wrong or unknown protocol" really means, though I doubt I'll have time to do that.

---

### Post by Galactix on 2011-02-16
... I tried monkeying around with:
```

mysql_options(mysql, MYSQL_OPT_PROTOCOL, MYSQL_PROTOCOL_SOCKET);

```

prior to calling mysql_real_connect, because it seems to complain about the type of protocol.

I want to try to explicitly tell which protocol to use. Unfortunately, I cannot figure out how to convert a mysql_protocol_type enum to the const char* which mysql_options expects as 3rd argument (simply casting results in SegFaults) so I'm at a loss here.

---

### Post by johnl on 2011-02-16
Out of curiosity, I setup mysql server on my system and tried your exact code with libmysqlclient16 -- it worked fine with "localhost", "127.0.0.1" and NULL as the server address, working with both the mysql root user and a test user I created.

Have you changed the configuration of the mysql server at all?  Perhaps the problem is on that side.

Edit:  to use mysql_options you should call it like this:

```

unsigned int arg = MYSQL_PROTOCOL_SOCKET;
    
if (mysql_options(mysql, MYSQL_OPT_PROTOCOL, &arg) != 0) {
    /* bad option */
}

```

When I passed "127.0.0.1" as the host address and MYSQL_PROTOCOL_SOCKET, I got the same error that you get (since it wants to use TCP when given an IP address, I suspect).  I changed the host address to NULL and it worked as expected.

---

### Post by Galactix on 2011-02-17
John, thanks for your support. 

I'm also using libmysqlclient16. The only changes to mysql were made through phpmyadmin - making the user account and creating some tables.

Your code only compiles if I change "unsigned int" to "const char", get the following compile error using g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5:

```
error: cannot convert ‘unsigned int*’ to ‘const char*’ for argument ‘3’ to ‘int mysql_options(MYSQL*, mysql_option, const char*)’

```

---

### Post by Galactix on 2011-02-17
Ok, I also made a quick tester:

```
#include <iostream>
#include <mysql.h>

//g++ dbtest.cc -o dbtest -I/usr/include/mysql -lmysqlclient

using namespace std;

int main(){
    cout << "Testing your database..." << endl;
    MYSQL *mysql;
    mysql = mysql_init(NULL);
    if(!mysql_real_connect(mysql,
                       "", 
                       "sim",
                       "", 
                       "simres",
                       0,  
                       NULL,
                       0)){
        cout << "MySQL error: Failed to connect to database: " << mysql_error(mysql) << endl;
    }else{
        mysql_close(mysql);
        cout << "Connection to db established and closed." << endl;
    }   
    return 0;
}
```

It is odd, it works though it is the exact same code as I use embedded in my larger project. (I can only connect with 'root'+pwd or 'sim' without pwd, but I guess this is a mysql issue I'll have to solve).

Anyway, I now know it works in isolation - now on to figure out why it doesn't work in the other heap of code :D

---

