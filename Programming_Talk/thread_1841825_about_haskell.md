---
title: "about haskell"
date: 2011-09-10
forum: Programming Talk
---

### Post by shubham1 on 2011-09-10
i want to know about haskell is it a compiler language.
i use php with mysql.
is haskell easy than c++ is it faster
some very good editors for haskell can you tell me is haskell
how can i run haskell programs i run c++ programs in codeblock
without compiling how will i test
who uses haskell
how can i test the source in a browsre lke in php is it possible i heard about this is haskell website.
is it good alternative to java too
will you recommend me it 
please also tell some usefull software , compilers , browsres , editors or any software for haskell development.
can i write executables in php.
i herad about mobile applications in php.
it would be best to write in php but what to install how to start how to test.

---

### Post by psld on 2011-09-10
i want to know about haskell is it a compiler language.
Compiler language? It is a functional language, it is good for writing compilers among other things.

is haskell easy than c++ is it faster
It is a bit different than other languages you might be used to, but when you know it it is easier than C++ and you get like 1% of the bugs and lines of code.

some very good editors for haskell can you tell me is haskell
Dont know, I use vim.

how can i run haskell programs i run c++ programs in codeblock
without compiling how will i test
Haskell has an interpreter, GHC.


who uses haskell
Not very used in the industry.

how can i test the source in a browsre lke in php is it possible 


i heard about this is haskell website.
?

is it good alternative to java too
For some things, like compilers.

will you recommend me it 
Yes, it is nice.

please also tell some usefull software , compilers , browsres , editors or any software for haskell development. 
Everything you need is at the official website haskell.org

---

### Post by shubham1 on 2011-09-10
[B]you get like 1% of the bugs and lines of code.
what do you mean by this
can haskell be used to write softwares
is haskkell like php with many inbuilt functions and lucid syntax
do you use it
[/B]_*can i use php to make software or mbile software it will be the best to make throught php.*_

---

### Post by shubham1 on 2011-09-10
run exe in php

---

### Post by nvteighen on 2011-09-10
What is this about? PHP or Haskell? Man, this is possibly the first time in history those languages have been put together...

