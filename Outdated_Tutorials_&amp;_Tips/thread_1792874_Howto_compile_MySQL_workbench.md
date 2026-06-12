---
title: "Howto compile MySQL workbench"
date: 2011-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by WitchCraft on 2011-06-28
First, you need all the build dependencies:

```

sudo apt-get install build-essential autoconf automake libtool libzip-dev libxml2-dev libsigc++-2.0-dev libglade2-dev libgtkmm-2.4-dev libgl1-mesa-dev libmysqlclient16-dev uuid-dev liblua5.1-dev libpcre3-dev g++ libgnome2-dev libgtk2.0-dev libpango1.0-dev libcairo2-dev sqlite3-dev python-dev libboost-dev libctemplate-dev

```

Then you run:
```

./autogen.sh

```

If it fails, fix the errors, and re-run ./configure

If it finished successfully, you can start compiling MySQL-Workbench:
```

make install DESTDIR=/home/<username>/mysql-workbench

```

You can also use the parameter -jX, which improves build-speed by making use of several build-threads (X is the number of to be used parallel threads)


Then, inside your supplied output directory, change to /usr/local/bin  startup MySQL Workbench like this:
```

./mysql_workbench

```

---

### Post by WitchCraft on 2011-07-02
Note that if you get a error message, like 
> 
stricmp not found / not defined


You have to replace stricmp with strcasecmp.

[B]Note also that if you didn't on purpose compile the old version of mysql-workbench, you can stop now. Take the source of the alpha release, because the stable one doesn't yet give you the opportunity to do anything with your database.
[/B]


So you go to:
mysql-workbench-gpl-5.1.19-src/library/grt/src/diff/grtdiff.cpp
and replace stricmp with strcasecmp. There is exactly one occurence.


Or go to this page:
[http://dev.mysql.com/downloads/workbench/5.2.html](http://dev.mysql.com/downloads/workbench/5.2.html)

Download mysql-workbench-gpl-5.2.34-1ubu1010-i386.deb
(whatever is the correct version for your OS)

Then do:
```

sudo apt-get install python-pysqlite2 python-paramiko libctemplate0

```

and afterwards install mysql-workbench
```

sudo dpkg -i mysql-workbench-gpl-5.2.34-1ubu1010-i386.deb 

```

---

