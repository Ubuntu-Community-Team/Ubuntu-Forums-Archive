---
title: "Best way to write modular software"
date: 2007-10-18
forum: Programming Talk
---

### Post by sapo on 2007-10-18
Hi,

We have a serious problem here which we are trying to solve because it's adding way too much complexity to our softwares.

We are a small company with 4 programmers and 4 distinct softwares written in delphi, using 3-tier architecture (using remobjects components).

The problem is that the 4 softwares are almost completelly written from scratch, and none is modular, so we have a lot of duplicate stuff, i.e. we have 4 distinct customers forms, 4 distinct customers table, etc.

This is a pain to maintain, because sometimes we need to change something or add something and we have to change 4 distinct source codes.

And we don't have any clues how to make our systems modular, in fact we don't even know where to start, we want to do something like a plugin system, that can be plugged and taken off without breaking everything.

Does anyone here knows how to do it? Or maybe advice me some book to read, anyway any help is welcome.

Thanx

---

### Post by ankursethi on 2007-10-18
I don't know how Delphi plays with other programming languages, but I guess you could build some kind of API that could then be used with something like Python, Ruby or Lua. Many (most?) OSS projects do this, including Blender, OpenOffice and even GNOME itself.

Ignore me, by all means. I'm not a software developer :)

---

### Post by slavik on 2007-10-18
use a database?

---

### Post by sapo on 2007-10-18
I think I didn't expressed myself clearly, I don't want to plug module at runtime, I just want to make just one module and then reuse it in all my softwares.

We do it with some forms and use inheritance, but the problem is with things that depend on a database, also all the databases have different table structures.

---

### Post by pmasiar on 2007-10-18
Some adult around need to start managing you projects :-)

To make them using same common libraries, you will ned to refactor the code, which is pain if you don't have good tests to make sure your changes did not break functionality, which I guess you don't. 

My bet would be: learn about better practices (hire someone who knows how to program in teams), and your next code do right way. Changing old code will be very painfull and expensive. You have real problem.

---

### Post by Quikee on 2007-10-18
> We do it with some forms and use inheritance, but the problem is with things that depend on a database, also all the databases have different table structures.

With a proper O/R mapping framework you are more transparent to things like that. You let the O/R mapping framework do the database stuff - all you care about now are objects.  

You can also look at resources about [SOA (Service Oriented Architecture]("http://en.wikipedia.org/wiki/Service-oriented_architecture") which is getting more popular every day and it promotes modularity. 

In the end you will have to look at and rework the architecture of your program and abstract and divide responsibility (of objects) as much as possible.

---

