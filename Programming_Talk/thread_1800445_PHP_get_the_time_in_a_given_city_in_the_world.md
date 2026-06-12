---
title: "PHP get the time in a given city in the world?"
date: 2011-07-09
forum: Programming Talk
---

### Post by honeybear on 2011-07-09
Hi,

```
$timevariable = ?? 
```

Would by change anyone has heard about how get the time in a given city in the world using PHP?  of the REMOTE IP?

Cheers to Tux world !

---

### Post by wojox on 2011-07-09
This is how I use to do it:

[PHP]
#!/usr/bin/php
<?php
$now = time();  // use this so all times are to the same second
$tz = getenv("TZ"); // save local setting so we can reset it later
putenv("TZ=GMT");
printf("The time in London is %s\n", date('H:i:s', $now));
putenv("TZ=Hongkong");
printf("The time in Hongkong is %s\n", date('H:i:s', $now));
putenv("TZ=$tz");
printf("The local server time is %s\n", date('H:i:s', $now));
?> 
[/PHP]

---

### Post by honeybear on 2011-07-09
> **wojox said:**
> This is how I use to do it:

[PHP]
#!/usr/bin/php
<?php
$now = time();  // use this so all times are to the same second
$tz = getenv("TZ"); // save local setting so we can reset it later
putenv("TZ=GMT");
printf("The time in London is %s\n", date('H:i:s', $now));
putenv("TZ=Hongkong");
printf("The time in Hongkong is %s\n", date('H:i:s', $now));
putenv("TZ=$tz");
printf("The local server time is %s\n", date('H:i:s', $now));
?> 
[/PHP]

Sounds very good, but would you know how without changing the "TZ" Enviroment

---

### Post by v8YKxgHe on 2011-07-09
There is no need to set the environment all the time. Simply use PHPs many DateTime classes/functions, [http://php.net/datetime](http://php.net/datetime) for example:

[PHP]$a = new DateTime('now', new DateTimeZone('Europe/Paris'));
var_dump($a->format('H:i:s'));[/PHP]

---

### Post by honeybear on 2011-07-09
> **AlexC_ said:**
> There is no need to set the environment all the time. Simply use PHPs many DateTime classes/functions, [http://php.net/datetime](http://php.net/datetime) for example:

[PHP]$a = new DateTime('now', new DateTimeZone('Europe/Paris'));
var_dump($a->format('H:i:s'));[/PHP]

```
$hostname = gethostbyaddr($_SERVER['REMOTE_ADDR']);
$datum = date("d-m-y / H:i:s");
$a = new DateTime('now', new DateTimeZone('Europe/Paris'));
var_dump($a->format('H:i:s'));

```
It is not working 

nothing comes up in the page :(

---

### Post by v8YKxgHe on 2011-07-09
Ensure that you have "display_errors" on and that you have a high enough "error_reporting" level. This can be done either in your php.ini configuration file or you can put the following at the top of your script:

[PHP]error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', true);[/PHP]

---

### Post by honeybear on 2011-07-09
> **AlexC_ said:**
> Ensure that you have "display_errors" on and that you have a high enough "error_reporting" level. This can be done either in your php.ini configuration file or you can put the following at the top of your script:

[PHP]error_reporting(E_ALL | E_STRICT);
ini_set('display_errors', true);[/PHP]

The problem is : ```
**[COLOR="Red"]new[/COLOR]** DateTime('now', new DateTimeZone('Europe/Paris'));
```
 
and that one that writes on the screen
```
[COLOR="Red"]var_dump[/COLOR]($a->f
```

I tried:

$a = var_dump 

:(

---

### Post by v8YKxgHe on 2011-07-09
Your previous post makes 100% no sense. What do you mean, and what is the *actual* error produced by PHP?

---

### Post by wojox on 2011-07-09
Works fine for here:

[PHP]
#!/usr/bin/php
<?php
$dateTime = new DateTime('now', new DateTimeZone('Europe/Paris'));
echo $dateTime->format("Y-m-d H:i:s");
?>
[/PHP]

Had to get rid of 

```
$hostname = gethostbyaddr($_SERVER['REMOTE_ADDR']);
```

I'm just using php-cli. I guess your using $hostname somewhere else in the script? Cause it really serves no purpose here.

---

### Post by honeybear on 2011-07-10
> **wojox said:**
> Works fine for here:

[PHP]
#!/usr/bin/php
<?php
$dateTime = new DateTime('now', new DateTimeZone('Europe/Paris'));
echo $dateTime->format("Y-m-d H:i:s");
?>
[/PHP]

Had to get rid of 

```
$hostname = gethostbyaddr($_SERVER['REMOTE_ADDR']);
```

I'm just using php-cli. I guess your using $hostname somewhere else in the script? Cause it really serves no purpose here.


Hi, 

Thanks. Yeah, actually, I would like to output the time of a given city into a log file. Instead of prompting an echo on the html/site, how could I put the time of the city in my variable $timereal? 

Thank you in advance and wishing a nice day:)

---

### Post by LoneWolfJack on 2011-07-10
you will first have to understand timezones. even though some relate to cities, most don't. there is no built-in PHP function that will return the current time for a given city.

you will have to map each city to a timezone and then calculate the time based on GMT time.

---

