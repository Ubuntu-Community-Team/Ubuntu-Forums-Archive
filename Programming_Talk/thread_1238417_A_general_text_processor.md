---
title: "A general text processor?"
date: 2009-08-12
forum: Programming Talk
---

### Post by Vadi on 2009-08-12
Hi,

Does anyone know of a general text processor that can depending on defined variables, include/exclude certain parts of text?

ala cpp and its #includes, except that it can't be used (it'll mangle non-C).

---

### Post by Cyanidepoison on 2009-08-12
You can use the CPP on files other than C/C++ source code.

---

### Post by tvtech on 2009-08-12
> **Vadi said:**
> Hi,

Does anyone know of a general text processor that can depending on defined variables, include/exclude certain parts of text?

ala cpp and its #includes, except that it can't be used (it'll mangle non-C).

bluefish editor.  It is designed for coding, mostly html but it will handle all common languages. it's available in add/remove

---

### Post by issih on 2009-08-12
you could just use the c++ preprocessor as suggested before:

g++ -E -Dflag inputFile > outputFile

the -E tells the compiler to stop after the preprocessing, the -D inputs a 'define' of your choosing to filter the source text according to the preprocessor directives in the inputFile, and then you squirt the output on std out to a file.

It would work...not sure its all that user friendly, but I'm not sure what you are trying to do :)

---

### Post by Vadi on 2009-08-12
vadi@ubuntu-laptop:~/Desktop$ nano test 
vadi@ubuntu-laptop:~/Desktop$ g++ -E -DBLAH test > result
g++: test: linker input file unused because linking not done
vadi@ubuntu-laptop:~/Desktop$ cat test 
#if (defined BLAH)
lol!
#endif
haha.
vadi@ubuntu-laptop:~/Desktop$ cat result 
vadi@ubuntu-laptop:~/Desktop$ 


Anything I'm missing?

---

### Post by Cyanidepoison on 2009-08-12
```

Macintosh:ryan $ cat foo.txt
#ifndef FOO
text
#endif
Macintosh:ryan $ cpp -DFOO foo.txt
# 1 "foo.txt"
# 1 "<built-in>"
# 1 "<command line>"
# 1 "foo.txt"
Macintosh:ryan $ cpp foo.txt
# 1 "foo.txt"
# 1 "<built-in>"
# 1 "<command line>"
# 1 "foo.txt"

text
Macintosh:ryan $ 

```

---

### Post by Vadi on 2009-08-12
That's as far as I got when trying at first. Do you know how to remove those #'s ?

(me no speak awk voodoo)

---

### Post by Cyanidepoison on 2009-08-12
Pipe it through a Python script or something to only print out lines that don't start with #.

---

### Post by ArmenianLeader4 on 2009-08-13
I didn't read the whole thread, but I know that there is a coding editor called bluefish that works pretty well.

---

### Post by PaulFr on 2009-08-13
```
cpp -P -DFOO foo.txt
``` leaves blank lines instead of the standard line markers. An awk script might do better, if the input is largely text rather than C code (#includes, #if, ...).

---

### Post by mali2297 on 2009-08-14
There is [GPP]("http://en.nothingisreal.com/wiki/GPP") and of course the classical [M4]("http://www.gnu.org/software/m4/").

---

