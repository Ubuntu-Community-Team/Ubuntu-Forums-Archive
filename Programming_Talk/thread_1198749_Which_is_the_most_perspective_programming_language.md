---
title: "Which is the most perspective programming language ?"
date: 2009-06-27
forum: Programming Talk
---

### Post by credobyte on 2009-06-27
Ok, so .. It's been a while when I first started to learn programming and it's time to choose - what do I need. In the last few months I've tried almost all languages ( just kidding ) - C, C++, Java, Python. Everything looks nice and I've found a few great things in all of these languages, BUT, I'm not sure about one thing .. which one is the most perspective language for starting to build up my career as a programmer ( I've been working with PHP for 5 years and looks like it's a *waste of time* ) ?
I know, it can take a while, but, I need your opinion. What would you choose ? Which one should be ( and "will" be ) the hottest ( job opportunities ) language in the future ( 5, 10 years .. ) ?

**Note:** This is not another "best programming language" thread. I'm interested in long-term benefits.

---

### Post by monkeyking on 2009-06-27
It depends on what you want to do,
and your overall background.

Ff you are inclined for webstuff,
learn c# or whatever ppl are using these days.

If you are into largescale numbercrushing then c/c++.

One thing that will benifit you alot would be shell scripting.

---

### Post by soltanis on 2009-06-27
Definitely depends on sub-specialty like above poster said. Different industries use different software. If you're working Business stuff, accounting, systems analysis and stuff, you might use COBOL or FORTRAN; in the games industry, C++ is the dominant language; in interactive web stuff, there's a huge variety from traditional CGI/webserver admin stuff like Perl up to C#, python, ruby, Java. Research the field you are looking to get in to (the best way is to look at jobs listings to see what companies are looking for) and go with that language.

---

### Post by credobyte on 2009-06-27
> in the games industry, C++ is the dominant language
And that's what this post is not all about :) C++ is the main language used for game development, BUT - only 1-3% of all C++ programmers can get into this industry ( as it's an extremely small and requires VERY good math skills ).

> Ff you are inclined for webstuff,
learn c# or whatever ppl are using these days.
C# .. where it's being used and why it's better than others ? I'm looking for real suggestions/arguments, not "whatever you want" :)

---

### Post by slavik on 2009-06-28
> **credobyte said:**
> And that's what this post is not all about :) C++ is the main language used for game development, BUT - only 1-3% of all C++ programmers can get into this industry ( as it's an extremely small and requires VERY good math skills ).


C# .. where it's being used and why it's better than others ? I'm looking for real suggestions/arguments, not "whatever you want" :)
Do you know the type of programming/industry you want to be in? I believe this question has been asked, but not answered.

---

### Post by nvteighen on 2009-06-28
As all above said, it depends on what you like. System programming (C, C++, ObjC in case of Mac) is absolutely different to algorithmic research (Lisp, Prolog, other very-high-level languages).

What kind of projects have you been working **for fun**? Take a look if you can discover some common pattern on them... It may show you what you like to do.

You know, we live towards the future but building up from our past ;)

---

### Post by credobyte on 2009-06-28
Programming for Linux - that's all what I'm currently interested in. Kernel modules, administration tools, etc. ! Most of all Linux apps are written in C, so .. is Java even worth a try ? Will C/C++ be the main 2 languages for Linux platform in long-term ( not only for a year or two ) ?

---

### Post by jespdj on 2009-06-28
Java is still the dominant programming language for enterprise development. Most big Internet companies, including Google and Amazon, use Java for server side software.

If you want a job as an enterprise software developer then Java is a great choice.

One website that measures the popularity of programming languages is the [Tiobe index](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html).

But really, it depends on what branch of the software development business you want to go in. If you want to develop desktop applications for Linux, then Python, C# (on Mono) or C++ are better choices than Java. If you want to develop kernel modules, then C is really the only choice and will remain so for the forseeable future (the Linux kernel itself is written in C).

---

### Post by jpkotta on 2009-06-28
The language isn't important.  Or rather, it's not as important as good programming skills.  If you can't write good code, it doesn't really matter if you know the "right" language.  Conversely, if you can write good code in one language, it is not that difficult to write good code in another, or to learn another for that matter.  That being said, languages are not equal, so you should definitely learn several different ones, and learn them _well_.  Personally, I would recommend C and Python, and something like Scheme or Haskell.  Perl, Octave/Matlab, Bash, and Mathematica are some others that I've had to learn and mostly enjoyed using.

