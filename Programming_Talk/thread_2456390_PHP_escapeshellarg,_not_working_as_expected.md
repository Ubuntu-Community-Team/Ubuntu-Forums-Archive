---
title: "PHP escapeshellarg, not working as expected"
date: 2021-01-10
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2021-01-10
I am getting differnet results in php-cli and apache2
```
chad@X470GamingPlus:~$ cat Desktop/test.php 
<?php
$string="&#31040;";
echo "Specal Char = $string\n";
echo "Escaped = ".escapeshellarg($string)."\n";
?>
chad@X470GamingPlus:~$ php Desktop/test.php 
Specal Char = &#31040;
Escaped = '&#31040;'
chad@X470GamingPlus:~$ curl http://10.0.0.50:81/test.php
Specal Char = &#31040;
Escaped = ''
chad@X470GamingPlus:~$
```
EDIT:
found this in /etc/apache2/envvars
```
## The locale used by some modules like mod_dav
export LANG=C
## **Uncomment the following line to use the system default locale instead**:
#. /etc/default/locale

export LANG
```
uncommenting that line fixed it

---

