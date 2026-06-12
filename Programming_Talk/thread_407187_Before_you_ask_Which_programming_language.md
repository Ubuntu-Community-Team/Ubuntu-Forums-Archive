---
title: "Before you ask: Which programming language?"
date: 2007-04-11
forum: Programming Talk
---

### Post by samjh on 2007-04-11
Quite a lot of people ask about which programming languages should be used, what GUI toolkits, etc.

There have been many occasions where such discussions turn into flamewars.

Before asking such questions, please ensure you use the SEARCH function to look for related topics.  You can also consult the excellent thread: [How to start programming - guides and links for many languages](http://ubuntuforums.org/showthread.php?t=333867).

Understand that programming languages are like construction materials.  Specific materials are used for specific buildings.  You do not use wooden frames for a 100-storey sky scraper.  You also do not use reinforced concrete for a garden shed.  You CAN use those materials, but they are not the best choices.

Programming languages are divided into several "levels".  Each level indicates how closely the language interacts with the computer hardware.  The closer to the hardware a language is, the more difficult it is to use for a programmer.  Languages that try to detach a programmer from the hardware are higher-level, and are easier to use.

Low-level languages allow the programmer to have specific control over the hardware.  There is more micro-management needed for the programmer, and the programmer needs greater understanding of hardware operations than when using higher-level languages.  Therefore, low-level languages are good for developing operating systems, device drivers, and other software that need direct access to hardware facilities.  This type of programming is known as "Systems Programming".

Higher-level languages tend to take care of hardware-specific operations by themselves, and allow the programmer to concentrate on other matters.  These languages are usually easier to use than low-level languages, and are most often used for computer application software, like word processors, web browsers, etc.  This type of programming is known as "Application Programming".

There also exist languages that are very far detached from hardware, or even a particular operation system.  These kinds of languages sometimes focus on interacting with the Internet, or otherwise act as "scripts" for performing tasks similar to application programs.  These are collectively known as scripting languages.  The most common uses of these languages are "Shell Scripting", "Macros", and "Web Programming".

You may ask about speed of these languages.  Remember that most programs don't need to run fast.  But as a general rule of thumb, low-level languages are faster than high-level languages.  Keep in mind that many high-level languages allow low-level programming languages to be integrated into its programs, to compensate for their lack of speed.

Some languages are multi-purpose, and may serve in Systems Programming as well as Application Programming, or Application Programming and Web Programming.

(There are other, more specialised categories.  These include Artificial Intelligence, Database Management, etc.  These will not be discussed here.)

The key is to identify what you want to program, and which tool is best for you.

Here are some languages for each of the above categories.  It is not an exhaustive list, but only lists historically and industrially important languages, and languages that can be used on Linux/Unix.  Some languages appear in more than one category.  I have only listed languages in the *most often used categories*, even if some languages are capable of other rare uses.

**Systems Programming:**

Ada, Assembly, C, C++, Machine Language, Objective-C, Object-Pascal, Pascal, PL/1

**Application Programming:**

Ada, BASIC, C, COBOL, Common Lisp, C#, C++, Fortran, Java, Lisp, Lua, Objective-C, Object-Pascal, Pascal, Python, SmallTalk, Visual Basic .NET

**Web Programming:**

ASP (and ASP.NET), ECMA Script (eg. JavaScript), Flash ActionScript, Java (and JSP), JScript, Perl, PHP, Python, Ruby

**Shell or Application Scripting:**

Bourne Shell, C Shell, Common Lisp, Lua, Python


Aside from the hierarchy of "levels", languages are also divided along their features.  While searching for an appropriate programming language for your task, you will come across several features that are commonly used to describe languages.  A brief outline of the most common buzzwords are listed here.

**Dynamic-typing:**
Allows the use of data without the need for a programmer to specify what type of data it is (eg. integers, floating point numbers, characters, etc.).  Usually a feature of very high-level languages like Python and Ruby.  It makes the languages easy to use, but requires careful testing because errors can occur when incompatible data are operated together (such as adding an integer to a character).

**Static-typing:**
Requires that the programmer specify what type of data is used.  For example, a variable *x* may be an integer, so the programming needs to declare that.  Usually reduces productivity slightly, but with the benefit of producing self-explanatory code.  Still requires careful testing because errors may be produced when incompatible types are operated together.

**Type enforcement:**
The programming language checks for compliance to a declared type.  For example, a compiler or interpreter will realise that if *x* is an integer, then assigning a letter as its value is illegal, and will warn the programmer.  Some language have "strong" type enforcement, which catches many such mistakes (eg. Java).  Other languages have "weak" type enforcement, and may allow such mistakes to slip by (eg. C) until the program is run.

**Garbage collection:**
Most low-level programming languages, and some high-level ones, require the programmer to specify when to set aside and taken back memory reserved for particular pieces of data.  This is called manual or explicit memory management, and is normally required when using complex or large data.  Many high-level languages now use automatic memory management, also known as "garbage collection", which uses an automated process to keep track of memory used by a program's data and frees memory that is no longer needed automatically, without having the programmer specify when and how to do it.  Up until several years ago, garbage collection was process-intensive - ie. it caused slower program execution than manual memory management.  But technology has caught up so that some of the better implementations of garbage collection have very little speed penalties.  Still, in general, garbage collectors do impose some speed penalty.  Most automatic memory management is found in interpreted programming languages, or languages which operate in a "run-time environment" (ie. software that acts like a computer within a computer, for running programs written using a particular programming language).
Obviously, manual memory management makes for more difficult programming, with usual benefit of increased performance.  Garbage collection makes for easier programming, but usually with slight loss in performance.

**Object-oriented programming:**
A language feature which allows data, functions, and procedures, to be incorporated into self-contained modules.  These modules are called "objects".  All objects belong to "classes", which dictate what data, functions and procedures the object contains.  For example, a "Draw" object may include data about colours and texture, and functions and procedures for drawing shapes or changing colours.  Object-oriented programming makes designing some kinds of programs easier than using other models.

**Structured programming:**
A programming philosophy which emphasises systematic design and implementation of code using a modular approach to design, and the usage of set processes.  Structured programming languages all support the use of "sequence", "selection", and "repetition" to control how the program behaves.  Structured programming also encourages designing programs according to top-down or bottom-up approaches.  Top-down means designing the program first as a whole entity, and then breaking up the entity into small modules for more detailed design.  Bottom-up means designing small modules first, that will eventually join together to form the total program.


For more information, Wikipedia provides an excellent resource for finding out about various programming languages and their features:
[http://en.wikipedia.org/wiki/Category:Programming_language_topics](http://en.wikipedia.org/wiki/Category:Programming_language_topics)

Wikibooks also has various tutorials for many programming languages:
[http://en.wikibooks.org/wiki/Wikibooks:Programming_languages_bookshelf](http://en.wikibooks.org/wiki/Wikibooks:Programming_languages_bookshelf)


Before you start any thread about "which language should I choose", be sure to clearly state WHY you want to start programming, and what kinds of programs you are interested in creating.

If you want to write device drivers or work on the Linux kernel, then choose a Systems Programming languages (C is the language used for the Linux kernel and its drivers).  If you want to write web applications, then choose a Web Programming languages.  If you want to write nifty applications to do cool things on your desktop, choose an Application Programming language or Application Scripting language.  The choices go on...

---

### Post by pmasiar on 2007-04-11
Excellent, let's try to keep this discussion without flamewars, so it can become a sticky. Maybe discussion can be in different thread, to keep this one cleaner. OR just PM poster for small addition/misunderstandings

It does not make sense to ask "which" language is better in general - languages are specialized tools - each specialized in their areas. There is no solver bullet. Languages were designed to solve problems in some specialized areas, and might be bad fit outside the intended area. Don't hammer the screw in - use screwdriver. We can discuss:
1) what is the niche, how wide or narrow it is, 
2) how good fit language is for the intended area, 
3) how area is changing and in which direction, 
4) what other contenders are emerging in each area. 
5) how hard it is to learn, how language scales from small projects to big ones
6) how widespread it is - it means support with libraries, help forums, etc.

