---
title: "can anyone explain, point to regular expression help? PHP"
date: 2011-02-14
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-14
I am baffled by regular expressions such as are used in PHP preg_ functions.

---

### Post by Arndt on 2011-02-14
> **sdowney717 said:**
> I am baffled by regular expressions such as are used in PHP preg_ functions.

Is it a basic introduction to regular expressions you need? Or the Perl regexp features? Did you google for "regular expression"? Did you not find anything, or was something unclear in what you did find?

---

### Post by sdowney717 on 2011-02-14
just a basic understanding for PHP expressions
[http://php.net/manual/en/function.preg-split.php](http://php.net/manual/en/function.preg-split.php)
<?php
// split the phrase by any number of commas or space characters,
// which include " ", \r, \t, \n and \f
$keywords = preg_split("/[\s,]+/", "hypertext language, programming");
?>

I dont understand how they know to create the "/[\s,]+/"
and the manuals dont explain this well.

---

### Post by Arndt on 2011-02-14
> **sdowney717 said:**
> just a basic understanding for PHP expressions
[http://php.net/manual/en/function.preg-split.php](http://php.net/manual/en/function.preg-split.php)
<?php
// split the phrase by any number of commas or space characters,
// which include " ", \r, \t, \n and \f
$keywords = preg_split("/[\s,]+/", "hypertext language, programming");
?>

I dont understand how they know to create the "/[\s,]+/"
and the manuals dont explain this well.

I google for you, and this was the first hit:

[http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

