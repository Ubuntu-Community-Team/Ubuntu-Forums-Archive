---
title: "The Perfect Programming Language"
date: 2009-08-25
forum: Programming Talk
---

### Post by jamescox84 on 2009-08-25
What would make the perfect programming language?  We all have programmed in one language or another.  We all love parts of a language, and hate other parts.  What ingredients would make a tasty language.  It could be something borrowed or something new.

**From C**
[LIST]
[*]Universal, write-once, run anywhere...  even where Java won't run.
[*]Compiles to efficient machine code.
[/LIST]

**From C++**
[LIST]
[*]Const-Correctness.  I really like this feature!
[*]Strong Typing (applies to all strongly typed languages).
[*]Templates.
[/LIST]

**From Java**
[LIST]
[*]Exception Safety.
[*]Big class library.
[/LIST]

**From Python**
[LIST]
[*]Simple tidy syntax (I like indentation for statement grouping, I mean you do it in C-style languages anyway).
[*]Interpreter makes debugging a piece of cake.  (This point applies to all interpreted languages)
[/LIST]

**From Ruby**
[LIST]
[*]Open classes.
[*]Closures.
[/LIST]

**From Lisp**
[LIST]
[*]No syntax (kinda), minimal syntax at least.
[*]Macros.
[*]Easy to implement domain specific languages.  Mainly due to the first point.
[*]REPL, makes it easy to test small chunks of code (although all interpreted language provide similar functionality).
[/LIST]

Just some food for thought, also are we just going to end up describing Lisp with square brackets?  Of course maybe the perfect programming language already exists, I've just perhaps never used it (for long enough).

---

### Post by pepperphd on 2009-08-25
The perfect language already exists, it is called Ook.

[http://www.dangermouse.net/esoteric/ook.html](http://www.dangermouse.net/esoteric/ook.html)

Okay seriously now, I'd like to add to your list of features to pull from other languages. From C++, pull function overloading. I love Python but not being able to have two versions of a function within one class bothers me.

---

### Post by Simian Man on 2009-08-25
C++ doesn't have strong typing, it has weak, static typing.

Strong typing means types can't be converted from one to the other in an erroneous way.  Static typing means the types are checked at compile time.  Python has strong, dynamic typing.  If you want strong, static typing, check out Ocaml or Haskell.  Actually you should check out those languages either way :).


[quote=pepperphd]Okay seriously now, I'd like to add to your list of features to pull from other languages. From C++, pull function overloading. I love Python but not being able to have two versions of a function within one class bothers me.[/quote]
I really dislike function overloading actually.  If there are two different functions, they should have different names in my opinion.

---

### Post by ibuclaw on 2009-08-25
There is no such thing as a "perfect language" ... only the "right language for the right job". Nothing more, nothing less.

... My favourite language as of this moment is D ...
Coming from a C/Perl background, it is so refreshing. Almost like I've finally found my middle ground language. :)

I must admit though, being on the more feature rich alpha compiler, you can run into strange bugs if your imagination is wild enough.

---

### Post by jamescox84 on 2009-08-25
Simian Man, yes your right C++ is not realy strongly typed, but then it's not as weak as C.  I will ammend to say it's type-safe, and that's what I like.

pepperphd, I think function overloading make alot of sense in an OOP language, but because the typing is dynamic in Python you couldn't realy implment the feature (assuming overloading to handle different typed arguments).  But you can make a function in Python check the type of the argument type() and you can use optional (arg='default'), variable (*args), and keyword (**kwargs) arguments to get around the restriction of differnt behaviour for different signitures, all be it in a altogether more messy way.

---

### Post by jamescox84 on 2009-08-25
tinivole, I agree with you sentiment.

> There is no such thing as a "perfect language" ... only the "right language for the right job".

But is this because we are always balancing expressive power with computing power.  If a language could be both executed fast, and be highly expressive, would it not at least be nearly perfect.  Do you not think there could be a language that is better than anything we already have?

---

### Post by Simian Man on 2009-08-25
Actually Ocaml satisfies most of your qualifications:

[quote=jamescox84]
From C

    * Universal, write-once, run anywhere... even where Java won't run.
    * Compiles to efficient machine code.[/quote]
Ocaml does not have the portability of C but, as it's implemented in C, it is extremely portable.  Moreover it offers a Java-style bytecode compiler/interpreter for binary portability.  Ocaml also compiles to fairly efficient machine code - not as much as C, but it's much faster than languages like Python or Lisp.


[quote=jamescox84]
From C++

    * Const-Correctness. I really like this feature!
    * Strong Typing (applies to all strongly typed languages).
    * Templates.[/quote]
In Ocaml, all variables are effectively constants by default, so this feature is even more important than it is in C++.  I already mentioned that Ocaml uses strong static typing.  It also features type inference which means that you do not even have to declare the types you use - the compiler will figure them out from the usage and use the most general type that will work.  If you like these three features, you'd love Ocaml.


[quote=jamescox84]
From Java

    * Exception Safety.
    * Big class library.[/quote]
Ocaml also has exception saftey and a surprisingly large standard library - though not as large as Javas.


[quote=jamescox84]
From Python

    * Simple tidy syntax (I like indentation for statement grouping, I mean you do it in C-style languages anyway).
    * Interpreter makes debugging a piece of cake. (This point applies to all interpreted languages)[/quote]
Syntax is debatable, but I find Ocaml fairly nice.  It also comes with an interpreter and a debugger that can actually step *backwards* through your code :).


