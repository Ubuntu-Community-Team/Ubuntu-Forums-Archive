---
title: "Programming Languages with Compilers for Ubuntu?"
date: 2010-08-23
forum: Programming Talk
---

### Post by issachan on 2010-08-23
:KS Hi everybody! I need your help, my instructor has issued our first assignment for the semester - No I don't want you to do my homework for me - I just need some advice.

I need to choose 5 languages to study and create a simple program in each that can output a string and numbers, perform and output basic addition and subtraction, and output a string in ASCII numerical format. 

I need to learn the basics of each language and find compilers that run on Ubuntu.

One more thing... _I can't use C or BASIC_.

Here's a few languages he suggested... FORTRAN, COBOL, Ada, and ALGOL. I need languages that are easy to learn. He didn't mention anything about versions though, in any case, what do you recommend?

---

### Post by schauerlich on 2010-08-23
[http://en.wikipedia.org/wiki/List_of_programming_languages_by_category](http://en.wikipedia.org/wiki/List_of_programming_languages_by_category)

have fun.

---

### Post by Nytram on 2010-08-23
I'd recommend Python as one of your languages. It's very easy to use and comes built in to Ubuntu, no need to download anything.

---

### Post by GenBattle on 2010-08-24
I'd recommend Google Go (aka golang). It's a very unique language, not because it invents anything new, but because it combines alot of very alternative techniques to make a language that is fast to write, compile and run. You have to download and build the compilers from the repository, but its very straightforward on ubuntu. I reckon Go would give you alot to write about in your assignment.
[http://golang.org/](http://golang.org/)

I would also recommend python for this sort of assignment, again because it has a unique syntax and style.

---

### Post by juancarlospaco on 2010-08-24
> **nytram said:**
> i'd recommend python as one of your languages. It's very easy to use and comes built in to ubuntu, no need to download anything.

**+1**  :)

---

### Post by schauerlich on 2010-08-24
If you want something different, try common lisp. [http://en.wikipedia.org/wiki/Common_lisp](http://en.wikipedia.org/wiki/Common_lisp)

---

### Post by V for Vincent on 2010-08-24
I'm working on Scala for the moment. It's pretty interesting and it compiles to JVM bytecode.

---

### Post by lobralleo on 2010-08-24
Again, Python would be a great choice to include in your list.
Perl could also be a nice complement and it is usually included in most linux distros.

---

### Post by d3v1150m471c on 2010-08-24
> **juancarlospaco said:**
> **+1**  :)
python is great if you don't plan on compiling anything. to the best of my knowledge it's a scripting language. I'd recommend C++ and python though.

to compile c++:
```

g++ -o output input.cpp

```

---

### Post by GeneralZod on 2010-08-24
"D" is an interesting language that compiles to native code: the compiler is called "dmd" (for Digital Mars Compiler).  There's also the "ldc" compiler for it.

---

### Post by GenBattle on 2010-08-24
Yea python isn't a compiled language. GoLang and Vala would be my two reccommendations for compiled languages.

---

### Post by Bachstelze on 2010-08-24
Ada
Haskell
Some Lisp dialect
C++ or Java
Python, Perl or PHP, or Ruby, or Tcl, or Lua.... or any scripting language.

I think that will give you a nice overview of the available "types" of languages

---

### Post by escapee on 2010-08-24
If not all of them have to be compiled - this would be my pick if I was in your situation:

Go 
Common Lisp
Erlang
Haskell
Python (or Ruby)

Each one has a style behind it so it'll keep things fresh :)

---

### Post by bunburya on 2010-08-24
Does it have to be compiled or can it be interpreted?

---

### Post by Tahakki on 2010-08-24
LOLCode. :D

Also, Python isn't a compiled language, so maybe best to bear that in mind. Have a look at Java for sure, and C++.

---

### Post by nvteighen on 2010-08-24
Lol... The professor prohibits C and BASIC and suggests FORTRAN, ALGOL, Ada... How old is he? Is he one of those who thought C was useless because it was too high level for the 1970s (not to say BASIC)?

Ok, now into the serious business: I'd go for Python or maybe Common Lisp, unless you need a statically compiled language. 

If you need a statically compiled language that generates some native code, I'd go for *sigh*... C++... just because he doesn't want C. I know, using C++ when C is prohibited sounds almost like cheating, but hell, I don't understand what this professor's criteria are. Just be careful enough not to write C-like C++.

But please, first ask whether interpreted languages are allowed because I'd really try to avoid C++ if I were you.

I now need to wash my mouth for having recommended C++ to someone... (mea culpa, mea culpa...) :(

---

### Post by wmcbrine on 2010-08-24
Does it have to be compiled? That's a strange requirement, and (depending on how you interpret it -- no pun intended) it eliminates many of the best languages from consideration.

Pascal should certainly be on your list, although at this point I wouldn't recommend it outside the context of an educational assignment like this.

---

### Post by Bachstelze on 2010-08-24
> **nvteighen said:**
> Lol... The professor prohibits C and BASIC and suggests FORTRAN, ALGOL, Ada... How old is he? Is he one of those who thought C was useless because it was too high level for the 1970s (not to say BASIC)?

Ok, now into the serious business: I'd go for Python or maybe Common Lisp, unless you need a statically compiled language. 

If you need a statically compiled language that generates some native code, I'd go for *sigh*... C++... just because he doesn't want C. I know, using C++ when C is prohibited sounds almost like cheating, but hell, I don't understand what this professor's criteria are. Just be careful enough not to write C-like C++.

But please, first ask whether interpreted languages are allowed because I'd really try to avoid C++ if I were you.

I now need to wash my mouth for having recommended C++ to someone... (mea culpa, mea culpa...) :(

You might be overinterpreting things.  Maybe the purpose of the assignment is to introduce students to new languages, and if they have studied C previously, choosing it would defeat the point.

---

### Post by diesch on 2010-08-24
> **Tahakki said:**
> LOLCode. :D

Also, Python isn't a compiled language, so maybe best to bear that in mind. Have a look at Java for sure, and C++.

The Python language specs don't say anything about compiling. Like with Java the reference implementation (CPython - that's what most people mean if they talk about Python) compiles to byte code.

---

### Post by Jekshadow on 2010-08-24
Here are a few:

[LIST]
[*]Perl
[*]Ruby
[*]Python
[*]Clojure
[*]Java
[*]C# (via Mono)
[*]Pascal
[/LIST]

---

### Post by dv3500ea on 2010-08-24
It'll probably be most beneficial to you if you choose languages that are very different from each other.

I would go with:
[LIST=1]
[*][D]("http://www.digitalmars.com/d/") | [Go]("http://golang.org/") | [Java]("http://www.sun.com/java/")
[*][Ruby]("http://www.ruby-lang.org/") | [Python]("http://www.python.org/") | [Perl]("http://www.perl.org/")
[*][LISP]("http://clisp.cons.org/") | [Scheme]("http://www.gnu.org/software/guile/") | [Haskel]("http://www.haskell.org/")
[*][Javascript(ECMAscript)]("http://live.gnome.org/Seed") | [Self]("http://selflanguage.org/") | [Io]("http://www.iolanguage.com/")
[*] [An assembly language]("http://en.wikipedia.org/wiki/Assembly_language")
[/LIST]

---

### Post by juancarlospaco on 2010-08-24
> **d3v1150m471c said:**
> python is great if you don't plan on compiling anything. to the best of my knowledge it's a scripting language. I'd recommend C++ and python though.


Then say it to my **.PYC** files, compiled binary bytecode?,
also how i make static compiled binary-only programs, or im wrong?.
Title says *"Programming Languages with Compilers"* Python is these i think.
:)

---

### Post by trent.josephsen on 2010-08-24
> **juancarlospaco said:**
> Then say it to my **.PYC** files, compiled binary bytecode?,
also how i make static compiled binary-only programs, or im wrong?.
Title says *"Programming Languages with Compilers"* Python is these i think.
:)
compiled != bytecode-compiled

