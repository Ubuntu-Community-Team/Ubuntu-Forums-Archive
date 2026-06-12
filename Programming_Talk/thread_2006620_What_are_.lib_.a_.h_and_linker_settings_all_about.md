---
title: "What are .lib .a .h and linker settings all about?"
date: 2012-06-19
forum: Programming Talk
---

### Post by nerdinator on 2012-06-19
When I first learnt OOP programming in C++, there  was a simple .cpp file I had to create with a main function, and .h files which I needed to include if I had classes to use and that was it.

I am very confused about what each of these things I did actually did to my project.
When I wrote my first OpenGL project,
1.I downloaded a couple of packages using the terminal. 
(they were :```
[I]
sudo apt-get install mesa-common-dev[/I][I]
sudo apt-get install freeglut3-dev[/I]
```They got a bunch of header files to /usr/include/GL. 

2.I wrote the program in a .cpp file and included 2 files:
```

#include "GL/freeglut.h"
#include "GL/gl.h"

```They would have told the compiler all the types and functions I used in the program.

3. I went to Linker Setting in Code Blocks(which I use) and put
```
-lGL -lglut
``` there.

My questions:
1.What did I actually download in step 1?
Did they all go to the /usr/include/GL directory ?
How come I don't have to place them in my project's home directory?

2. I opened gl.h and checked.
There was no```
 #include "gl.cpp"
```.
Then where are the implementations of the functions in gl.h?

3. What am I doing by putting those : 
```
-lGL -lglut
``` there.
If they are libraries why am I not using a full pathname with the file name of the library?

4.Why do we need .lib and .a files?
Can't we accomplish everything with .h for declarations and .cpp for implementations, linked up extensively?
Doesn't the linker link up .h and .cpp files which we specify using the include directive?

Thank you

---

### Post by Bachstelze on 2012-06-19
1. You can run [font=monospace]dpkg -L *packagename*[/font] to see the contents of a package. You don't have to place everything in your home directory because the files are placed in standard locations where the compiler will look for them.

2. They are in the .a files, but in object (compiled) form, not source form.

3. Yes, they are libraries. You don't use the full path- and filenames because it is all standardized. For example [font=monospace]-lGL[/font] tells the linker to use any file named libGL.a that it finds in the standard library directories.

4. Technically, you could use .cpp files instead of .a files. The problem of usin .cpp files of course is that you have to compile everything (your program and thelibraries).

---

### Post by nerdinator on 2012-06-19
2. But I can't find any  #include directive referring to a .a file at all.  Then how does gl.h know where the implementations of functions are?

4.When we use an include directive to link to a .cpp file , linking happens right? The same linking that happens when we add those things in the linker settings?
So why can't we #include  .a files instead of adding libraries in linker settings?

Thank you

---

### Post by Bachstelze on 2012-06-19
> **nerdinator said:**
> 2. But I can't find any  #include directive referring to a .a file at all.  Then how does gl.h know where the implementations of functions are?

gl.h doesn't know where the implementations are, and it doesn't need to. All that is needed in order to compile your functions is the prototype of all the functions you call, not their implementations.

> 4.When we use an include directive to link to a .cpp file , linking happens right?

No. Linking happens later, when object files are linkeds in order to produce an executable.

> So why can't we #include  .a files instead of adding libraries in linker settings?

Because #include directives are processed before compilation, and linking is done after. #include works on source, linking works on object.

You seem to be very confused, and you really need to read more about that. [This](http://www.cs.cf.ac.uk/Dave/C/node3.html) is the first link I get on Google.

---

### Post by nerdinator on 2012-06-20
I did read much about it.  And I found out [here]("http://stackoverflow.com/questions/5735379/what-does-include-actually-do") ,that #include directive is equivalent to copying and pasting the contents of the file. 

I have only 1 issue unresolved. I couldn't read about it anywhere.
If gl.h doesn't know where the implementation is ,then how will the program find the implementation? 
In this case it would have to be in a pre compiled .a in object form.  But would it have to  look in the entire library for an implementation?  What if 2 functions have the same name and one of them is invoked?

---

### Post by Bachstelze on 2012-06-20
> **nerdinator said:**
> 
What if 2 functions have the same name and one of them is invoked?

In that case, which implementation is used seems to be implementation-defined. In particular, Linux and OS X seem to behave differently in that regard.

---

### Post by jim_24601 on 2012-06-20
> **nerdinator said:**
> I did read much about it.  And I found out [here]("http://stackoverflow.com/questions/5735379/what-does-include-actually-do") ,that #include directive is equivalent to copying and pasting the contents of the file. 

I have only 1 issue unresolved. I couldn't read about it anywhere.
If gl.h doesn't know where the implementation is ,then how will the program find the implementation? 
In this case it would have to be in a pre compiled .a in object form.  But would it have to  look in the entire library for an implementation?  What if 2 functions have the same name and one of them is invoked?

Yes, the preprocessor, when it encounters a #include directive, will effectively copy and paste the included file in place (which may in turn result in more files being included and pasted into the code). But this isn't the end of story as far as the compiler is concerned.

The compiler acts on what are called translation units: roughly speaking a translation unit is a source (.cpp) file plus all the headers that it includes (and all the headers that they include and so ad infinitum). The compiler compiles away happily munching source code and producing machine language[1], and unless your program is completely trivial, it will sooner or later encounter a function call.

There are several ways in which a function call can be implemented in machine language, but the basic idea is: Put the arguments where the called function can get at them according to some agreed calling convention, call the actual code, retrieve the result, and perhaps do some cleaning up afterwards. Provided the compiler has seen the function definition (usually in some header file), it knows what arguments the function takes, what it returns and the calling convention that defines how these are passed in and out. The only thing it's missing is the address of the actual code.

Now if the function implementation is in a different translation unit, be it somewhere else in the same program or in an external function, it doesn't know what the address should be. The function may not even have been compiled yet. So it compiles everything else, but leaves a placeholder for the address for the linker to fix up.

It is the linker's job to find the missing functions that each object file needs. The object file that the compiler produces contains a list of symbols that the compiler knows should exist in the complete program but that it hasn't compiled itself (the imports). It also contains a list of symbols that the compiler has compiled and wants to make available to other parts of the program (the exports).

The linker does not know[2] whether a given symbol is a function or a global variable, and it does not know what arguments a function takes, how they are to be called or what they return. But it does not care. The compiler has dealt with all that and all the linker needs to provide is the symbol address. It can do this because the symbol is defined in one of the object files that it is linking (otherwise you get a linker error) and it decides for itself where to put them in the completed executable. All it has to do is fix up the placeholder addresses that the compiler has given it.

The program once it is running doesn't need to search for the function, because the linker has already done it. It simply executes the call instruction.

A C++ program can legitimately contain several functions with the same name but different sets of arguments. Not to mention class member functions and namespaces. This would present a problem, since the linker knows nothing of arguments, classes, namespaces etc. So the name the compiler gives the linker is actually a "mangled" name, which encodes the argument list, namespace etc. into a new name that is unique to that particular version of that function. The linker uses the mangled name, and all the callers call the right function and all is good.

All the above assumes that we are doing static linking only, i.e. .o and .a files. Dynamic linking is more complicated but is basically the same process: the executable has a list of imports, the shared libraries have a list of exports, and the dynamic linker (this time) fixes up the program on the fly when it is loaded.

(There's nothing to stop the program itself from containing code to load a shared library explicitly, look up the address of a function and call it through a pointer, but it's not usually done because it happens automatically in most circumstances.)

(OK, that was kind of long, but it's a complicated subject. I hope I've given a reasonable overview of what goes on.)

[1] This is a gross oversimplication. Your modern compiler will go through several intermediate stages between source code and machine language, not even counting the linker. But it will do for our purposes.

[2] Well, it might, if it was doing some clever post-optimisation. But it doesn't need to.

---

### Post by nerdinator on 2012-06-22
Thanks a lot, jim_24601 ! :)
Being simple in language ,that really helped me .

Thank You [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") :)
[]("http://ubuntuforums.org/member.php?u=561272")

---

### Post by nerdinator on 2012-06-22
And,with reference to
```
-lGL -lglut
```
which I added to the linker settings in Code::Blocks in order to link to 
the libraries. 
Now should I find these keywords to any general library?

When I ran ```
[FONT=monospace]dpkg -L freeglut-3 dev[/FONT]
```I thought that the libraries went here (though there were many other things):
```
/usr/lib
/usr/lib/libglut.a
/usr/lib/libglut.so
```I find no correspondence to  the keywords and the .a file.
How are the keywords determined?

---

### Post by Bachstelze on 2012-06-22
libglut.a -> -lglut
libGL.a -> -lGL

You really don't see any relation?

---

### Post by nerdinator on 2012-06-22
I'm sorry, I do.
:-#

---

