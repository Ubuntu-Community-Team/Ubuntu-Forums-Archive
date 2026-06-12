---
title: "How do I run C / C++ programs?"
date: 2005-07-09
forum: Programming Talk
---

### Post by erik-the-red on 2005-07-09
So, I wrote out a basic "Hello, World!" application in C and then I used gcc [filename].c.

The compilation went fine, but how do I actually run the program?

---

### Post by adwait on 2005-07-09
./a.out

---

### Post by zeroK on 2005-07-09
gcc -o test test.c
./test

:)

---

### Post by the_it on 2005-07-12
gcc's default usage is 

```
$ gcc <source code>
```

What that does is that it compiles the said source code into the default output file, which is normally a.out.  Of course, most people use the -o option in this way

```
$ gcc -o <outputfile> <sourcecode>
```

It compiles the source code and creates the executable specified in the outputfile.

to run the output file, or any program for that matter, you simply need to type its name if it is in the system path.  Normally, however, the current working directory ( the ./ directory ), is not included in the system path.  Thus you normally have to specify where the program is, which is in the current directory.

so it's probably 
```
$ gcc -o <outputfile> <sourcecode>
$ ./<outputfile>
```

---

