---
title: "In PHP why is (0=='string')"
date: 2013-07-07
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2013-07-07
[PHP]#!/usr/bin/php
<?php
if(0=="string")
        echo "Mind Blown\n";
else
        echo "All is right in the world\n";
?>[/PHP]
```
~$ php /tmp/test
Mind Blown
```

---

### Post by spjackson on 2013-07-07
Why? Because...
[http://php.net/manual/en/language.operators.comparison.php](http://php.net/manual/en/language.operators.comparison.php) "If you compare a number with a string or the comparison involves numerical strings, then each string is converted to a number and the comparison performed numerically. These rules also apply to the switch statement. The type conversion does not take place when the comparison is === or !== as this involves comparing the type as well as the value."

and...
[http://www.php.net/manual/en/language.types.string.php#language.types.string.conversion](http://www.php.net/manual/en/language.types.string.php#language.types.string.conversion) "If the string starts with valid numeric data, this will be the value used. Otherwise, the value will be 0 (zero)."

---

### Post by CptPicard on 2013-07-07
Welcome to figuring out why PHP frankly just sucks ;)

---

### Post by pqwoerituytrueiwoq on 2013-07-07
thanks [spjackson]("http://ubuntuforums.org/member.php?u=1128302")

---

### Post by nvteighen on 2013-07-07
Obligatory "PHP: a fractal of bad design" [http://me.veekun.com/blog/2012/04/09/php-a-fractal-of-bad-design/](http://me.veekun.com/blog/2012/04/09/php-a-fractal-of-bad-design/)

---

### Post by pqwoerituytrueiwoq on 2013-07-07
But if it is in php as opposed to javascript you don't have to worry about IE screwing something up, all it has to do is fail at rendering the output
i am self taught in javascript, and when i started using php it just came to me fairly quickly and easily

---

