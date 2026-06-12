---
title: "PHP from shell"
date: 2009-08-19
forum: Programming Talk
---

### Post by niiize on 2009-08-19
Have apache2 installed but cannot find the right php path, even tho my website works fine with php scripts in it. i need to find out because i want to be able to run scripts from shell #!path/to/php

thank you

---

### Post by Mirge on 2009-08-19
which php

or

whereis php

---

### Post by niiize on 2009-08-19
forgot to mention that i've tried this......... :P

'whereis' only returns 
php:
and 'which' return nothing at all

---

### Post by v8YKxgHe on 2009-08-19
You need to use the CLI version of PHP. The version you have installed is most likely a module to Apache2, so there will be no binary you can use like that.

The package is 'php5-cli'.

---

### Post by niiize on 2009-08-19
super. thank you. works fine.

---

### Post by slakkie on 2009-08-19
Btw, #!/usr/bin/env php is something you can use, so when migrating from one system to another you don't need to remember the path to php (although on some systems the path to env is different..).

---

