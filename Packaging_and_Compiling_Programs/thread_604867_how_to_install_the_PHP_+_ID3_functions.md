---
title: "how to install the PHP + ID3 functions"
date: 2007-11-06
forum: Packaging and Compiling Programs
---

### Post by cmancre on 2007-11-06
Hi. I don't know if here's the best place to post this. Anyway...

I'm trying to work with the php id3 functions
[http://pt2.php.net/manual/en/ref.id3.php](http://pt2.php.net/manual/en/ref.id3.php)

I did a apt-cache search id3 | grep php and there is a package named php-getid3. I thought this was sufficient but isn't, the id3 functions still unrecognizable.

Or, do I really need to follow the pear extentions? 

Need a little help here please.

ps: i already reload the apache2 :lolflag:

---

### Post by jonathanmotes on 2008-12-14
I'm trying to figure this out as well. Anyone know how to do it? I'm hoping there is a package so that I don't have to compile it.

Thanks!

---

### Post by mkrahmeh on 2008-12-14
i dont know much about php but did you install the script (getid3) ?? since packages found in the cache doz not necessarily mean that the package is installed on your machine..

you may inquire the package found in the apt-cache 
```
apt-cache show php-getid3
```
and the description shows a homepage for this package
[http://www.getid3.org/]("http://www.getid3.org/")
this might help

---

