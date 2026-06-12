---
title: "PHP4 programs compatible with PHP5?"
date: 2006-07-19
forum: Programming Talk
---

### Post by Peter Mount on 2006-07-19
Hello

I've set up LAMP with Dapper for developing web apps on my computer at home. I installed PHP4 with:

sudo aptitude install php4

This was after I enabled the extra repositories as per the instructions at: 

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I noticed that register_globals is set to off in php.ini (when I used phpinfo() in a file in localhost). Have there been other changes made to the defaults in php4 for Dapper and does this mean that web apps developed in php4 will be compatible with php5? Or is it best to still test seperately in php5 as well?

I installed mysql 4.1 and apache2 as well. PHP4.x and mysql 4.x is what my web host uses. I just want to make sure about compatibility with later versions of php and mysql when they upgrade.

Thanks

---

### Post by dabear on 2006-07-19
> **Peter Mount said:**
> Hello

I've set up LAMP with Dapper for developing web apps on my computer at home. I installed PHP4 with:

sudo aptitude install php4

This was after I enabled the extra repositories as per the instructions at: 

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I noticed that register_globals is set to off in php.ini (when I used phpinfo() in a file in localhost). Have there been other changes made to the defaults in php4 for Dapper and does this mean that web apps developed in php4 will be compatible with php5? Or is it best to still test seperately in php5 as well?

I installed mysql 4.1 and apache2 as well. PHP4.x and mysql 4.x is what my web host uses. I just want to make sure about compatibility with later versions of php and mysql when they upgrade.

Thanks

register globals has been off per default for a long time by now (php 4.2.0 ). Most php4 based scipts should be compatible with php5, but you may get into some trouble with curtain software, at least on MS Windows, where the mysql extension is not enabled per default.
All in all, php5 is just a new zend engine with better - but still extremly bad support for oop.

---

### Post by ifokkema on 2006-07-20
> **dabear said:**
> register globals has been off per default for a long time by now (php 4.2.0 ).
True, and not without reason: it can lead to a huge security hole in your scripts if you rely on it. Try and write your scripts regardless of certain PHP settings, such as register globals and magic quoting.

There are some differences in OOP in PHP4/5 and the way you call the constructor of a class.
In PHP4 the contructor has the same name of your class name. In PHP5, it's called __construct().

---

### Post by fluffington on 2006-07-20
> **ifokkema said:**
> True, and not without reason: it can lead to a huge security hole in your scripts if you rely on it. Try and write your scripts regardless of certain PHP settings, such as register globals and magic quoting.

Ignoring the state of magic quotes is a pain, since it likes to modify the input before it gets you your script. I ended up putting this together a while back, and it's made PHP development a lot less stressful:

```
<?php

if(get_magic_quotes_gpc()){
	stripslashes_recursive($_GET);
	stripslashes_recursive($_POST);
	stripslashes_recursive($_COOKIE);
}
set_magic_quotes_runtime(0);

function stripslashes_recursive(&$x){
	if(is_array($x)){
		foreach(array_keys($x) as $k){
			$k2 = stripslashes($k);
			$x2 =& $x[$k];
			unset($x[$k]);
			$x[$k2] =& $x2;
			stripslashes_recursive($x[$k2]);
		}
	}
	else $x = stripslashes($x);
}

?>
```

> In PHP4 the contructor has the same name of your class name. In PHP5, it's called __construct().

PHP5 accepts PHP4-style constructors in the absence of a __construct method. It makes life a lot easier when writing stuff that has to run in both.

---

### Post by ifokkema on 2006-07-21
> **fluffington said:**
> I ended up putting this together a while back, and it's made PHP development a lot less stressful
Funny, I always do the exact opposite; if magic quoting is off, I quote everything. I personally find that magic quoting is more often on than off, and I usually take the $_GET and $_POST variables in queries, anyway. I unquote everything using a function similar to yours, if I have to print the variables on screen.

> **fluffington said:**
> PHP5 accepts PHP4-style constructors in the absence of a __construct method. It makes life a lot easier when writing stuff that has to run in both.
Ah, thanks for that. Until now, I have the PHP4 constructor call the __construct().

---

### Post by fluffington on 2006-07-21
> **ifokkema said:**
> Ah, thanks for that. Until now, I have the PHP4 constructor call the __construct().

I was doing that for a while, too. That's what happens I'm too lazy to RTFM, I suppose.

---