Talking about the superiority of one language over another without mentioning what is intended usage area is as stupid as comparing cars: family sedan vs 18-wheel truck. Truck is good to haul vegetables from Florida, but not for daily commute :-) 

Lets look what we have:

[LIST]
[*]**Assembler:** copies processor architecture. But: processors implementing high-level languages are possible, like Forth and Lisp. So we will see.

[*]**C:** Layer on top on (traditional) assemblers. Almost as fast as Assembler, easier (but still rather hard) to code in. Couple hundreds of millions of lines of code was written in it, and that code will stay for very long time.

[*]**C++:** C with OOP. Slower than plain C, but helps manage big projects better. Same as C.

[*]**Java:** Goal was multiplatform high-level language like C++, but easier to code in, which you can distribute in binaries on many platforms. Now we are down to 3 main platforms (GNU/Linux, Apple Mac, Windows), and Java created reimplementation of most features of both. MS has own java-like language (C#) and has lots of motivation to make life of java on windows uncomfortable. Linux has all the tools java reimplemented, and now as java is GPL can cherry-pick and integrate the rest. But additional abstraction layer java adds does not make much sense for GNU/Linux: we distribute sources, not binaries. So my position is, although Java is rather popular now and for next 5-10 years, Java will become dead end like Cobol: target area evaporating.

[*]**C#:** MS own improved C++, competing with java. Although implementation for GNU platform exists (Mono), viability on other platforms is questionable (and certainly is NOT a goal for MS - quite the opposite, they see C# as tool for platform vendor lock). 

[*]**Forth:** high-level language designed to run directly on stack architecture of CPU. Extremely compact and fast interpreter: champion for devices.

[*]**Perl:** flexible text processing and system administration. Designed to be very expressive and flexible, like a human language. Big part of what other languages have in libraries is included as part of language - so language was designed to be flexible to be able to ignore big parts of it. As a result - way too much flexible to be usable for big projects. Still great for quick one-off ten-liners for sysadmin work, if you remember all the quirks. Pioneered dynamic typing and scripting approach in mainstream languages. Once was "duck tape of the internet", but losing mind-share. OOP was bolted on, and looks ugly.

[*]**Ruby:** Improved OOP Perl for web applications done right. Less quirky than perl, but you can feel perlishness. Popularity based on great web framework, Rails, which mainstreamed "conventions instead of configuration" approach. Rails did not invented Model-View-Controller paradigm, but made it popular. Especially java programmers, for so long struggling with static typing and overconfigured frameworks, liked and hyped it.

[*]**Python:** Universal dynamically typed multi-paradigm OOP language optimized to be readable and easy to learn, yet great for RAD (Rapid App Development). Although it is great for text processing, for some time neglected web applications (giving opening to Ruby). Catching up big time now.

[*]**PHP:** For creating web-pages by beginners. Because low skill level of average coders, bigger projects gets really messy. Idea of "code within the web page" was reimplemented for most other languages (including java, VBasic, and even python: yes you can have "Active Python Pages").

[*]**SQL:** standard for database access, transaction processing
[/LIST]
... and many more languages. Cobol, Fortran, PL/1, Ada, Pascal, Lisp, Erlang, Haskell, Logo, Smalltalk, Prolog, XSLT ... 8K+ of them.

So we have two big fuzzy areas:
* **Low-level systems programming,** with clear winners: Asm and C in their respective areas, optimized for processing speed (NOT for productivity in application development). Question is, with increase of CPU cores, they might want to do something else in core, like implement Forth in core.

* **High-level Application development,** where productivity is important, and most important speed is "speed to market". In that area, as CPU speed increases and prices fall, dynamic typing and interpreters (vs. compilers) become very popular.

---

### Post by Wybiral on 2007-04-12
> **pmasiar said:**
> But: processors implementing high-level languages are possible, like Forth and Lisp. So we will see

*Sits and waits* :)

