---
title: "Eclipse C++: changing compile-time flags"
date: 2009-07-22
forum: Programming Talk
---

### Post by gamelord12 on 2009-07-22
I'm writing a game using Allegro in C++ using Eclipse, but I can't find how to add compiler flags, which are necessary in order to use a library that enables PNG images to be used.  My compiler is MinGW.  Also, I'm developing the game on Windows first, Linux second, though I doubt this changes anything with helping me through the Eclipse interface.

---

### Post by dwhitney67 on 2009-07-22
Search for the properties of your project.  There is a section dedicated to adding/specifying special compiler options.  There's another section that is similar, but for linker options.

IMHO, you should forgo the use of the IDE until you understand how to build the same application using the command line.  The IDE robs you of valuable know-how, and makes you less of a programmer/developer.  End of opinion.

---

### Post by gamelord12 on 2009-07-23
I've compiled programs by command line quite a bit in my various computer science classes.  The problem I was having is just finding those options in the IDE.  I think I just found it in project properties->C/C++ Build->Settings->MinGW C++ Linker->Miscellaneous.  I'll be doing some tests on that in the next day or so.

---

### Post by gamelord12 on 2009-07-23
Okay, I don't think that allows me to add other files to be compiled.  How would I do this command:

g++ -o prog.exe prog1.cpp prog2.cpp -flag1 -flag2

in Eclipse using MinGW?

---

### Post by dribeas on 2009-07-24
> **gamelord12 said:**
> Okay, I don't think that allows me to add other files to be compiled.  How would I do this command:

g++ -o prog.exe prog1.cpp prog2.cpp -flag1 -flag2

in Eclipse using MinGW?

In general IDEs work on a per-file basis. If the project contains source1.cpp and source2.cpp and you want to pass in -copt1 -copt2 -lopt1 -lopt2 (where copt are compiler options and lopt are link options) the compilation process would be:

```

g++ -c -o source1.o -copt1 -copt2 source1.cpp
g++ -c -o source2.o -copt1 -copt2 source2.cpp
g++ -o prog.exe -lopt1 -lopt2 source1.o source2.o

```

That is, you do not compile more than one source file in a single step. If you are having problems with using the IDE, I can suggest using cmake to generate both makefiles and eclipse project files (plus a set of other IDE project files).

But you should really follow dwhitney advice and work first on the command line, then with simple makefiles (manually created) to learn and understand the build process.

---

### Post by gamelord12 on 2009-07-24
As I already said, I've had a good handful of computer science courses where we not only learned what's involved in the build process (linking, assembling, etc.), but we also worked exclusively with the command line; I know how to do that, the only difference being that we worked with C rather than C++.  The problem is that there are no simple instructions for "Here's how to do this in an IDE as opposed to via the command line", which is really all I want to know.

---

### Post by dwhitney67 on 2009-07-24
The following instructions apply if you have created a "Managed-Make C++ Project".

1.  Right-click on your project name; select **Properties**.

2.  Click on **C/C++ Build**.

3.  Under **GCC C++ Compiler**, select **Directories**.

4.  Click the little "+" icon to add the path to your header file(s).  You do not need to specify the -I.  Repeat step 4 for additional paths.

5.  Under **GCC C++ Linker**, select **Libraries**.

6.  Click the little "+" icon for **Libraries**, and add your library.  Repeat as necessary for each library.

7.  If any of your library entries do not fall under a standard path (eg. /usr/lib or /usr/local/lib), then add this path by clicking the "+" icon under **Library Search Path**.  Repeat as necessary.

When you are done with all this, select the **OK** button at the lower-right of the window.  Then attempt to build your project.

P.S.  If you need to set specific compiler flags (eg. -pedantic -ansi), under **GCC C++ Compiler**, peruse the various sub-categories to see if there is a check-box you can use, or just click on **Miscellaneous** to input your own.

---

### Post by gamelord12 on 2009-07-25
Alright, it worked.  Thanks.

---

