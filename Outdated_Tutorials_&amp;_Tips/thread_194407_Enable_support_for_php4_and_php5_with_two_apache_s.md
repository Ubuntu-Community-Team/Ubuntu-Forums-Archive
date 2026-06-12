---
title: "Enable support for php4 and php5 with two apache server"
date: 2006-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by merinda on 2006-06-11
I likes php5 better than php4. So I installed it right away:
apt-get install php5 apache2-mpm-prefork

But I have to install php4 in order to do web development. My client hosts his web in web hosting which supports php4 only. But I do not want to remove my php5. So here is the way to enable both of them:
apt-get install php4 apache

After that you have to edit these files:
**/etc/apache/httpd.conf**
Uncomment this line:
      *AddType application/x-httpd-php .php*
and this:
      *Listen 3000*
But I use port 3000 ( ruby on rails ) however, so I change it to:
      *Listen 2999*

**/etc/apache/modules.conf**
Add this line:
      *LoadModule php4_module /usr/lib/apache/1.3/libphp4.so*

You're done. To test it, make this file:
[PHP]
<?php
// file: /var/www/test.php

phpinfo();

?>
[/PHP]

and put it in /var/www/.

Start the apache2 server for php5:
/etc/init.d/apache2 start

And start the apache 1.3 server for php4:
/etc/init.d/apache start

Use your browser to open this url:
[http://localhost/test.php](http://localhost/test.php) 
[http://localhost:2999/test.php](http://localhost:2999/test.php)

There is another alternative. Use one apache server only. One php as apache module, another as cgi binary. But I don't like this alternative because you have to use extension beside than .php. For example, to use php4 you use extension .php4 and to use php5 you use extension .php. Or vice versa. I don't like it because I do my web development work with php4 using php framework. I don't want to change all php files extension inside that framework to .php4.

Tested on Dapper Drake.

---

### Post by CalvinChile on 2006-07-28
Hi Merinda,

I did as you explained but every time I try to open a php file, the broser try to download the file...  Any idea?

If I stop apache2 and only start apache, then [http://localhost](http://localhost) doesn't load properly on the browser, but the other way around the page displays fine but still php files doesn't show up.

Thanks
Calvin

---

### Post by merinda on 2006-07-31
Are you saying that after starting apache2 when you try to open php file, the browser try to download it?
if yes, where do you save your php file and what url you use to access this file in browser?

yeah, I have an idea.

---

### Post by adamkane on 2006-07-31
Apache2 With php5 and php4:
[http://www.howtoforge.com/apache2_with_php5_and_php4](http://www.howtoforge.com/apache2_with_php5_and_php4)

---