---

### Post by Mirrorball on 2007-04-12
> **pmasiar said:**
> Because PHP does not know OOP...
This is not true. PHP does support OOP, especially PHP5.
[http://www.php.net/manual/en/language.oop.php](http://www.php.net/manual/en/language.oop.php) (OOP in PHP4)
[http://www.php.net/manual/en/language.oop5.php](http://www.php.net/manual/en/language.oop5.php) (OOP in PHP5)

---

### Post by marianom on 2007-04-12
Very good thread. Congrats samjh, pmasiar.

To enrich what has been said, let me mention a few more that I'm not sure if they fit in any of the categories given:
Database server-based procedural extensions: Oracle's PL/SQL (which is OO too by the way), Sql Server's T-SQL, PostgreSQL's PL/pgSQL.
They have the advantage that as they're in the server side and -in certain type of tasks- they're capable of do faster processing with huge amount of data (cursors et all).

---

### Post by maxamillion on 2007-04-12
kudos on the thread :D

---

### Post by pmasiar on 2007-04-16
> **pmasiar]  
But: processors implementing high-level languages are possible, like Forth and Lisp. So we will see[/quote]
[QUOTE=Wybiral said:**
> *Sits and waits* :)

[Lisp machine](http://en.wikipedia.org/wiki/Lisp_machine) - sold real Lisp machines in AI boom at the beginning of 1980. Went bankrupt in 1986, but some Symbolics 3600 machines are claimed be still in use.

[Forth](http://en.wikipedia.org/wiki/Forth_%28programming_language%29)  became popular 5 years later (as Forth79 and Forth83) and it is extremely easy to implement in a chip - simpler than any other high-level language. [This guy](http://www.ultratechnology.com/) still plays with Forth chip, he replaced $5 mouse chip with a Forth chip and has [PC in a mouse](http://www.ultratechnology.com/scope.htm) - for $10, same price as standard mouse. Problem is, nobody believes it is possible... :-(

---

### Post by pmasiar on 2007-04-21
Someone asking this same question again - can we make this sticky? Maybe more language comparisons (with cool head - no religions) will make this thread more useful?

---

### Post by barmazal on 2007-04-21
hopefully ppl will remain calm and just point their posts without attacking any other language.

What i use and why.

PHP - scripting language without proper IDE hosting it unlike Java and .NET which grew up from ASP, vary widely used, alot of systems build and open sourced, large support commmunity, does what i need since i generally dislike stuff like JAVA and .NET which inserts lines of code without to ask if i want it to.

PHP is easy to learn since it has thousands of tutorials and already done things and hosting of PHP is the cheapest amoung all other techologies.

I need just intellisense and autocomplete, seems PDT from Eclipse will do it when final released this summer.


Java Script, very important language for Web tehcnology which runs on client side, this allows you many manipulations such as statistics and most of all AJAXing
Action Script, used in Flash and very similar to Javascript so no problem there

Trying out now Ruby and Rails Web component, hopefully will like it more than PHP

---

### Post by pmasiar on 2007-04-22
to quickly compare different languages, see how they handle task beyond obligatory hello_world(): [http://www.99-bottles-of-beer.net/](http://www.99-bottles-of-beer.net/) shows how to print (in)famous song. So it includes non-trivial stuff like loops.

My favorite from [esoteric languages](http://en.wikipedia.org/wiki/Esoteric_programming_language), see also [top 25](http://www.99-bottles-of-beer.net/toplist_esoteric.html) 
- just 1 character, 9 in language [hq9+](http://www.cliff.biffle.org/esoterica/hq9plus.html)
- [this](http://www.99-bottles-of-beer.net/language-petrovich-812.html) solution by language [petrovich](http://www.dangermouse.net/esoteric/petrovich.html)
- [piet](http://www.dangermouse.net/esoteric/piet.html) has [pretty solution](http://www.99-bottles-of-beer.net/language-piet-1269.html)

Of course you want to see real languages - just search by name. 

I really like [Forth](http://www.99-bottles-of-beer.net/language-forth-793.html) version, it shows how conscise the language is, and how it builds new concepts from existing.

---

### Post by Wybiral on 2007-04-22
> **pmasiar said:**
> to quickly compare different languages, see how they handle task beyond obligatory hello_world(): [http://www.99-bottles-of-beer.net/](http://www.99-bottles-of-beer.net/) shows how to print (in)famous song. So it includes non-trivial stuff like loops.

My favorite from [esoteric languages](http://en.wikipedia.org/wiki/Esoteric_programming_language), see also [top 25](http://www.99-bottles-of-beer.net/toplist_esoteric.html) 
- just 1 character, 9 in language [hq9+](http://www.cliff.biffle.org/esoterica/hq9plus.html)
- [this](http://www.99-bottles-of-beer.net/language-petrovich-812.html) solution by language [petrovich](http://www.dangermouse.net/esoteric/petrovich.html)
- [piet](http://www.dangermouse.net/esoteric/piet.html) has [pretty solution](http://www.99-bottles-of-beer.net/language-piet-1269.html)

Of course you want to see real languages - just search by name. 

I really like [Forth](http://www.99-bottles-of-beer.net/language-forth-793.html) version, it shows how conscise the language is, and how it builds new concepts from existing.

My obfuscated C macro 99-bob...

```

#include <stdio.h>
#define f printf
#define b(x)f("%i bottles of beer"#x, i);
#define a(x)b()f(" on the wall. "#x);
#define d f("Take one down, pass it around, ");
#define c a()b(.\n)d--i;a(\n);
#define e char i=99; while(i){c};
int main(){e}

```

---

