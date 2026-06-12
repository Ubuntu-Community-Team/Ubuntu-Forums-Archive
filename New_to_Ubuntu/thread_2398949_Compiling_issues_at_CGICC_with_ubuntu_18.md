---
title: "Compiling issues at CGICC with ubuntu 18"
date: 2018-08-20
forum: New to Ubuntu
---

### Post by heartlyforjesus on 2018-08-20
Hi, I have upgraded my desktop from Ubuntu 16.04 to Ubuntu 18. After I updated it, when I try to compile a CGI program, I got below error.

```
relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a PIE object; recompile with -fPIC




```

This is my compilation code.

```
g++ -Ofast -g -std=c++0x -fPIC test.o -lm /usr/lib/libcgicc.a -L/usr/local/lib -o test.cgi



```

How do i fix this issue in ubuntu 18

---

### Post by spjackson on 2018-08-20
You've shown the link command but not the one that compiles source into test.o. I expect that you need -fPIC in the compilation command as well.

---

### Post by heartlyforjesus on 2018-08-21
> g++ -fPIC -Ofast -g -std=c++0x  -c test.cpp -o test.o

[COLOR=#242729][FONT=Arial]g++ -fPIC -Ofast -g -std=c++0x test.o -lm /usr/lib/libcgicc.a -L/usr/local/lib -o test.cgi.[/FONT][/COLOR]


This is the complete build commands. But it comes with the same error.

---

### Post by spjackson on 2018-08-22
> **heartlyforjesus said:**
> 
```

g++ -fPIC -Ofast -g -std=c++0x  -c test.cpp -o test.o

[COLOR=#242729][FONT=Arial]g++ -fPIC -Ofast -g -std=c++0x test.o -lm /usr/lib/libcgicc.a -L/usr/local/lib -o test.cgi.
[/FONT][/COLOR]
```
This is the complete build commands. But it comes with the same error.
A simple cgi program using libcgicc.a builds ok for me on Ubuntu 18 using commands similar to those you mention above.

If the problem is not in test.o, which it shouldn't be because you created it with -fPIC then it must be in one of the included libraries.

I'm a bit puzzled by [COLOR=#242729][FONT=Arial] -L/usr/local/lib since you don't seem to be pulling in any libraries that would be there, but perhaps that's a red-herring, unless you have your own libm in /usr/local/lib.

 Where did you get [COLOR=#242729][FONT=Arial]/usr/lib/libcgicc.a from? I don't have one and the package libcgicc-dev seems to install that library in /usr/lib/x86_64-linux-gnu/libcgicc.a and linking to this works for me with -fPIC.[/FONT][/COLOR][/FONT][/COLOR]

---

