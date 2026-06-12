---
title: "application development in linux"
date: 2009-11-17
forum: Programming Talk
---

### Post by ganeshmallyap on 2009-11-17
Hi all,

In my leisure hours I have been programing in Microsoft Windows using C++/C# etc so far and now I have migrated to Linux (Linux Karmic amd64).  I have seen there are tons and tons of application development tools available in linux.  But what attracted me the most were C/C++ (gtk/gtkmm/Qt) from the ones I heard about.

I tried installing couple of IDEs' such as Anjuta, Netbeans, Qt creator, Lazarus etc along with other necessary supporting libraries such as build_essentials, GVim etc.  I found Gvim is very simple and straight forward but involves a learning curve.  And I was not sure how to use that for larger projects.  

You may recall in Borland C++ for windows there were some compiler code generations options such as - choosing of processor architecture (8086/386/pentium) optimization level 0, 1, 2, 3 and memory overflow checks, 32 bit/64 bits code etc.  But I could not locate them in the above mentioned IDEs' except Lazarus.  Ofcourse Lazaraus is not for C/C++.  I am not sure whether there is a different place to specify them or I am missing something here.  I also tried compiling a tiny C program using GCC at terminal (gcc <filename>.  And I noticed it created a output file with default extension .o.  All I remembered from my MS platform experience was there were multiple levels in compilation of a programme such as object code creation then linking of the object code and finally generation of machine code.  But I did not notice any messages about this while GCC was compiling the tiny program I had written.

So I wanted to know whether I am doing this right.  If yes, is GCC creating a machine executable code (binary) or is that a intermediate object code?  If that is a proper binary code then how do I enable the code optimization options in the above said IDEs'? Thanks a ton in advance.

---

### Post by jujum4n on 2009-11-17
Not entirely sure what your asking but the .o files are object files and you can link them together to create binaries using make files. Here is some general information on makefiles [http://www.gnu.org/software/make/manual/make.html#Simple-Makefile](http://www.gnu.org/software/make/manual/make.html#Simple-Makefile) 
 
For c++ development I personally like to use Kdevelop as an IDE. When I code with the QT libraries, I tend to use QDeveloper combined with QtDesigner.

---

### Post by TheStatsMan on 2009-11-17
I think Vim is definitely the best tool for C++, but you need a few plugins. 
Just google vim c++ to get started. 

If you are going to go the vim root though you will need to use a Makefile. This tends to make changing compiler options a lot easier and quicker than an IDE, which tends to be a bit clumsy for those sought of things. If you want to know what options you have available take a look at the GCC manual [http://gcc.gnu.org/onlinedocs/](http://gcc.gnu.org/onlinedocs/).

Alternatively if you want something that is self contained and has everthing built in already then have a look at code::blocks. You will be able to some change compiler options and most of what you want through menus. This approach, however, is very inefficient in comparision to vim.

---

### Post by phrostbyte on 2009-11-17
Usually the build process of a Linux app is controlled by a "makefile" which is a special declarative language for building things. With one you can set many different options. Some IDEs like MonoDevelop/Eclipse/QtCreator and possibly Ajunta can generate Makefiles for you. But I think most people prefer to write them by hand. The best way to learn IMO is to download the source of some apps [remember Linux is mostly open source :)] and look how they did it. It's usually Makefile.am or Configure.in the files which control the build.

---

### Post by korvirlol on 2009-11-18
The best way (imo) which teaches you the most, and gives you the most control is to not use an IDE.

Manage your own implementation and header files in your own applicable directories, and manage compiling with a makefile. No matter what people say, IDEs add over head to compiling your program.

As for omptimization, g++ has the -O flag which corresponds directly to what you are talking about with optimization (g++ -O2).

---

### Post by ganeshmallyap on 2009-11-18
Thank each one of you for your valuable reply.

---

### Post by pokerbirch on 2009-11-18
+1 for code::blocks IDE, especially if you're looking for something similar to VS.

---

