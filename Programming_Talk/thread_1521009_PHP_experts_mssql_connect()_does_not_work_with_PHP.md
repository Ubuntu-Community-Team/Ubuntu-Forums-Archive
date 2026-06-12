---
title: "PHP experts mssql_connect() does not work with PHP 5.2.10"
date: 2010-06-30
forum: Programming Talk
---

### Post by akvino on 2010-06-30
php -v gives:
PHP Warning:  PHP Startup: mssql: Unable to initialize module
Module compiled with module API=20050922, debug=0, thread-safety=0
PHP    compiled with module API=20060613, debug=0, thread-safety=0
These options need to match
 in Unknown on line 0
PHP Warning:  PHP Startup: pdo_dblib: Unable to initialize module
Module compiled with module API=20050922, debug=0, thread-safety=0
PHP    compiled with module API=20060613, debug=0, thread-safety=0
These options need to match
 in Unknown on line 0
PHP 5.2.10 (cli) (built: Aug 10 2009 05:20:34) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies


Apache main log gives:
[Wed Jun 30 08:21:38 2010] [notice] Digest: done
PHP Warning:  PHP Startup: mssql: Unable to initialize module\nModule compiled with module API=20050922, debug=0, thread-safety=0\nPHP    compiled with module API=20060613, debug=0, thread-safety=0\nThese options need to match\n in Unknown on line 0
PHP Warning:  PHP Startup: pdo_dblib: Unable to initialize module\nModule compiled with module API=20050922, debug=0, thread-safety=0\nPHP    compiled with module API=20060613, debug=0, thread-safety=0\nThese options need to match\n in Unknown on line 0


I got both php-mssql and php-pdo packages installed (this is on RedHat).

Any hints on how to fix this?

---

### Post by akvino on 2010-06-30
Figured it out.

---

### Post by Cavillis on 2011-02-08
can you post with something more detailed than "fixed"? I have the same error but can't figure out how to fix it.

---

