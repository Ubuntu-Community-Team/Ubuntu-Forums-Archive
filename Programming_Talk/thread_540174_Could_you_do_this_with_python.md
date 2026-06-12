---
title: "Could you do this with python?"
date: 2007-09-01
forum: Programming Talk
---

### Post by triptoe on 2007-09-01
Just curious.. I have this idea.. say you order from various websites.. maybe 10 different sites and you order different things from each of them. Say you saved your ordering information like shipping address, billing address and information.. to some file to use to interact with each site.

How hard would it be to have a program that interacted with each site you ordered from, used the information you supplied.. and the only input necessary would be the item you wanted to order.

I assume since many websites are different you would need to build up a template or database on how to order from each site individually... but how hard would that be? 

In this way you could automate your ordering and schedule it on certain dates.. nad have it automatically reorder things you needed...

Just curious if anyone has any kidn of experience.

---

### Post by pmasiar on 2007-09-01
yes, it is possible, but not simple.

Recently even module for screenscraping was released, which compares two pages from same site and separate common parts and variable parts.

---

### Post by scooper on 2007-09-01
It's a pain, primarily because the format of the data is not designed for machine interpretation.  It may not have a regular or predictable format, and the format will evolve over time.  I see it as a solution strategy of last resort.  The best way is to find a legitimate API or some other form of access, like an XML file, preferably with a schema.

That said, the difficulty of scraping data from web sites varies greatly.  Some sites have simple structures and plain old regular expressions can find and extract what you need.  Other sites have amazingly nested structures of tables and div blocks that can drive you crazy.

---

### Post by nanotube on 2007-09-02
well, if you use the Browser class from the mechanize module, it should be pretty easy. [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)

i've used it myself a few times when i needed to automate some web browsing. check it out. the documentation is pretty decent, the code is easy to build.

ask if you have questions while you're working on it. :)

---

