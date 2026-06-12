---
title: "Building C++ application"
date: 2007-03-17
forum: Packaging and Compiling Programs
---

### Post by alphilli on 2007-03-17
I need to port a simple console application from Windows to Linux (Ubuntu).

I would appreciate some suggestions on which IDE to use.  I installed the KDevelop but that seems totally useless.  Even their default "Hello World" doesn't build. It first says there is no makefile "Run Automake & friends".  So I tell it to go ahead and then it says "make aclocal: Command not found". Then I try to get help and all I get is the message: "Cannot find the htsearch executable".

It seems as though KDevelop is next to useless so I'm wondering which IDE people use for development on Ubuntu Linux.

Or maybe there is some other add-in that one has to put on in order to make KDevelop work at all.

Thanks.

---

### Post by maddog39 on 2007-03-18
Its really simple, and you probably dont even have to change any code. KDevelop is useless and dont use it unless you are doing a huge application or you specifically need its features. Linux is not like Visual C++ where you load it up and hit the compile button. If you have many files you need to write Makefiles or use Autoconf/Automake and the sort. Assuming this is really small and the prorgam is only one file. Simply run from termianl:
```

g++ -g -Wall program_file.cpp -o program_name

```
The above was simple an example. The g++ is the GNU C++ compiler command, -g tells it to add a debugger, and -Wall enables all warnings to be output, program_file.cpp is your programs source code/.cpp file, and -o is your output binary and the program_name is whatever you want the executable file to be.

If it tells you the command can't be found or whatever, run this and then try recompiling your program.
```

sudo apt-get install g++

```

---

### Post by alphilli on 2007-03-18
Thanks.

Mine is a little more complex than a single source file.  It has about 30 .cpp files.

I guess that means I have to create a makefile from scratch.  I was hoping there was something that would help with that step but I guess not.

I'm surprised that there still isn't a decent IDE on Linux.  I really thought unix/linux had evolved a bit over the past 10 years (that's about the last time I did any unix development).

Do people still do command line debugging in unix/linux?  Interactive (GUI) debugging is the main advantage of a decent IDE.

Thanks for your input.

---

### Post by barney_1 on 2007-03-18
Check out the last post in this thread:

[http://www.ubuntuforums.org/showthread.php?t=369560](http://www.ubuntuforums.org/showthread.php?t=369560)

Inostdal seems to have an IDE for C++ that he really likes.

---

### Post by hod139 on 2007-03-19
> **alphilli said:**
> 

I'm surprised that there still isn't a decent IDE on Linux.  I really thought unix/linux had evolved a bit over the past 10 years (that's about the last time I did any unix development).
There's anjunta, kdevelop, eclipse (with the CDT plugin for C/C++), code::blocks (my favorite), etc.  See the "What's your favorite IDE" sticky for many many more".

---

### Post by alphilli on 2007-03-20
I've tried KDevelop and Eclipse and they sure didn't seem to provide significant functionality so I don't hold out much hope for the other one.   

I guess it's pretty hard to compete with Visual Studio.

---

### Post by silas_irl on 2007-03-21
I'm more an emacs, shell and gdb kind of guy, so I haven't used IDE's in Linux in quite a while, but I used to like anjuta, but at the time it needed to be better polished, perhaps it is now.

And KDevelop is just over-bloated, it does so much crap with autoconf/automake and the amount of intermediate files it generates for a simple hello world program.

[quote=alphili]I guess it's pretty hard to compete with Visual Studio.[/quote]Yeah it is, Microsoft have a very good IDE there.

I'd personally have a good look at anjuta, and try it out.

---

### Post by IronAvatar on 2007-04-13
> **alphilli said:**
> I need to port a simple console application from Windows to Linux (Ubuntu).

I would appreciate some suggestions on which IDE to use.  I installed the KDevelop but that seems totally useless.  Even their default "Hello World" doesn't build. It first says there is no makefile "Run Automake & friends".  So I tell it to go ahead and then it says "make aclocal: Command not found". Then I try to get help and all I get is the message: "Cannot find the htsearch executable".

It seems as though KDevelop is next to useless so I'm wondering which IDE people use for development on Ubuntu Linux.

Or maybe there is some other add-in that one has to put on in order to make KDevelop work at all.

Thanks.

You need to install a bunch of packages first (I forget the exact name for them) before kDevelop will work.  This is more a Unbuntu setup issue (perhaps the Ubuntu installer should have "setup profiles" that install the required basic packages for developing in the language of your choice?) than a reflection on kDevelop.

Although IMHO, kDevelop is a festering piece of elephant dung.  With so much hard work having gone into the IDE, the whole thing is ruined by it's restrictvie and hard to use project structure.  

Code::blocks is your friend :)

---