[quote=jamescox84]
From Ruby

    * Open classes.
    * Closures.[/quote]
I don't know what open classes are (classes you can add methods to later?), but Ocaml doesn't have them I believe.  It does have closures and, do to its functional nature, many other functional features like pattern matching, lambdas, first-class functions...


[quote=jamescox84]
From Lisp

    * No syntax (kinda), minimal syntax at least.
    * Macros.
    * Easy to implement domain specific languages. Mainly due to the first point.
    * REPL, makes it easy to test small chunks of code (although all interpreted language provide similar functionality).[/quote]
Ocaml definately has syntax, but it comes with a preprocessor called camlp4 that allows for changing the syntax considerably.  It also comes with an REPL as I already mentioned.

There is no "perfect language", but I find Ocaml to be the best.  Using much anything tends to be a pain :).

---

### Post by hessiess on 2009-08-25
C is only ``write once, run everywere'' if you are extreamly cairful what libs you depend on. Personally I like C++ and Lisp (CL and Clojure). Haskell is weird.

And almost all high level languages have atleast some support for closures and lambdas, not just ruby.

Pythons syntax sucks, mixing tabs/spaces creates a syntax error.

> 
but it's much faster than languages like Python or Lisp.

Common Lisp can be as fast as C,  it just depends on the implementation and the use of type-hints

---

### Post by fishy6969 on 2009-08-25
COBOL every time (so long as the time is before the year 2000)

---

### Post by pepperphd on 2009-08-25
> **hessiess said:**
> 
Pythons syntax sucks, mixing tabs/spaces creates a syntax error.

Which is one reason Python is so readable.

---

### Post by JordyD on 2009-08-25
> **hessiess said:**
> mixing tabs/spaces creates a syntax error.

Which is good. It means you can find and fix your mixed tabs and spaces.

---

### Post by hessiess on 2009-08-25
> **JordyD said:**
> Which is good. It means you can find and fix your mixed tabs and spaces.

Which wouldn't be nesoserry if the language just used {}!

---

### Post by ibuclaw on 2009-08-25
> **hessiess said:**
> Which wouldn't be nesoserry if the language just used {}!

May I also add that the usage of TABS are not encouraged in the industry. As different systems/text editors treat tab differently, so you can't guarantee that how your code looks in one program will look the same in another.

I have set TAB as an autocomplete in Vim personally. Because I can. :)

