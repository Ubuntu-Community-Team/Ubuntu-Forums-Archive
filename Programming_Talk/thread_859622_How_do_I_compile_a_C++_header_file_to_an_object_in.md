---
title: "How do I compile a C++ header file to an object in g++?"
date: 2008-07-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-14
I have a C++ .h file which contains 2 classes and a main function.  Normally, I seperate between the .cpp and .h files.  But I am actually using another program to generate the single header file...easier for it than generating 2 files.  I can compile it by doing g++ filename.h.  However, I do not get an object file to execute.  How do I compile header file to object in g++?

---

### Post by SNYP40A1 on 2008-07-14
Sorry, I meant executable, not object.

---

### Post by rnodal on 2008-07-15
I may be wrong but I believe that g++ does not process the header files as you are thinking. I think you need to have a cpp file that uses that header minimum. Header files are meant to be used for definitions but you may know that already.

---

### Post by Zugzwang on 2008-07-15
If you just want to make an executable file out of them anyway, why don't you just rename them to ".cpp"?

I think you are trapping into the problem that gcc/g++ is an all-in-one command - It compiles, links and makes pre-compiled headers. So why not trying the trick mentioned above?

Note that .cpp files may #include other .cpp files, so they are strictly speaking equivalent to ".h" files (but it is convention not to use them in this way).

---

### Post by dribeas on 2008-07-15
> **SNYP40A1 said:**
> I have a C++ .h file which contains 2 classes and a main function.  Normally, I seperate between the .cpp and .h files.  But I am actually using another program to generate the single header file...easier for it than generating 2 files.  I can compile it by doing g++ filename.h.  However, I do not get an object file to execute.  How do I compile header file to object in g++?

You want to make it a .cpp file. You should never implement functions in .h files, unless you define them as inlined, but then again, that is not even possible with main, so you must make it into a .cpp. Defining a non-inlined function in a header file will force the compiler into creating the symbols in all compilation units that include that header, and during link time you'll run into trouble as a symbol is defined in more than one compilation unit.

Header files are devised to define interfaces that can be used in different compilation units. If you only have a compilation unit, they are not what you need.

David Rodríguez Ibeas

---

### Post by KingTermite on 2008-07-16
> **dribeas said:**
> You want to make it a .cpp file. You should never implement functions in .h files, unless you define them as inlined, but then again, that is not even possible with main, so you must make it into a .cpp. Defining a non-inlined function in a header file will force the compiler into creating the symbols in all compilation units that include that header, and during link time you'll run into trouble as a symbol is defined in more than one compilation unit.

Header files are devised to define interfaces that can be used in different compilation units. If you only have a compilation unit, they are not what you need.

David Rodríguez Ibeas

+1

Header files are not designed to contain the "actual" implementation code and it may not even process the main inside of it as a header file. You should look at a few C++ tutorials to see how C++ programs are typically structured.

---

