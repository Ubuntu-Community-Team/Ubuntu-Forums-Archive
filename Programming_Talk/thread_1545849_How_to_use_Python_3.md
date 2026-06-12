---
title: "How to use Python 3?"
date: 2010-08-04
forum: Programming Talk
---

### Post by genjix on 2010-08-04
None of the external packages work for Python 3 under lucid. Python 3 is big improvement over Python 2... Is there anyway to get them to work?

When is Ubuntu going to drop Python 2 and get with the times?

---

### Post by Bachstelze on 2010-08-04
> **genjix said:**
> 
When is Ubuntu going to drop Python 2 and get with the times?

Ubuntu uses Python for *a lot* of things, and in case you didn't know, *a lot* of third-party modules have not been ported to Python 3 yet.

```
sudo apt-get install python3
python3
```

---

### Post by Queue29 on 2010-08-04
> **genjix said:**
> 
When is Ubuntu going to drop Python 2 and get with the times?

When everybody else ports their apps to Python3. Ubuntu doesn't actually write the software it packages, it just repackages it all. 

Arch on the other hand is currently porting things to work with Python3:

[http://wiki.archlinux.org/index.php/DeveloperWiki:Python_Todo_List](http://wiki.archlinux.org/index.php/DeveloperWiki:Python_Todo_List)

---

### Post by HoKaze on 2010-08-04
It would be nice if Ubuntu updated to Python 2.7 as this will continue to be supported for quite some time and is the last release in the 2x series in addition to offering Python 3, which will slowly but surely eventually get adopted but in the meantime far too many apps rely on python 2.6 (or older!) and people are still using 2.6 and 2.7 for the sake of compatibility. 
It should also be noted that python 3 hasn't been ported to as many platforms as 2 has, which may also be a factor worth mentioning. People will go to the new version in due time and due course, mass migration is rarely ever a fast thing when it comes to software...I mean, just look at all the people still using Windows XP despite that now being about 9 years old if memory serves?

---

### Post by interval1066 on 2010-08-04
The amount of crap, er, apps, written in python is staggering, Canonical would do well to get to that final 2.x version in the name of compatibility.

---

### Post by genjix on 2010-08-05
well is there anyway to extend Python 3 using C++? How can I get Cython or boost-python working with Python 3?

Having just access to 'math' and 'sys' is a bit limiting after a while :p Shame as Python 3 is ****ing fantastic in everyway that my head spins

---

### Post by genjix on 2010-08-09
like at the moment I have python 3 installed which is a great language but it has ZERO modules. that's hardly useful at all.

how can I get a non-crippled python 3? maybe ubuntu maintainers should consider packages for python 3 also or for them to also install their py3 counterparts...

---

### Post by Bachstelze on 2010-08-10
> **genjix said:**
> 
how can I get a non-crippled python 3?

Grab the source for the modules you want and port them to Python 3.

---

### Post by ssam on 2010-08-10
there are still a few big modules holding up mass migration.
pygtk/pygobject - this is being worked on heavily. eg see [http://live.gnome.org/Hackfests/Python2010](http://live.gnome.org/Hackfests/Python2010)

numpy/scipy - quite a few things use numpy. they are nearly there [http://projects.scipy.org/numpy/ticket/1520#comment:1](http://projects.scipy.org/numpy/ticket/1520#comment:1)

once these are done i'd expect a flood of porting.

---

### Post by genjix on 2010-08-10
well I was able to easily build Cython from source with no problems against Python 3.

Surely Ubuntu should first concentrate on releasing a Cython-Python 3 compatible package first so that we have all the packages depending on Cython working, and gain the ability to extend python yourself.

---

### Post by Bachstelze on 2010-08-10
> **genjix said:**
> well I was able to easily build Cython from source with no problems against Python 3.

Awesome! I'm waiting for your packages. :)

---

### Post by genjix on 2010-08-10
How do I make a package? Will it be in Ubuntu? (I'd rather not spend days to make a package and have it not used :p)

---

### Post by arminbw on 2011-01-20
deleted

---

### Post by arminbw on 2011-01-20
> **genjix said:**
> How do I make a package? Will it be in Ubuntu? (I'd rather not spend days to make a package and have it not used :p)

Just tried to use your pyosc cython thing on Ludic Lynx. A nice package would be neat indeed.

---