```

imap <Tab> <C-P>
imap <S-Tab> <C-N>

```

---

### Post by Mirge on 2009-08-25
Still just learning Python, and I'm still on the fence about whether I like being forced to indent or not... I _always_ indent anyway, so it's not a huge bother, but my code looks kind of naked without braces marking blocks of code lol.

---

### Post by lisati on 2009-08-25
> **fishy6969 said:**
> COBOL every time (so long as the time is before the year 2000)

From COBOL program we can take the idea of self-documenting code. 

Any mind-reading languages out there which do what we want in preference to doing what we say?

---

### Post by uljanow on 2009-08-25
The perfect programming language is plain english. But there doesn't seem to be compilers for all platforms and architectures.

---

### Post by TheStatsMan on 2009-08-25
> **Simian Man said:**
> 
Syntax is debatable, but I find Ocaml fairly nice. 

I think syntax must be a personal thing. For a while, I really tried to like ocaml because I like the idea of it, but to me I found the syntax like fingernails on a black board.

---

### Post by kpkeerthi on 2009-08-26
> **jamescox84 said:**
> 
**From C**
[LIST]
[*]Universal, write-once, run anywhere...  even where Java won't run.
[/LIST]

Is this true? No compilation (on the target platform) required?

I can compile a Java source file to a binary (.class file) and run the same on IBM z/OS. Can this be done for C? (Compile a C source file in Windows to a .exe and run the exe on z/OS?)

---

### Post by jamescox84 on 2009-08-26
> **hessiess said:**
> And almost all high level languages have atleast some support for closures and lambdas, not just ruby.


This is true, there is no doubt that some of the features I listed fall under many languages, it’s just that I thought of them when I wrote that heading.

> **Simian Man said:**
> Actually Ocaml satisfies most of your qualifications

Simian Man, I will be looking at OCaml, sound very interesting, and yet another tool at my disposal.

> **tinivole said:**
> May I also add that the usage of TABS are not encouraged in the industry. As different systems/text editors treat tab differently, so you can't guarantee that how your code looks in one program will look the same in another.

I have set TAB as an autocomplete in Vim personally. Because I can. :)

```

imap <Tab> <C-P>
imap <S-Tab> <C-N>

```

If you use TAB to set the general indentation level, and space to indent further when continuing a line, no TABs after the first non-TAB character and TAB set to 8 characters.  I find this works well with most text editors.  I use this in C and C++ all the time, not C# or Java though, because it’s not cool.

> **uljanow said:**
> The perfect programming language is plain english. But there doesn't seem to be compilers for all platforms and architectures.

Not sure about this.  Natural languages are very ambiguous, but if you could live with the computer misunderstanding you now and then (arguably it does so when you use programming languages, although this is really always you not correctly expressing your intentions), this would open programming up to almost anyone.  I think when programming becomes a so simple and accessible that all users can do it, just like using a word processor, we will have our next computer revolution.  Will it be natural language that makes this happen, or perhaps something before that?  I hope it’s the latter mainly so it can happen sooner.

> **lisati said:**
> From COBOL program we can take the idea of self-documenting code. 

Any mind-reading languages out there which do what we want in preference to doing what we say?

Code as documentation, should make the list.
Mind reading, defiantly, but only when the technology arrives, say… 2-3years.  :)

> **kpkeerthi said:**
> Is this true? No compilation (on the target platform) required?

I can compile a Java source file to a binary (.class file) and run the same on IBM z/OS. Can this be done for C? (Compile a C source file in Windows to a .exe and run the exe on z/OS?)

Sorry, a little sarcasm there.  Of course a compiled C program won't run on anything but the arch + os, it was targeting (unless it targets a VM).  However I would still argue that C is more portable, as long as you stick to standard C and it's standard libs.

Which reminds me:
**From Java**
[LIST]
[*]Universal binarys, that can run unmodified on any architecture supported by a runtime VM.  (Available in many other languages as well)
[/LIST]

---

