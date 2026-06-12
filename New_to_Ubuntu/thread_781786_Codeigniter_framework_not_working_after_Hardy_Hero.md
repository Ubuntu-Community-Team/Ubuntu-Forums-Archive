---
title: "Codeigniter framework not working after Hardy Heron upgrade"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2008-05-04
So I upgraded from Gutsy Gibbon to the Heron.
The upgrade was extremely easy, the update manager worked flawlessly.

I've noticed all around speed improvements and firefox 3 is super fast.

There's one snag though.  I developed a site using the php CodeIgniter framework.  After the upgrade, the site doesn't work locally any more.  When I try to go to the directory on my [http://localhost](http://localhost) server it is completely blank, and when I view the source there is abosolutely nothing.  All other files and sites work locally, and I put a test PHP file in the directory and when I access that directly it loads.  

Anyone know what could have this happen?  I don't see any errors in the apache log and theres no codeignither log.  The only thing that looks kinda weird in the apache log is:
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysql.so' - /usr/lib/php5/20060613+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mysqli.so' - /usr/lib/php5/20060613+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/pdo_mysql.so' - /usr/lib/php5/20060613+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Sun May 04 07:47:53 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5 with Suhosin-Patch configured -- resuming normal operations
```

Anyone have any ideas as to how to fix this?  Thanks.  Ubuntu rules.

---

### Post by steve.klebanoff on 2008-05-04
I think this could definitely be related to that mysql warning.  
When I try to load phpmyadmin I get:

```

phpMyAdmin - Error

Cannot load mysql extension. Please check your PHP configuration. - Documentation

```

---

