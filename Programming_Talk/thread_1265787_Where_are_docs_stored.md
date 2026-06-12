---
title: "Where are docs stored"
date: 2009-09-13
forum: Programming Talk
---

### Post by kehon on 2009-09-13
I used to know where they were once because I saw it on a website but I can't remember it and can't find them.

The Doc's I'm referring to are the lib*-dev for libraries such as boost-doc etc

---

### Post by Sgt-Slyde on 2009-09-13
I usually go to [http://www.boost.org/doc/libs/1_40_0/libs/libraries.htm](http://www.boost.org/doc/libs/1_40_0/libs/libraries.htm).  

I also ran a quick search and found a bunch of links here:

[http://fr2.rpmfind.net/linux/rpm2html/search.php?query=boost-doc](http://fr2.rpmfind.net/linux/rpm2html/search.php?query=boost-doc)

---

### Post by Can+~ on 2009-09-13
/usr/share/man
/usr/share/doc

If you're looking for the one particular to a package, read the contents with apt-cache and find where it dumped it.

---

### Post by kehon on 2009-09-13
sorry but that's not what I was talking about. 
I also use the docs from the boost site also.
What I'm talking about is when you install boost and other libraries, most of them install doc's also so that the library docs can be accessed off line.

---

### Post by Can+~ on 2009-09-13
You can see them directly on the /usr/share/doc, or, if you have DevHelp installed, you can see them directly (at least some of them under Programming > Devhelp).

Sample: [http://img.photobucket.com/albums/v517/CanXp/python/screenshot1.png](http://img.photobucket.com/albums/v517/CanXp/python/screenshot1.png)

---

### Post by kehon on 2009-09-13
thanks it was in /usr/share/doc
file:///usr/share/doc/libboost1.37-doc/
I was looking for the place where all the library docs were stored and that was it.
Thanks for both of your support.

---

