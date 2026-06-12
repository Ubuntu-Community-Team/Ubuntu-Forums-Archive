---
title: "[SOLVED] When I change .html to .php the page wont be shown!"
date: 2008-09-18
forum: Programming Talk
---

### Post by gjoellee on 2008-09-18
Hi there! I was about to update my page to v.2.0 with a totally new theme etc... it is based on "CrystalX". However I need the website to be in php, but when I change the "index.html" to "index.php" (just renaming the file) and uploads it to the server it shows nothing!

When I rename it back to "index.html" and uploads it to the server the website suddenly shows again.

Please help...:)

I downloaded the tamplate form here: [http://www.oswd.org/design/preview/id/3465/](http://www.oswd.org/design/preview/id/3465/)


NOTE: I have added the file as a .txt file to this post

---

### Post by gjoellee on 2008-09-18
Two screenshots so you can see what I mean:)

---

### Post by LaRoza on 2008-09-18
Try using an absolute address when you put in the URI.

[http://domain.com/index.php](http://domain.com/index.php)

It could be the server doesn't automatically server index.php ;)

---

### Post by gjoellee on 2008-09-18
> **LaRoza said:**
> It could be the server doesn't automatically server index.php ;)

if there is anything it is that (quote), but I have been using .php before and had no problems. 

Using a server from [www.one.com](www.one.com)

---

### Post by egorgry on 2008-09-18
Does your webserver have php support?

put this in a file called php_info.php and point your browser to it. Make sure it has the proper permissions. 


```
<?php phpinfo() ?>
```

---

### Post by rlzyoner on 2008-09-18
I'd say its that your server doesnt support php

*Egorgry got there before me*

---

### Post by gjoellee on 2008-09-18
> **egorgry said:**
> Does your webserver have php support?

put this in a file called php_info.php and point your browser to it. Make sure it has the proper permissions. 


```
<?php phpinfo() ?>
```

[http://kshoster.net/abs.php](http://kshoster.net/abs.php) I am not sure where to look and what to look at

---

### Post by egorgry on 2008-09-18
Doesn't look like a server issue. I put index.html and index.php in after your domain name and I didn't get anything. Does your site use a CMS that ties into a mysql db or something? could it be a the database?

---

### Post by gjoellee on 2008-09-18
> **egorgry said:**
> Doesn't look like a server issue. I put index.html and index.php in after your domain name and I didn't get anything. Does your site use a CMS that ties into a mysql db or something? could it be a the database?

[http://kshoster.net/index.html](http://kshoster.net/index.html) is uploaded now:)
[http://kshoster.net/index.php](http://kshoster.net/index.php) is not working
(none of the pages contains anything actually)

I am not using CMS or MySQL

---

### Post by egorgry on 2008-09-18
are both the php and html file in the www root directory? I've seen that cause issues. If so mv index.html index.html.orig and leave the index.php in place.

---

### Post by gjoellee on 2008-09-18
> **egorgry said:**
> are both the php and html file in the www root directory? I've seen that cause issues. If so mv index.html index.html.orig and leave the index.php in place.

still the same problem....

---

### Post by adcwoef on 2008-09-18
It works now. What did you do?

---

### Post by gjoellee on 2008-09-18
I made a new template. Thread solved

---

### Post by simz on 2008-09-26
It was the xml start (<?) and end (?>) tags that caused the issue. The server was set to accept short-tags.

-simz

---