It would be best if the OP can clarify whether the intent is really just compiled languages, or if that was just an unfortunate way to phrase "languages supported on Ubuntu".  Depending on who you ask, JIT-compiled and bytecode-compiled scripting languages may or may not be considered "compiled languages" in the abstract.

---

### Post by matchett808 on 2010-08-24
I am really suprised that no-one has recommended bash (its a shell scripting language used for ubuntu terminal basically). obv. this might not come within the context of what ur teacher is looking for but it is easy as pie. I took me a very short time to learn bash, I am currently learning ruby and looking at others, the amount of time I have done ruby I could already write bash scripts by this point.....I would question ur lecturer more about the spec. for the assignment....

Just my two pennies!

---

### Post by juancarlospaco on 2010-08-24
> **trent.josephsen said:**
> c
it would be best if the op can clarify whether the intent is really just compiled languages, or if that was just an unfortunate way to phrase "languages supported on ubuntu".  Depending on who you ask, jit-compiled and bytecode-compiled scripting languages may or may not be considered "compiled languages" in the abstract.

+1

---

### Post by issachan on 2010-08-26
**[COLOR=DarkOrchid]Awesome! Thank you all for your great suggestions![/COLOR]**

I'm going to ask my instructor for some details about the assignment before choosing any languages. I'll let you all know what I find out!

