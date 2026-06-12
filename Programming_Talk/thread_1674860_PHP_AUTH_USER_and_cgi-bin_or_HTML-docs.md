---
title: "PHP_AUTH_USER and /cgi-bin or HTML-docs"
date: 2011-01-24
forum: Programming Talk
---

### Post by kuifje09 on 2011-01-24
After trying a lot with next script :

<?php
echo $_SERVER['PHP_AUTH_USER'];
?>

I found this gave no output when placed in the /cgi-bin/..
But worked fine when placed between the html docs.

For the html docs you need to log in. thats okay !
for the html docs apache is configured whith :  require valid-user
and of cource the /cg-bin is not. But I think this is silly.
I would have placed all php-script in /cgi-bin, but that seem to fail.
i.e. echo $_SERVER['SERVER_NAME'];  is printed well from /cgi-bin/

The php script is called after you have logged in. 

Whats wrong with me ?

---

