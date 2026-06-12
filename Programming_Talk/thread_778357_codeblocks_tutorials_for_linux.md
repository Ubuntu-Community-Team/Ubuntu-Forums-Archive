---
title: "code::blocks tutorials for linux?"
date: 2008-05-02
forum: Programming Talk
---

### Post by iansane on 2008-05-02
Hi, I have been learning c++ for a few weeks. So far I have just been writing in gedit and then compiling with g++.

Some have said, I should be using an IDE because it is easier. I have to disagree. I just installed code::blocks which was recommended and have no idea how to build a project. I'm finding tutorials that are made for the windows dist. I don't understand a lot of terminology in the IDE user manual.

Does anyone know of any good step by step tutorials for code::blocks?

Also the hello world tutorial I found tells me to use mxsmith pluging, and code::blocks tells me mxsmith is not loaded. I'm having trouble finding mxsmith to load it.

I am new to programming and only know the basics of compiling a single cpp source file.

Thanks for any help

---

### Post by TreeFinger on 2008-05-02
Why do you want to use an IDE? If you don't have a need, then just keep doing what you are doing.

---

### Post by tseliot on 2008-05-02
> **iansane said:**
> Some have said, I should be using an IDE because it is easier. I have to disagree. I just installed code::blocks which was recommended and have no idea how to build a project.
Try Kdevelop and start a new project.

---

### Post by Zugzwang on 2008-05-02
> **tseliot said:**
> Try Kdevelop and start a new project.

..which doesn't help much since KDevelop then wants to know the type of the project: QMake, Custom Makefile, Automake, "A simple Hello world program", whatever. How should the OP know what to take?

The OP is right. There is a huge need for tutorials, Maybe we should start a "Programming in Linux" Wikibook explaining all these terms. ;-)

---

### Post by tseliot on 2008-05-02
> **Zugzwang said:**
> ..which doesn't help much since KDevelop then wants to know the type of the project: QMake, Custom Makefile, Automake, "A simple Hello world program", whatever. How should the OP know what to take?
Well, I usually choose Qmake since I use QT4.

He can choose [this]("http://albertomilone.com/new_project.png") and then add files to his project

---

### Post by iansane on 2008-05-03
Thanks for the replies.

I haven't been using an IDE. It was suggested on Gamedev.net that an IDE would be easier and code::blocks and visual c++ were suggested. I wanted something for linux though, not windows so I managed to compile and install codeblocks, which looks really cool. :-)

There's been an ongoing disagreement among some class mates and instructors of mine as to whether using visual c++ is "real c++ programming" or actually just "windows programming with c++". I don't know enough to make that judgment call, but it makes sense to me. Also some disagreement as to whether learning through a GUI is good or bad.

So I'm writing basic programs in gedit and compiling with g++. So far the only cross platform difference has been that "system ("pause")" doesn't work in linux.

Anyway, the point is that this single source file compiling doesn't help with understanding the terminology and methods involved in building projects. I still really don't understand what "make" is.

I know I have the responsibility to learn what things are like "make" and "compile links". I'm just looking for a good book or tutorial that explains all of this stuff in detail with step by step instructions for creating an example project. Actually doing it while learning really helps me to understand it.

As far as code::blocks, I found out I had to "make" and "make install" for wxsmith from the code::blocks source I downloaded, and it seems to have installed the plug in, but when I restart the app, it fails to load that plug in. I need it to follow a "hello world" tutorial for using wxwidgets in code::blocks.

Do you guys think I should just stick with what I'm doing and the other stuff will eventually fall into place and make sense? 

Thanks

---

### Post by LaRoza on 2008-05-03
> **iansane said:**
> 
There's been an ongoing disagreement among some class mates and instructors of mine as to whether using visual c++ is "real c++ programming" or actually just "windows programming with c++". I don't know enough to make that judgment call, but it makes sense to me. Also some disagreement as to whether learning through a GUI is good or bad.

So I'm writing basic programs in gedit and compiling with g++. So far the only cross platform difference has been that "system ("pause")" doesn't work in linux.

Do you guys think I should just stick with what I'm doing and the other stuff will eventually fall into place and make sense? 

Thanks

That shouldn't be a disagreement. Visual C++ isn't standard C++, and therefore, isn't C++. It is a Windows C++ like language.

system() shouldn't be used. That is in a lot of texts because people in Windows double click (or the IDE runs) the application in a DOS emulator window, which closed. If you are compiling with g++, run it in the terminal. If you really need to have the application wait at the end for user input, use getchar() or whatever C++ uses.

Use what works now. No reason to use super computer to browse the net, no need to use large complicated tools for simple tasks.

---

### Post by Npl on 2008-05-03
> **LaRoza said:**
> That shouldn't be a disagreement. Visual C++ isn't standard C++, and therefore, isn't C++. It is a Windows C++ like language.Thats nonsense, and how to you argue its not Standard C++? If mean it has its own extensions, then well - g++ has its own share of extensions too.
Standard C++ sources should compile nicely on both compilers but **you** have to make sure you dont use propietary extensions. (Everything else is just a bug - and again both compilers could have them, recent MS-Compilers are very close to the standard actually).

system( command ) calls invokes executables, and this alone should tell you that you cant expect to work on all platforms (Linux has a different shell and programms than windows).

And make is a buildsystem, common in Linux, but has no ties to any C++ Standard. Visual C++ doesnt need make as it has similar functionality builtin.

---

### Post by LaRoza on 2008-05-03
> **Npl said:**
> Thats nonsense, and how to you argue its not Standard C++? If mean it has its own extensions, then well - g++ has its own share of extensions too.
Standard C++ sources should compile nicely on both compilers but **you** have to make sure you dont use propietary extensions. (Everything else is just a bug - and again both compilers could have them, recent MS-Compilers are very close to the standard actually).

system( command ) calls invokes executables, and this alone should tell you that you cant expect to work on all platforms (Linux has a different shell and programms than windows).


Is it? I heard Visual C++ doesn't have the C++ standard implemented. As a non Windows programmer, I haven't used it. 

I know what system() does. I was saying it shouldn't be used like that IMO.

---

### Post by Npl on 2008-05-03
> **LaRoza said:**
> Is it? I heard Visual C++ doesn't have the C++ standard implemented. As a non Windows programmer, I haven't used it.Visual Studio 6 had alot derivations from the standard, but that Version is 10 Years old. Newer Versions are very standards-compliant.

> **LaRoza said:**
> I know what system() does. I was saying it shouldn't be used like that IMO.This was directed at iansane :)

---

### Post by Mickeysofine1972 on 2008-05-03
I use code::blocks and find it very good as a replacement for vc++.

I personally have only done SDL based programs so i can only really offer you help on that sort of thing and how to add libraries and compile for windows/Linux.

If you have a specific question I could help you with I will be happy to help.

Or if you want to take a look at my current game project on sourceforge.net you can see how I have set up my project file which is included in there.

You can get it by doing the following:

```
sudo apt-get install subversion
svn co 'https://isoccer.svn.sourceforge.net/svnroot/isoccer/' iSoccer
cd iSoccer
make linux64 #if you have 32bit linux then use linux32
./iSoccer
```

Mike

---