### Post by kpkeerthi on 2009-08-26
> **jamescox84 said:**
> 
Sorry, a little sarcasm there. 
Sorry if it sounded like. I just wanted to make my point clear.

---

### Post by jamescox84 on 2009-08-26
I must apologise.  I wasn't saying it was you being sarcastic, it was me when I wrote the bit about where &#8220;Java won't run&#8221;.  I understand you weren&#8217;t being sarcastic and that you had a very valid point!

---

### Post by jamescox84 on 2009-08-26
Simian Man, WOW Ocaml looks great!  Just flicking through [The Basics]("http://www.ocaml-tutorial.org/the_basics").  I'm only at the function definition syntax, and already I like.  

**From Ocaml**
[LIST]
[*]Nestable comments.  (D has this aswell)
[*]Function / Variable definition share same syntax.
[/LIST]

Thanks for bringing this to my attention.  I can't wait to learn more!

---

### Post by samjh on 2009-08-26
The perfect programming language would be one that has:
* The low level control of Assembly
* The expressiveness of Lisp
* The provable safety of Ada
* The compiled efficiency and portability of C
* The dynamic execution of Python

In other words, the perfect programming language would be called, *I*, for "Impossible". ;)

---

### Post by delfick on 2009-08-26
perfect language : [http://en.wikipedia.org/wiki/LOLCODE](http://en.wikipedia.org/wiki/LOLCODE)

hahaha, just kidding :p

imho, perfect language would be fast python....
(i.e. something these two projects are heading towards : [http://codespeak.net/pypy](http://codespeak.net/pypy) and [http://code.google.com/p/unladen-swallow/](http://code.google.com/p/unladen-swallow/))

and just to add a nice language, [http://falconpl.org/](http://falconpl.org/) (scripting language that implements 6 major programming paradigms)

:)

---

### Post by Reiger on 2009-08-26
> **jamescox84 said:**
> Simian Man, yes your right C++ is not realy strongly typed, but then it's not as weak as C.  I will ammend to say it's type-safe, and that's what I like.

I am sorry? C++ allows you to do operations on the raw structure of the data in the address space, which is to say *anything* can be converted to & modified as the old C-style **char (walk the the bytes of the object). Where is your type safety now? :P

Plus C++ doesn't do boundary checking, which is *why* exploits resulting from buffer overruns & underruns are at all possible. Where is your type safety after that piece of fuzzed input, then? :P

For true portability: Forth. Also for true extensibility: Forth. Merely write a new definition and have it automatically part of the "standard library" as it were.

---

### Post by Reiger on 2009-08-26
> **tinivole said:**
> May I also add that the usage of TABS are not encouraged in the industry. As different systems/text editors treat tab differently, so you can't guarantee that how your code looks in one program will look the same in another.

OTOH, using TAB's is much safer than using spaces in XML because you cannot guarantee one XML "user agent" treats trailing whitespace the same as another. In particular, when converting XML source to other output by means of XSLT trailing whitespace tends to count as #PCDATA rather and is therefore not cut off; trailing tabs on the other hand are removed if the appropriate pragmas <xsl:strip-space elements="*"/><xsl:output indent="no"/> are set...

---

### Post by jamescox84 on 2009-08-27
> **samjh said:**
> The perfect programming language would be one that has:
* The low level control of Assembly
* The expressiveness of Lisp
* The provable safety of Ada
* The compiled efficiency and portability of C
* The dynamic execution of Python

In other words, the perfect programming language would be called, *I*, for "Impossible". ;)

Why is this impossible?  Could it not be implemented in a C++ style "you pay for what you use”, allowing a completely dynamic language that can optionally become stricter or faster where the programmer needs it?  Could *I* just mean "Imagine"?

Imagine That!  I don’t think it’s impossible, just very, very, very, very, very, very hard to meat all the criteria you mentioned.

---

### Post by jamescox84 on 2009-08-27
Could a graphical langauge ever be perfect?

---

### Post by CptPicard on 2009-08-27
> **jamescox84 said:**
> allowing a completely dynamic language that can optionally become stricter or faster where the programmer needs it?


You mean like Common Lisp? :) Completely dynamic, highly abstract language where, if you want to, you can declare your types (and the compiler knows how to infer as far as is possible from those declarations so you don't need to repeat yourself), write imperative code that maps relatively cleanly to machine code if needed, disable safety-checks completely if you feel like it, and can hide all the ugly parts behind macros... and all this completely flexibly within the same language so that you don't necessarily even notice when you're moving between abstraction levels...

---

### Post by CptPicard on 2009-08-27
Plain English would far too vague (in a sense, too expressive) to specify exactly a rather limited process such as Turing-complete computation. I take my Lisp for that any day over a natural language thanks... :)

---

### Post by uljanow on 2009-08-27
> **CptPicard said:**
> Plain English would far too vague (in a sense, too expressive) to specify exactly a rather limited process such as Turing-complete computation.

That is a problem only for implementors of compilers. ;). Nonetheless it would require some breakthroughs in AI.