Haskell is a natively compiled (code written in it gets transformed into native binary), pure-functional (meaning that there's no state... well, there is with Monads... ok, it gets complicated), static-typed language...

PHP is completely different, mainly used for web applications, dynamic websites... You can create local scripts with it, but most people don't use it for that.

Care to explain what you're asking about? If you want a language to write a compiler, you can do that in any (but I would recommend something built around C and ASM... maybe with parts written in something else, higher-level).

---

### Post by karlson on 2011-09-11
> **shubham1 said:**
> i want to know about haskell is it a compiler language.

[http://www.haskell.org/ghc](http://www.haskell.org/ghc)
> 
i use php with mysql.
is haskell easy than c++ is it faster

What does PHP and MySQL have to do with Haskell?  The functional paradigm is quite different from what you might be used to with PHP and c++.  As far as speed of C++ and Haskell you might just want to test them head to head to see which one is faster.
> 
some very good editors for haskell can you tell me is haskell
how can i run haskell programs i run c++ programs in codeblock
without compiling how will i test


I think you are looking for an IDE rather then an editor and I'd check to see if the more commonly used ones like Code::Bloks have a plugin for Haskell.  Futhermore debugging a C++ program without compiling to my knowledge is only possible with ROOT's C++ interpreter.  So I am not sure what you are talking about.  I am sure that Haskell provides a debugger facility as most other languages do.
> 
who uses haskell

See this:
[http://ubuntuforums.org/showthread.php?t=1829002](http://ubuntuforums.org/showthread.php?t=1829002)
> 
how can i test the source in a browsre lke in php is it possible i heard about this is haskell website.

Can you clarify what you mean?
> 
is it good alternative to java too

To do what?
> 
will you recommend me it

See the question above.

> 
please also tell some usefull software , compilers , browsres , editors or any software for haskell development.

[http://www.haskell.org](http://www.haskell.org)
> 
can i write executables in php.
i herad about mobile applications in php.
it would be best to write in php but what to install how to start how to test.

You are jumping around a bit so I suggest you clarify the following in your thoughts.

1.  Why do you want to use Haskell?
2.  Is the problem you are trying to solve will be solved better with Haskell?
3.  Is this a project that will be used or is it just a mental excercise?
4.  If this is an application you are trying to distribute who will support it? And even better who will extend it?

---

### Post by shubham1 on 2011-09-11
i use php but i heard this in forum but i dont remember the link.

---

### Post by shubham1 on 2011-09-11
> **karlson said:**
> [http://www.haskell.org/ghc](http://www.haskell.org/ghc)

What does PHP and MySQL have to do with Haskell?  The functional paradigm is quite different from what you might be used to with PHP and c++.  As far as speed of C++ and Haskell you might just want to test them head to head to see which one is faster.


I think you are looking for an IDE rather then an editor and I'd check to see if the more commonly used ones like Code::Bloks have a plugin for Haskell.  Futhermore debugging a C++ program without compiling to my knowledge is only possible with ROOT's C++ interpreter.  So I am not sure what you are talking about.  I am sure that Haskell provides a debugger facility as most other languages do.

See this:
[http://ubuntuforums.org/showthread.php?t=1829002](http://ubuntuforums.org/showthread.php?t=1829002)

Can you clarify what you mean?

To do what?

See the question above.


[http://www.haskell.org](http://www.haskell.org)


You are jumping around a bit so I suggest you clarify the following in your thoughts.

1.  Why do you want to use Haskell?
2.  Is the problem you are trying to solve will be solved better with Haskell?
3.  Is this a project that will be used or is it just a mental excercise?
4.  If this is an application you are trying to distribute who will support it? And even better who will extend it?
i want to use haskell for running exe ie creating softwares
i get that haskkell is easy than c++
			 				is it good alternative to java too 			 		
this means that could haskkell replace java and do thw work of java 
haskkell is a funcional programming language so is it not like c++ could it not do the work of c++

---

### Post by shubham1 on 2011-09-11
thanks for the links

---

### Post by karlson on 2011-09-11
> **shubham1 said:**
> i want to use haskell for running exe ie creating softwares

Don't mean to be rude but aren't all programming languages are used to create software?
> 
i get that haskkell is easy than c++

To You or in general?
> 
is it good alternative to java too

I am going to ask the same question I asked before: To do what?
> 
this means that could haskkell replace java and do thw work of java 
haskkell is a funcional programming language so is it not like c++ could it not do the work of c++
So can Java, C#, Perl, PHP, Python, Ada, PL/I, ALGOL, PASCAL, Oberon, Modula and most other languages one can think of given appropriate libraries but that doesn't mean that one would use them for the task at hand.

If you have your mind set to do something in Haskell, why don't you just do it rather then asking whether or not it can be done?

---

### Post by shubham1 on 2011-09-11
> **karlson said:**
> Don't mean to be rude but aren't all programming languages are used to create software?

To You or in general?

I am going to ask the same question I asked before: To do what?

So can Java, C#, Perl, PHP, Python, Ada, PL/I, ALGOL, PASCAL, Oberon, Modula and most other languages one can think of given appropriate libraries but that doesn't mean that one would use them for the task at hand.

If you have your mind set to do something in Haskell, why don't you just do it rather then asking whether or not it can be done?
in comparision of java in creating hashing and encrypting algorithm
_***So can Java, C#, Perl, PHP, Python, Ada, PL/I, ALGOL, PASCAL, Oberon,  Modula and most other languages one can think of given appropriate  libraries but that doesn't mean that one would use them for the task at  hand.***_
can php do the work of c++

---

### Post by karlson on 2011-09-11
> **shubham1 said:**
> in comparision of java in creating hashing and encrypting algorithm


Programming Language is a tool implementing an algorithm on a computer.  So the question is whether or not an Algorithm implemented in Java will run faster then the one implemented in C++ and Haskell.

> 
can php do the work of c++

Not sure what you mean here.  Like what?  write a library for PHP that would do same thing that you are doing in C++ and you have the ability of doing the same  thing.

I just doing see a point of using a Web Server include language to be used as let's say for GUI development.

---

### Post by shubham1 on 2011-09-12
php is a server side programming langauge
can you tell me how to get started in haskkell what to install waht is the extension of haskell
will there be regular updates of haskell please tell me how to start 
haskell is a functional programming language ????? what is functoonal programming language
is haskell not a compiler language i want haskell to run exe and create softwares

---

### Post by karlson on 2011-09-12
> **shubham1 said:**
> php is a server side programming langauge

So what?
> 
can you tell me how to get started in haskkell what to install waht is the extension of haskell

Open aptitude/Adept/Synaptic and search for "haskell"
> 
will there be regular updates of haskell please tell me how to start
haskell is a functional programming language ????? what is functoonal programming language

[http://www.haskell.org](http://www.haskell.org)

> 
is haskell not a compiler language i want haskell to run exe and create softwares
See above.

---

### Post by slavik on 2011-09-12
Subham, this is not a forum where you will be spoon fed information at a rate that pleases you. If you have specific questions/difficulties relating to haskell, feel free to ask after consulting the vast information available on the world wide web (tell us which of those things don't make sense to you).

---

### Post by shubham1 on 2011-09-13
thanks all

---

