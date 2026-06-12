---
title: "Looking an specific mathematical library in C/C++"
date: 2007-07-01
forum: Programming Talk
---

### Post by crislosi on 2007-07-01
Hi ! Well it's my first post in this forum and my english is very poor but i need help.
I want making a mathematical program written in C/C++ but i don't know implement a concrete work. I want that my program when it ask an analytical expression of a mathematical function so that my program knows is a mathematical function and not a string. I put an example that i want my program works:

Example:

Please enter the expression of a function

cos(x+1)+2*x²-5x+ln(x)  ( Well, this is a string)

How can i say to my program code rthat th espression cos(x+1)+2*x²-5x+ln(x)  is a mathematical expression and not a string.

I've loked for in GSL library but i didn't find anything, is there an specific library in C/C++ that makes this problem?
Where can i found it?

Thank you very much for all
Greetings

---

### Post by PaulFr on 2007-07-01
Maybe you want to look at a **computer algebra system** - see **[http://en.wikipedia.org/wiki/Computer_algebra_system](http://en.wikipedia.org/wiki/Computer_algebra_system)** for details. One computer algebra system available for Ubuntu is maxima (with GUI as wxmaxima or xmaxima). ```
 sudo apt-get install wxmaxima maxima-doc maxima-share
``` The main web page for wxMaxima is at **[http://wxmaxima.sourceforge.net/wiki/index.php/Main_Page](http://wxmaxima.sourceforge.net/wiki/index.php/Main_Page)** Good luck.

---

### Post by dsl on 2007-07-01
You could use *flex* to do lexical analysis and *bison* to parse the expression. Both are in the repositories together with their documentation and examples.

When bison recognizes a given syntactical form, eg "a+b", it performs the action you told it to; it can make an addition or even write code to make an addition. In the first case you are using it to make an interpreter, in the second case to make a compiler.

The same could also be done directly in C/C++, but with some more effort. Most books have a simple "calculator" example on which you could build.

hth

---

### Post by kknd on 2007-07-01
If youre looking for a math parser in C++, try muParser. Its open-source and fast.

---

### Post by crislosi on 2007-07-02
Hello, first thank you for your answers.

**PaulFR**->, I know maxima+wxmaxima, but i want create my own program

**dsl**-> i'll try flex and bison reading the documentation, i've heard about these packages but i don't know about their works. About creating myself code in C/C++ i think could do it with a stack ( pila en castellano) but it's very laborious. I thought that there is a library with this function make itself yet.

**kknd-**> muParser is in the repositories? i don't know this library.

Well, thank you again and excuse me my bad english.

Greetings! :D

---

