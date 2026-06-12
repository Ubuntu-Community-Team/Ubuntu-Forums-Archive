---
title: "Source code management help"
date: 2009-10-21
forum: Programming Talk
---

### Post by icodemonkey on 2009-10-21
In the 15 years I have been coding for I have (and I'm sure a great many of you are in the same boat) collected a huge amount of source code, snippets, library's and HOWTOs.  
 now its getting hard to find a piece of code from amongst the thousands of files I have organised in a B.S.D.S. (Big Scary Directory Structure), I have tried a lot of solutions but have found none that fit my need:  
     *portable.
     *easy to navigate.
     *easy to edit. (add, delete and edit)
     *easy import of files.
 

 My question for the other codemonkeys out there is....
 

 what app, method or system do you use to organise your source code library?

---

### Post by hessiess on 2009-10-21
Just subversion + thunar

---

### Post by icodemonkey on 2009-10-21
> **hessiess said:**
> Just subversion + thunar
how portable is that system ie can it run off off a thumb drive / portable HDD?

---

### Post by hessiess on 2009-10-21
> **icodemonkey said:**
> how portable is that system ie can it run off off a thumb drive / portable HDD?

Subversion is mostly server side, but you need a client for it. All of the SVN clients I have found for Windows use the registry, which means that it may not run in a less privileged account. Thunar is just a file manager and can be substituted with Nartulas/ Explorer/Finder etc.

Git has poor support for Windows, both bzr and Mercurial are written in python, which would be a problem unless you can get the python interpreter running off an external drive. Darcs might work if you can Haskell to compile it statically.

---

### Post by myrtle1908 on 2009-10-21
Can't you simply place a CVS repo on a USB stick and check-in/check-out from home, work wherever.  Fairly certain I did this many moons ago but have forgotten the details.

---

