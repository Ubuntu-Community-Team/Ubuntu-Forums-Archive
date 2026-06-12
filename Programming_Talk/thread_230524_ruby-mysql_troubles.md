---
title: "ruby-mysql troubles"
date: 2006-08-06
forum: Programming Talk
---

### Post by Blindbatts on 2006-08-06
I'm trying to install the ruby-mysql and am having some problems.

I have mysql installed right, I can login to it as root and such.

ruby is working, I have a simple webrick server working with it and am able to host webpages and view them in firefox.

but when I am following this guide:
[http://www.tmtm.org/en/mysql/ruby/](http://www.tmtm.org/en/mysql/ruby/)

basically at step 1, I can't proceed, when I try to configure it by running 
ruby extconf.rb, I've tried both of their recommended switches but the output is always the same.

this is the output I get -
```

blind@blind-laptop:~/Desktop/mysql-ruby-2.7.1$ ruby extconf.rb \ --with-mysql-include=/usr/local/mysql/include/mysql \ --with-mysql-lib=/usr/local/mysql/lib/mysql
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lm... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lz... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lsocket... no
checking for mysql_query() in -lmysqlclient... no
checking for main() in -lnsl... no
checking for mysql_query() in -lmysqlclient... no
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/usr/bin/ruby1.8
        --with-mysql-config
        --without-mysql-config
        --with-mysql-dir
        --without-mysql-dir
        --with-mysql-include
        --without-mysql-include=${mysql-dir}/include
        --with-mysql-lib
        --without-mysql-lib=${mysql-dir}/lib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-mlib
        --without-mlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-zlib
        --without-zlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-socketlib
        --without-socketlib
        --with-mysqlclientlib
        --without-mysqlclientlib
        --with-nsllib
        --without-nsllib
        --with-mysqlclientlib
        --without-mysqlclientlib

```

I appreciate any help!

---

### Post by asimon on 2006-08-06
How do you have installed mysql? Via Ubuntu's packages? Then make sure you also have libmysqlclient15-dev installed (or libmysqlclient14-dev if you're using mysql version 4.x). You need this package if you want to compile any mysql stuff.

The default paths for Ubuntu's mysql packages are: /usr/include/mysql for -with-mysql-include and /usr/lib for --with-mysql-lib, but the ruby install script should find them automatically.

BTW, ruby-mysql is already packages for Ubuntu. The package is called 'libmysql-ruby', so you don't really need to compile it your own.

---

### Post by Blindbatts on 2006-08-06
Thank you!

I installed the packages you listed and everything is playing nicely now :)

---

### Post by DeadEyes on 2006-08-07
Thanks asimon I had been having the same problems.

---

### Post by spoonclaymore on 2008-05-04
These directions worked for me as well. Using ruby 1.8.6, mysql  Ver 14.12 Distrib 5.0.45.

---

