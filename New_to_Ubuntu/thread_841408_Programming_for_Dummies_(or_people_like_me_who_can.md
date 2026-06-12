---
title: "Programming for Dummies (or people like me who can't seem to figure anything out)"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by sonicskywalker on 2008-06-26
OK, I'm a convert from Windows. I can now navigate the Ubuntu environment. Unfortunately, I know nothing about developing for Linux. I've been able to work in Java with Eclipse, but I'd like to move on to C++ or maybe learn a BASIC dialect. Where should I start? What packages and programs do I need to download? All help is greatly appreciated.

---

### Post by bumanie on 2008-06-26
I'm not a programmer, but I think most of the open source is programmed in "C" and "Perl". To compile "C" you need to install build-essential > sudo apt-get install build-essential This is the gcc compiler. To compile > gcc <file.c> > gcc <file.c> -o <file.c> > ./<file.c Look up "C" tutorials for more info - many are written with the assumption that one is using linux. I can't provide any more information about "C" or "Perl". A programer who knows much more than I will probably be able to help more. Be patient and someone with more knowledge will help.

---

### Post by ConMan318 on 2008-06-26
Fortunately, many programming compilers/interpreters are pre-installed in Ubuntu.  I think C/C++, Java, Python, Perl, Ruby, Lisp, and others are already there.  For C (and I think C++, too) you do need to install one extra package to recognize some basic functions, with "sudo apt-get install build-essential".

Since you don't know what you want to learn exactly, I'd recommend looking up some tutorials online (those are everywhere, [http://ubuntuforums.org/showthread.php?t=832449](http://ubuntuforums.org/showthread.php?t=832449) is a good starter).  Usually the first step in these tutorials is getting the compiler/interpreter for the language the tutorial is about.  Obviously I can't tell you what packages you'll need for every language, so you'll kind of have to pick one. :p  But you'll probably find that you already have it installed.  Good luck!

And for the record, I think you should start with C++; it's is widely used for a variety of applications and is easy to start learning.  There are also enormous amounts of resources about it, so you won't have trouble finding a good tutorial.

---

### Post by WRDN on 2008-06-26
If you want to start programming C++, have a look at Code::Blocks program. Its a pretty good compiler/ IDE.

You can test to see if you have the ability to compile already by creating a cpp file (source code file for C++) and then attempting to compile it in the terminal.

First, create a file called "test.cpp" anywhere (in this short tutorial, it will be on the Desktop). Now, open the file using a text editor, and enter the following:

```

#include <iostream>

using namespace std;

int main()
{
cout<<"Hello World\n";
return 0;
}

```

Yes! It's the infamous Hello World program :)

Now, open the terminal, and change the directory to the one the file is located in.
In this case, I would type:

```
cd Desktop
```

Now, type

```
g++ test.cpp -o test
```

Finally, enter the command

```
./test
```

All being well, it should compile and run.
If the libraries for g++ are not already installed though, you should recieve directions on installing them.

Happy Coding :)

---

### Post by mcduck on 2008-06-26
Nope, the compilers aren't installed by default, they come in the "build-essential"-package. Java definitely isn't installed by default.

Python is included in the default install (as it's used by many of the default applications and tools) and it happens to be one of the best languages to start programming.. And you don't even need to compile Python apps (it's possible, though)..

---

### Post by sonicskywalker on 2008-06-26
Thank you for responding. I can see i'm not the only one who is confused by this problem. I once tried to have a go with python on Windows, but was instantly repelled by wierd errors. (I think Python is in love with the Internet and doesn't know how to function without it. Kind of like Ubuntu. :( )

In the meantime, the gcc looks good (now that I've finally seen someone explain in English how to do it)

I already know C++, but I know it for windows. Does anybody know where to find a good tutorial that explains the differences in the language, or can I still use most of the same include files? (Obviously I can use iostream and namespace std!)

> Yes! It's the infamous Hello World program 


i have vowed to NEVER make another one of those. Instead, perhaps, i will create a "Goodbye, cruel world!" program. :lolflag:

---

