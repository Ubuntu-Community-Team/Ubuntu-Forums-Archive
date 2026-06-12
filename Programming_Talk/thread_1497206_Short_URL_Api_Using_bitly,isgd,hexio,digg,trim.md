---
title: "Short URL Api Using bitly,isgd,hexio,digg,trim"
date: 2010-05-30
forum: Programming Talk
---

### Post by astkboy2008 on 2010-05-30
Short URL is commonly used today for several reasons: **avoid  url garbling**, take smallest space especially for long url which  need to be posted at limited space format eg: twitter, also often used  to manipulate user for specific purposes eg: hiding orginal url for  phising and ads/affiliation links.
There are many websites that provide shortening url services, **tinyurl**,  **bit.ly**, **hex.io** are some of them, and  as addition to my simple twitter, plurk and facebook api implementation,  i have created a PHP script to create short url on the fly, currently  support: tinyURL, bit.ly, is.gd, tr.im and hex.io, but you can easily  add other providers.
**how i can use this api**?
its very easy but first you should add this class in your includes [short-url class.php]("http://www.jooria.com/view/file/466/short-url%20class.php")
now for example after include the class you have to doing some thing like this
[PHP]echo ShortUrl::create("http://www.codingforums.com/",'tinyurl')[/PHP]
and you can see this simple demo [sample.php]("http://www.jooria.com/view/file/466/sample.php")
[PHP]<?php

$url = 'http://codingforums.com';
echo ShortUrl::create($url,'trim');
echo '<hr />';
echo ShortUrl::create($url,'tinyurl');
echo '<hr />';
echo ShortUrl::create($url,'isgd');
echo '<hr />';
echo ShortUrl::create($url,'hexio');
echo '<hr />';
echo ShortUrl::create($url,'bitly','your_user_name','your_api_key');
?>
[/PHP]

---

### Post by diesch on 2010-05-30
*tr.im* doesn't work anymore, and *hex.io* seems to have some problems with its blacklist.

This services work similar to *is.gd*: 

```
    '7ax.de': 'http://7ax.de/api.php?url=%s',
    'fa.by': 'http://fa.by/?module=ShortURL&file=Add&mode=API&url=%s',
    'migre.me': 'http://migre.me/api.txt?url=%s',
    'rod.gs': 'http://rod.gs/?longurl=%s',
    'urlg.in': 'http://urlg.in/yourls-api.php?action=shorturl&format=simple&url=%s',

```

---

### Post by astkboy2008 on 2010-05-31
mmmmmmm let me check it and fix

---

