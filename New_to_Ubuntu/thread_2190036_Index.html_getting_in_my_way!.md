---
title: "Index.html getting in my way!"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by nick.kendall on 2013-11-25
Hi all, 

I'm hoping there's an Ubuntu / Apache expert out there that can help. I've created a wiki site on our Ubuntu 12.04 server, it's located in /var/www/wiki-new/ and has the main page of index.php.

How can i get it so that the index.php page within that folder is shown when you browse to the server name or ip address. At the moment all I'm getting is the standard Apache "It works" index.html page. If i browse to the full URL of the server, including the file destination ([http://server/wiki-new/index.php](http://server/wiki-new/index.php)) it displays ok, but i want to be able to do [http://server](http://server). 

I've edited the httpd.conf and the dir.conf files to include this line - DirectoryIndex /var/www/wiki-new/index.php - and have also tried creating a htaccess file in the www folder with this line - Redirect permanent /index.html /wiki-new/index.php - but to no avail.

Any help would be really gratefully received.

Many thanks

---

### Post by Lars Noodén on 2013-11-25
Shouldn't you move the index.html file first?  Then also you have you added a line in the configuration for [DirectoryIndex](http://httpd.apache.org/docs/2.4/mod/mod_dir.html#directoryindex) which includes *index.php*?

```

<Directory /var/www/wiki-new>
    DirectoryIndex index.html
    DirectoryIndex index.php
</Directory>

```

---

### Post by nick.kendall on 2013-11-25
Thanks for the reply, I've managed to fix the problem by editing the index.html to redirect to the correct url. It's a bodge but it works!!

Thanks anyway

---