C will never go away on Linux.  It will always be the language of the kernel as long as Linus is in charge.  Bourne shell (/bin/sh, NOT /bin/bash) will likely be around for many years, as this is the traditional system scripting language.  On Debian systems, Bourne shell is what to use on init scripts.  You should also use Bourne shell on any shell script that is meant to be run on other Unix-like OSes, including different Linux distros.

---

### Post by credobyte on 2009-06-28
Thanks you guys - looks like I'm going to start off with Python ( before looking at C ) :)

---

### Post by pokerbirch on 2009-06-28
Biggest problem with Java is that the industry is flooded with university graduates and (in the UK at least), the salaries are very low unless you have exceptional skills. I don't program for a living but i don't think you should just learn just *one* language. Learn as many as you can, including one or two "old" languages because they are still in use but demand large salaries.

---

### Post by CptPicard on 2009-06-28
You may also want to at least take a look at Lisp. I know it looks weird to a lot of people at first blush, but it is rather profound while being very simple in basic construction... good for "perspective" as you put it. :)

---

### Post by JordyD on 2009-06-28
> **CptPicard said:**
> You may also want to at least take a look at Lisp. I know it looks weird to a lot of people at first blush, but it is rather profound while being very simple in basic construction... good for "perspective" as you put it. :)

:D Every time I see you recommend a language it's lisp.

---

### Post by CptPicard on 2009-06-28
> **JordyD said:**
> :D Every time I see you recommend a language it's lisp.

Yeah, well... you may want to use other languages for some specific purposes for reasons of "technical suitability", but it's not as if they genuinely have anything that Lisp doesn't have or what you can't fairly easily build on top of Lisp's easy yet powerful basics. For actually learning about how to construct various kinds of solutions to all kinds of problems, Lisp is very instructive, although you may not actually use it for "everything" in the real world.

---

### Post by wojox on 2009-06-28
You said you've coded php?

Go with C because that's primarily what php is written in. Along with perl.
All those predefined functions you call and set arguments to are C.

As far as C++ or Java I found C++ to be a little better adjusting to when dealing with classes. I think it's because Java's  pure and C++ you can still intertwine your C knowledge with.

Just a thought.

---

### Post by Darkspark on 2009-07-03
Well, it does depend on what you want to do but C++ is the easiest to learn first. From there, you can relate it to any other object-oriented language, Java for example. It all about the semantics, then the syntax follows. So while it does depend on what you are doing, languages fall into four main groups: logical, procedural, functional, and object-oriented. The last being the most popular, and logical is more math-based, for things like AI, and the middle two less common to use. Also, python, functional, is good since it does have to compile, and easy to porgram in. I learned it in two days. Draw back to it was memory usage, and slowness. Python is handy, but the code is ran through an interpreter. C++ can be considered a hybrid between procedural and OO. So start with something simple yet can become complex.

---

### Post by nvteighen on 2009-07-03
> **Darkspark said:**
> Well, it does depend on what you want to do but C++ is the easiest to learn first.

No way. Your post is even contradictorious, as you say you learned Python in two days...

C++ is too complex, makes you deal with high-level and low-level stuff simultaneously and that can only deal to confusion if you are a newbie programmer. Apart from giving you a false impression on what programming is (modelling a reality in a formal language).

> So while it does depend on what you are doing, languages fall into four main groups: logical, procedural, functional, and object-oriented. The last being the most popular, and logical is more math-based, for things like AI, and the middle two less common to use. Also, python, functional, is good since it does have to compile, and easy to porgram in. I learned it in two days. Draw back to it was memory usage, and slowness. Python is handy, but the code is ran through an interpreter. C++ can be considered a hybrid between procedural and OO. So start with something simple yet can become complex.

No, that's completely wrong. The paradigms are declarative (e.g. HTML), imperative (e.g. C, C++, Java, Python, etc.), logical (e.g. Prolog) & functional (e.g. Lisp, OCaml, Haskell, etc.). The math-based paradigm is the functional, not the logical... And object-oriented is a **design paradigm** (like procedural), not a programming paradigm... OOP is usually imperative programming, but it can also be done in functional programming.

You can have OOP in C. Ok, you don't get explicit syntax support like in C++, but it's OOP.

Python is mainly imperative... and too OOP-biased IMO. It has some functional programming features, though really limited (but IMO they are a good way to introduce you into functional programming before getting into some Lisp, for example).

But the idea on high-level languages is to be nearer to your mind's concepts and further from the machine's internals.

---

### Post by CptPicard on 2009-07-03
> **nvteighen said:**
> 
C++ is too complex

