---
title: "C++ MySQL with a RakNet Server"
date: 2012-03-16
forum: Programming Talk
---

### Post by Pierrick584 on 2012-03-16
Ok, the raknet part is half irrevelant, as i dont specificaly need to directly mix both, but anyway.

I'm working on a raknet server, and i'm starting to use mysql, but not only i suck at SQL language, i also never used SQL in C++, i found quite a few tutorials, but they are all different and get into much more complex query and when i try to modify the code a bit for my need, i get errors.

Right now i do have the connection part working, and what i'm trying to do, is search the database for a username, and extract the password associated with it, so we can compare with the user input, so... search username though user input (witch has passed though the network with raknet) and get the password associated with the user if we found it..

I dont realy ask that you do everything for me, realy, i can find out how to do my query alone, but i tried a dummy query (SELECT * FROM account) and its not even the problem realy... as i cant use the MySQL API correctly..  i wont copy code (or maybe if asked) cause as i said, i found many tutorials all working differently, nothing worked yet, id prefer that someone refer me to the RIGHT way to do it (a guide they trust, or whatever)

Thanks alot for your time / help guys :)

---

### Post by codemaniac on 2012-03-16
To show/list the users in a MySQL database, first log into your MySQL server as an administrative user, then run this MySQL query .

```
select host, user, password from mysql.user;
```

---

### Post by Pierrick584 on 2012-03-16
missunderstanding, i dint ment the mysql users, i ment the users for the software i'm working on.

"users" as in, part of the tables.

in my account table, i have id, user, password, ect... so trying to get one value, getting the password associated with it..

---

### Post by codemaniac on 2012-03-16
So you wanna a piece of code that will retrieve user credentials from the accounts table @ MYSQL DB . Am i getting you ?

---

### Post by codemaniac on 2012-03-16
APPEND : If the above is the case , you can write a shell script that will hit the MySql DB and grep out the user/pass from accounts table ..

---

### Post by codemaniac on 2012-03-16
```
  1 /* Sample C code that will hit mysql DB*/
  2 #include <mysql.h>
  3 #include <stdio.h>
  4 main() {
  5    MYSQL *conn;
  6    MYSQL_RES *res;
  7    MYSQL_ROW row;
  8    char *server = "localhost";
  9    char *user = "codemaniac";
 10    char *password = "codemaniac";
 11    char *database = "arijitdevdb";
 12    conn = mysql_init(NULL);
 13    /* Connect to database */
 14    if (!mysql_real_connect(conn, server,
 15          user, password, database, 0, NULL, 0)) {
 16       fprintf(stderr, "%s\n", mysql_error(conn));
 17       exit(1);
 18    }
 19    /* feed your SQL query */
 20    if (mysql_query(conn, "select * from accounts")) {
 21       fprintf(stderr, "%s\n", mysql_error(conn));
 22       exit(1);
 23    }
 24    res = mysql_use_result(conn);
 25    /* Output data*/
 26    printf("Data in accounts table\n");
 27    while ((row = mysql_fetch_row(res)) != NULL)
 28       printf("%s \n", row[0]);
 29    /* close connection */
 30    mysql_free_result(res);
 31    mysql_close(conn);
 32 }
```

This is a sample code to retrieve informations from your sample accounts table .
Before you compile let your compiler recognize the libs .

> mysql_config --libs
mysql_config --cflags

Now complile .
```
gcc -o outfile $(mysql_config --cflags) mySqlTest.c $(mysql_config --libs)
```

then run 
```
./outfile
```

---

### Post by Pierrick584 on 2012-03-16
Well, i were a litle bit more looking for some insight about where to learn the correct way to do it, of course some code is apreciated too, even though you then discarded it, shell script wouldnt have been an issue because i am currently starting to build a game server, working on the login part right now, hard to make a full server out of a shell script ;)

I'm gonna try out this code (as in, cut it to integrate in my current code, and see if i manage to get it work) and let you know, thanks for your help, realy!

Also, i'm working in codeblock, i arleady have some code working with "mysql.h" so i believe i can safely ignore the libs config thing?

If not, is that something i must place in compiler setting >> other option   ?

---

### Post by Pierrick584 on 2012-03-16
Also, right before i read your answer, i had an interesting result with what i tried to do...

The way my server work right now...

