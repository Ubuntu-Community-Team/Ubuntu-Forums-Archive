---
title: "PHP 5 just don't work properly... (set variable using browser)"
date: 2009-08-19
forum: Programming Talk
---

### Post by Repgahroll on 2009-08-19
Hello!

I just installed PHP5 server on my machine, and everything seems OK, but i made a simple script that don't work and i don't know why, but i think it's a PHP fault:

```
<?php

echo "the item is:";

if ($item=="a") {

echo ("item a");

} 

if ($item=="b") {

echo ("item b");

}
?> 
```

When i access the page (index.php), it prints the text "the item is:", okay, but it's supposed to print also the lines "item a" or "item b" if i set the variable "$item" to "a" or "b" using "index.php?item=a" or "index.php?item=b", however such thing doesn't happen, it never prints nothing but the "the item is:" line.

Can you help me please??

Thank you very much and sorry my english.

---

### Post by v8YKxgHe on 2009-08-19
Why are you thinking providing a HTTP GET parameter will set a variable within PHP? You need to use $_GET['foo'], where by 'foo' would come from the URL, e.g. index.php?foo=bar.

Also, as 'echo' is not a function, you do not need the parenthesis - so just the following is fine:

```
<?php echo 'bar'; ?>
```

Edit:

This just shows that you're not using the correct error reporting and/or display errors as well. You *always* develop so you can see the errors, set this top of your file:

```
<?php error_reporting( E_ALL | E_STRICT ); ini_set( 'display_errors', true ); ?>
```
Or set it in your main 'php.ini' file (if using Apache with this, it'll be in /etc/php/apache2/php.ini)

---

### Post by Repgahroll on 2009-08-19
```
<?php

$item = $_GET['item'];

echo "the item is:";

if ($item=="a") {

echo "item a";

}

if ($item=="b") {

echo "item b";

}
?> 
```

:D Now it's working very well! 

Thank you very much man! :) Very quick and precise answer!!

Sorry, it was my fault actually!

---

### Post by v8YKxgHe on 2009-08-19
No worries. You can also use 'else if' instead of 2 'if' blocks, such as:

```

if ( 'foo' == 'bar' ) {

} else if ( 'foo' == 'zomg' ) {

}

```

---

### Post by Mirge on 2009-08-19
Heh in your first code snippet, it looked like you were trying to use register_globals... I was about to cry.

---

### Post by credobyte on 2009-08-19
[php]$item; // PHP4
$_GET['item']; // PHP5
[/php]

Don't mix them ;)

---

### Post by Mirge on 2009-08-19
> **credobyte said:**
> [php]$item; // PHP4
$_GET['item']; // PHP5
[/php]Don't mix them ;)

How is that PHP4 vs PHP5? lol

---

### Post by credobyte on 2009-08-19
> **Mirge said:**
> How is that PHP4 vs PHP5? lol

$item, by default, ( index.php?item=something ) can be used only in PHP4 - PHP5 doesn't do it by default ( tough, you still can get it ). Anyway, these are just my memories - haven't had a chance to use PHP4 and all it's *essentials* :)

---

### Post by Mirge on 2009-08-19
> **credobyte said:**
> $item, by default, ( index.php?item=something ) can be used only in PHP4 - PHP5 doesn't do it by default ( tough, you still can get it ). Anyway, these are just my memories - haven't had a chance to use PHP4 and all it's *essentials* :)

That would require using the register_globals directive, which is disabled by default in PHP 4.2.0 & higher. See: [http://us.php.net/manual/en/ini.core.php#ini.register-globals](http://us.php.net/manual/en/ini.core.php#ini.register-globals)

---

### Post by credobyte on 2009-08-19
> **Mirge said:**
> That would require using the register_globals directive, which is disabled by default in PHP 4.2.0 & higher. See: [http://us.php.net/manual/en/ini.core.php#ini.register-globals](http://us.php.net/manual/en/ini.core.php#ini.register-globals)

Nutshell of what I was trying to explain :idea:

---

