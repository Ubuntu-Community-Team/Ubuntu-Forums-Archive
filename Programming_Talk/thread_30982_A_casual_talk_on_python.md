---
title: "A casual talk on python"
date: 2005-05-01
forum: Programming Talk
---

### Post by und3rdog on 2005-05-01
So I finally broke down and got a pocket guide to Python.  Just flipping through I noticed python has pretty extensive points for OO programming.  My question to start this off.  In what ways does python differ from other OO langs. (i.e. Java)  as far as class structure goes?  Are there special rules such as no inner classes, or maybe no anonymous inner classes?  Anyone care to discuss quirks and fine points of python coding?  For examples let's implement a trie in python.

-Luke

---

### Post by jerome bettis on 2005-05-02
no responses??  there's tons of python programmers in here.  i was looking forward to reading the 8 pages of this thread today so i'd have some inspiration to learn this language next week.

post up!!!11

---

### Post by toojays on 2005-05-02
Maybe there is tons of Python programmers here, or maybe there isn't. A lot of the people who read this forum are too new to programming to be able to compare OO subtleties of different languages.

The only one I could think of off the top of my head is that Python allows multiple inheiritance and Java doesn't. On the other hand, Python doesn't have interfaces, whereas Java does.

The main gripe I hear about OO programming in Python is that there isn't really such a thing as private methods. The convention is to prefix methods which are supposed to be private with a couple of underscores. The only time that's going to be a problem is if a team has programmers with no discipline or scruples, and that's hardly Python's fault.

---

### Post by toojays on 2005-05-02
Luke,

Did you mean "implement a tree"? Why? It's not going to cover any special features of Python, and it's particularly not going to cover any object-oriented aspects of the language. I don't see where you're going with this . . .

---

### Post by Foopy on 2005-05-02
In my opinion, the "quirks and fine points" of Python aren't what makes it so much more fun to program in than other languages I know.  In fact, Python's OO model feels a bit hacked together, especially when it comes to things like static methods--the OO models of other high-level languages like Java or Ruby are much cleaner.

The reason I like Python so much has more to do with its general philosophy.  Its mantra of "there's only one way to do it", for instance, makes it easy to learn, easy to write, and highly readable.  Its nickname as "executable pseudocode" is well-earned, too: I've taught algorithms to people who didn't know Python using Python, and they thought it was pseudocode until I told them they were reading Python.  In short, Python makes programming as easy and fun as it was when I first learned BASIC programming as a kid--a user-friendliness that's sorely lacking in most of today's programming languages--yet it offers just as much power as Java or any other high-level language.

