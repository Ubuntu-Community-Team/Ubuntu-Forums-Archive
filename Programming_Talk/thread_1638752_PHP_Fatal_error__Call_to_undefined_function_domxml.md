---
title: "PHP Fatal error:  Call to undefined function domxml_new_doc()"
date: 2010-12-06
forum: Programming Talk
---

### Post by ivikas on 2010-12-06
Hi all,

      I am just starting google maps API tutorial at this link.

```

 http://code.google.com/apis/maps/articles/phpsqlajax.html

```

But this piece of code is not working and i don't have an idea as how to install this extension in Ubuntu Lucid

```

$doc = domxml_new_doc("1.0");
$node = $doc->create_element("markers");
$parnode = $doc->append_child($node);

```

And i get an error like this when i run this script using php command line

```

PHP Fatal error:  Call to undefined function domxml_new_doc() in /var/www/googlemaps/phpmysql/phpsqlajax_genxml.php on line 3

```

It will be highly appreciated,if any one could tell me a way to install and use this extension.

With Regards,
Vikas Mohan

---

### Post by roccivic on 2010-12-06
Ubuntu lucid ships with PHP5, but I see on php.net that domxml_new_doc() is a PHP4 function. Try googling: "domxml_new_doc() php5", maybe there is an alternative.

---

