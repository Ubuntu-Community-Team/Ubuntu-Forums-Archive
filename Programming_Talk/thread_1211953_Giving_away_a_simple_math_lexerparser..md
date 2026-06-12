---
title: "Giving away a simple math lexer/parser."
date: 2009-07-13
forum: Programming Talk
---

### Post by moma on 2009-07-13
Hello.

I just worked with my [Gscreendump project...]("http://code.google.com/p/gscreendump/w/list") and ended up to remove some code from it. Instead of destroying the excess code I want to give it away to you.

The code contains a simple lexer + math parser written i c. No extra libraries are required but you will need the "build-essential" package for compilation.

The type of parser is [recursive descent...]("http://en.wikipedia.org/wiki/Recursive_descent_parser") and it can do various calculations with numbers + add strings and numbers. Here are some examples. 

[COLOR="DimGray"]15 - 8 / 4 * 2;

x=sqrt(2) + max(-1,+1, 3, 2.3); y=int(x);

'Circle with diameter ' + 1.00 + ' has circumference equal to ' + M_PI;

a = 'sin(30)=' + sin(rad(30)) + ' cos(90)=' + cos(rad(90)) + ' sin(90)=' +  sin(rad(90));

Some boolean expressions that return 0.0 (false) or 1.0 (true).
b = 4 >= 0xA && (1 < 3)

10 > 0xB || int(M_PI) == 3
[/COLOR]
You can process several lines of code in one go. You could read the code from a file. 
It also accepts multiline comments within /* ... */ and single line comments starting with //
Eg.

[COLOR="DimGray"]/* This is you code */
a=1
b=2
c=a+b // This is a sum

/* d=a^b  */
[/COLOR]----------

Download the code "parser.tar.gz" from here: [http://www.futuredesktop.org/adt/parser](http://www.futuredesktop.org/adt/parser)

Unpack the files (unless you do it in your GUI):
$ [COLOR="DarkGreen"]tar -xvzf parser.tar.gz [/COLOR]

It contains these files: 
[COLOR="Gray"]comp.sh[/COLOR] (compile and link)
[COLOR="Gray"]lexer.c lexer.h[/COLOR]  (the lexer part)
[COLOR="Gray"]parser.c  parser.h[/COLOR]  (parser)
[COLOR="Gray"]main.c [/COLOR] (edit this to test it)

Compile the code (the comp.sh script compiles and links it):
$ [COLOR="DarkGreen"]cd parser[/COLOR]
$ [COLOR="DarkGreen"]./comp.sh[/COLOR]
Run it 
$ [COLOR="DarkGreen"]./main [/COLOR]

Edit the main.c to test your own expresssions.

Boa sorte.
---------
[COLOR="Red"]EDIT 13-Jul-2009 16:07:[/COLOR]  Added exponential ^ operator and fixed some errors. Re-load your copy.

---

### Post by Paul Miller on 2009-07-14
This is a great example project for someone interested in how parsers or compilers work.  You should put this on some coding web site rather than just posting it here and letting it get buried in the forums. :-)

---

