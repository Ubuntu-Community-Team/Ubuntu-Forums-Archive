---
title: "dynamic link librariy (dll) concepts needed"
date: 2008-06-23
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-23
this is what i have just read :
> So far, we have assumed that an executable only consists of object files. In practice, they often also link against libraries that implement ready-made functionality. There are two main types of library:Static libraries are put directly into the executable, as if they were object files. This ensures that the library cannot get lost but increases the size of the executable.Dynamic libraries (also called shared libraries or DLLs) are located at a standard location on the user's machine and are automatically loaded at application startup

i cant understand the way an application ,during its runtime (that is after it has been compiled and the linking process is over)...can use a library !
what i have read and understood is that when an application binaries are distributed , they have been through the steps of compiling and linking...how come the executable now be rebuild (that too without the .o file) ??

i am very much a noob to c++ world ..so please forgive me if i am being tooo silly somewhere !!:)
hopefully someone can elaborate the difference between shared and dynamic link libraries...they seem to be of much importance today.
the wiki guys are pretty tough:(...i couldnt grasp the thing thoroughly !!

---

### Post by LaRoza on 2008-06-23
A dynamically linked library is Microsofts term for a shared library. (In Linux, they end with .so)

The easiest way to see the use of them is to think of the Flashplayer plugin. It is loaded during the runtime and used. 

[http://en.wikipedia.org/wiki/Shared_library](http://en.wikipedia.org/wiki/Shared_library)

A shared library is the same concept as a dynamically linked library.

A statically linked library is different.

---

### Post by CptPicard on 2008-06-23
Off the top off my head, correct me when I'm wrong...

The operating system has an element called the loader, whose job it is to load executables and other binaries from disk and to place them in RAM so that they can be used. A binary can make use of shared libraries by being first compiled so that where there is code that is not statically compiled (that is, actual part of the binary), there is a sort of symbolic reference to this external, yet missing, piece of code. Think of it as a sort of unset pointer that is not filled in yet.

Ok, now that the binary gets loaded and it needs a shared library, the loader sees that there also needs to be in RAM the code requested from the shared library. If it is not yet in RAM, loader goes out there and gets the stuff from disk. Now, supposing the stuff is in RAM, all that remains to be done is to fill in the actual addresses of the shared code into the freshly loaded binary, in the places where these symbolic references are. So it requires OS level support in this sense, but it's not rocket science. :)

---

### Post by JupiterV2 on 2008-06-23
The problem simplified:

There are many libraries that do something you want to do. Instead of coding it from scratch every time you write a program, someone has taken the time to make a library for you, saving you that time.

The standard C++ libraries are one such beast and cmath.h is a great example. You want to raise a number to an exponent but do you really want to code that from scratch every time? Do you even know how to do it, especially do it efficiently? You must then include the library at compile time into your program with the -lm switch (short for -lmath). Now you can take advantage of the math functions provided as a part of the C++ standard library(actually, its from the C standard but lets not split hairs).

Another example is writing a program with a GUI. GTK+, wxWidgets, and Qt all provide shared libraries for programmers to take advantage of. If you take a look at the amount of code required to code a GUI from scratch you'll appreciate shared libraries in a WHOLE new way.

Static Libraries have an extension of .a in linux (I have no idea what it would be in Windows). They are compiled directly into the binary just like an object (.o) file. As a matter of fact, that's exactly what they are. Static libraries are a collection of pre-compiled object files (.o) that have been archived into a single file, hence .a is essentially short for .archive.

Shared/Dynamic Libraries (.so in linux, .dll in Windows) are also pre-compiled, linked at compile time, but are not compiled into the program itself. As CptPicard has already stated, the library is loaded into RAM during runtime if it is not already loaded. The danger? If there is an error in a shared library, it will effect the stability of your code. However, the advantage is that  it can be updated independent of your program without recompiling the program itself.

So, if you want to be sure that a library will be accessible without fail at runtime, use a static library. If you want to take advantage of shared code, thereby reducing program size and potentially memory consumption (the shared library needs only be loaded once into memory to be shared by multiple programs at once) then use a shared library.

---

### Post by dexter.deepak on 2008-06-24
thanks a lot for all these concepts..yet one of the doubts need be cleared ..let me reformat my question:

the .exe files in ms windows are "executables", that is ,they have been "compiled && linked(with all possible shared/static libraries)"
now can we add a new piece of object (called dll) at runtime to this .exe file ?

in short, can we add a precompiled,prelinked "object"...which is itself an "executable" (.a or .o) to another "executable" which has seperately been compiled and linked ?

can you also give some examples of static and dynamic libraries ?

the "cmath.h and the libraries used by qt"  are called shared libraries by jupiterV2 ..on the other hand he is also saying 
"You must then include the library at compile time into your program with the -lm switch " 
now...if it is included at the compile time only, the how come is it shared/dynamic ?? it is just an ordinary library..a collection of programs..

---

### Post by galileon on 2008-06-24
you include the switch when compiling to tell the compiler 

"hey, when my program is run, its gonna need the maths library. however, i have decided that I don't want the maths library to be stuck into my program (and mmake it fat), but I want my program to use the maths library already on the user's system. 

so, don't worry about it too much, just put a note for the OS Loader to remind him to look for the actual place he loads the maths library, and to send a memo to my program so it can find the maths functions when it needs them."

Usually, to make it static, ie include the whole maths library with your program, the maths library would need to be compiled with its own static switch to give a file mathslibrary.a, ie an archieve of the maths functions and then your program would be linked to it in the sense that they get stuck in one massive blob. Thats static linking.

Dynamic linking is the note we ask the compiler to leave in our code (with the -lm, or -lgtk, or -lqt, etc), without sticking the whole maths/gtk/qt blob onto the "executable file" that we would distribute. 

hope this makes sense...

---

### Post by dexter.deepak on 2008-06-24
thanks galileon .. i think i got it..just to confirm these postulates:

A) libaries are not static/dynamic ...it is the way of using them in your program that is static/dynamic.
B) any libraries which are used for compiling and are not part of the OS native libraries are "generally" statically linked, in the sense that the application user at the other end may not have the needed libraries to run the program.these are specified by #include directive.
C) libraries which are usually a part of the OS native libraries are linked dynamically,as they are once loaded in ram, and can be shared by other programs also...which isnt possible in case of static ones.
the dynamic linking is specified usually by giving options like "-lm"
D) platform independent applications (like qt) must "not" use dlls as using a part of the native OS code may generate inconsistencies.

