---
title: "Anjuta IDE help - can't open *.o file"
date: 2007-02-13
forum: Programming Talk
---

### Post by billdotson on 2007-02-13
I am starting to learn C++ and I used Anjuta to compile a simple script and it's output was Hello.o 
But when I try to open it with Anjuta it says there isn't an application or plug-in available to handle it.  

I don't know anything about programming in any language, so I decided to start with C++
From what I understand I need a program to compile the code and a program to link it.  I want to be able to do anything that is possible with C++ using Anjuta.  I have heard of different libraries and stuff like that like a GUI library for instance.   I saw them on this page [http://www.thefreecountry.com/sourcecode/cpp.shtml]("http://www.thefreecountry.com/sourcecode/cpp.shtml") 

What do I do to turn Anjuta into a fully useful C++ environment where I can do anything I need to with C++ (GUI or terminal) seeing as how I am going to start learning more of it?  Also what is a good free, legal C++ environment for Windows when I use Windows?  

Thanks.

---

### Post by Mirrorball on 2007-02-13
Hello.o is a binary file, you can't open it with Anjuta. It means that your Hello.cpp source file has been compiled, but to get an executable file, it must be linked. Anjuta usually runs the compiler and the linker. I don't know what you did, but are you sure that Hello.o was the only output?

---

### Post by billdotson on 2007-02-13
I am sure I opened the text file and told it to compile.  The only output I got was the .o file on the desktop where everything was being sent to

---

### Post by fct on 2007-02-14
Paste the source code here.

BTW, don't use "script" for C/C++ source code, it gets confusing since scripts aren't meant to be compiled, just run by an interpreter.

---

### Post by Mirrorball on 2007-02-14
Here:
[http://www.anjuta.org/documents/C/anjuta-manual/anjuta-manual.html#building](http://www.anjuta.org/documents/C/anjuta-manual/anjuta-manual.html#building)
You should press F11 and then F3.

---

### Post by billdotson on 2007-02-14
here is the source 

#include <iostream>
using namespace std;

int main()
{
cout << "Hello World!\n";
return 0;
}

When I open the file it doesn't even have a build tab in the menu bar.. what is going on? It was working yesterday..

---

### Post by Mirrorball on 2007-02-14
Did you create a project? Maybe you should read a tutorial on Anjuta. These tools are not intuitive, you have to learn how to use them.

---

