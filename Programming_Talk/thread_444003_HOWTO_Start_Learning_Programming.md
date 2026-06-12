---
title: "HOWTO: Start Learning Programming"
date: 2007-05-14
forum: Programming Talk
---

### Post by JT673 on 2007-05-14
I have only been on here for a while, but I feel compelled to make a thread to guide beginners on the right path to programming "pro-dom" :)...

[SIZE="5"]How?[/SIZE]

[LIST=1]
[*]Choose a language, any language.  As the FAQ states, there is no best language that will stay on top for the rest of your programming career.  However, it is recommended to learn a language still in use today so that you don't have to run around in circles to get help.  [TIOBE]("http://www.tiobe.com/tpci.htm") is a list of major programming languages.
[*]Download the language.  Google in "[language]", "[language] download", "[language] development kit", etc., and you're bound to hit something called an interpreter and maybe a compiler.  Some languages, like Java, need a compiler, so download the development kit (in this case, JDK, Java Development Kit), as opposed to the end-user version (JRE, Java Runtime Environment), which doesn't have the necessary programs to help you on your way.
[*]Remember, Mr. Google is your friend. Depending on the language you chose, there should be plentiful tutorials around.  Sometimes there are documentations or manpages (download packge "manpages-dev") of the languages that help A LOT:

[LIST]
[*][Java]("http://java.sun.com/javase/6/docs/") has the THE best documentation I have seen.
[*][Perl]("http://www.perl.com/pub/q/documentation") documentation has some nice tutorials.
[*][Ruby]("http://www.ruby-doc.org/") documents the full API (application programming interface, basically a library like DirectX and OpenGL) and has a full online book.
[*][Python]("http://docs.python.org/download.html") has both downloadable docs and an full online manual written by the creator of Python himself.
[*][C++]("http://docsrv.sco.com/man/html.3C++std/CONTENTS.html") docs only list the standard library, but you can find a C++ tutorial with Mr. Google, can't you?

[/LIST]
[*]And we're always here too!  If you've got a bug, we can fix it!
[/LIST]

[SIZE="5"]FAQ[/SIZE]

*What programming language is the best?*

There is no best language that will has on that throne for the more than 20-30 years.  FORTRAN beat assembly, BASIC beat FORTRAN, C beat BASIC, C++ beat C (well...maybe "tied with" is a better wording), and Java beat C/C++.  This cycle happens quite haphazardly, and you should anticipate which language is going to secure your job, but ONLY by learning multiple languages.  Also, you CANNOT really anticipate how long the language is going hold out, so try to learn new ones on spare time, if only just to skim over the syntax.

*What programming language is the easiest?*

Brief history/study into programming languages.  There are interpreted and compiled languages (or dynamic and static languages, in that order).  In interpreted languages, you hand the application runner the source, the text file you wrote.  This category includes HTML, Ruby, Python, Perl, and other assorted languages.  Compiled languages need you to feed it to the compiler to print out bytecode (0's and 1's), AND THEN give it to the runner.

Generally speaking, interpreted languages are easier because they are not as typed strongly, or with excess syntax :P.  However, compiled languages are used more often with large corporations, because they remove the overhead of general interpretation of the source ahead of time, and most corporations (*coughmicrosoftcough*) would like to keep their source away from other programmers, which is something they usually can't do with interpreted langauges.

******************************

Enjoy, and happy hacking!

---

### Post by encompass on 2007-05-14
To support people wanting to learn how to use the python language.  I am working on a project here...
[https://launchpad.net/pystart/](https://launchpad.net/pystart/)
Should be a great program when done... it is part of Google Summer of Code.

---

### Post by ghostdog74 on 2007-05-15
there's a sticky on this...

---

### Post by pmasiar on 2007-05-15
> **JT673 said:**
> I have only been on here for a while, but I feel compelled to make a thread to guide beginners on the right path to programming "pro-dom" :)...


I agree with you in about 60% what you say, but... there are big omissions and misunderstandings.

Link to sticky [ How to start programming - guides and links for many languages](http://ubuntuforums.org/showthread.php?t=333867) is *so* obviously missing here... I am curious what we could do to make it more prominent, so people will actually notice it? :-(

> Choose a language, any language.  As the FAQ states, there is no best language that will stay on top for the rest of your programming career.  

1) Programmer needs to know multiple languages, but *NOT* all languages are equally good for beginner. I would argue that dynamically typed language with simple syntax, like Python, is better suited to be first language than strictly statically typed language like java, which forces from the day 1 to define objects. So "choose a language" is not helpful: IMHO **expert with knowledge of many languages can (and should be able to) tell which language is better as *first* language, and why.**

And if we admit than more than one language is needed, ie combination Python + C covers both easy to learn, high-productivity language, and (creating libraries linked from Python for) high-performance oparations.

> TIOBE is a list of major programming languages.

TIOBE is yet another lying statistics (together with "popularity of languages" based on number of sold books. I do check it occasionally, but I am fully aware how misleading it is.

If language is simpler to learn and has many excellent free online resources, like Python has, it will not register on TIOBE or for book sellers. And opposite is true too: if language is over-complicated, over-engineered and has many complex hard to learn libraries, many books and seminars will be available for it. Don't ask [pointy-haired boss](http://en.wikipedia.org/wiki/Pointy_Haired_Boss) about which language is better - you are better off asking pineapple (see cartoon at link above).

>  interpreted languages (...) includes HTML, Ruby, Python, Perl (...) are easier because they are not as typed strongly, or with excess syntax :P.  However, compiled languages are used more often with large corporations, because they remove the overhead of general interpretation of the source ahead of time, 

1) HTML as programming language? give me a break. It is markup/presentation notation, but nothing more. :-)

2) Python is strongly, dynamically typed language, to explain difference see [http://en.wikipedia.org/wiki/Type_system](http://en.wikipedia.org/wiki/Type_system)

Python is *compiled* into .pyc bytecode, which you can distributed instead of sources, and compiled into binaries if needed. Alsi, it is used extensively by ie Google or NASA, and many other big companies.

---

