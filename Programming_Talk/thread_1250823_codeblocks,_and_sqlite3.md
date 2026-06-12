---
title: "code::blocks, and sqlite3"
date: 2009-08-27
forum: Programming Talk
---

### Post by Arla on 2009-08-27
Hey all,

Hopefully someone can help me get this working,

I'm trying to use sqlite3 with C++ using code::blocks as the IDE.

Compiling my code with

g++ main.cpp -o main -lsqlite3

works just fine, however I'm not sure how to add that -lsqlite3 command into code::blocks, every time I try to run I get 

> 
/home/james/Documents/GPS/Test/main.cpp|8|undefined reference to `sqlite3_open'|

(one for each of the sqlite3 commands I use).

My code is below just for kicks, it's a STUPIDLY simple sample code, as I say really just trying to get things working right now

> 
#include <sqlite3.h>
#include <stdio.h>
sqlite3* db;
char* db_err;

int main()
{
    sqlite3_open("my_db.sql3", &db);
    sqlite3_exec(db, "create table 'helloworld' (id integer);", NULL, 0, &db_err);
    sqlite3_close(db);
}


---

### Post by Arla on 2009-08-27
Well answering my own damn question, figured it out.

I needed to add -lsqlite3 into the linker options (under build options, other linker options)

---

