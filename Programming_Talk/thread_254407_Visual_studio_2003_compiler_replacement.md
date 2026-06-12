---
title: "Visual studio 2003 compiler replacement"
date: 2006-09-09
forum: Programming Talk
---

### Post by kthakore on 2006-09-09
I am looking for a C++ compiler that can compile C++ files as VS2003 does. No I am not looking for a IDE replacement for VS2003, in fact I prefer a compiler like g++, but I am not sure if g++ will compile C++ as VS2003 does. Any help is very much appreciated.

---

### Post by Grey on 2006-09-09
erm... g++ compiles my code just fine... what exactly are you having issues with?  I gather that you have some code that compiled in MSVC, but not g++?  Could you provide some examples, and perhaps we could help you find a solution?

Most linux IDEs, such as kDevelop or Anjuta are just frontends for g++ anyway.

---

### Post by kthakore on 2006-09-10
Well I don't have any code as of now, but I am in a engineering C++ courses and they are very specific about using MSVS2003. My prof told me that most of the code will be generic C++ but, some may not, and I was wondering if linux has a compiler that will compile any C++ codes generic or otherwise.

---

### Post by kthakore on 2006-09-10
Well I guess what I am looking for is a linux compiler that will make a win32 .exe file from generic C++ code.

---

### Post by arkangel on 2006-09-10
if the code is portable , will compile in several plataforms (most of the console app), but if in you code you are calling microsoft-specific functions like the ones found in Microsoft Foundation classes or windows forms   (hidden in some twisted dll) it wont compile.

you can use a cross compiler to generate code that will run on windows, but i  never tried too hard and i duno that  if you will  be able to compile big projects   that use soem of the functions i told you above 

 look here 
[http://wxwidgets.org/docs/technote/crosscmp.htm](http://wxwidgets.org/docs/technote/crosscmp.htm)
or google : cross c++ compilation linux windows

---

### Post by kthakore on 2006-09-11
```
UPDATE: Well I found a cross copiler called minGW but I don't hink it can handle stuff like OPENGL and directx
```

The search continue, any help is very much appreciated

---

### Post by nereid on 2006-09-11
Hi,

maybe you would like to take a look at the following links

[http://wiki.qgis.org/qgiswiki/BuildingWindowsBinaryOnLinux](http://wiki.qgis.org/qgiswiki/BuildingWindowsBinaryOnLinux)
[http://rooster.stanford.edu/~ben/linux/crosshowto.php](http://rooster.stanford.edu/~ben/linux/crosshowto.php)

---

### Post by kthakore on 2006-09-11
thx for the links neried those really helped

---

### Post by kthakore on 2006-09-12
Are some more googling and searching I found another sloutions ppl can take, altough I am much more happier with mingw and nano. But for IDEers out there this link is a good shot 

[http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html]("http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html")

---

### Post by arkangel on 2006-09-15
OpenGl is an standard,  if you write code for OpenGl  it will be portabel on any plataform that support it (Unix,linux, windows,etc) 

DirectX is a windows specif palataform , it will only  compile under windows

---

### Post by kthakore on 2006-09-15
Thanks for that reply darkangel

oh does any noe now where i can find tutorials for mono and apache

---

### Post by 3rdalbum on 2006-09-16
If you write your program using Winelib rather than real Windows function calls, then it will compile and run on Windows and Linux, as long as you have Winelib; but I don't know how to create an actual win32 .exe file.

---

### Post by X.Cyclop on 2006-09-16
You may want to use Code::Blocks with GCC. Code::Blocks can import VC++ projects.:wink:

---

### Post by kthakore on 2006-09-18
Thats awesome!!! Thx

---

