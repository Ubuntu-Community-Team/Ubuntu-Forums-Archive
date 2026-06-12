---
title: "using flex and bison to build C++ code under anjuta"
date: 2008-06-20
forum: Programming Talk
---

### Post by Tony Flury on 2008-06-20
My end goal is to use flex and bison to build a small library that can be passed a text string with a know (sql based) syntax, and for it to instatiate a set of classes that represent the meaning of the input string.

I have a lex and yacc input files which i can build into a C program thus 

flex -i sql.l
bison sql.y
cc lex.yy.c sql.tab.c -o example

When i run ./example it takes input from stdin and does parse and analyses the syntax of the input as expected - generating output to stdout,

When i try to use these same .l and .y files under Anjuta in a C++ project it fails - lots of warnings about functions being redefined - as expected. I have treid to follow the tutorials at various places, but none of them produce the right results either : 
a) if i use the Automake on my Anjust project it invoke ylwrap which seem to fail silently and the make stops.
b) if I manually invoke flex, bison and gcc i get warnings about redefined functions and undefined tokens.

Can someone point me in the right direction for the following steps :

1) how do i get flex and bison to generate valid c++ code

2) how do i get that code to compile and link under anjuta

3) assuming i get this far - how do i get the pareser to accept a string input - rather than from stdin ?

I would judge my C++ knowledge to be intermediate (I am comfortable with Classes, overloading operators etc, although some of the finer points of inheritance/polymorphism still allude me). My Anjunta knodledge is basic.

---

### Post by Tony Flury on 2008-07-08
bump - i know this question is two weeks old - but if anyone has some good guidance that would be appreciated.

---

### Post by rnodal on 2008-07-08
Could you post the code? If you are using headers (your own ones) make sure that you prevent re-definition. It seems to me that it may be a miss-configured IDE but I can tell. Provide your code and if the code its not the problem then post the make file or whatever script is being used to build the program.


-r

---

