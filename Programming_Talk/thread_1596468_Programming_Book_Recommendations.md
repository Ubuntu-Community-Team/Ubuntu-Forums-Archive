---
title: "Programming Book Recommendations"
date: 2010-10-14
forum: Programming Talk
---

### Post by xnerdx on 2010-10-14
Hey everyone! I'm looking for recommendations for a good intermediate/advanced C++ programming book (preferably one available on Safari). I have read _Practical C++ Programming_ and _C++ Without Fear_ and I want to move onto a more advanced book. I understand C++ programming for the most part and I am more interested in OOP. I’m trying to find a book that is going to be a challenge and that will teach me how to program OOP through example, and then give me an “assignment” to review the content just reviewed, any recommendations? Thanks in advance!

---

### Post by matthew.ball on 2010-10-14
Don't know to what level the two books you mentioned take you, but Bruce Eckel has a reasonably decent set of books "Thinking in C++" (volumes 1 & 2).

Volume 1 is basically an introduction to C++, firstly covering "the C in C++" and then focusing more on what makes C++, well C++. It's pretty much an introduction to programming book, with a particular emphasis towards C++.

Volume 2 covers templates, generics, design patterns and concurrency in C++ fairly well (it's assumed that you know what was covered in the first volume).

His books should be available free online too.

If you're really interested in object-oriented programming, it couldn't hurt to take a look at the Gang-of-Four text "Design Patterns: Elements of Reusable Object-Oriented Software". Though, this isn't *just* C++, it also has some snippets in Smalltalk.

---

### Post by GeneralZod on 2010-10-14
For being "advanced" in the C++ language itself, I always recommend (pretty much unreservedly):

[Effective C++](http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=sr_1_1?ie=UTF8&s=books&qid=1287059977&sr=8-1) and [More Effective C++](http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=sr_1_2?ie=UTF8&s=books&qid=1287059977&sr=8-2), then [Exceptional C++](http://www.amazon.com/Exceptional-Engineering-Programming-Problems-Solutions/dp/0201615622/ref=sr_1_1?ie=UTF8&s=books&qid=1287060071&sr=1-1) and [More Exceptional C++](http://www.amazon.com/More-Exceptional-Engineering-Programming-Solutions/dp/020170434X/ref=sr_1_3?ie=UTF8&s=books&qid=1287060071&sr=1-3).

There are various other books dedicated solely to e.g. templates, etc, but I wouldn't recommend them quite as wholeheartedly.  It's always nice to have a copy of the [ISO C++ Standard](http://webstore.ansi.org/RecordDetail.aspx?sku=INCITS%2FISO%2FIEC+14882-2003), but it might be worth waiting for the upcoming C++0x one (I don't regret purchasing the 2003 one, though).  I have a hardcopy of the 2003, but find the electronic version infinitely more useful.

To get well-acquainted with the STL, I recommend [Effective STL](http://www.amazon.com/Effective-STL-Specific-Standard-Template/dp/0201749629/ref=sr_1_1?ie=UTF8&s=books&qid=1287060220&sr=1-1) which covers a lot of "gotchas" and best practices.

It's also good to get acquainted with the Boost C++ libraries, especially as many of them are going to be subsumed into the base C++ language and libraries proper in the upcoming C++0x: there is extensive documentation on their [site](http://www.boost.org/doc/libs/1_44_0/), but you might want to look at a standalone book that gives an introduction to some of the more important libraries, such as [this one](http://www.amazon.com/Beyond-Standard-Library-Introduction-Boost/dp/0321133544/ref=sr_1_2?ie=UTF8&s=books&qid=1287060632&sr=1-2).

> I understand C++ programming for the most part and I am more interested in OOP. I&#8217;m trying to find a book that is going to be a challenge and that will teach me how to program OOP through example, and then give me an &#8220;assignment&#8221; to review the content just reviewed, any recommendations? 

This ones a bit trickier, and there's a lot of personal taste involved.  If I were to make one single suggestion about OO, it would probably be [Agile Software Development, Principles, Patterns, and Practices](http://www.amazon.com/Software-Development-Principles-Patterns-Practices/dp/0135974445/ref=sr_1_2?ie=UTF8&s=books&qid=1287060772&sr=1-2).  The word "Agile" seems to make a lot of people roll their eyes dismissively, but it is only a fairly minor part of the book.  The book itself covers (though not always in great detail - parts of it serve as a good "jumping off" point for future reading) a whole range of OO and "good design" oriented stuff, including GOF (& other's) Design Patterns; designing for unit testing/ Test-Driven Development; various good OO design principles (SRP, OCP, LSP, ISP, etc); several worked examples explaining step-by-step all of the decisions and trade-offs made; etc.  In my opinion, it crams a hell of a lot of good stuff into 500 or so pages - stuff that's usually spread out over a bunch of other, overlapping, expensive books.

It also has a special place in my heart for very clearly stating that almost ever decision made will be a trade-off, and will likely break some "good design" rules of thumb: a breath of fresh air after reading several books that were litanies of contradictory "Thou Shalt not do this" and "Thou Shalt not do that" that could easily leave the neophyte paralysed into indecision.  It also features clear statements to the effect of "'Not OO' is not synonymous with 'bad'", again a breath of fresh air after reading several books that the phrase use "Not OO" with exactly the same tone as they would use the "bad".

Note that it is not heavily-focussed on C++, though, but good OO design is good OO design.  (Incidentally, something to keep your eye on if you are into C++ & OO is [this](http://blog.objectmentor.com/articles/2010/10/08/cpp-and-ood-the-least-you-need-to-know) - there's an incomplete C++ & OO book downloadable for free).

In a similar vein, but even less C++-focussed (pure Java, actually!), I feel I greatly benefitted from reading [Growing Object-Oriented Software, Guided by Tests](http://www.amazon.com/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627/ref=sr_1_1?ie=UTF8&s=books&qid=1287062080&sr=8-1) (my bias is probably showing at this point: I'm tremendously excited by Unit Testing/ TDD and its effect on the design of code :)).

A book that dramatically changed the way I program is [Clean Code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&s=books&qid=1287061809&sr=8-1) which again contains a bunch of worked examples and which is quite inspirational (but which can also be quite infuriating - if you're anything like me, be prepared to strenuously disagree with some of the author's conclusions and assertions! It's great for stirring debate and introspection).

You'll almost certainly want to read the venerable [Refactoring: Improving the Design of Existing Code ](http://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672/ref=sr_1_1?ie=UTF8&s=books&qid=1287062194&sr=8-1), if only for the section on "code smells".  Many people will also recommend [Design Patterns](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/ref=sr_1_1?ie=UTF8&s=books&qid=1287062256&sr=8-1), but to be honest, if money is tight, you can probably get a lot of the basics from sites such as [this one](http://www.vincehuston.org/dp/) and Wikipedia.

Edit:

Typos.

---

