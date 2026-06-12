---
title: "I want to disable the NOTICE in php in terminal"
date: 2011-10-12
forum: Programming Talk
---

### Post by Mostafatherock on 2011-10-12
[B]Hi everyone

I want to run php files in the terminal but every time it gives me a NOTICE[/B] [B]

My ubntun is 10.10 and I'm using php5[/B] [B]

I tried to disable the NOTICE from the php.ini by replacing [/B] [B]

[PHP]error_reporting = E_ALL[/PHP]To be[/B] [B]

```
error_reporting = E_ALL & ~E_NOTICE & ~E_WARNING
```This is what I'm trying to do[/B] [B]

I want to run this script in the terminal[/B] [B]

[PHP]#!/usr/bin/php5 
<?php
$x=he;
$y=llo;
echo $x.$y;
echo "\n";
echo strlen("This is the the sentence");
?>[/PHP]and this is the out put

```
mostafa@mostafa:/var/www$ ./1.php 
```[/B]```
 [B]
PHP Notice:  Use of undefined constant he - assumed 'he' in /var/www/1.php on line 3
PHP Notice:  Use of undefined constant llo - assumed 'llo' in /var/www/1.php on line 4
hello
24[/B]
```[B]

I Just want to disable this notice ... how can I do that ??
[/B]

---

### Post by An Sanct on 2011-10-12
[LEFT][COLOR=black]$x=he;
$y=llo;

are unknown, follow the advice the server gives you! "*assumend [COLOR=Red]'[/COLOR]he[COLOR=Red]'[/COLOR]*" and "*assumend [COLOR=Red]'[/COLOR]llo[COLOR=Red]'[/COLOR]*"

means the code should be 
$x=[COLOR=Red]**'**[/COLOR]he[COLOR=Red]**'**[/COLOR];
$y=[COLOR=Red]**'**[/COLOR]llo[COLOR=Red]**'**[/COLOR];[/COLOR]

After this modification, the warning will disappear. But warning will still stay present (you want that!)
[/LEFT]

---

### Post by Mostafatherock on 2011-10-12
errrrrrrr ..... I didn't continue reading the rest of the notice  :D :D

Thanks alot An Sanct, it's working perfect now !!

---

