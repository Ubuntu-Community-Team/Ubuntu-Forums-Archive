---
title: "Looking for a disappeared g++"
date: 2005-09-10
forum: Programming Talk
---

### Post by kalindriv on 2005-09-10
Hi, I formatted my pc yesterday and I upgraded all. I have to develop a C++ program, but I can't compile with eclipse or even with a self-made makefile.

This is the eclipse report when I push the compiling botton!!!

```
**** Full rebuild of configuration Debug for project prova_stringa ****

make -k clean all 
rm -rf  ./main.o  ./main.d prova_stringa
 
Building file: ../main.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -omain.o ../main.cpp
/bin/sh: g++: command not found
make: *** [main.o] Error 127
make: Target `all' not remade because of errors.
Build complete for project prova_stringa

```

Is there someone who can help me? What should I do? Why g++ is not there?? Should I install something??

Using Synaptic I found that I don't have g++ installed and there are many versions... should I install one of these?
Instead there is gcc-3.3-base installed

The real strange thing is that 3 days ago, everything worked...

---

### Post by mostwanted on 2005-09-10
> Using Synaptic I found that I don't have g++ installed and there are many versions... should I install one of these? 

I don't mean to sound arrogant, but *D'uuuh*! ;)

---

### Post by kalindriv on 2005-09-10
I typed:
```
 #sudo apt-get install build-essential 
```

Now I can compile with the self-made makefile \\:D/ 

But....using Eclipse I can't compile and this is the report:  :mad: 

> 
Severity Description Resource In Folder Location Creation Time
2 *** [main.o] Error 127 prova_stringa  10 settembre 2005 11.23.51

Severity Description Resource In Folder Location Creation Time
1 Error launching external scanner info generator (gcc -E -P -v -dD /media/win_d/eclipse_workspace/.metadata/.plugins/org.eclipse.cdt.make.core/specs.cpp) prova_stringa  10 settembre 2005 11.23.51

Severity Description Resource In Folder Location Creation Time
0 File not indexed because it was not built main.cpp prova_stringa  10 settembre 2005 11.23.48

What is it? What can I do?

---