+1. For learning the kinds of languages generally in that "group" of languages, something like Java or C# serves better. The key is learning the static-typed object-oriented design mindset, that is, what kind of object to put where. Unfortunately learning both programming from scratch and that *and* the C++-style "minding the machine while you're doing it" feels like a tall order for a n00b. (I for one know that my learning process would have been greatly advanced by taking things one thing at a time)

> Apart from giving you a false impression on what programming is (modelling a reality in a formal language).

Well, OOP makes a lot of claims to modelling reality in formal language. It's partially correct but as far as I am concerned the jury is still out. :) But, I certainly agree with you that the point here is about working with the machine vs. working with the problem by means of the language...

> The paradigms are declarative (e.g. HTML), imperative (e.g. C, C++, Java, Python, etc.), logical (e.g. Prolog) & functional (e.g. Lisp, OCaml, Haskell, etc.).

It's interesting to note that functional programming is, in its pure form, essentially declarative programming... you tell "what is". Prolog's predicates are a step further -- a relation that just gets "satisfied" instead of evaluated. When you add mutable state, you move over to imperativeness.

> OOP is usually imperative programming, but it can also be done in functional programming.

Functional languages tend to be rather object-oriented too, all data really is a kind of object that then needs to get matched to a function. It is all very implicit though.

It is interesting to note that Lisp already is pretty object-oriented and duck-typed to boot... it's not some fad that someone came up a decade ago like some people like to imagine.

> 
Python is mainly imperative... and too OOP-biased IMO.

Try Ruby then, it is almost as "object-obsessed" as Java is. :)


> **Darkspark said:**
> Python is handy, but the code is ran through an interpreter.

Actually, it's bytecode-compiled...

> So start with something simple yet can become complex.

Actually I always felt like Python fits the bill there perfectly without "becoming complex" simply by virtue of the language itself being complex...

---

### Post by nvteighen on 2009-07-03
> **CptPicard said:**
> 
Functional languages tend to be rather object-oriented too, all data really is a kind of object that then needs to get matched to a function. It is all very implicit though.


I know... you've seen my FreeTruco code :D

What I was referring to is the fact that OOP code is usually written in imperative languages. Well, of course, because most code is nowadays written in imperative languages... So my argument was a bit redundant, actually.

OOP is clearly a design issue that has to be implemented somehow, not a paradigm that establishes the point of view of our model. For example, in Clojure (a pure-functional Lisp dialect), your reality will be modelled assuming there's no state, so that the result of anything at any point of execution is always predictable knowing the parameters it takes. In imperative languages this is not the case, as you introduce the ability of setting states and therefore use time as a kind of "implicit global variable". Depending on what you're doing, you'll choose the paradigm that best fits you. 

But OOP, in the other hand, is about modelling with "objects", so it's not about the base on how we'll consider reality; instead, it's about how to segmentate the reality, given some point of view on it. So, you could have stateless objects or stateless procedures or stateless pizzas, or stateful objects or whatever... as you see, the paradigm is about a general constraint applied to a "minimal unit of design" (design pattern).

---

### Post by Reiger on 2009-07-03
Funnily enough the OP says of PHP 5 that it is a waste of time, but I find that looking at the job market PHP (5) is among the languages with the most `accessible' jobs. (I.e. doesn't require 15 years of additional fairly specific field knowledge too.) Apart from that I found that wherever there is a Java web application there also is a job for an XSLT guy. Guess that Java developpers love to run their object through an XML encoder and basically tell the XSLT guy `here you go, your job to make this actually worth looking at'.

> **jpkotta said:**
> On Debian systems, Bourne shell is what to use on init scripts.  You should also use Bourne shell on any shell script that is meant to be run on other Unix-like OSes, including different Linux distros.

