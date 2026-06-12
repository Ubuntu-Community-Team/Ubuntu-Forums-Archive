---
title: "list function in perldl dos not work"
date: 2005-09-19
forum: Programming Talk
---

### Post by ked on 2005-09-19
Hopefully there are someone out there familiar with perldl (PDL) :)  The function 'l' is supposed to list the last commands on the perldl prompt.

_perldl> _l 10

should list the last 10 commands but what I get is 

_perldl> _l 10
Can't locate object method "GetHistory" via package "Term::ReadLine::Stub" at /usr/bin/perldl line 251, <STDIN> line 1.

I've searched both PDL and perls FAQ/forums/bugs databases but nothing's even close to my problem. :(

---

