---
title: "[SOLVED] Passing parameters"
date: 2008-08-17
forum: Programming Talk
---

### Post by The Midnight Coder on 2008-08-17
I need help passing paramaters to a c++ built application

Basicall what I want to be able to do in a terminal is something like this:```
myapp -something somethingelse
```

I want to know what was passed to the application.

How do I do this?

---

### Post by mike_g on 2008-08-17
You can get getopt or getopt_long to deal with the commandline parameters for you. For info in the terminal type:
```
man getopt
```
Theres some examples of the usage there. There also some more info on it in chapter 2 of advancedlinuxprogramming. you can dl the pdf here:
[http://www.advancedlinuxprogramming.com/alp-folder](http://www.advancedlinuxprogramming.com/alp-folder)

---

### Post by The Midnight Coder on 2008-08-17
At first glance it looks confusing but I think I get how to use it but not how to call it. Would it be something like using system() to call?

Is there any other way to get the parameters other than this way? Like some code perhaps? I need to be able to implement it on any system as I have to compile on windows systems elsewhere (aka school)...

---

### Post by mike_g on 2008-08-17
It seems you may not know this yet, so I'll explain.

parameters are passed in with argc and argv. If youre using CL parameters you main function wants to look like this:
```
int main(int argc, char* argv[])
```
argc holds the number of parameters passed in; argv holds an array of strings with each parameter.

your program name is allways argv[0]. So to print the parameters you could do something like;
```
int main(int argc, char* argv[])
{
    printf("Program: %s\n", argv[0]);
    for(int i=1; i<argc; i++)
    {
        printf("Param %d = %s\n", i, argv[i]);
    }
    return 0;
}
```
You could then parse the strings yourself, but getopt makes life easier.

Edit:
> I need to be able to implement it on any system as I have to compile on windows systems elsewhere (aka school)...
Oh, if thats the case then you probably dont want to use getopt. THe code I posted should give yu an idea of how to get the arguments tho. Also, you might want to use cout instead of print since your working with c++.

---

### Post by The Midnight Coder on 2008-08-18
OK Thanks. I wanted to find out how to do this so that I could understand how to do it. I am just starting out some of the major concepts of C++ so is there some tutorial on it?

---

### Post by dwhitney67 on 2008-08-18
> **The Midnight Coder said:**
> OK Thanks. I wanted to find out how to do this so that I could understand how to do it. I am just starting out some of the major concepts of C++ so is there some tutorial on it?
What you are inquiring about is not a "major" concept of C++.  The answer supplied by **mike_g** will probably be the best you can get.  Not only did he explain argc and argv, he provided a code example.

Here's a similar coding example; if you don't understand the code, I suggest you save it to a file, compile it, then run the code with some command line arguments.  Maybe afterwards you will understand the concept.
[PHP]#include <iostream>

int main( int argc, char **argv )
{
  for ( int i = 0; i < argc; ++i )
  {
    std::cout << "arg " << i << " = " << argv[i] << std::endl;
  }
  return 0;
}[/PHP]
Note that the first argument to any C/C++ program is the program's name itself.  This is always located in argv[0].

---

### Post by The Midnight Coder on 2008-08-19
Yes I could understand that...What I meant was is there any tutorial on things like this? Like more than the basics which I am familiar with...

---

### Post by dwhitney67 on 2008-08-19
> **The Midnight Coder said:**
> Yes I could understand that...What I meant was is there any tutorial on things like this? Like more than the basics which I am familiar with...
Try this link:  [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

P.S.  I should further add that the main() function is basically like any other function, with the exception that it is automatically called when a program is started.  By convention, 'argc' and 'argv' are parameters that are used to represent the number of command line arguments and the list of command line arguments, respectively.  However one does not have to stick with convention; this is also legal:
[php]
int main( int numArgs, char **cmdLineArgs )
{
  ...
}
[/php]
Just think of 'numArgs' and 'cmdLineArgs' (or 'argc and 'argv') as being local variables to the function main().

---

### Post by The Midnight Coder on 2008-08-19
Now how that a link like that slip through my fingers??

Thanks dwhitney67

---

