---
title: "PHP Script Conversion"
date: 2007-02-09
forum: Programming Talk
---

### Post by amitroy5 on 2007-02-09
How can I make this script work without register_globals:

```
<? if ($page) { if ( @filesize ("$page" . ".html") ) { require ("$page.html"); } else { require ("missing.html"); } } else { require ("home.html"); } ?>
```
This calls any file form my website. Thus, I only need one layout for the whole thing.

As well as this one?

```
<? echo($email); ?>
```
I need this when the URL is [http://mysite.com/script.php?email=whatever@whatever.com](http://mysite.com/script.php?email=whatever@whatever.com)

It just hit me how insecure the second script is. I played around with it and I began inserting PHP code, making my website very easy to hack. Thanks!

---

### Post by mvaniersel on 2007-02-09
It's easy, you need to use $_GET['email']

See also: [http://www.w3schools.com/php/php_get.asp]("http://www.w3schools.com/php/php_get.asp")

---

### Post by gradedcheese on 2007-02-09
I would also use isset rather than the current statement, ie: if( isset( $_GET['page'] ) )

By the way, this is kind of a security disaster: you're taking an untrusted variable (ie: from the browser via GET or POST) and then, based on it, including a file.  Ouch!  Additionally, there is a file_exists function, calling filesize to see if something exists seems really odd.

If you really want to do this (and I am not sure why you would), you should build a list of files as key=>path, and have the GET or POST variable provide the key, from which you look up the path and import/require it.  Otherwise they can put arbitrary file paths there which, as long as they exist, would be included.

---

