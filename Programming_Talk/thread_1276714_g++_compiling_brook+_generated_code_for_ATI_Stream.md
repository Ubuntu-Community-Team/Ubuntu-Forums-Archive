---
title: "g++ compiling brook+ generated code for ATI Stream"
date: 2009-09-27
forum: Programming Talk
---

### Post by dracule on 2009-09-27
Hi, 

I tried out the example problem for ATI stream found in the programming guide (sum.br)

but I cant get the CPP file that brcc generated to compile

here is my g++ code:
> g++ -o output sum.cpp -I /usr/local/atibrook/sdk/include -L/usr/local/atibrook/sdk/lib -llibbrook

and it fails with
> /usr/bin/ld: cannot find -llibbrook
collect2: ld returned 1 exit status

if I take out the part with the -llibbrook I get a bunch of errors taht basically look like 
> undefined reference to `brook::Technique::~Technique()'


so what is going wrong? I know libbrook.so is in /local/atibrook/sdk/lib because I followed the directories in there.

---

### Post by MadCow108 on 2009-09-27
-llibbrook searches for liblibbrook.so (it adds lib and the extension)
you probably want -lbrook

---

### Post by dracule on 2009-09-27
> **MadCow108 said:**
> -llibbrook searches for liblibbrook.so (it adds lib and the extension)
you probably want -lbrook
thanks, just what I needed

---