did i get it right ?

one more doubt...what i have read:
.cpp is converted to .o by compiler, .o is finally just "linked"
(statically/dynamically) to the libraries to give an executable,which is "run" ...and it doesnt have "any" dependencies

but you all seem to be saying that .o (or an archive .a) is linked to the final executable ..that is to say that even the executable "has" dependencies.....
is that your point ?? or is it that i have read/understood some wrong concepts about the compiling process ??

---

### Post by galileon on 2008-06-24
> **dexter.deepak said:**
> 
A) libaries are not static/dynamic ...it is the way of using them in your program that is static/dynamic.

yes, though some libraries are more commonly statically linked (usually small ones, eg a tiny library for parsing xml files), others are more usually dynamically linked (eg QT, GTK, etc, which are quite large), yet Skype distributes a statically-linked version of skype+QT, so that people without libqt installed can still run it...

> **dexter.deepak said:**
> 
B) any libraries which are used for compiling and are not part of the OS native libraries are "generally" statically linked, in the sense that the application user at the other end may not have the needed libraries to run the program.these are specified by #include directive.
yes. except that the #includes are used for both static and dynamic libraries, - #include just means to copy-paste the function declarations so that the compiler knows that those symbols you don't seem to have declared and defined (eg functions declared in libqt) are actually going to be available one day when the program is loaded by the OS Loader, and not just cry out because it can't find them during compilation.


> **dexter.deepak said:**
> 
C) libraries which are usually a part of the OS native libraries are linked dynamically,as they are once loaded in ram, and can be shared by other programs also...which isnt possible in case of static ones.
the dynamic linking is specified usually by giving options like "-lm"
correct afaik,

> **dexter.deepak said:**
> 
D) platform independent applications (like qt) must "not" use dlls as using a part of the native OS code may generate inconsistencies.
if you mean dll in the m$ sense, then QT probably uses dlls on windows and uses .so files on linux, but that doesn't need to concern programmer who's using QT for the GUI in his programs...

> **dexter.deepak said:**
> 
one more doubt...what i have read:
.cpp is converted to .o by compiler, .o is finally just "linked"
(statically/dynamically) to the libraries to give an executable,which is "run" 

up to here is alright, but

> **dexter.deepak said:**
> 
...and it doesnt have "any" dependencies

