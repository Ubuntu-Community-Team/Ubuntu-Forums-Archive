---
title: "[SOLVED] PHP Parse error!"
date: 2008-05-20
forum: Programming Talk
---

### Post by Rytron on 2008-05-20
Hi,

I get this error

Parse error: parse error, unexpected '}', expecting ',' or ';' in C:\wamp\www\-php\PHP-4-If Else Statements.php on line 8



Here is the php:

```
<?php

$first=30;

$second=40;

$third=50;

if ($first<$second)

    {echo"this is true"}

else

    {echo"this is false"}

/*    

    if ($first==$second)

    {echo"this is true"}

else

    {echo"this is false"}

*/

 /*   

      if ($first!=$second)

    {echo"this is true"}

else

    {echo"this is false"}

*/

?>


```
What is wrong with this code?

Thanks.

---

### Post by grepgav on 2008-05-20
put semicolons after the echo statements.

EX:

echo "Hello, World";

you are closing the {} without terminating the echo statement.

---

