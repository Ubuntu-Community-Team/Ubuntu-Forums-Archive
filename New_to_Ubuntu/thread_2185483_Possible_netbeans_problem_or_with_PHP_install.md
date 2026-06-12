---
title: "Possible netbeans problem or with PHP install"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by r3bol on 2013-11-02
Hi, I'm trying to develop with php using the netbeans ide.  I can't seem to get any output though after running the script (Mode = Run as - Script). 
I think it might be to do with my php install. Here is what netbeans outputs with a simple "hello world" attempt...

```
"/usr/bin/php" "/home/asdf/dev/projects/php/OOP/netbeans02"
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/gd.so' - /usr/lib/php5/20090626+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mcrypt.so' - /usr/lib/php5/20090626+lfs/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysql.so' - /usr/lib/php5/20090626+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysqli.so' - /usr/lib/php5/20090626+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/pdo_mysql.so' - /usr/lib/php5/20090626+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
Done.
```
The PHP shell outputs are just warnings, so perhaps it's something else. Does anyone have ideas why there would be no PHP output from netbeans?

Thanks.

---

