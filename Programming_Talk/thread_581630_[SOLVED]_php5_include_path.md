---
title: "[SOLVED] php5: include_path"
date: 2007-10-19
forum: Programming Talk
---

### Post by ingridt on 2007-10-19
ubuntu feisty: apache2 + php5

what is the best approach to set include_path? 

Sometimes .htaccess can be used: where to find it?
Sometimes php.ini is to be used: where to find it?
Sometimes each script has to contain a ini_set('include_path...

Which one is advised for ubuntu?

---

### Post by tkharris on 2007-10-19
> Sometimes .htaccess can be used: where to find it?

In whichever directory you're docroot is in.  ( ensure that allow override all is set in the config, and note this will only work with mod_php, not php through cgi ) 

> Sometimes php.ini is to be used: where to find it?

locate php.ini

> Sometimes each script has to contain a ini_set('include_path...

That's done in the php file.  :)

---

### Post by ingridt on 2007-10-19
I understand that ubuntu leaves the choice to me? :)


In that case I would use the same method as the remote server (where I have the live site online) forces me there: ini_set in every script-page.

---

### Post by ingridt on 2007-10-19
The included path seems correct to me, but still the file to include is not found?:confused:

This is the full path to the file: 
/var/www/ingrid/SPLIB/Database/MySQL.php

These are the include-sentences in my script:
ini_set('include_path', ".:/var/www/ingrid/SPLIB:/usr/share/php:/usr/share/pear");
require_once('/Database/MySQL.php');

both set in the beginning of the script.

What is wrong? 
This is the error message:
Warning: require_once(/Database/MySQL.php) [function.require-once]: failed to open stream: No such file or directory in /var/www/ingrid/oef/test.php on line 17

Fatal error: require_once() [function.require]: Failed opening required '/Database/MySQL.php' (include_path='.:/var/www/ingrid/SPLIB:/usr/share/php:/usr/share/pear') in /var/www/ingrid/oef/test.php on line 17

---

### Post by tkharris on 2007-10-19
Have you tried with
```

require_once('Database/MySQL.php');
or:
require_once('/var/www/ingrid/SPLIB/Database/MySQL.php');

```
?

---

### Post by #Reistlehr- on 2007-10-19
by requireing the file with a / in the front of the path, you are basically telling the script to search for the file off the root of the drive.

Also, if the file is in a subdirectory or the directory you are in, you dont have to set the include path for it.

---

### Post by ingridt on 2007-10-20
Solved:
it was the / before Database in the require statement that make it fail!

Thank you both for the very usefull answers.

---

