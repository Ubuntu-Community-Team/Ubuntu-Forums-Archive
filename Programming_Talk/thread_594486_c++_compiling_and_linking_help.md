---
title: "c++ compiling and linking help"
date: 2007-10-28
forum: Programming Talk
---

### Post by omkarwagh on 2007-10-28
i am quite a beginner to programming so you'll probably find this a stupid question.

i have a project that involves a number of header files .h (that contain the declarations of a number of classes and functions) while some other people have made a number of .cpp files that implement these functions. 

i also have a main.cpp file that uses all these header contained stuff. however i am not able to link all these things properly.
in windows at least simply including the header files in the main.cpp would automatically compile all the header files along with the implementations and include them. however in ubuntu i am getting a number of 
"Undefined reference to ****" if i use g++.
i also need to include mesa(glut) header files. even they are not being included using the simple
#include<GL/glut.h> giving the same "Undefined reference to ****"

My other problem was the follows:-
also, i tried to use gcc but it gives a huge number of errors involving maybe iostream or stl_vector or god only knows what. ive been using g++ since. any ideas on how to use iostream or vectors in gcc? (because gcc is linking these automatically not g++).

hope i dont have to go back to windows. :P

---

### Post by hecato on 2007-10-28
Perhaps you mean by windows an IDE like VC??

"undefinied reference" is a linker error.

IDE is different than command line, in this case, you need to pass the library name not only the source file to compile.

Also sure tht it say 

> Undefined reference to ****The linker normally know the name  of what is referenced but not definied in any object file that is linking also it doesnt know nothing about what .h o .c or .cpp files the compiler load for output the objects files where it work, thus doesnt know nothing about " #include<GL/glut.h>".


Try to learn the different messages that compiler and  linker write.
Examples of compiler errors or warnings:[LIST]
[*]sintaxis error in 14 line (or some like that)
[*]struct X have not member WTF
[*]cast not valid... or cant cast automagically (or something like that)
[*]warning assigning a unsigned number to a signed number
[*]and so on
[*]Cant include x.h file
[*]Undefined WINDOWS in a #ifdef line
[*]functions no enought arguments, to many arguments, redefinition of function (when you dont declare in a good place the prototype and it assumer one)
[*]and so on[/LIST]Linker msg:[LIST]
[*]undefinied reference to function in module algo.o at address xxxx or some like that
[*]the library cant be found
[*]there no exist such library or the name of the library is not correct (see the search paths or that the library is actually there)
[*]and so on[/LIST]

---

### Post by dwhitney67 on 2007-10-28
To compile multiple C++ modules, you need a command similar to the following:

```
$ g++ mod1.cpp mod2.cpp etc.cpp -o myExeName
```

Hopefully your main() function is in one of those modules.

I don't know anything about glut, and I will not do any research into it... I'll leave that up to you.

However, if you need to link in libraries with your C++ program, then the syntax, similar to above is:

```
$ g++ mod1.cpp mod2.cpp etc.cpp -L*<path to library>* -l*glut* -o myExeName
```

where *<path to library>* is where the glut library (-ies) reside, and *glut* is the shortened name of libglut.a.  (Note, I don't know jack about glut, thus this library name may be incorrect).

If the Glut library is a shared library (ending in a .so extension), then the syntax above should include a *-shared* option _before_ the library name is specified.

P.S.  For projects involving "many" modules, it perhaps always desirable to create a Makefile to build the project.  Search this forum (or other forums) on how to create/use a Makefile.  Here's GNU's Makefile link:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

