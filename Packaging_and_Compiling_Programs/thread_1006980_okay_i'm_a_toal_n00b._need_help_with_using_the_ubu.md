---
title: "okay i'm a toal n00b. need help with using the ubuntu compiler"
date: 2008-12-09
forum: Packaging and Compiling Programs
---

### Post by TIMB3RW01F on 2008-12-09
like i said, i'm a total noob. i want to learn how to program. i'm doing the basics but i need to know how to invoke the ubuntu compiler. can anyone help me? i'm sorry.

---

### Post by Simian Man on 2008-12-09
Ubuntu doesn't have a compiler.  There are many compilers available for Linux, many of which are available in the Ubuntu repositories.  What compiler (or interpreter) you use will depend on what programming language you learn.

For someone new to programming, I'd recommend Python.  The intepreter should already be installed, so just find a book or tutorial that looks good and go for it.

---

### Post by steviefordi on 2008-12-10
I'm a little confused as to what you're asking so I'm going to give you two answers:

**1.** If you want to learn how to program, there's an excellent    beginners tutorial at:

[http://pine.fm/LearnToProgram/](http://pine.fm/LearnToProgram/)

The programming language used in this tutorial is Ruby, for which you can install the interpreter (bit like a compiler) from synaptic package manager. I think Ruby is an excellent beginners language and you will do well to find a better tutorial.

**2.** If you need to know how to compile because you've downloaded an application's source code, the info you need can be found here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

and here:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Hope this helps
Cheers
Steve.

---

### Post by mankyd on 2008-12-11
I would like to provide a slightly clearer answer here:

As Simian Man stated, there is no "Ubuntu" compiler. Ubuntu is the name of a collection of packages and programs that make up the Operating system. The compiler is not necessarily part of that. But, that was not your question...

There are many languages out there to learn. One basic distinction between languages is "compiled" languages,  (which require compilers, obviously)  v.s. "scripting" languages, (which generally use what are called interpreters.) That distinction is a bit of misnomer because even scripting languages can be compiled, but I digress. Here is a list of few popular languages as divided by this distinction (in no particular order):

Compiled:
-C
-C++
-Java (java actually requires an interpreter to run, but must be compiled first)

Scripting:
-Javascript
-PHP
-Ruby
-Python
-Perl

Each one requires its own set of programs and libraries to work. For C and C++ on Linux (i.e. Ubuntu), this is generally a program call gcc. You would write your program in a text editor, save it, and run the following command:

```
gcc source_code.c -o executable_program
```

That gives you a program, called executable_program, that you can then run. Many intro to programming courses offered through schools start you out C and/or C++.

Scripting languages, however, tend to be in vogue these days and tend to be easier to work with. I myself am currently employed as a PHP programmer (though I wish it was another language :P.) I would agree with Simian Man that Python can be a good place to start. After writing your Python code, you would execute it from the command line as such:

```
python source_code.py
```

Another language that I find very interesting is Javascript. It's easy and very powerful in and of itself. There's not much in the way of interesting library support for it like the other languages, but its a great way to learn the basics of programming. You can either run Javascript in a web page (where Javascript is most often used) or you can run it from the command line with either Rhino or SpiderMonkey, both of which can be installed through Synaptic. You would then execute your javascript programs as such:

```
js source_code.js
```

Hope this helps!

---

### Post by mankyd on 2008-12-11
BTW, here's some quick source code examples for the 3 commands I listed above. These should help get you started:

C:
```
#include <stdio.h>

int main() {
    printf("hello, world\n");
    return 0;
}
```

Python:
```
print "hello, world"
```

JavaScript:
```
print("hello, world");
```

Each one of those, as may be apparent, prints "hello world" to the screen when executed from the command line.

---

