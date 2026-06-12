---
title: "Changing index page to something other than index.html in Apache"
date: 2011-12-24
forum: Programming Talk
---

### Post by Orcris on 2011-12-24
In Apache, I want to make my index page index.php instead of index.html. I can't find any good help on Google, so how do I do this?

---

### Post by Bachstelze on 2011-12-24
It should be done automatically when you install the PHP module. Do you have it installed?

---

### Post by Lars Noodén on 2011-12-24
Take a look at the [DirectoryIndex](http://httpd.apache.org/docs/2.3/mod/mod_dir.html#directoryindex) configuration directive.  You can add index.php to the list.

---

### Post by joshp1 on 2011-12-26
to change anything in Apache you have to edit the .htaccess file to make another default page aka index.html. If you have php installed on the server it's already done

DirectoryIndex filename.html
or
filename.php, filename.jsp, filename.shtml, filename.pl, filename.py, or filename.rb, instead of filename.html

look up editing or writing .htaccess files

---

