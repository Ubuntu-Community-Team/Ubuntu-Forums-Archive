---
title: "c# and linux"
date: 2006-04-27
forum: Programming Talk
---

### Post by malavar on 2006-04-27
hey i was wondering what you guys think about c# and linux. i have a book called "Programming C#" published by "oreilly". the author says the book is focused on c# and the .NET platform BUT also goes on to state: "You learn c# specifically to create .NET applications. someone please tell me what i am missing... if c# and linux are even a worthwhile combo.

---

### Post by kostkon on 2006-04-27
[QUOTE=malavar]someone please tell me what i am missing... if c# and linux are even a worthwhile combo.[/QUOTE]

Of course, they are a good combo. There is the Mono Project specifically for running and developing .NET applications on Linux.

[http://www.mono-project.com/Main_Page]("http://www.mono-project.com/Main_Page")

---

### Post by malavar on 2006-04-27
ok thanks for the quick reply, i have mono installed :) now i guess ill begin studying the book.

---

### Post by lnostdal on 2006-04-27
hm, - i'm thinking; what happens if MS wants to f**k everything up and sue Novell/Mono for some retarded patent-thing? :rolleyes:

edit:
..or what if they "embrace and extend" their implementation of the standards, so nothing really is portable after all?   (like "MS Java" in 1996-8 )

---

### Post by MojoX on 2006-04-28
[QUOTE=lnostdal]hm, - i'm thinking; what happens if MS wants to f**k everything up and sue Novell/Mono for some retarded patent-thing? :rolleyes:

edit:
..or what if they "embrace and extend" their implementation of the standards, so nothing really is portable after all?   (like "MS Java" in 1996-8 )[/QUOTE]
The patent thing seems like a decent question.  Novel did a patent review in 2004; I don't know what the outcome was, but the Open Invention Network was founded in 2005 to allow free software projects to have a defensive patent strategy.  With Mono, it seems, in general, it is as exposed to patent threats as any other project (especially when you consider things like [this]("http://www.ipww.com/display.php/file=/texts/0506/venture")). However, in my well-underinformed opinion, specifically related to the .NET compatibility (ie. the stuff not in the standard), Mono might face more of a threat.  They would likely have to drop that stack if anything went down.  (But I really don't know for sure. Maybe one of the Mono experts here will.)  Even if they dropped that stack, for those in the free and open source software world, Mono will still be more than useful.

That brings us to your second point.  *When* MS *further* embraces and extends the standard, it won't really matter for the free software world.  Mono provides good tools.  That is good enough.  IMO, people should just code and be happy.  Preferably, IMHO, using free culture innovations, like Python, Perl, Ruby, etc.

At any rate, while Mono is good technology, the free software world seems to be closing in on some real alternatives to .NET and Java.  I find [Parrot]("http://www.parrotcode.org/") an interesting multi-language VM and can't wait to see how Ruby 2.0 and Rite ([YARV]("http://www.atdot.net/yarv/")?) turn out... whenever that will be.  It'd be great to see Parrot really take off.

**edit:** corrected date typo.

---

