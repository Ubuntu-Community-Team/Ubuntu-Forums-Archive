---
title: "MySQL troubles"
date: 2008-11-11
forum: Packaging and Compiling Programs
---

### Post by Sabian02 on 2008-11-11
I have installed libmysql++-dev and I am sure the "/usr/include/mysql/mysql.h" is being included in the build however I keep running into build errors along the lines of

"/src/sql.cc:77 undefined reference to 'mysql_error'" 

As well as some other mysql definition errors, all of which I checked with grep and they are indeed defined in my mysql/mysql.h file. 

Anyone else run into this problem? any quick fixes?

So far I have tried:

explicit -I/usr/include/mysql in makefile
and
placing #include "/usr/include/mysql/mysql.h" in the code itself

to no avail.

Any help is deeply appreciated, thanks!

---

