---
title: "PHP 5.2.4 in Ubuntu 8.04 &quot;global&quot; broken."
date: 2008-10-09
forum: Programming Talk
---

### Post by TitanKing on 2008-10-09
Very odd problem, I realized something odd was going on when I needed to create a simple function with global variables inside function, according to the manual, this should print the number 3;

[PHP]$a = 1;
$b = 2;

function Sum()
{
    global $a, $b;

    $b = $a + $b;
}

Sum();
echo $b;[/PHP]

However, mine prints the original $b which is 2, it seems it is ignoring global. 

Is this a bug?

---

### Post by ianhaycox on 2008-10-09
For your example my system, PHP Version 5.2.4-2ubuntu5.3, on Hardy prints 3 !

---

### Post by TitanKing on 2008-10-09
Thanks for your reply. This is very weird, well I will just have to work around this problem as I have no idea what could be causing this.

Regards

---

### Post by rnodal on 2008-10-09
Could you give it a try to this as see if you get the same result?
[PHP]<?php
$a = 1;
$b = 2;

function Sum()
{
    $GLOBALS['b'] = $GLOBALS['a'] + $GLOBALS['b'];
} 

Sum();
echo $b;
?>
[/PHP]

-r

---