When he told us about the assignment, he said the main purpose of it is to get the class to learn about other programming languages instead of similar variations of what we already know like C and BASIC. He didn't say anything about web scripting languages not being allowed or if compilers are a requirement, but the assignment he gave out states "...you will need to find compilers that you can use to complete the assignment..." - but the university focuses on Microsoft products and uses Windows throughout so perhaps that has something to do with it? In any case I'll ask him about the languages everyone has suggested.

Thanks again! If you think of more, let me know, this is great, not only for this assignment but future reference as well! :D

---

### Post by issachan on 2010-08-29
Well, I asked my teacher about whether scripting languages were allowed, and his words exactly were... "Well, I didn't outlaw them" and then began to stress that I wouldn't learn anything from the assignment by doing languages I know.

I don't know anything about the languages I asked him about (see the list below), yet for whatever reason he assumes that I know them already. Perhaps because some are similar to C? In any case....

So as long as I don't use **BASIC or C, or any of their derivatives** then it _should_ be ok... so no C++, C#, etc.

Here's a list I made of potential candidates after reading all the suggestions and doing my own research... 

_Top 5_
Java 
Python 
Perl 
Common LISP (CL) 
Bash 

_Runner Ups_
Ruby
Squeak
Squirrel 
Pascal
Haskell

To get the best grade, I probably need to choose _non-scripting languages_, so I need to modify the above list. 

If you have any suggestions, please let me know! 

I've only had 2 weeks of class and I've already irritated him by simply asking a simple question - I don't want to make things worse and have him hating me the whole semester and docking my grade because of it! :(

---

### Post by Bachstelze on 2010-08-29
Well, it depends what you mean by "scripting languages". If you mean "interpreted languages", then Python, Perl and Bash are out.  So if you need compiled languages, that doesn't leave us much choice, you could go with Ada, Java, Haskell, Pascal or Fortran, and Common Lisp.

---

### Post by schauerlich on 2010-08-29
> **issachan said:**
> _Top 5_
Java 
Python 
Perl 
Common LISP (CL) 
Bash 

Hmm... Well, Java should definitely be out, as it's pretty much a nicer C++. And perl is pretty C-ish too. I'd replace them with a Smalltalk (like Squeak) and something functional (you could do that in Clojure or Scheme, but since you already have a lisp... perhaps Haskell or Erlang?)

---

### Post by wmcbrine on 2010-08-29
> **issachan said:**
> Well, I asked my teacher about whether scripting languages were allowed, and his words exactly were... "Well, I didn't outlaw them" and then began to stress that I wouldn't learn anything from the assignment by doing languages I know.You know, between this, and the bizarre ALGOL/FORTRAN suggestions, I have to wonder if your teacher isn't a bit out of touch with current programming trends.

In which case, move Lisp to the top of your list. It's still cool, but it's way old, so he'll have heard of it.

---

### Post by issachan on 2010-10-18
I just wanted to say thanks to everyone for their help!
[COLOR=Magenta][B][SIZE=4]
Thank you!!! [/SIZE][/B][/COLOR]

I got an A on the assignment, thanks to all of your suggestions. 

Here's the languages I chose...

Pascal
Ada
Fortran
Java
OCaml

He let me use Java, so I jumped on the opportunity. Also I chose OCaml because I was seriously pressed for time and it was similar enough to C that I found it easier to work with than some of the other languages.

Anyway, thanks again everyone!

---

