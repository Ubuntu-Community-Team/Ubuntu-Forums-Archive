---
title: "Math for programming"
date: 2007-12-12
forum: Programming Talk
---

### Post by helphope on 2007-12-12
Hi everybody

I'd like to start off with programming, but first I was wondering which math is mostly needed.
I was thinking of binary calculation, for instance, but I have no other idea (maybe some Boolean logic).

Almost an absolute beginner (html, css, just a bit of javascript  and something about Pyton).

Thanks for any help

:confused:

---

### Post by pedro_orange on 2007-12-12
Well it depends on what sort of programming you're going to be doing to be honest!

If you want to be doing graphical programming vectors and matrices are a must. On the other hand, if you're making applications like a booking system then you just need to know how to add up :) (altho you just tell the program to add it up for you! BODMAS is your friend!)

---

### Post by Deathshrimp316 on 2007-12-12
Basic arithmetic is really all you need to begin programming. Of course if you start programming applications that for example may simulate certain physics principles then you'd have to know about algebra, possibly calculus, etc.

Boolean binary operations are useful, but you'll pick them up as you go along - you won't need to know this when you start coding. Now if you ever decide to delve into assembly programming for example, knowledge  of this would be a must, but assembly is really not for beginners anyway.

---

### Post by helphope on 2007-12-12
Thanks for answering.

I'd like to write a programm  for   text analysis; so that it can read different encodings, produce frequency list and word concordances, search it through regular expressions, ...
What's more I'd like to join the program itself and the text which has to be analysed together, so that the program and the text are "one thing".

I was thinking of Python for this.

thanks

---

### Post by Thanoulis on 2007-12-12
Fist pick your favorite computer language.Then try to play with her (make some programs,either silly or small ones).Maths are important, but they are just a tool.
To learn effective programming, experience and open mind come first.
Good luck! :)

---

### Post by pedro_orange on 2007-12-12
The language you write this in is completely up to you. It doesn't really matter - as long as you feel comfortable (& somewhat) confident. 

Just read up on

Parsing: [http://en.wikipedia.org/wiki/Parsing](http://en.wikipedia.org/wiki/Parsing)
Natural Langauge Processing: [http://en.wikipedia.org/wiki/Natural_language_processing](http://en.wikipedia.org/wiki/Natural_language_processing)

(If thats what you need! I do business application programing so this is out of my scope really!)

Once you've got the principles down you can apply it in any language. A piece of advice, don't try to re-invent the wheel. If someone's written a good piece of code you can apply to your problem (& assuming they don't mind you using it) save yourself the time and trouble and use it!

---

### Post by Lster on 2007-12-12
Learn the operator precedence of the language you pick - that is probably one of the most important things.

Also, modulus has so many uses - it is great to know.

---

### Post by pmasiar on 2007-12-12
Python seems to be very appropriate language for such task. Wiki in my sig has links to free online books and training tasks. Python has module re.py for regex, and nlp for natural language processing.

Of course you will need to learn enough math to understand the stats you create (including bugs in logic). If you need stronger stats, RPy is bindings for industry-strength (and Free) stats package R.

> Learn the operator precedence of the language you pick 

... seems like advice from a Perl hacker. In Python, I prefer to put proper parentheses, just in case. :-)

---

### Post by iharrold on 2007-12-12
I took two semesters of Differential Equations, three semester of Calculus, and a trig refresher as a freshman (for some reason when I went to high school trig really wasn't taught) as just the fundamental math classes.  For my major specific classes related to math and extensions of the fundamentals, I took 2 semesters of physics, 1 semester of Finite Structures, 1 semester of Data Structures, 1 semester of Probability and Statistics, 2 semesters of Electrical Circuits, 1 semester of Electronic Design, 2 semesters of Digital Design (binary math) and a few other classes that were just too painful to remember and had to go buffalo hunting with a several cases of whiskey to forget.  ;)

With all that, I would say I am an average programmer, though a good digital system architecht.  

Figure out what you want to do, what you are interested in doing and learn it.  A college education doesn't make someone smart, it just tends to teach them how to learn.  You learn  best by doing in my oppinion.  I always think back to [Srinivasa Ramanujan Iyengar]("http://en.wikipedia.org/wiki/Srinivasa_Ramanujan"), an indian with no formal education who by all accounts is one of maths greatest genius's.  Later of course he was formally educated.  

In todays day and age with the internet and cheap and easily available books, there really is no reason why a determined individual cannot discover new things on their own... with some assistance of course.

---

### Post by slavik on 2007-12-12
Someone say text processing? I would argue that Perl is better than Python for text processing tasks. But that's me.

---

### Post by pmasiar on 2007-12-12
Yup, thats just you :-)

