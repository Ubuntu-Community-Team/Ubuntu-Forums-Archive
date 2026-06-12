---
title: "Trouble compiling mysql apps"
date: 2005-11-14
forum: Programming Talk
---

### Post by messorian on 2005-11-14
Hi all, hopefully someone can help with this.  I am attempting to write a mysql app but I get an error while attempting to compile it. 
Here is the command I am using to compile the application:
"g++ mysqlApp.cpp -lmysqlclient -L/usr/local/mysql/lib  -I/usr/local/mysql/include -lz"  

and I get the following error:
"/usr/bin/ld: cannot find -lz"

But when I check for the library I get the following:
"ls /usr/lib/libz*
/usr/lib/libz.so.1             /usr/lib/libzzip.so
/usr/lib/libz.so.1.2.3         /usr/lib/libzzipwrap-0.so.12
/usr/lib/libzzip-0.so.12       /usr/lib/libzzipwrap-0.so.12.0.83
/usr/lib/libzzip-0.so.12.0.83  /usr/lib/libzzipwrap.a
/usr/lib/libzzip.a             /usr/lib/libzzipwrap.la
/usr/lib/libzzip.la            /usr/lib/libzzipwrap.so"

So does anyone have an idea of what I need to make the application compile properly?  Also, if I need to post anymore information, let me know and I'll gladly provide it :)

---

### Post by messorian on 2005-11-14
I think I got it, I changed -lz to -lzzip

---

### Post by nagilum on 2005-11-14
There should be a tool called 'mysql_config' which gives you all the right arguments you need in order to compile the source. Just run the compiler like this:

g++ mysqlApp.cpp $(mysql_config --cflags --libs --include)

---

### Post by dudus on 2006-04-12
you shold download libmysqlclientxx-dev from the repos.
substitute xx with your mysql verssion.
this dev package comes with mysql header and mysql_config

---

### Post by cbschuld on 2006-07-28
I ran the following with success:

```
LINUX> sudo apt-get install libmysqlclient12-dev
```

---