NO. That is *very* wrong. First of all Debian uses Dash (Debian's implementation of Ash) which is a lot more lightweight for the /bin/sh shell. This is because init scripts and such like do not need fancy terminal output and other such capabilities, which makes bash a bit overkill and its cost in speed not worth the features. By default all *sh scripts are executed through /bin/sh for efficiency.

Furthermore if you want your scripts to be portable you should not write bash but you should write POSIX sh. This will be your best bet at ensuring compatibility across a wide array of sh implementations.

---

### Post by Darkspark on 2009-07-04
> **nvteighen said:**
> No way. Your post is even contradictorious, as you say you learned Python in two days...

C++ is too complex, makes you deal with high-level and low-level stuff simultaneously and that can only deal to confusion if you are a newbie programmer. Apart from giving you a false impression on what programming is (modelling a reality in a formal language).



No, that's completely wrong. The paradigms are declarative (e.g. HTML), imperative (e.g. C, C++, Java, Python, etc.), logical (e.g. Prolog) & functional (e.g. Lisp, OCaml, Haskell, etc.). The math-based paradigm is the functional, not the logical... And object-oriented is a **design paradigm** (like procedural), not a programming paradigm... OOP is usually imperative programming, but it can also be done in functional programming.

You can have OOP in C. Ok, you don't get explicit syntax support like in C++, but it's OOP.

Python is mainly imperative... and too OOP-biased IMO. It has some functional programming features, though really limited (but IMO they are a good way to introduce you into functional programming before getting into some Lisp, for example).

But the idea on high-level languages is to be nearer to your mind's concepts and further from the machine's internals.

Sorry about the procedural, a.k.a. imperative, mix up as well as the mismatch of logical, but you are still wrong. They are often grouped into these four families:
Imperative
Functional
Logic
Object-oriented

Please look at the following links:
[http://en.wikipedia.org/wiki/Object-Oriented_programming](http://en.wikipedia.org/wiki/Object-Oriented_programming)
[www.webber-labs.com/mpl/lectures/ppt-slides/01.ppt](www.webber-labs.com/mpl/lectures/ppt-slides/01.ppt)

And while Python was easy to learn, so is C++ if you progress from its imperative roots to its OOP ability, not both at the same time, of course. Did I mention C++ was a hybrid? Guess you learned the C++ language all at once.
And C++ is more widely used, which is the purpose of the post. Just don't get too attached to the syntax. Oh, and C does not support classes. Obviously, you don't understand the concept of OOP. For instance, OOP offers abstraction, encapsulation, inheritance, and polymorphism. Show me that built-in to C.

---

### Post by lisati on 2009-07-04
Here's my $0.02:

Probably just as important as a choice of programming language and having a decent level of maths skills is the ability to organize your thoughts well on what you hope to achieve with a program.

---

### Post by jon zendatta on 2009-07-04
Isn't it like you learn one language and learn it good, then other languages will follow.

---

### Post by nvteighen on 2009-07-04
> **Darkspark said:**
> Sorry about the procedural, a.k.a. imperative, mix up as well as the mismatch of logical, but you are still wrong. They are often grouped into these four families:
Imperative
Functional
Logic
Object-oriented

Please look at the following links:
[http://en.wikipedia.org/wiki/Object-Oriented_programming](http://en.wikipedia.org/wiki/Object-Oriented_programming)
[www.webber-labs.com/mpl/lectures/ppt-slides/01.ppt](www.webber-labs.com/mpl/lectures/ppt-slides/01.ppt)


I know OOP is usually considered a "programming paradigm", but a little observation just tells you it can't be. If you can code OOP in two different paradigms, then it's not a paradigm by itself. And surprise, what is CLOS in Common Lisp? OOP in functional programming.

> 
And C++ is more widely used, which is the purpose of the post. Just don't get too attached to the syntax. Oh, and C does not support classes. Obviously, you don't understand the concept of OOP. For instance, OOP offers abstraction, encapsulation, inheritance, and polymorphism. Show me that built-in to C.

GLib/GTK+. There you have all OOP in C. It's a classic example.

You are too attached to the syntax... Ok, OOP in C gets really awkward and complex, but you can do it with a combination of compiler tricks, macros and good design. If the concepts are there, there is OOP.

As a little example of basic OOP, here I send you a C code I wrote. It's nothing impressive, it just sorts stuff into a tree. And additionally, I send you the Python version so you see how the design is exactly the same (with Pythonic-code, not a faulty translation), except for the obvious drawback in C of lacking a list data structure which I implemented by myself (also in OOP)... in Python that is not necessary at all.

EDIT: Use the Makefile in the C version to compile.

---

### Post by CptPicard on 2009-07-04
> Did I mention C++ was a hybrid? Guess you learned the C++ language all at once.

As a matter of fact, professional, idiomatic, safe C++ does preferably make use of the whole deal, and correctly. Making all the pieces fit right takes quite a bit of understanding, and I have always felt like it's often not worth it.

> Just don't get too attached to the syntax. Oh, and C does not support classes. 

I do not understand what syntax has to do with it. In a lot of ways, C++'s classes are mere syntactic sugar on top of virtual function pointer table and dispatching mechanism that you can fairly easily construct in C (and I often do) -- there is nothing *that* conceptually  remarkable there.

Of course, C++-like languages particularly *stress* this syntactic sugar in their language design...

> Obviously, you don't understand the concept of OOP.

I would suggest you avoid fighting words. :) Obviously, your concept of OOP comes essentially just from C++/Java/C#-like languages, and you have not seen the idea elsewhere. It is a far broader issue, with ways to implement it in various languages.

The core point in OOP is that you have a data "object" that has associated code. This associated code is discovered in various ways (method dispatching). Often this plays together with the data record's data type inheritance hierarchy. 

A lot of languages very implicitly object-oriented -- for example in Python everything really is an object to begin with, and you can create your own classes -- the OOP-mechanism is in a sense "softer" and more malleable than in static-typed languages though. For example you can stick new methods onto individual objects at runtime.

Then there is Lisp, which decouples methods and the data hierarchy more, and allows for multiple dispatch and method combinations... you this stuff up, you'll be surprised. :)

---

### Post by Can+~ on 2009-07-04
> **Darkspark said:**
> Oh, and C does not support classes.

You can create classes in any language, if that language provides you with the "class" statement to do it nicely, it's another story. 

Paradigms can be implemented as a fundamental rule for the language, but that doesn't stop you from creating it yourself. In fact, C has a very simple and raw way to do Polymorphism.

[PHP]#include <stdio.h>
#include <string.h>

typedef struct
{
	// Common properties
	int common_number;
	char common_string[20];
}common;

typedef struct
{
	// Common properties
	int common_number;
	char common_string[20];
	
	int x, y, z;
}type_a;

typedef struct
{
	// Common properties
	int common_number;
	char common_string[20];
	
	char name[20];
}type_b;

void printData(void *common_stuff)
{
	// Oh no! it's a void type! What should I do?
	
	// Cast!
	common *something = (common*)common_stuff;
	
	printf("common number: %d\ncommon string: %s\n", something->common_number, something->common_string);
}

int main(int argc, char **argv)
{
	type_a samplea;
	type_b sampleb;
	
	// Set up some common values
	samplea.common_number = 15;
	strcpy(samplea.common_string, "Hello world!");
		
	sampleb.common_number = -5;
	strcpy(sampleb.common_string, "Goodbye world!");
	
	// Set up individual values
	samplea.x = 5; samplea.y = 7; samplea.z = 63;
	strcpy(sampleb.name, "I'm sample B!");
	
	// Now pass it
	printData(&samplea);
	printData(&sampleb);
	
	return 0;	
}[/PHP]

Why did it work? Because we assumed that the first blocks on memory are of a certain type (in fact, we know that, the compiler does not)

---

### Post by CptPicard on 2009-07-04
An interesting aside here is to consider that of course anything from some Turing-complete language can be implemented in any other Turing-complete language, but it's a matter of how hard it is. OOP is typically either implicit (and more or less explicit in addition) in a higher-level language, but if you consider something like functional programming, getting proper higher-order functions and closures forces you to write a huge amount of interpreter in a language that does not have them from the start... interestingly, object-oriented programming still falls out almost trivially as an application of storing data in closures and dispatching via calling the lambda expression...

---

### Post by scourge on 2009-07-05
I've been having interesting times with Common Lisp lately. I had to learn some basics of it on a uni course, and I decided to dive a bit deeper. The first thing I noticed was that it would take quite some time to become as productive with Lisp as I am with Python and C++.

I seem to have some mental blocks which prevent me from writing good Lisp code, maybe due to years of imperative programming. For example I keep using the loop function and iterator variables a lot instead of recursion, and I didn't really understand why there needs to be a function that returns a list with the first element removed (cdr). I'm currently practicing by implementing common algorithms like quicksort, and some of them have been really easy to write in Lisp. So I'm getting better and I can see how learning Lisp could make me a better programmer. But when it comes to pushing real applications out in the open I'll probably rely on C, C++ and Python for a long time.

---

### Post by Reiger on 2009-07-05
> **CptPicard said:**
> interestingly, object-oriented programming still falls out almost trivially as an application of storing data in closures and dispatching via calling the lambda expression...

Heh, anyone who's had a bit of fun implementing stuff in JavaScript (where the problem of contradicting and mutually incompatible implementations is a serious issue) will probably agree with that... And consider the common technique of returning closures as Interface:
layer(troubleSome)(params);

With layer being something like:
```

function layer(troubleSome) {
 switch(troubleSome) {
   case 'foo' : return function(params) { /* do stuff here */};
   case 'bar' : return function(params) { /* do stuff here */};
   default : return function(params) { /* empty: hey we have the abstract class/adapter thing here! */ };
 }
}

```

Essentially we have a raw implementation of what is know in Java as `Interface'.

In Java you'd write:
```

interface Layer {
 [some type here] troubleSome(params);
}
abstract class DefaultLayer implements Layer { /* code here* /
} 
class Foo extends DefaultLayer {
  [some type here] troubleSome(params) {/ * code here */ }
}
/* etc */

```
And then you still have to do initialization, which is simplified to the single chained function call, but to get the same out of Java you have to implement some kind of `decision maker' code.

---

### Post by JoshuaOne on 2009-07-05
Hi, I like to start learning programming, i buy the book Beginning Linux Programming 3rd edition, (like to work with GCC
I realy do not know what to compile, please help me
Thansk anyway,

Greetings JoshuaOne

> **credobyte said:**
> Ok, so .. It's been a while when I first started to learn programming and it's time to choose - what do I need. In the last few months I've tried almost all languages ( just kidding ) - C, C++, Java, Python. Everything looks nice and I've found a few great things in all of these languages, BUT, I'm not sure about one thing .. which one is the most perspective language for starting to build up my career as a programmer ( I've been working with PHP for 5 years and looks like it's a *waste of time* ) ?
I know, it can take a while, but, I need your opinion. What would you choose ? Which one should be ( and "will" be ) the hottest ( job opportunities ) language in the future ( 5, 10 years .. ) ?

**Note:** This is not another "best programming language" thread. I'm interested in long-term benefits.

---

### Post by CptPicard on 2009-07-05
> **scourge said:**
> The first thing I noticed was that it would take quite some time to become as productive with Lisp as I am with Python and C++.

It's the same thing with all "paradigm shifts". I currently find Lisp to be extremely fast to write stuff in, but Python admittedly comes close... the problem with Python is that when there is a performance issue, in Lisp you can at least rewrite stuff to be faster...

> 
I seem to have some mental blocks which prevent me from writing good Lisp code, maybe due to years of imperative programming.

The thing behaves somewhat differently but I must admit that after really "getting"  Lisp a few years back I just don't understand why someone would design a programming language like C++. The idea of for example sticking code into singly-dispatching objects starts feeling a bit weird ;) 

> 
 For example I keep using the loop function and iterator variables a lot instead of recursion

Not such a stylistic faux pas in Common Lisp (like it would be in Scheme which really discourages not recursing). Macros really are used heavily, and "loop" is common. This is in particular because the standard at least didn't(?) mandate tailcall optimization, but of course in practice any worthwhile implementation does it.

> 
and I didn't really understand why there needs to be a function that returns a list with the first element removed (cdr).

Well to be exact it returns the other element of the pair.. :) and it's interesting how you can build all kinds of stuff only by being able to put "two things together"...

> So I'm getting better and I can see how learning Lisp could make me a better programmer. But when it comes to pushing real applications out in the open I'll probably rely on C, C++ and Python for a long time.

It's the practicality vs. elegance thing... mostly the issue is with lack of libraries, but that is because Lisp has been such a niche thing for such a long time. I am glad to see it enjoy a resurgence in popularity though... there are for example Qt bindings being developed, and really, that should be such a good fit for CL :)

---

### Post by scourge on 2009-07-05
> **CptPicard said:**
> ... the problem with Python is that when there is a performance issue, in Lisp you can at least rewrite stuff to be faster...

I never use Python for anything performance-critical. But I got the impression that Lisp can be pretty fast. Then again, writing high-performance code requires careful design in any language, so optimizing Common Lisp code isn't probably much easier than optimizing C. I'm talking about low-level optimization of course.


> The thing behaves somewhat differently but I must admit that after really "getting"  Lisp a few years back I just don't understand why someone would design a programming language like C++. The idea of for example sticking code into singly-dispatching objects starts feeling a bit weird ;)

After having read Thinking in C++, C++ makes a lot more sense to me as a system programming language than it did before. Multiple dispatch is one of the features that were considered for C++, but had to be dropped mainly for performance reasons. The same applies to many other features that would make C++ easier, like having a common superclass for all user-defined classes.

> This is in particular because the standard at least didn't(?) mandate tailcall optimization, but of course in practice any worthwhile implementation does it.

One would think that going crazy with recursion (like Lispers often seem to do) could be pretty dangerous without tail call optimization.


> Well to be exact it returns the other element of the pair.. :) and it's interesting how you can build all kinds of stuff only by being able to put "two things together"...

