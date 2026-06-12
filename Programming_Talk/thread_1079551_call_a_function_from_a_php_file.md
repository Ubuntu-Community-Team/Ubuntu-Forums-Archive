---
title: "call a function from a php file"
date: 2009-02-24
forum: Programming Talk
---

### Post by vitotol on 2009-02-24
hello guys, i'd like to call a function from another php file...
how can i do that?

---

### Post by cabalas on 2009-02-24
Before you are able to call a function you must first include/require the file it is in, here is a trivial example:

functions.php
[PHP]
<?

  function add($a, $b) {
    return $a + $b;
  }

?>
[/PHP]

The file you want to call it from:
[PHP]
<?
  require_once("functions.php");

  echo "Adding 1 and 2 gives you: " . add(1, 2) . "\n";
?>
[/PHP]

you should look at these doc pages for more info

[http://php.net/include](http://php.net/include)
[http://php.net/include_once](http://php.net/include_once)
[http://php.net/require](http://php.net/require)
[http://php.net/require_once](http://php.net/require_once)

---

### Post by vitotol on 2009-02-25
thanx man, i did it.

---

