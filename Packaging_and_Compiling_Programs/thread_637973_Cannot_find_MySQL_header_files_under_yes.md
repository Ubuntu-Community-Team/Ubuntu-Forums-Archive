---
title: "Cannot find MySQL header files under yes"
date: 2007-12-11
forum: Packaging and Compiling Programs
---

### Post by maz00 on 2007-12-11
Hi all, 

I'm trying to configure Ubuntu for the first time (and haven't touched *nix for 3 years now) and surprise, I'm running into problems :)

I've install mysql using apt-get install mysql (which works)
I've downloaded the source for apache2 and installed it (works)
I've downloaded the source for php and installed. It worked except no mysql support. So I went back and now I'm trying to add mysql to it using --with-mysql= however, it return this error


./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/

configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!

I've tried everything and still no go. This is what I have installed for mysql
ii  libdbd-mysql-per 4.004-2          A Perl5 database interface to the MySQL database
un  libmysqlclient15 <none>           (no description available)
ii  libmysqlclient15 5.0.45-1ubuntu3  MySQL database client library
un  mysql-client     <none>           (no description available)
ii  mysql-client-5.0 5.0.45-1ubuntu3  MySQL database client binaries
ii  mysql-common     5.0.45-1ubuntu3  MySQL database common files
un  mysql-doc-5.0    <none>           (no description available)
ii  mysql-server     5.0.45-1ubuntu3  MySQL database server (meta package depending on
ii  mysql-server-5.0 5.0.45-1ubuntu3  MySQL database server binaries
un  virtual-mysql-cl <none>           (no description available)
un  virtual-mysql-se <none>           (no description available)


Any pointers here? what am I missing? 

BTW, some sites say search for 'find / -name mysql.h' and that file doesn't exist on my computer at all. 

Thx
Maz

---

### Post by dholbach on 2007-12-12
```
sudo apt-get install libmysqlclient15-dev
```
maybe?

---

### Post by abrahamchaffin on 2008-05-14
That worked for me -

Thanks

---

### Post by f3ath on 2008-07-26
> **dholbach said:**
> ```
sudo apt-get install libmysqlclient15-dev
```
maybe?

i think ```
sudo apt-get install libmysqlclient-dev
``` is better, because it allows automatic library updates

---

### Post by gbstack on 2011-06-06
it works well,thank you very much!

---

### Post by rajeshgautam on 2011-08-05
> **f3ath said:**
> i think ```
sudo apt-get install libmysqlclient-dev
``` is better, because it allows automatic library updates

This worked for me. Thanks :D

In ssx/genv2.cpp you might need to add #include <string.h> to fix an compile error of strcmp

---

### Post by kpothi on 2012-03-24
> **f3ath said:**
> i think ```
sudo apt-get install libmysqlclient-dev
``` is better, because it allows automatic library updates

This worked for me. Thanks for the solution!

---