That's one of the things I hadn't done much with any other language. It's definitely cool how much can be achieved with just car and cdr and recursive function calls.


> It's the practicality vs. elegance thing... mostly the issue is with lack of libraries, but that is because Lisp has been such a niche thing for such a long time. I am glad to see it enjoy a resurgence in popularity though... there are for example Qt bindings being developed, and really, that should be such a good fit for CL :)

For most of my projects easy distribution to end-users and good cross-platform library support are more important than language features. It's about time CL gets Qt bindings.

---

### Post by CptPicard on 2009-07-05
About the CL+Qt combo... just imagine how cool it must be to work on a live Lisp image that has Qt widgets in it with whose signals/slots you can mess with hopefully while your app is running... *drool*. Finally, GUI development that probably does not suck. ;)

---

### Post by jpkotta on 2009-07-07
> **Reiger said:**
> 
NO. That is *very* wrong. First of all Debian uses Dash (Debian's implementation of Ash) which is a lot more lightweight for the /bin/sh shell. This is because init scripts and such like do not need fancy terminal output and other such capabilities, which makes bash a bit overkill and its cost in speed not worth the features. By default all *sh scripts are executed through /bin/sh for efficiency.

Furthermore if you want your scripts to be portable you should not write bash but you should write POSIX sh. This will be your best bet at ensuring compatibility across a wide array of sh implementations.

Bourne shell is **not** the same as Bash.  Bash is the Bourne *Again *shell.  Dash most certainly is an implementation of Bourne shell.  So is Bash, but it's not very strict about it and will let you use bashisms without warnings or errors.  I suppose I should have said "learn POSIX-compliant Bourne shell".

---

### Post by monkeyking on 2009-07-07
Without trying to start a flamewar, and without being obnoxious.

I've never understood why people want to use lisp, the only reason would be to be able to understand these strange copy pastes for the .emacs that are found everywhere.

All these parenthesis looks arcane, like some less intrusive version of brainfuck [http://en.wikipedia.org/wiki/Brainfuck#Examples](http://en.wikipedia.org/wiki/Brainfuck#Examples)

If the OP wants to be sure of a job opportunity in 5 years,
I would say that the safest choice would be c/c++.
Not because its the best, but because its widespread.

But even more importantly I would say the parallelle computing and cluster programming is the future (for c/c++).
Threads, mpi and so on.

But also cobol which is the defacto language in the banking industry is not very likely to become obsolete.
This is a safe bet.

Depending on the background, the tools used within the biotech industry(R,bioconductor) would also be quite good to learn.
But this not really for codemonkeys but for the academic inclined

---

### Post by unknownPoster on 2009-07-07
> **monkeyking said:**
> Without trying to start a flamewar, and without being obnoxious.
 
I've never understood why people want to use lisp, the only reason would be to be able to understand these strange copy pastes for the .emacs that are found everywhere.
 
All these parenthesis looks arcane, like some less intrusive version of brainfuck [http://en.wikipedia.org/wiki/Brainfuck#Examples](http://en.wikipedia.org/wiki/Brainfuck#Examples)
 
If the OP wants to be sure of a job opportunity in 5 years,
I would say that the safest choice would be c/c++.
Not because its the best, but because its widespread.
 

 
 
I definitely agree on the c/c++ part. Also, at the end of every semester for the past 2 years, my University has sent out mass emails searching for a COBOL programmer. So if you can master that language, I'd imagine you could easy find a job some where...
 
Anyhoo, to the LISP part...
 
I'm not a skilled Lisper by any means, but I am enjoying learning it. Coming from my programming background, all C, C++, and Java, my first impressions of LISP are as follows:
 
[LIST]
[*]It's very concise, one function in C which would take many lines can only take 2-3 in LISP, granted that could be said for Python or any other higher level language...
[*]It's syntax is very elegant and easy to read, once you begin to "not see" the parens.
[*]One of the most interesting things I have found in LISP is SLIME, granted my interpretation of it may be a bit off, but in a properly set up LISP environment, the programmer is able to modify functions/programs WHILE they are running. One doesn't have to incessantly go through the compile/debug process as you would with C.
[*]Coding errors do not completely throw off the program. In C, one misplaced character can cause your program to completely halt, while in LISP, the debugger just prints out the error, but then continues the the next highest level of execution.
[/LIST]Forgive me if my interpretations of LISP are wrong, but this is how I feel after spending about 2 weeks with LISP.

---

### Post by CptPicard on 2009-07-07
> **monkeyking said:**
> 
I've never understood why people want to use lisp, the only reason would be to be able to understand these strange copy pastes for the .emacs that are found everywhere.

All these parenthesis looks arcane, like some less intrusive version of brainfuck

I have never understood why some people whose central complaint about Lisp seems to be the *parenthesis* (a core enabling feature of the language mind you) seem to think they actually have a valid take on other people's interest in Lisp... ;)

I have actually read *intelligent* criticisms of Lisp, but these aren't it.

> 
But even more importantly I would say the parallelle computing and cluster programming is the future (for c/c++).
Threads, mpi and so on.

Hmm... if one really is interested in what kind of things are truly (theoretically) important in parallel/multicore computing, one should direct one's attention to functional programming... the C/C++ view (actually, most stateful langauges' view) on it can get messy and difficult fast.


> **unknownPoster said:**
>  
Anyhoo, to the LISP part... ... Forgive me if my interpretations of LISP are wrong, but this is how I feel after spending about 2 weeks with LISP.

Hooray, someone who gets it. Now, get on with understanding why the code-is-data duality really is important (macros), why it is interesting that all you essentially need is closures and function definition/application mechanism... actually, those alone let you do pretty much anything, and theoretically, you could build everything you have in Lisp based on them and then some nice syntax-tree mangling using the macros...

Programming is symbolic abstraction. Rest is details.

---

### Post by nvteighen on 2009-07-07
> **CptPicard said:**
> 
Programming is symbolic abstraction. Rest is details.

This quote should be saved as a Sticky.

---

### Post by martinvahi on 2013-04-26
As of spring 2013 it seems that the web software will consist of 2 parts: client side and server side.

The server side is probably done in Java, using the Spring framework. The safe bet for client side is pure JavaScript. Thanks to the node.js the server software can also be written in JavaScript and that saves a lot of development effort, because string processing functions and a lot of other utility code can be written once and run at both sides, server side and JavaScript side.

Unlike Java, the JavaScript has native, designed-in, full Unicode support. As of 2013 Java has proper Unicode support "hacked in" after the "committee" came to a self-evident conclusion that 2 bytes is not enough to represent all world characters. 2013 era JavaScript implementations use the runtime compilation that Java once pioneered. As of 2013 2 major web browsers support hardware accelerated 3D in the form of WebGL and there exists JavaScript based software that reads in game maps of some classical first person shooters.

As of 2013 I believe that till about 2025 business application software will probably be done in JavaSript.

What regards to the system programming, then a statically typed, compile-time optimized, optimized to the metal type of language that has a lot of convenience features is the answer. C++ seems to be the only such language out there. C++ has a huge "package" (history), weird old-fashioned features and mishaps, but that just shows, how extensively the C++ has been used in exactly that role: static, compile-time analysis based, extensively optimized to the bare metal and rich with features.

The issue with the system programming is that it is a niche area. It does not seem to have much perspective due to an extremely small market (if I dear to say so while literally every application program depends on system software). Reality check: how many people do You know, who have written file system drivers, kernel code, low-level database drivers, printer/scanner/photo-camera firmware, video/image/sound codecs, database engines, decoding of UDP packets, car engine control software, elevator software, security electronics firmware, video card drivers, WiFi card drivers?

As of 2013 the embedded market seems to be on a rise, but that happens in China and embedded electronics projects assume huge investments and sales, which is not feasible to small companies. Small-scale production products are pretty expensive and have a possibility to use more expensive electronics that can probably do the job by running high-level, interpreted, programming languages.

One of the problems of the system programming is also the fact that it is pretty much at the end of the value chain. End users pay for application software or hardware (like printers, scanners) and then the application software developers or hardware developers should, somehow, miraculously, finance the system software development, or mega-corporations and states finance compiler/kernel/stdlib/etc development.

The states participate in system software development by financing universities. Universities have always been under-financed. Mega-corporations, like Microsoft, IBM, etc. probably do not have that many positions available for projects that just improve development. As the saying goes: if You want to sell, be a pain killer, not a vitamin. The way, how system software helps to increase the sales of application software or saves development cost, is pretty impossible to understand to managers that do not code themselves and worry about meeting profit requirements and deadlines. Most likely the managers nod politely and acknowledge that the system software is important, but consider it a low priority issue, which also determines the resources spent on it.

C++ is probably the language of the war industry. "Smart" munitions are probably something, where it's beneficial to keep the cost of electronics cheap. Nonetheless, the wizards of kings (and smaller mafia) have always had the threat of being "tied to a bridge next to a bomb" during the retreat of their kings, e.g. "no loose ends" left behind.

A third perspective is that some languages, like the PHP, continue to be popular due to the fact that they are easy to use for novice programmers, web-developers, hobbyists. PHP has terrible syntax, myriad of design flaws (the Unicode support hack, dumb default config, etc.), sloppy implementation (RAM usage, assign by value, etc.) but solid database connectivity. If sites like the Wikipedia run on such languages, then the languages, in this case, PHP, will not go extinct too soon. For example, in 2013 the PHP is much safer to use for enterprise software than the much saner Ruby, because the database connectivity of Ruby is quite shaky, exotic, unreliable from support point of view.

Thank You for reading. :-)

---