I just started learning RakNet, and my server is actualy some hacking i've done though some tutorial example, i created a shared library that contain all of my sql task (cause i plan to actualy split my server in multiple binary, so they can use all the same shared library) and i can use it to connect without issue, yet, once i receive the username and password from the client, i put them into a string, i print it to the server screen for debugging purpose, then i call the function that do a query(still in the shared library), including these string as argument, and, even though the function's code isint realy great at the momment, i get a segmentation fault at the calling, it cant even process the first function instruction, witch is a simple std::cout.


Here is my library code, and the part of my server witch call it

sssql.cpp
```
#include "sssql.h"

sssql::sssql()
{
    //ctor
}

sssql::~sssql()
{
    //dtor
}


bool sssql::checklogin(std::string, std::string)
{
    std::cout << "create pointer";
         MYSQL *connect; // Create a pointer to the MySQL instance
         std::cout << "pointer created";
         std::cout <<"mysql_res pointer thing to receive value";
MYSQL_RES *res_set; /* Create a pointer to recieve the return value.*/
        std::cout << "another success..";
    MYSQL_ROW row;  /* Assign variable for rows. */
    mysql_query(connect,"SELECT * FROM account");
    /* Send a query to the database. */
    unsigned int i = 0; /* Create a counter for the rows */

    res_set = mysql_store_result(connect); /* Receive the result and store it in res_set */

    unsigned int numrows = mysql_num_rows(res_set); /* Create the count to print all rows */

    /* This while is to print all rows and not just the first row found, */

    while ((row = mysql_fetch_row(res_set)) != NULL){
        printf("%s\n",row[i] != NULL ?
        row[i] : "NULL"); /* Print the row data */
}

}

bool sssql::connectdb()
{
     MYSQL *connect; // Create a pointer to the MySQL instance
    connect=mysql_init(NULL); // Initialise the instance
    /* This If is irrelevant and you don't need to show it. I kept it in for Fault Testing.*/
    if(!connect)    /* If instance didn't initialize say so and exit with fault.*/
    {
        printf("MySQL Initialization Failed");
        return 1;
    }
    /* Now we will actually connect to the specific database.*/

    connect=mysql_real_connect(connect,SERVER,USER,PASSWORD,DATABASE,0,NULL,0);
    /* Following if statements are unneeded too, but it's worth it to show on your
    first app, so that if your database is empty or the query didn't return anything it
    will at least let you know that the connection to the mysql server was established. */

    if(connect){
        printf("Connection Succeeded\n");
    }
    else{
        printf("Connection Failed!\n");
    }
}





```

sssql.h
```
#ifndef SSSQL_H
#define SSSQL_H
//#include "my_global.h" // Include this file first to avoid problems
#include "mysql.h" // MySQL Include File
#define SERVER "localhost"
#define USER "root"
#define PASSWORD "pc"
#define DATABASE "pcnviolagame"
#include <stdio.h>
#include <string>
#include <iostream>
class sssql
{
    public:
        sssql();
        virtual ~sssql();

        // Check login info
        std::string usrcheck;
        std::string passwd;
        bool connectdb();
        bool checklogin(std::string, std::string);
    protected:
    private:
};

#endif // SSSQL_H

```




loginserver.cpp (part of it)
```
            case ID_GAME_MESSAGE_1:
                {
                    RakNet::RakString rs;
                    RakNet::BitStream bsIn(packet->data,packet->length,false);
                    bsIn.IgnoreBytes(sizeof(RakNet::MessageID));
                    bsIn.Read(rs);
                    std::string username;
                    username = rs.C_String();
                    bsIn.Read(rs);
                    std::string password;
                    password = rs.C_String();
                    std::cout << "Comparing \"" << username << "\" " << password << " with the database...\n";
                    sql.checklogin(username, password);  // SEGMENTATION FAULT HERE

```


Have i just done something realy simple, wrong?

---

### Post by codemaniac on 2012-03-16
Here are some resources you can start with mysql .Choose your language and hop in .
Sky is your limit . :)
[http://dev.mysql.com/usingmysql/java/]("http://dev.mysql.com/usingmysql/java/")

[http://dev.mysql.com/doc/refman/5.1/en/connector-cpp.html]("http://dev.mysql.com/doc/refman/5.1/en/connector-cpp.html")

---

### Post by Pierrick584 on 2012-03-16
Thanks, i did saw that one, though it seems quite different from the code i've been using, so i wasnt sure about it.

On a side note, i'm still stuck with that seg fault, and i feel its just some kind of beginner misstake..

---

