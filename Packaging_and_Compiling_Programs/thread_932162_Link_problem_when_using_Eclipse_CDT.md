---
title: "Link problem when using Eclipse CDT"
date: 2008-09-28
forum: Packaging and Compiling Programs
---

### Post by Mingliuestc on 2008-09-28
I am a new user of Eclipse IDE, recently I was trying poco c++ libs on Eclipse CDT, when I compile a example program, I ran into problem below:
make all 
Building target: test03
Invoking: GCC C++ Linker
g++ -L/usr/lib/ -o"test03"  ./main.o   -llibPocoXML.so
/usr/bin/ld: cannot find -llibPocoXML.so

before this, I had set the GCC C++ Linker under the project properties like this:
Libraries(-l) add libPocoXML.so
Library search path(-L) add /usr/lib

where am I wrong???

---

### Post by Ansible on 2008-09-28
Haven't used PocoXML, but I'm using the poco foundation lib in a project right now.  The way I set it up:

Under the "Libraries (-l)" list I put "PocoFoundation".  No .so or anything.  Yes, the library file is named libPocoFoundation.so; CDT 'helps' you by making the actual name not work.  Its the same with other libs, so openal instead of libopenal.so, etc. 

Under "Library search path (-L)" I have "usr/lib".  I don't remember if this is needed or not, but I have it.  

If you're using PocoXML, you might need PocoFoundation too.  Hope this helps!

---

### Post by Mingliuestc on 2008-10-05
It works! Thanks a lot:)

---