in that case I would argue that even if pattern matching looks simpler in Perl than in Python (because it is part of Perl syntax, while in Python you need to use re module), difference is pure syntax sugar (using same C library) - and rest (non-pattern matching) processing is simpler in Python.

So, pick your poison. :-)

---

### Post by helphope on 2007-12-12
Thanks to everybody for the answers. I didn't imagine all this

Of course  I didn't understand what stats are, maybe statistics applied to text? In this case the math involved would be statistics?  > Of course you will need to learn enough math to understand the stats you create (including bugs in logic). If you need stronger stats, RPy is bindings for industry-strength (and Free) stats package R

Thanks again

---

### Post by pmasiar on 2007-12-12
yes. stats == statistics in this context. You want to do frequency analysis and stuff, right? 

You better ask experts on statistics and text analysis (in a new post with more appropriate title), I am not one of them.

---

### Post by Lster on 2007-12-12
> **pmasiar said:**
> ... seems like advice from a Perl hacker. In Python, I prefer to put proper parentheses, just in case. :-)

No, just a C and Assembly programmer. :)

---

### Post by slavik on 2007-12-12
> **pmasiar said:**
> Yup, thats just you :-)

in that case I would argue that even if pattern matching looks simpler in Perl than in Python (because it is part of Perl syntax, while in Python you need to use re module), difference is pure syntax sugar (using same C library) - and rest (non-pattern matching) processing is simpler in Python.

So, pick your poison. :-)

But don't you recommend Python for the syntax as well?

```

open FILE,"text.txt" or die $!;
$file = join '', <FILE>;
map { $_{$_}++ } split /\W/, $file;
print "$_ = $_{$_}\n" for(keys %_);
close FILE;

```

pretty readable once you have an idea of what's going on. :) (there are more readable ways to do this, but this is Perl, not Python. :) Easy things should be easy.

Perl makes easy things easier and difficult things not impossible.

---

### Post by pmasiar on 2007-12-12
> **slavik said:**
> pretty readable once you have an idea of what's going on. :)

yes, but to get there is not easy, and to stay tuned in is also hard. I think you just proved my point about differences in syntax sugar (or syntax vinegar) pretty well, I don't see point in arguing it (here) any longer. 

IMHO you definitely **did** picked your poison :-) Enjoy!

---

### Post by muaddib on 2007-12-12
Basic algebra is important for any good programmer to know. Those who are concerned with more advanced algorithms should understand statistics and discrete math (which usually include topics such as logic, set theory, combinatorics, etc).

---

### Post by helphope on 2007-12-13
Thanks again to everybody

> Basic algebra is important for any good programmer to know. Those who are concerned with more advanced algorithms should understand statistics and discrete math (which usually include topics such as logic, set theory, combinatorics, etc).

Which is better, to study it in advance or to pick up the topic as long as it turns up? 

One more thing: can I find somewhere a specific introduction or guide to math for programming or do I have to rely on generic  math sites? I tried in google "math for programming" but the results are poor.

Thanks

:popcorn:

---

### Post by pedro_orange on 2007-12-13
I would say that you remember 10% of the things you read, 20% of the things you write, and 30% of the things you do!

So with that in mind, get your feet wet. You can read hundreds of books on "How to swim" but when you get in the deep end you're bound to sink! So just make some programs, if you stumble accross something you don't understand - then you research it & implement the concept with the knowledge of the language you have picked up.

Good luck.

---

### Post by pmasiar on 2007-12-13
> **helphope said:**
> Which is better, to study it in advance or to pick up the topic as long as it turns up? ... can I find somewhere a specific introduction or guide to math for programming 

