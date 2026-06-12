---
title: "Installing python2.4-mysqldb in Karmic?"
date: 2009-11-17
forum: Programming Talk
---

### Post by khughitt on 2009-11-17
Hi all,

Does anyone know of a good way to install libraries (most importantly MySQLdb) in older versions of python running on Karmic?

I installed python2.4 in order to test whether software is compatible on older systems, however, the MySQL adapter for 2.4 is no longer available in the repos. By installing the package 'python-mysqldb,' the library is installed for both 2.5 and 2.6

e.g. 

```

dpkg -L python-mysqldb
...
/usr/lib/pyshared/python2.6/_mysql.so
/usr/lib/pyshared/python2.5/_mysql.so
...

```

Any ideas?
Thanks!

---

