---
title: "Dev-C++ in linux"
date: 2007-09-09
forum: Programming Talk
---

### Post by malfist on 2007-09-09
I'm working on a project in my spare time that has been developed using Bloodshed Dev-C++ in windows. Is there anyway to open it in linux as a package and keep the compilation configuration the same? KDevelop complains of no makefile or autogen and Netbeans with the C/C++ add-on does similar. Any idea's on how to fix this?

---

### Post by Lacrimstein on 2007-09-09
Well, there is a Dev-C++ version for linux, but last time I checked you can't download it from Bloodshed directly - you have to order it on a CD for $28 (if you're a student) or $50 (if you aren't). But there probably is a number of sites where you can get it for :rolleyes:free

---

### Post by Lacrimstein on 2007-09-09
[http://sourceforge.net/project/showfiles.php?group_id=10639]("http://sourceforge.net/project/showfiles.php?group_id=10639") right here, for example :)
it looks like you will have to build it yourself, though... can't help you there

---

### Post by pmasiar on 2007-09-09
I don't think that using "cracked" "free" version will help you. Because the whole point of switching to Linux, IIUC, is to gain support from Linux developers, build a community, to expand your program, so you can share it with others, legally. 

Is it so? Or you have other plans?

---

### Post by malfist on 2007-09-09
No :(, it's a game that I love and asked to help improve on it. It's closed source. Although the group that I'm working for knows that if I start another project (which they will allow me to do) it will be open source.

edit: I'm a student, I knew bloodshed claimed there was one for linux but I couldn't find it's download. I can build it.

---

### Post by Lacrimstein on 2007-09-09
ok cool :) there is an installer package for linux.
you just have to press the "View older releases from the Binaries package " link, and its there. 
Also, this isn't "cracked"- its  the real thing, except quite old... don't know if its compatible with the newer versions' files...

---

### Post by malfist on 2007-09-09
It looks like it's been coded in delphi (there are newer versions that are platform independant) but I don't know how to compile them, it doesn't come with a ./configure or INSTALL or anything like that so I can figure it out, anyone know how?

---

### Post by the_unforgiven on 2007-09-10
Another way to solve it is using Dev-C++, just export the Makefile - last time I checked dev-c++ (which, admittedly, was quite a few years ago :p), it did allow you to export the makefile.

Then, just edit the makefile to change the compiler location (and maybe tweak the makefile a bit to suit your setup). 

Now, it should be possible to compile your favourite program coded using dev-c++ in linux too (provided it doesn't depend on any windows specific code).

I don't know whether you'd be able to use any IDE in linux, but using a simple text editor like vim, you should be able to make changes in the code and compile again.

HTH ;)

---

### Post by malfist on 2007-09-10
Wait what? Use Dev-C++ to export the makefile so I can use Dev-C++? I'm not understanding you.

edit: there is a windows makefile but I can't get it to work with linux, after modification it complains about *.o is unrecognized file format by g++.

---

### Post by Tomosaur on 2007-09-10
> **malfist said:**
> Wait what? Use Dev-C++ to export the makefile so I can use Dev-C++? I'm not understanding you.

I think he meant:
On Windows, open the project file in Dev-C++.
Export the project Makefile.
Move the source code and the Makefile to Linux.
Use some Linux based tool to build the project.

---

### Post by Rui Pais on 2007-09-10
or you can use Code::Blocks on Linux, that can import Dev-C++ projects:
[http://www.codeblocks.org](http://www.codeblocks.org)

---

### Post by yesar92 on 2011-06-28
Hello, 

I think you can use wine to do it. I recently read a post about it , it is good that I still keep my bookmarks :) 

[http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/](http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/)

---

### Post by scu-ba-de-buntu on 2011-06-28
> **yesar92 said:**
> Hello, 

I think you can use wine to do it. I recently read a post about it , it is good that I still keep my bookmarks :) 

[http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/](http://crunchbanglinux.org/forums/topic/6129/install-devc-on-linux-wine/)



yesar92, this thread has been dead since 2007.

That said, Dev-cpp with MingGW works fine under wine and can compile win32 code. Several years ago that was how I wrote code for windows machines. I even began porting/fixing the linux client with Kylix and then Lazarus, but there are much better tools these days. I would highly recommend the CODE::BLOCKS IDE or eclipse IDE over Dev-Cpp these days. Simply use the cross-compilation tools if you need to compile win32/wince binaries.

Using CODE::BLOCKS will give you a similar IDE and project management solution with the benefit of being cross platform as well.

---

### Post by cgroza on 2011-06-28
> **scu-ba-de-buntu said:**
> yesar92, this thread has been dead since 2007.

That said, Dev-cpp with MingGW works fine under wine and can compile win32 code. Several years ago that was how I wrote code for windows machines. I even began porting/fixing the linux client with Kylix and then Lazarus, but there are much better tools these days. I would highly recommend the CODE::BLOCKS IDE or eclipse IDE over Dev-Cpp these days. Simply use the cross-compilation tools if you need to compile win32/wince binaries.

Using CODE::BLOCKS will give you a similar IDE and project management solution with the benefit of being cross platform as well.
Or get rid of all problems and use EMACS or Vim.

---