Don't be afraid to learn. When learning math, you train your brain to be detail-oriented and handle abstract concepts - this is what programming is too, only programming objects and concepts are more complicated and less logical than math concepts are. Consider math to be exercise machine for your abstract thinking.

---

### Post by iharrold on 2007-12-13
Math isn't easy.  I don't think the human brain is designed to crunch math and approach it in as straight forward method as say a computer.  But we are imaginitive and creative which allows us to problem solve.  

If I have been coding for several days straight or doing some differential equations for a bit, I tend to dream about them.  I find this very disturbing.  And this is coming from someone who hated math all through HS and never really liked it in college.  Though, there is some bizarre beauty in solving correctly a difficult math problem.  

Ok, I'm rambling now.  Basically moral of the story is still figure out what you want to do.  Don't get discouraged and seek help.  If your help doesn't teach you seek more help.  We learn by failing.

---

### Post by Wybiral on 2007-12-13
lol, I've actually had dreams about code too. Particularly when I go to bed after hours of working on one problem.

---

### Post by slavik on 2007-12-13
abstract thinking is what allows us to solve problems. :) some have it developed better than others.

---

### Post by helphope on 2007-12-13
> Basically moral of the story is still figure out what you want to do.

This is what to do:
1) build a program which enable me to do text analysys andtext retrieval (There are some around there - some complex such as wordsmith other simpler: but I want to do this just as a hobby. 

2) I'd like the program may run both in windows (as an *.exe) and in linux

3) Possibly the linguistic corpus should be built in.

This is how I think to proceed

1) Follow all the tips I got here: ask for help, learn modules, learn operator precedence, ...

1) As to math: I'll study the topics that have to be studied

2) As to the programming tool: I'll try with python and the Python modules NLTK

3) First, I'll start off [COLOR="Red"]Text procesisng in Python[/COLOR]  [[http://gnosis.cx/TPiP/]("http://gnosis.cx/TPiP/")]

Thanks

---

### Post by slavik on 2007-12-13
any language that has an interpreter written in C can be compiled ... heck, look at all the games/programs that embed a Perl/Python/Lua/Tcl parsing module into the binaries ...

@pmasiar, the so called syntax sugar you are talking about is exactly the reason why text processing is easier in Perl than many other languages (even Java which has a regex library). Python is just a wrapper around C functions, too.

---

### Post by Snowball on 2008-03-24
Hello,

I have been trying, for some while now, to use complex numbers in my c++ programm. Of course, I can program a class for it myself but I figured somebody else would have done this already.

So I started looking in the synaptic package manager. I downloaded the libcln4 package. But where did it go? What do I need to include in my program so I can use complex number functionality (which is now somewhere installed on my computer)?

I started looking on the internet for the usage of libcln4. Apparently, I need to use GNUmake. But making a GNUmake file is not trivial, so it seems. And the GNUmake manuals are far too general and advanced for my simple electronics calculation tool.

Can anybody help me on this issue? How can I use complex numbers in C++ in the easiest way?

---

### Post by LaRoza on 2008-03-24
> **Snowball said:**
> 
Can anybody help me on this issue? How can I use complex numbers in C++ in the easiest way?

[http://www.opengroup.org/onlinepubs/009695399/basedefs/complex.h.html](http://www.opengroup.org/onlinepubs/009695399/basedefs/complex.h.html)

The standard library of C has complex.h, I am not sure if C++ uses another one.

---

### Post by ruy_lopez on 2008-03-24
> **Wybiral said:**
> lol, I've actually had dreams about code too. Particularly when I go to bed after hours of working on one problem.

The solutions I dream are inaccessible outside their scope.

---

### Post by LaRoza on 2008-03-24
> **ruy_lopez said:**
> The solutions I dream are inaccessible outside their scope.

I would like to remind everyone that this is a necromance, and to keep that in mind when responding.

On topic, I have had dreams in/about code as well. Good for debugging.

---

### Post by Fbot1 on 2008-03-24
All math has an application. One area that I think is largely lacking is exploiting probability but you may not need it. It's really hard to select what you need beyond the basics.

---

