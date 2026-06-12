---
title: "The best free resources for learning Perl?"
date: 2009-04-24
forum: Programming Talk
---

### Post by reprobus on 2009-04-24
I am trying to learn perl. I found the free ebook "Beginning Perl" and the tutorial on perl.com, also a friend introduced me to the perldoc program and CPAN which are very useful. What free websites, ebooks, tutorials, etc do you guys recommend?

---

### Post by bapoumba on 2009-04-27
Moved to PT.

---

### Post by ghostdog74 on 2009-04-27
> **reprobus said:**
> I am trying to learn perl. I found the free ebook "Beginning Perl" and the tutorial on perl.com, also a friend introduced me to the perldoc program and CPAN which are very useful. What free websites, ebooks, tutorials, etc do you guys recommend?
straight from the Perl documentation. See my sig. Otherwise, on the command prompt (terminal) , type perldoc perl or perldoc perltoc.

---

### Post by tr333 on 2009-05-10
perldoc is definitely a good start; especially pages like [perlstyle](http://perldoc.perl.org/perlstyle.html).
Some more great perl resources:
[FMTEYEWTK](http://www.perl.com/doc/FMTEYEWTK/) by Tom Christiansen (Perl Cookbook); particularly his [style slides](http://www.perl.com/doc/FMTEYEWTK/style/slide-index.html).
The one and only [PerlMonks](http://www.perlmonks.org/).
[CPAN](http://cpan.org/) - the home of all perl modules/documentation.

Don't forget one thing about perl:  There's more than one way to do it!

---

### Post by khelben1979 on 2009-05-10
On [perlcast.com]("http://perlcast.com/") you have several perl podcasts. I'm downloading them myself right now.

---

### Post by unutbu on 2009-05-10
Perhaps your local library has "Programming Perl" by Larry Wall, Tom Christiansen and Jon Orwant. This is the best book I have ever read on Perl.
If your local library doesn't have it, don't forget to check interlibrary loan.

This book is also bundled in "The Perl CD Bookshelf" published by O'Reilly.

You can also download all the examples in the book here:
[http://examples.oreilly.com/pperl3/](http://examples.oreilly.com/pperl3/)

---

### Post by jimi_hendrix on 2009-05-10
the LaRoza's wiki (see stickie) has a good free book that you can download in pdf format

---

### Post by sujoy on 2009-05-10
also see this thread,
[http://stackoverflow.com/questions/194812/list-of-freely-available-programming-books](http://stackoverflow.com/questions/194812/list-of-freely-available-programming-books)

---

### Post by nvteighen on 2009-05-10
Here you got a good index:

[http://lambdagrok.wikidot.com/learn:perl](http://lambdagrok.wikidot.com/learn:perl)

---

### Post by fredscripts on 2009-05-10
Books: Learning Perl and then Intermediate Perl.

Always reading and then coding and reading the docs. Perl documentation ($perldoc perl) is by far the best documentation of all programming languages.
CPAN is that place where you go when you feel you're reinventing the wheel. You can be sure that if something isn't on CPAN, it isn't on the net. Also, when you read a module documentation, the first you get is a SYNOPSIS when the majority of the time is the only thing you need to use the module.

For example, the other day I needed to use a Binary Search Tree in python. I googled and I didn't found anything easily useful after visiting more than 5 webs. The wikipedia code was wrong ( I had to correct it, and still have some bugs ).

It took me 2 seconds to find just what I wanted in CPAN: [http://search.cpan.org/~stevan/Tree-Binary-0.07/lib/Tree/Binary/Search.pm](http://search.cpan.org/~stevan/Tree-Binary-0.07/lib/Tree/Binary/Search.pm) , and even with a very cristal example of how to use at the beginning (I didn't need to know all the algorithmics of the BST, just use it), and I can be sure that if it's in CPAN this is a good code (tested by CPAN testers, not like python wikipedia one).

Welcome to Perl. I recommend you mastering regular expressions and also learn something about the perl command line (perldoc perlrun), you can do amazing things with one line in Perl. For example, 

```
 perl -pi -e 's/FOO/BAR/' foo.txt 
```

will replace FOO by BAR in the file foo.txt.

---

### Post by slavik on 2009-05-10
fyi, fot the more complex stuff, there are also simple modules, like XML::Simple, IMAP::Simple and such.

---

### Post by ghostdog74 on 2009-05-11
> **fredscripts said:**
> 

For example, the other day I needed to use a Binary Search Tree in python. I googled and I didn't found anything easily useful after visiting more than 5 webs. The wikipedia code was wrong ( I had to correct it, and still have some bugs ).
depending on what you really want to do, some of the things in Python like sets, bisect can be used. also look [here](http://groups.google.com.sg/group/comp.lang.python/search?hl=en&group=comp.lang.python&q=binary+search+tree&qt_g=Search+this+group)

---