If it helps at all, here's a link to the article that got me to give Python a try a few years ago; it's Eric S. Raymond's account of why he likes Python.  The best thing about it is that it approaches Python from the perspective of a skeptic--which is what everyone is when they're considering learning a new language.

  [http://www.pythonology.com/success&story=esr](http://www.pythonology.com/success&story=esr)

- Atul

---

### Post by und3rdog on 2005-05-02
Ahh yes Raymond's article.  After reading that from else where on this board I was prompted to start this thread.  I merely wished to discuss some of the do's and dont's  of the language,  that's what I meant by "quirks and fine points".  I believe those small gotchas are what makes a language ard to learn.  I read serveral places now about the odd syntax for private members.  Does that apply to constructors in python as well, futhermore does python have constructors?
To answer toojay, no I meant trie.  It's a data structure based on a tree where each node can have an abritrary number of sub nodes.  Traditional this is done by having 3 pointers within each node (parent, oldest sibiling, youngest child).  I can think of a way an inner class would aid in structure.  However I know very little syntax for python.  So have at it!

-luke

---

### Post by Foopy on 2005-05-02
Oh, okay.

I think part of the reason there may not be many replies to your original post may be due to the fact that a lot of the information you seek is readily available on the web.  If the python handbook you bought doesn't tell you if python classes have constructors, then it's a pretty bad book.  You might want to take a look at Magnus Hetland's [Instant Python](http://hetland.org/python/instant-python.php) tutorial for help on basic OO programming in Python; his book [Practical Python](http://www.amazon.com/exec/obidos/tg/detail/-/1590590066/qid=1115055435/sr=8-1/ref=sr_8_xs_ap_i1_xgl14/104-7578511-0812728?v=glance&s=books&n=507846) is also quite good, as is David Beazley's [Python Essential Reference](http://www.amazon.com/exec/obidos/ASIN/0735709017/qid=1115055509/sr=2-1/ref=pd_bbs_b_2_1/104-7578511-0812728).  Of course, the [official Python tutorial](http://docs.python.org/tut/tut.html) on python.org isn't bad, either.

That said, it may be more effective if you came up with your own trie class and asked for stylistic advice, or, if you run into some kind of snag making your class, posting what you've got so far and asking for more specific help.  You may also want to check out the [Python tutor mailing list](http://mail.python.org/mailman/listinfo/tutor), which is quite active and helpful.

---

### Post by Mike Buksas on 2005-05-14
> **Foopy]Oh, okay.

I think part of the reason there may not be many replies to your original post may be due to the fact that a lot of the information you seek is readily available on the web.  If the python handbook you bought doesn't tell you if python classes have constructors, then it's a pretty bad book.  You might want to take a look at Magnus Hetland's [Instant Python](http://hetland.org/python/instant-python.php) tutorial for help on basic OO programming in Python said:**
> Practical Python[/URL] is also quite good, as is David Beazley's [Python Essential Reference](http://www.amazon.com/exec/obidos/ASIN/0735709017/qid=1115055509/sr=2-1/ref=pd_bbs_b_2_1/104-7578511-0812728).  Of course, the [official Python tutorial](http://docs.python.org/tut/tut.html) on python.org isn't bad, either.

That said, it may be more effective if you came up with your own trie class and asked for stylistic advice, or, if you run into some kind of snag making your class, posting what you've got so far and asking for more specific help.  You may also want to check out the [Python tutor mailing list](http://mail.python.org/mailman/listinfo/tutor), which is quite active and helpful.

 Don't forget [Dive into Python](http://diveintopython.org/). The HTML version is part of the standard install. See /usr/share/doc/diveintopython/README.Debian 

The quirks of Python depend a lot on which language you're approaching it from. As indicated, the static and class methods seem like a bit of a hack, even C++ is more elegant in this regard. If you come from a strongly typed background (Java, C++) then Python's dynamic typing will seem a bit odd. (Variables can be assigned to objects of any type, but the intrepreter will not convert between them willy-nilly). 

On the whole, Python is very elegant and probably not excessively quirky. It's also very easy to pick up, as I think "Dive into Python" will demonstrate.

---

### Post by poster_nutbag on 2005-05-15
No private or protected areas in Python classes, so none of the get_foo() and set_foo() that you tend to see in C++ - but Pythons dynamic variables mean you don't really miss this.

Meta-class hacking is much easier: adding and changing functions whilst code is running is easy.

Unlike some other languages, there is generally a more obvious way to do things in Python. You'll pick things up quickly.

Code runs slow, but code development is faster. If speed is your thing, then you'll end up using external C/C++ code anyway.

I've being programming in Python for around a year or so now (used to be C++/Perl) and from my experience with it I'd say that Python classes look simple to start with but are very pliable to work with.

---

### Post by nobodysbusiness on 2005-05-16
[QUOTE=und3rdog]Does that apply to constructors in python as well, futhermore does python have constructors?[/QUOTE]

Yes, Python has something like a constructor. It's the __init__ method, which is the first method called when an instance of a class is created. From "Dive into Python": ([Link](http://diveintopython.org/object_oriented_framework/private_functions.html))

If the name of a Python function, class method, or attribute starts with (but doesn't end with) two underscores, it's private; everything else is public.

---

### Post by jerome bettis on 2005-05-16
[QUOTE=nobodysbusiness]If the name of a Python function, class method, or attribute starts with (but doesn't end with) two underscores, it's private; everything else is public.[/QUOTE]

so does that mean it's really private and can't be called from elsewhere or is it just assumed that the programmer will conform to this practice and pretend that it is private?

also what's the reasoning behind all of the underscores?   seems kinda .. :neutral:

---

### Post by Foopy on 2005-05-16
[QUOTE=jerome bettis]so does that mean it's really private and can't be called from elsewhere or is it just assumed that the programmer will conform to this practice and pretend that it is private?

also what's the reasoning behind all of the underscores?   seems kinda .. :neutral:[/QUOTE]

Python's so-called "private methods" are one of the few inhumane elements of the language, in my opinion.  What actually occurs is that when you have a class "A" which defines a method "__foo()", Python secretly mangles the name "__foo()" to become "_A__foo()".  Other code outside of A can explicitly call the mangled _A__foo() method without penalty.  Also, if one were to misspell a call to "self.__foo()" within a method of A--for instance, calling "self.__foi()", then the resultant traceback would complain that your A instance has no attribute '_A__foi()', which can easily confuse users who don't know about the name mangling.

The fact that a method starting with two underscores but not ending with two underscores is private whereas a method starting with two underscores and ending with two underscores is *not* private is another inhumane detail that is both cumbersome to remember and cumbersome to explain.

One of the important lessons I've learned about good programming style is that just because a language feature exists doesn't mean you should use it.  Due to the fact that "private" class methods aren't actually private, the issues with what kind of name actually constitutes a private method, and the fact that name mangling can potentially confuse people who don't know about it, I prefer to start my "private" classes with a single underscore (e.g., "_foo()") simply to indicate to readers that the function isn't intended to be called by client code.  Whether you ultimately use private classes is up to you, of course, but in my opinion it just complicates the language without adding anything particularly useful to it.  I've also never actually seen private classes used in any of the Python code I've read.

---

### Post by jerome bettis on 2005-05-16
thanks for explaining.

i think that's really dumb to do that.  maybe it's because i've been in c++ and java for so long i'm just used to they way things work over there and everything else seems foreign and nonsensical.

i'd like to know why they did that .. maybe they decided to alter method names to avoid using dispatch tables?  what ever the reason is i'm curious and would like to hear the benefits of it.  as of now i don't think i'm gonna bother learning python .. it seems quirky and i'm not a fan of interpreted languages (java is sloowwww . i doubt python is much better).

i think i'm gonna take a look at D instead.  it looks interesting: [http://www.osnews.com/story.php?news_id=6761](http://www.osnews.com/story.php?news_id=6761) .. i just hope the frontend to the compiler is easy to get installed and it works ok.

---

### Post by Foopy on 2005-05-16
Well, another big disadvantage of Python's "private" methods is that, because public/private inheritance dichotomies are what a lot of people coming from other OO languages are used to, it's one of the first things they want to know about when learning Python, and a lot of them get turned off by what they see.  IMO the Python language designers should have just gone the route of Smalltalk and avoided an enforced public/private dichotomy at all; it's really nothing to be ashamed of.

In any case, I think the private method issue is one of the few "quirky" things about Python; by and large, Python is the most enjoyable language I've used, for reasons I mentioned earlier in this thread.

If speed is of concern in a particular task, then don't use Python for it.  Yet it should be noted that a lot of programming tasks don't actually require a lot of speed, and among programming languages there are usually trade-offs between ease of implementation, ease of maintenance, readability of source code, and efficiency.  Python excels at the first three, but wasn't really even designed for the latter--as such, comparing it to a language like C/C++ in the absolute sense is like comparing apples to oranges.  When speed is a concern for certain parts of a project, it's also possible to code the performance-sensitive components in C/C++ and bind them to Python using a tool like SWIG or the Python C extension API.

If you're interested in a language that's somewhat similar to Python but has a much cleaner OO model, you might want to check out [Ruby](http://www.ruby-lang.org/en/).

- Atul

---

### Post by jerome bettis on 2005-05-16
excellent.  i've been reading that link for a couple hours and ruby is definately what i was looking for.  thanks.

i guess i can put up with an interpreter again.

---

### Post by nobodysbusiness on 2005-05-18
I was in the same boat not long ago, trying to decide what new language to learn. (I eventually narrowed it down to Python or Ruby). Although Ruby has more elegance in it's design, I ultimately decided to go with Python because of the amount of libraries, online books and other helpful code available. Maybe in a few years, if Ruby continues to gain mindshare, I'll switch over. For now, though, I'm quite happy with Python.

---

### Post by Foopy on 2005-05-18
[QUOTE=nobodysbusiness]I was in the same boat not long ago, trying to decide what new language to learn. (I eventually narrowed it down to Python or Ruby). Although Ruby has more elegance in it's design, I ultimately decided to go with Python because of the amount of libraries, online books and other helpful code available. Maybe in a few years, if Ruby continues to gain mindshare, I'll switch over. For now, though, I'm quite happy with Python.[/QUOTE]

I agree.  Aside from some things the language inherited from Perl, I think Ruby is a very clean language, but the fact that it's not really *that* different from Python combined with its lack of mindshare makes it a less-than-optimal choice for me.

---

### Post by jerome bettis on 2005-05-18
well 2 days later and i think i know ruby pretty good already.  it's nice, i think i'll enjoy programming in it.  no semicolons!! no name analysis and no typechecking makes my life easy.  but i do hear what you two are saying about python being a better choice and i think you might be exactly right because of the reasons you gave.  

i like the idea of no { } or begin end things to delimit blocks, just indent - it makes total sense because you do it anyway.  but the whole private method, name altering thing just seems like a mess.  but i think i'll get over it.

---

### Post by DirtDawg on 2005-05-18
You know what I like about Python? It's easy to play with. I'm strictly an amature tinkerer and sometimes I just want to screw around. Although I've heard again and again that you should plan programs out before typing a single character to prevent massive design problems, I have a tendancy to think, "Golly Gee Whiz, I feel like throwing together a stupid rinky-dink program that does absolutely nothing of value but amuse me for a half hour". Sure enough, there' always design problems in the "finished" product, but I really have fun. 
Though I've read about "private" attributes before, they're pretty abstract to me due to my limited understanding of programming in general, so the issue's neither here nor there for me.

---

### Post by okTober on 2005-05-20
I was thinking about teaching myself python. I have no experience with any other programming languages. I would like to learn the basic fundamentals of OO programmng and form good habits to *perhaps* apply to other languages down the line. I've read a lot of great things about python, especially about it being a great language for first time programmers. 

I've also heard people say it's best to start out in basic or pascal. Others have said to jump right into c/c++ or java. 

I think I'm going to give python a try. Since you guys are all experienced in python, I was wondering if any of you thought this was a bad idea. And if so, what would you suggest?

P.S. I don't plan on making a career out of programming. It's more of a personal interest I've had for quite some time.

---

### Post by mendicant on 2005-05-20
I think it's more important to have an idea of something to implement.  Then choose whatever language you want to try out.  Learning good habits and design is a bit more complex.  You can look at code, read books, and listen to other people talk about it, but as with a lot of things, it doesn't hit home until you make a bad design decision and it bites you in the rear later.  Of course, that doesn't mean you shouldn't read books, and look at code, but just that you really need to write some as well.  For that, having that idea to implement is handy.

---

### Post by Mike Buksas on 2005-05-20
[QUOTE=okTober]I was thinking about teaching myself python. I have no experience with any other programming languages. I would like to learn the basic fundamentals of OO programmng and form good habits to *perhaps* apply to other languages down the line. I've read a lot of great things about python, especially about it being a great language for first time programmers. 

I've also heard people say it's best to start out in basic or pascal. Others have said to jump right into c/c++ or java. 

I think I'm going to give python a try. Since you guys are all experienced in python, I was wondering if any of you thought this was a bad idea. And if so, what would you suggest?

P.S. I don't plan on making a career out of programming. It's more of a personal interest I've had for quite some time.[/QUOTE]

I think it would make an excellent first programming language. I started with Fortran and moved to C++. I use C++ every single day (well, weekday) but after a few weeks with Python, I was more productive in it than in C++. 

One possible downside is that, because it is a high level language, that it prevents you from learning how to do a lot of the simple things that you have to do in other languages. I don't see this as a big disadvantage. In fact, it lets you concentrate on the big picture of writing clear and maintainable programs while learning and leave the nitty-grity details for later.

So yea, I think it's a great choice.

Mike

---