---

### Post by Simian Man on 2009-08-27
> **uljanow said:**
> That is a problem only for implementors of compilers. ;). Nonetheless it would require some breakthroughs in AI.

No, English itself is extremely [ambiguous]("http://en.wikipedia.org/wiki/Ambiguous_grammar").  It would be impossible to use it as a programming language.  A subset of English would be possible, but most programming languages are subsets of English in one sense or another.

---

### Post by grayrainbow on 2009-08-27
> **uljanow said:**
> That is a problem only for implementors of compilers. ;). Nonetheless it would require some breakthroughs in AI.

Yep, that's exactly AI problem, but then...programming will be more like psychology, not like this thing that is called programming today...future will be grate :P. Btw, much of initialization scripts of Linux look bit like plain english :)

Perfect programming language...that's should be the language used by perfect programmer :)

---

### Post by Shin_Gouki2501 on 2009-08-27
its again amazing how much false information is thrown in here :D

1. answer to thread topic: [http://en.wikipedia.org/wiki/No_Silver_Bullet](http://en.wikipedia.org/wiki/No_Silver_Bullet)

2. actually , "plain" english is on the move. example BDD:
[http://tiagofernandez.blogspot.com/2009/08/bdd-with-groovy-and-scala.html](http://tiagofernandez.blogspot.com/2009/08/bdd-with-groovy-and-scala.html)

using DSL's it is possible to generate very nice solutions! If you look up BDD in Wikipedia you see that one of its goals is to give people ( stakeholders) the ability to "program" *without* knowing actually a (complete) programming language.
DSL should offer here a well defined tool for certain problems with easy access.

And i think that's sweet stuff. Very important here is expressiveness and since that is a bit vague, well it means : how can i transfer my thoughts *easily* into a form the computer understands.

---

### Post by nvteighen on 2009-08-27
> **CptPicard said:**
> Plain English would far too vague (in a sense, too expressive) to specify exactly a rather limited process such as Turing-complete computation. I take my Lisp for that any day over a natural language thanks... :)

+1000 for Lisp

There's no such thing as a perfect artificial language, because artificial languages are optimized for some specific task. Lack of task specification is only possible in natural languages, as their only task is communication, which is equal to all natural languages.

---

### Post by samjh on 2009-08-27
> **Simian Man said:**
> No, English itself is extremely [ambiguous]("http://en.wikipedia.org/wiki/Ambiguous_grammar").  It would be impossible to use it as a programming language.

+1.

Ask any lawyer or writer about the ambiguities of the English language.  Using plain English for programming is just crazy.

---

### Post by JordyD on 2009-08-28
> **samjh said:**
> +1.

Ask any lawyer or writer about the ambiguities of the English language.  Using plain English for programming is just crazy.

Legal documents should be written in C. :)

---

### Post by mmix on 2009-08-28
it is in mechanism, not in syntactic sugar or language, IMHO.

all is about data.

---

