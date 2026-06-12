---
title: "search and replace with sed"
date: 2009-09-07
forum: Programming Talk
---

### Post by aliahsan81 on 2009-09-07
Hi all i have file i want to to do search and replace

search this
"/var/www/dev01/example/joomlacms/components"

And replace with

"/home/example/public_html/joomlacms/components"

but problem is that like i have  many directories 

"/var/www/dev01/example/abc"
"/var/www/dev01/example/php"
"/var/www/dev01/example/new"

i want in one search to do 

"/home/example/public_html/example/abc"
"/home/example/public_html/example/php"
"/home/example/public_html/example/new"

Can some one help me out.Common part is example in search and replace

---

### Post by DaithiF on 2009-09-07
Hi,
> 
"/var/www/dev01/example/abc"
"/var/www/dev01/example/php"
"/var/www/dev01/example/new"

i want in one search to do 

"/home/example/public_html/example/abc"
"/home/example/public_html/example/php"
"/home/example/public_html/example/new"
```
sed 's#/var/www/dev01#/home/example/public_html#' somefile > somefile.new
```

---

### Post by aliahsan81 on 2009-09-07
thanks

---

