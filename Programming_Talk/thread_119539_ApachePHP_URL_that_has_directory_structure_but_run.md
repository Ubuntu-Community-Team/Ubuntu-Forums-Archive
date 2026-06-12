---
title: "Apache/PHP: URL that has directory structure but runs script with parameters"
date: 2006-01-19
forum: Programming Talk
---

### Post by me3ohm on 2006-01-19
Hi,

I have seen a PHP script that uses a directory structure in the URL but actually runs a script and then passes the rest of the directory script as variables.

I can't remember how it was done and I really want to use this feature!

for example:

[http://example.com/new/phone/BT](http://example.com/new/phone/BT) would run new.php and pass phone and BT into the POST variable. 

Any ideas?

Thanks

Matthew

---

### Post by john_spiral on 2006-01-19
Hi,

there might be a beter way of doing this, but here is my 2 cents:

have a look at the below page:

[http://uk2.php.net/basename](http://uk2.php.net/basename)

looks like the the basename function might be able to do it's magic.

---

### Post by sapo on 2006-01-20
This isnt php, its the apache mod rewrite, just google it :)

---

### Post by me3ohm on 2006-01-27
Thanks very much for all your help :-D

---

