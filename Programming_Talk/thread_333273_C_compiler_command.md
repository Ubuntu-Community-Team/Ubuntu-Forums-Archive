---
title: "C compiler command?"
date: 2007-01-07
forum: Programming Talk
---

### Post by Jamesbowden on 2007-01-07
I have been using C++ for a little while now, i install the build essential pack from the package manager so i could use the "gcc" and "g++" command to compile my code.

however i am thinking of doing a bit of C, but i dont know the command to compile it.

what command do i use?

---

### Post by Canis familiaris on 2007-01-07
Use the command:
```

user@user-pc:~/dev$  gcc filename.c -o program.bin
```

---

### Post by Jamesbowden on 2007-01-07
> **Anurag_panda said:**
> Use the command:
```

user@user-pc:~/dev$  gcc filename.c -o program.bin
```

I thought gcc was only for c++?

---

### Post by Canis familiaris on 2007-01-07
gcc is for C
g++ is for C++

---

### Post by Jamesbowden on 2007-01-07
> **Anurag_panda said:**
> gcc is for C
g++ is for C++

Ahh thanks.

---

### Post by mxrten on 2007-01-07
It's just the same as with c++-code, gcc can be used for both languages, just use a c-file instead.  Gcc decides which language to use based upon the file extension. 

You can force language selection with the  -x <language> flag... E.g. **-x c**

---

### Post by Canis familiaris on 2007-01-07
gcc intended mainly for C. If you try to compile C++ programs with gcc it refuses to compile classes (alteast when i try to compile)

---

### Post by moma on 2007-01-07
The basic gcc command looks like this
$ gcc -Wall program.c -o program

Run the program
$ ./program 

An old but good intro to c.  Replace cc with gcc.
[http://users.actcom.co.il/%7Echoo/lupg/tutorials/c-on-unix/c-on-unix.html](http://users.actcom.co.il/%7Echoo/lupg/tutorials/c-on-unix/c-on-unix.html)

Of course the [GCC...]("http://gcc.gnu.org") (GNU's compiler collection that includes c, c++, Ada, Fortran...) has it's own documentation: [http://www.gnu.org/software/gcc/onlinedocs/](http://www.gnu.org/software/gcc/onlinedocs/)
---------------

GCC can determine the source language from file extension.
 
$ gcc  test1.c  will start a c-compiler.  (a compiler in means of a module, program )
$ gcc  test1.cpp  will start a c++ compiler.  You must link with -lstdc++
$ gcc  test1.f77  will start a fortran compiler.
$ gcc  test1.java  will start the GCJ Java compiler.

gcc's  command line is rather general, so you may need to add flags and referencies to link libraries.

What is the difference between gcc and g++ ?
g++ is a program that calls  gcc with appropriate flags and libraries for c++ compilation.  Thus for c++ coding,  the g++ is more convenient to use than gcc.  
For example:

$ g++  test1.cpp  -o test1   
(is equal to) 
$ gcc  -lstdc++  test1.cpp  -o test1        ( requires linkage to libstdc++ library)

Run it
$ ./test1

See also:
Browse to [this...]("http://home.online.no/%7Eosmoma/opportunities.html") and locate 
[COLOR="Magenta"]* Linux development platform...(pdf) Chapter 3.3
* Advanced Linux programming(pdf)[/COLOR]

Download the books (pdf) and read ;-)

See also 2:
[http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696](http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696)

---

### Post by Canis familiaris on 2007-01-07
> **moma said:**
> 
What is the difference between gcc and g++ ?
g++ is a program that calls  gcc with appropriate flags and libraries for c++ compilation.  Thus for c++ coding,  the g++ is more convenient to use than gcc.  
For example:

$ g++  test1.cpp     
(is equal to) 
$ gcc  -lstdc++  test1.cpp     (requires linkage to libstdc++ library)


See also:
Browse to [this...]("http://home.online.no/%7Eosmoma/opportunities.html") and locate 
[COLOR="Magenta"]* Linux development platform...(pdf) Chapter 3.3
* Advanced Linux programming(pdf)[/COLOR]

Download the books (pdf) and read ;-)

See also 2:
[http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696](http://www.ubuntuforums.org/showthread.php?p=1962696#post1962696)

Er, thanks!

---

