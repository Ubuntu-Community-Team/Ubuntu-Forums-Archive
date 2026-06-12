---
title: "Tutorial On GNU Development Tool (automake, configure......)"
date: 2005-06-25
forum: Programming Talk
---

### Post by yccheok on 2005-06-25
Hi, currently I have a software project which I would like to develop using GUI too. So that user can install it using ./configure, make, make install. However, I have no knowledge on those tools in generating the Makefile and configure file, can anyone recommance me sites to do some reading?

Thanks.

---

### Post by word_virus on 2005-06-25
[QUOTE=yccheok]Hi, currently I have a software project which I would like to develop using GUI too. So that user can install it using ./configure, make, make install. However, I have no knowledge on those tools in generating the Makefile and configure file, can anyone recommance me sites to do some reading?

Thanks.[/QUOTE]

I think O'Reilly's got a book on this that's pretty good.  Also there's an article over at IBM DeveloperWorks that goes into detail about what happens when you use these tools to compile and install software that may prove to be illuminating, you may need to create an account on their site before you can access the material, though.  I first learned how to generate a (very simple) Makefile using a tutorial on the MSYS subsystem, which you should be able to find with some light googling.

I think you can also go straight to the source on this and download the Automake manual from gnu.org, but this may prove to be total overkill if you just want to get started and not learn all the intricacies of the system.


Oh, and here's a freebie:
[http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/)

that's probably a good start.

---

### Post by dcraven on 2005-06-25
In my opinion, the best way to get your project working with the GNU autotools is to look at other projects that use it. Look for a project that has similar requirements and specs as yours, and have a look at the source.

Cheers,
~djc

---

### Post by buffbikedude on 2005-06-26
> Oh, and here's a freebie:
[http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/) 

I am reading that book. "The goat book", I think it's called.

The place where I work has official support for three platforms - SuSE 9.0, Solaris, and Mac OS X 10.3. Any other UNIX thing is a pain in the butt. I am just a new developer there, but I hope to get them switched over to autoconf and automake.

---

### Post by oldmarti on 2005-06-27
Check this link. I think, there is enough information to start quickly using autotools:

[http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/dl/autotools.pdf](http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/dl/autotools.pdf)

Good luck!

---

