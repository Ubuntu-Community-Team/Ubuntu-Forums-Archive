---
title: "next step in C++"
date: 2012-07-25
forum: Programming Talk
---

### Post by Lymphocyte on 2012-07-25
so i got the basics of C++ nailed down like OOP and the basic stuff like Loops, ifs, breaks, variables. What should i do next in C++? When would i be able to get into the good stuff like GUI building and stuff like that?

---

### Post by Hetepeperfan on 2012-07-25
> **Lymphocyte said:**
> so i got the basics of C++ nailed down like OOP and the basic stuff like Loops, ifs, breaks, variables. What should i do next in C++? When would i be able to get into the good stuff like GUI building and stuff like that?
 
you could get a look at gtk+ :
[http://www.gtk.org/](http://www.gtk.org/)
or qt
or clutter: [https://clutter-project.org/](https://clutter-project.org/)

or google for other stuff like that...

---

### Post by josephmills on 2012-07-25
I like QT

qt 
[http://www.youtube.com/watch?v=6KtOzh0StTc&feature=list_other&playnext=1&list=SP2D1942A4688E9D63](http://www.youtube.com/watch?v=6KtOzh0StTc&feature=list_other&playnext=1&list=SP2D1942A4688E9D63)

qtquick
[http://doc.qt.nokia.com/4.7-snapshot/qtbinding.html](http://doc.qt.nokia.com/4.7-snapshot/qtbinding.html)


hope this helps

---

### Post by trent.josephsen on 2012-07-25
Why would you want to build GUIs? :P

Nah, I'll never understand it...

---

### Post by dwhitney67 on 2012-07-26
> **Lymphocyte said:**
> so i got the basics of C++ nailed down like OOP and the basic stuff like Loops, ifs, breaks, variables. What should i do next in C++?
How about learn more C++ than just the basics?

I've been working on/off with C++ for years, and there is still some things that challenge me.  Why not learn about the Boost Library?  Or expand your knowledge of OOD (this is not the same as OOP -- which is cake.).

---

### Post by codemaniac on 2012-07-26
Get involved in gnome or kde development .
[http://developer.gnome.org/references#c++-bindings](http://developer.gnome.org/references#c++-bindings)

You can also subscibe to their mailing list to get to know more on this .

---

### Post by 3Miro on 2012-07-27
> **Lymphocyte said:**
> so i got the basics of C++ nailed down like OOP and the basic stuff like Loops, ifs, breaks, variables. What should i do next in C++? When would i be able to get into the good stuff like GUI building and stuff like that?

Did you learn pointer? Learn dynamic memory, if you haven't already. Then go into wither QT or GTK.

---

### Post by Some Penguin on 2012-07-28
Do more challenging things.

For instance, think about problems where the scale means that the most straightforward, naïve solution is suboptimal or perhaps not even feasible unless you've got a ridiculous budget.


One hypothetical example:  

Online processing of a large data stream.  Let's say that there's a server which provides a JSON-centric API atop a database, in order to abstract away such things as the actual implementation details -- e.g. there's no particular reason a client should care about the exact names of columns, or even whether the data is stored within a relational database like PostgreSQL, an old-school DBM-family system like Tokyo Cabinet, or a more modern key-value store like Cassandra or MongoDB.

Let's say that one request you might make will basically result in streaming 30GB of results to you -- a giant JSON array, where each individual result has been serialized as a JSON object within that array.  And you've got some processing you want to do on all of 'em.

Now, buffering the entire result and deserializing it all at once would in theory provide you with the appropriate structures (the details would have to depend on the JSON deserialization library you use -- maybe it'd return a giant array, maybe it'd use an STL vector, it's not terribly important).  But, unless you like having your memory requirements spike by well over 30GB (given that you'd need to hold both the entire result from the HTTP request, AND the deserialized data, if done in the most straightforward way... so we're probably talking substantially more!), this isn't a *good* solution and will often not be feasible at all (unless e.g. you run all the time on high-memory quadruple extra-large ec2 instances with 68GB RAM :D).  And depending on the processing required (maybe you're only computing an aggregate from the fields -- perhaps they're transaction data and all you want is sufficient statistics to estimate a well-fitting distribution to model the value of each transactions; whatever), it may be incredibly wasteful to do so.  And there are FAR better solutions that actually aren't difficult at all...

Now, nothing above is remotely C++ specific, and that's sort of my point -- you shouldn't worry too much about language features (although there IS some mostly-C++-specific stuff you can work with, like multiple inheritance, that you won't necessarily see often with other languages), but you should worry about how you'd use what you know to approach non-trivial problems.  Worry about objectives first, and then worry about language-specific stuff only when they're really relevant... because at the end of the day, the goal tends to be to have built some system or application and not just to improve language proficiency.

---

### Post by Lymphocyte on 2012-07-30
> **3Miro said:**
> Did you learn pointer? Learn dynamic memory, if you haven't already. Then go into wither QT or GTK.

yes i did =D

I know the new keyword and delete keyword pointers are a little fuzzy but i know to do handal it

---

