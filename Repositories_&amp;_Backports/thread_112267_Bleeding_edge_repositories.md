---
title: "Bleeding edge repositories?"
date: 2006-01-04
forum: Repositories &amp; Backports
---

### Post by sowdog on 2006-01-04
Is there anything like a debian unstable repository? Bleeding edge for hoary ? I don't want to upgrade to dapper. Just a few apps like firefox,gaim and such?

---

### Post by 23meg on 2006-01-04
Nothing quite like Sid but there's backports. 

[http://backports.ubuntuforums.org/wiki/index.php/Main_Page](http://backports.ubuntuforums.org/wiki/index.php/Main_Page)

---

### Post by sowdog on 2006-01-04
Hum, backports doesn't seem as up to date either. Is there a sort of unofficial community maintained repository?

Btw, thanks for the prompt reply

---

### Post by Kyral on 2006-01-04
Dapper contains the bleeding edge as we sync from Sid. But watchout, Dapper is still development so things will break on you

Oh to answer the question of Firefox. Ubuntu depends on Firefox a lot more than other distros. A lot of things depend on Firefox for HTML/XML stuffs, so it affects a lot of packages

EDIT: Didn't see that you didn't want to not jump to Dapper.

---

### Post by Velvet Elvis on 2006-01-04
It's fairly easy to backport packages for your own use from dapper sources.

1. set your source repos in /etc/apt/sources.list to dapper.

```
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
```

2. sudo apt-get update
3. sudo apt-get build-dep, enter Y when prompted
4. apt-get source <packagename>
5. cd to the new source dir in your /home directory
6. sudo dpkg-buildpachage
7. cd ..
8. sudo dpkg -i *.deb

You're most likely to run into problems at #3.  If depends can't be met it's possiable to backport libraries to meet build deps, but it's not the best idea.

If you want to live dangerously, check out apt-build:

[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

---

### Post by sowdog on 2006-01-04
Is there an alternative that doesn't require dapper? I'd like something like backports or PLF but with more packages? I know , I'm geredy :razz:

---

### Post by az on 2006-01-04
With a six-month release, there is not a lot of room between backports and Dapper.

You know, you can always try to add the Dapper repo and apt-get install the one or two paclages that interst you.  You shouldn't bork your system up as much as if you dist-upgraded to Dapper.  Just like running a testing-Sid hybrid with debian (liek we all did before Ubuntu ;) ).

---

### Post by sowdog on 2006-01-06
[QUOTE=azz]With a six-month release, there is not a lot of room between backports and Dapper.

You know, you can always try to add the Dapper repo and apt-get install the one or two paclages that interst you.  You shouldn't bork your system up as much as if you dist-upgraded to Dapper.  Just like running a testing-Sid hybrid with debian (liek we all did before Ubuntu ;) ).[/QUOTE]

Tried to do that, but apt asked if i wanted to uninstall this huge heap of packages. Quickly chickened out. It's just the idea of waiting 4 more months till I get to update firefox and gaim :D

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=sowdog]Tried to do that, but apt asked if i wanted to uninstall this huge heap of packages. Quickly chickened out. It's just the idea of waiting 4 more months till I get to update firefox and gaim :D[/QUOTE]

Use Automatix to get new Firefox.

---

### Post by sowdog on 2006-01-06
Thanks poofyhairyguy. Very interesting app. :D

---

