---
title: "Ubuntu WIKI/Web site software?"
date: 2005-11-09
forum: Programming Talk
---

### Post by Michael Matthews on 2005-11-09
What software is used for Ubuntu WIKI, web site? I have looked for days for a clue.
Or is it all custom developed? I am looking for WIKI/Project software for my work.

TIA

---

### Post by DJ_Max on 2005-11-09
That would be the [Zope](http://zope.org) framework using [Plone](http://plone.org) CMS. I believe [MoinMoin](http://moinmoin.wikiwikiweb.de/) Wiki (they switched around back and forth between wiki's) All written in Python.

---

### Post by 23meg on 2005-11-09
If it's not MoinMoin it's probably hand coded. Take a look at [this page]("http://c2.com/cgi/wiki?WikiEngines") on the c2 wiki (the first wiki known to exist) for an almost exhaustive list of wiki engines.

---

### Post by Drain on 2005-11-09
If you're looking for a more "simple" piece of software, I believe Ubuntu has packaged [WordPress]("http://wordpress.org/"), which is a pretty nice blog platform.  It's probably not what you're looking for, but I'd figure I'd plug it anyway. :-)

---

### Post by simon w on 2005-11-10
Mediawiki and dokuwiki are more relevant applications that use PHP

---

### Post by az on 2005-11-10
[QUOTE=simon w]Mediawiki and dokuwiki are more relevant applications that use PHP[/QUOTE]

[https://wiki.ubuntu.com/wiki/credits](https://wiki.ubuntu.com/wiki/credits)
This wiki system is powered by  Ubuntu,  Python and  MoinMoin. 


I think the point in using moinmoin is to avoid php.

---

### Post by newbie2 on 2005-11-10
[QUOTE=azz][https://wiki.ubuntu.com/wiki/credits](https://wiki.ubuntu.com/wiki/credits)
This wiki system is powered by  Ubuntu,  Python and  MoinMoin. 


I think the point in using moinmoin is to avoid php.[/QUOTE]
IS there a point in avoiding php?...according this indexes , php has a lot of 'users' --> [http://www.php.net/usage.php](http://www.php.net/usage.php)
[http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm)

---

### Post by DJ_Max on 2005-11-10
So does Windows.... The point in avoiding PHP aside from any technical inferiorities, is to use something different.

---

### Post by newbie2 on 2005-11-10
[QUOTE=DJ_Max]So does Windows.... The point in avoiding PHP aside from any technical inferiorities, is to use something different.[/QUOTE]
so...php is inferior to python...why does open university chooses moodle,which is a php cms isn't it?... just curious... :???: 
[http://moodle.org/mod/forum/discuss.php?d=34002](http://moodle.org/mod/forum/discuss.php?d=34002)

---

### Post by DJ_Max on 2005-11-10
[QUOTE=newbie2]so...php is inferior to python...why does open university chooses moodle,which is a php cms isn't it?... just curious... :???: 
[http://moodle.org/mod/forum/discuss.php?d=34002](http://moodle.org/mod/forum/discuss.php?d=34002)[/QUOTE]
I don't know, one would have to ask them. I'm guessing moodle meets their needs. Asking that question is asking why Google uses Python extensively, or Sony uses ASP.NET written forums.

BTW, I never said PHP was inferior to Python. I just mention I won't go over the things Python has over PHP, or vice versa.

---

### Post by mattheweast on 2005-11-10
As many people have pointed out, the Ubuntu wiki is run by MoinMoin software and the website is run on Plone, soon the website will be switching to MoinMoin too, which is actually pretty good as a content management system :)

php is not run on any core Ubuntu servers because of security considerations (I don't know much about that though).

---

### Post by newbie2 on 2005-11-10
.my mistake...sorry...messed up with this message...but don't know how to delete it...the edit/delete button doesn't work here?

---

### Post by az on 2005-11-10
[http://lists.ubuntu.com/archives/ubuntu-doc/2005-April/001753.html](http://lists.ubuntu.com/archives/ubuntu-doc/2005-April/001753.html)

[http://lists.ubuntu.com/archives/ubuntu-doc/2005-April/001763.html](http://lists.ubuntu.com/archives/ubuntu-doc/2005-April/001763.html)

---