i'm not sure what you mean to ask here, but here goes: the executable that has been statically linked to all its libraries that it calls, does not have any dependencies (it doesnt require anything else to be present).

if it is dnamically linked, then it "depends" on the said libraries to be present (eg qt/gtk/etc), otherwise the program wouldn't know where to jump to when you say pushButton->setWidth(); for eg.

if the required dynamic lybrary is present, however, the loader will tell your program where to find that function when your program asks for it...


> **dexter.deepak said:**
> 
but you all seem to be saying that .o (or an archive .a) is linked to the final executable ..that is to say that even the executable "has" dependencies.....
is that your point ?? or is it that i have read/understood some wrong concepts about the compiling process ??

i guess the above comments might help with this one...

---

### Post by nvteighen on 2008-06-24
> **dexter.deepak said:**
> 
(...)
but you all seem to be saying that .o (or an archive .a) is linked to the final executable ..that is to say that even the executable "has" dependencies.....
is that your point ?? or is it that i have read/understood some wrong concepts about the compiling process ??

There's nothing such a "completely" standalone executable, unless it is an operating system. Even if you static link everything, you'll need a kernel that reads the executable format, places the thing into memory, run it only if you have permission, performs the proper system calls, etc.

---

### Post by dexter.deepak on 2008-06-24
loads and loads of thanks to all of you :guitar:
it sounds like a perfect understanding !!

---

### Post by CptPicard on 2008-06-24
> **dexter.deepak said:**
> 
A) libaries are not static/dynamic ...it is the way of using them in your program that is static/dynamic.

Libraries need to be compiled differently if you want to use them dynamically. See here

[http://www.ibm.com/developerworks/library/l-shobj/](http://www.ibm.com/developerworks/library/l-shobj/)

The key point is the "position independent code" part... the binary of the library must not contain fixed addresses as there is no telling where in RAM the library will actually end up at.

> 
B) any libraries which are used for compiling and are not part of the OS native libraries are "generally" statically linked, in the sense that the application user at the other end may not have the needed libraries to run the program.

Not really. It's preferable to just tell the user to get the dependency. This sort of "crossplatformness" would just create a number of really huge binaries.

> 
these are specified by #include directive.


You need #includes anyway, it's for the compiler to know what some symbol means.

> 
the dynamic linking is specified usually by giving options like "-lm"

I would rather say that all linking is specified with the -l switch. Dynamic is the default, you can override that with "-static" (see man gcc).

---

### Post by LaRoza on 2008-06-24
> **CptPicard said:**
> 
Not really. It's preferable to just tell the user to get the dependency. This sort of "crossplatformness" would just create a number of really huge binaries.


I agree.

---

### Post by dexter.deepak on 2008-06-24
thanks CptPicard.
the link you provided is just too good...though i have read only a half of it..i am having a problem:

it says that compiling and linking of a c program takes place in two steps :
>$ gcc -c hello.c
 $ ld -lc -o hello hello.c

i get an error in the second step:
```
dpak@dpak-server:~/c$ ld -lc -o hello hello.o
ld: warning: cannot find entry symbol _start; defaulting to 00000000080481a4
dpak@dpak-server:~/c$ ls
hello  hello.c  hello.o
dpak@dpak-server:~/c$ ./hello
bash: ./hello: No such file or directory

```

an interesting problem to me is that though i am getting an o/p file of "hello" .. why do i get an error that the file isnt present...i should have got some other message indicating that the file "hello" is corrupt.

---

### Post by CptPicard on 2008-06-24
gcc runs the linker implicitly as part of the command, I think the tutorial just points out that the linker step exists in there... but I have never really programmed anything "real" in C so I may be wrong :)

---

### Post by nvteighen on 2008-06-25
> **CptPicard said:**
> 
I would rather say that all linking is specified with the -l switch. Dynamic is the default, you can override that with "-static" (see man gcc).

Actually, -static tells the compiler to link **everything** statically. But you are able to link some things dynamically and other statically, by convenience.

If you only want the Standard Math Library statically linked, you do this:
```

gcc -o test test.c /usr/lib/libm.a

```

The reasonale: the .a file is a bunch of .o files and therefore, you can include them in the input list as usual. 

If, after compiling our fictional "test", you run:
```

ldd test

```
You'll see libc.so dynamically linked but not any trace of libm.so (the shared lib version of the math library).

Of course, such a movement should be done with care in useful cases to avoid double-linking and similar errors. And beware that static linking increases the binary size a lot!

---

