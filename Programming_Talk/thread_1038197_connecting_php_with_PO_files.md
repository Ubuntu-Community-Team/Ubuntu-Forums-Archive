---
title: "connecting php with PO files"
date: 2009-01-12
forum: Programming Talk
---

### Post by Uchiha_madara on 2009-01-12
Hi every one ,

i am working on translating a website by using 
php5 and po and mo Files ......

My Questions is : i need tutorial's or somebody tell how to [COLOR="SeaGreen"][B][SIZE="5"]connect the "MO" or "PO" files with php by using "gettext()"
function........[/SIZE][/B][/COLOR]
:popcorn:

---

### Post by drubin on 2009-01-12
I assume you are working with the gettext plugin/module for php...

[http://www.php.net/gettext](http://www.php.net/gettext) 
[http://mel.melaxis.com/devblog/2005/08/06/localizing-php-web-sites-using-gettext/](http://mel.melaxis.com/devblog/2005/08/06/localizing-php-web-sites-using-gettext/)

Those might be a start.

Ps was that huge font/color really necessary?

---

### Post by Uchiha_madara on 2009-02-03
i faced a fatal error that : 

> you called undefined function bindtextdomain() in localization.php line :4 .

---

### Post by drubin on 2009-02-03
That error means the function doesn't exist. you are trying to use it in your localization.php on line 4. ie look there.

Please also read the link in my sig for how to ask questions. You will get far more productive responses if you provide more details.

---

### Post by Uchiha_madara on 2009-02-21
> **drubin said:**
> That error means the function doesn't exist. you are trying to use it in your localization.php on line 4. ie look there.

Please also read the link in my sig for how to ask questions. You will get far more productive responses if you provide more details.

I slove it .....

the probelm is : is an error in Wamp server i have un installed it and use Xampp server ........

and the connection is succeeded ...

and the translation is done...


but, there is anther question is .....

what is the deference between the gettext() function and the plural form "ngettext()" function ...

and how can i use it.

---

### Post by drubin on 2009-02-21
[http://www.php.net/ngettext](http://www.php.net/ngettext)
[http://www.php.net/manual/en/function.gettext.php](http://www.php.net/manual/en/function.gettext.php)

The on it used for plurals.(ngettext) That is as far as I can help.

---

