---
title: "Gedit and C++"
date: 2008-02-18
forum: Programming Talk
---

### Post by Gerlads Mod on 2008-02-18
When I compile my C++ programs I use these 2 files.

Compile and gccp.

gccp is this...
```
#/bin/sh

echo compiling C++ using -ansi -pedantic-errors -Wall
g++ -ansi -pedantic-errors -Wall $1 $2 $3
```

And compile is this...
```
#/bin/sh

./gccp ProjectName.cpp
sleep 100
```

Once you give both these execution permissions, you can click on Compile and it will compile your C++ script into a.out.

I was hoping someone could help me out with making Gedit run these commands in external tools so I can just push F5 and it will compile.

Thanks in advance!

---

### Post by WitchCraft on 2008-02-18
if  you use Geany instead of gedit, you have a build/compile menu built in

---

