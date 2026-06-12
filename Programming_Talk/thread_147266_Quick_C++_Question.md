---
title: "Quick C++ Question"
date: 2006-03-19
forum: Programming Talk
---

### Post by cobbweb on 2006-03-19
Im new to C++. I'm not sure what package i need to install to get the c++ compiler and also, what do i type in the command line to compile and run the c++ code? Any help is wanted thank you 


 Cobbweb

---

### Post by hod139 on 2006-03-19
To install the build tools open a terminal and type
```

sudo apt-get install build-essential

```

This will install g++, a command line c++ compiler.

If you had a source file foo.cpp, you would compile by typing
```

g++ foo.cpp

```
which will produce an executable called a.out.  To run a.out, type
```

./a.out

```

If you want to specify an executable name, use the -o option
```

 g++ -o foo foo.cpp
 
```

then run by
```

./foo

```

For IDEs, see the sticky thread.  My personal choice is Kdevelop.

---

### Post by pranith on 2006-03-19
hi,
   you have to install a compiler first that is g++
install it using apt or synaptic 
then for compiling the programs the command is:
[COLOR="Red"]g++ <file name>[/COLOR]
this leaves executable named a.out in ur working directory to run it u have to type:
[COLOR="Red"]./a.out[/COLOR]

hope that helps...

---

### Post by hod139 on 2006-03-19
You shouldn't install only g++.  Sooner or later you will run into trouble.  Make sure you use the build-essential package.

---

