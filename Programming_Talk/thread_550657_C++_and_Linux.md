---
title: "C++ and Linux"
date: 2007-09-14
forum: Programming Talk
---

### Post by [pl]ice on 2007-09-14
hi guys,
  i'm learing c++ but its non platform so i'm looking for a solid book that will help me learning how to use c++ under linux.  I was wondering if someone could pls point me in the right direction. 
thank you

---

### Post by lisati on 2007-09-14
There are some free books available at [http://www.linux-books.us/linux_general.php](http://www.linux-books.us/linux_general.php) including one for C++

BTW, the command-line compiler that comes with Ubuntu is g++

---

### Post by pmasiar on 2007-09-14
Did you checked stickies for this forum? All mentioned there is not enough?

---

### Post by gnusci on 2007-09-14
> **pmasiar said:**
> Did you checked stickies for this forum? All mentioned there is not enough?

Here they are in case he can not find them:

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)

---

### Post by LaRoza on 2007-09-14
My wiki has tutorials and books for C++ and other languages. In my sig.

---

### Post by [pl]ice on 2007-09-15
yeh, got that one:
C++ GUI Programming With Qt 3 

but how bout programming without the Qt3 ? 

i haven't looked through that book yet, but its a good start!
 
any one does any C++ in linux? i'm looking more for guidance :guitar:

thanks

---

### Post by dwhitney67 on 2007-09-15
What kind of guidance?  Have you taken any coursework on the subject?  Many community colleges offer C++ classes.  I would recommend auditing one, that way you can focus on learning, and not just on getting a good grade.


Oops... I just realized you are in Poland.  I'm am definitely not qualified to write about what educational opportunities exist over there.  My initial statement concerns the course availabilities in the US.

---

### Post by ryno519 on 2007-09-15
> **'[pl]ice said:**
> yeh, got that one:
C++ GUI Programming With Qt 3 

but how bout programming without the Qt3 ? 

i haven't looked through that book yet, but its a good start!
 
any one does any C++ in linux? i'm looking more for guidance :guitar:

thanks

Well, GNU/Linux has a set of C headers which would be akin to the functions windows.h exposes in a Win32 environment. They're mostly located in /usr/include/linux if I remember correctly.

If you're just looking for a different toolkit, besides Qt3 (which I'm not a fan of, btw, so I might be a little biased ;) ) I could recommend [gtkmm]("http://www.gtkmm.org/"), which has very good online documentation and examples. It's pretty easy to pick up.

Some recommended reading for developing in a GNU/Linux environment would be [how to use the G++ compiler]("http://homepages.gac.edu/~mc38/2001J/documentation/g++.html"), [how to use Autoconf and Automake]("http://www.openismus.com/documents/linux/automake/automake.shtml") and of course... Design Patterns. ;)

I find C++ development in GNU/Linux simpler in some ways and harder in others when compared to Windows development. For instance, learning how to use the Autoconf and Automake tools takes a little trial and error, whereas in Windows you don't have to worry about distributing your work as source as often. However, the big plus on GNU/Linux is the very easy access of **VAST** amounts of shared code you can use in your projects.

I think you will find the pro's outweigh the cons. You get used to the compilation process very quickly and after you get that down, you're golden.

---

### Post by samjh on 2007-09-15
> **'[pl]ice said:**
> hi guys,
  i'm learing c++ but its non platform so i'm looking for a solid book that will help me learning how to use c++ under linux.  I was wondering if someone could pls point me in the right direction. 
thank you

If you're going to attempt learning C++ by yourself, make sure you learn how to self-study first: ie. do your own research.

But as usual, I'll deliver some tips on a silver platter. ;)

**1. Install your compiler**

Open up your terminal (you should at least be familiar with the Linux command-line), and type this:
```
sudo apt-get install build-essential
```This will give you the GNU C++ compiler and related utilities for developing applications and packages in Ubuntu.

**2. Learn to use gedit**

This part isn't hard at all.  Go to your Applications menu, Accessories, and then select Text Editor.  Gedit is the standard text editor in Ubuntu (if you are using Kubuntu, it is Kate).  It should be more than enough for a beginner programmer, and it has some useful plugins which you can install using this command in your terminal:
```
sudo apt-get install gedit-plugins
```Have a tinker around, and get used to it.

**3. Some good quality tutorials**

Here are some good quality tutorials for C++ programming in general:
[www.cprogramming.com](www.cprogramming.com)
[www.cplusplus.com](www.cplusplus.com)

**4. How to use the g++ compiler**

When you installed build-essential in Step 1, one of the programs it installed was g++, which is the GNU C++ compiler.  It's one of the best there is, and the de facto standard C++ compiler for Unix and LInux.

To compile a simple program - let's call it *helloworld.cpp* - into an executable - let's call that just *helloworld* - do this:

Use your terminal to navigate to the same directory as your source code file (ie. where *helloworld.cpp* is), and command your terminal thus:
```
g++ helloworld.cpp -o helloworld
```That command will take *helloworld.cpp*, compile it, link the necessary libraries with it, and produce the output file you specified (using the -o switch): *helloworld*.

To run *helloworld*, do this in your terminal:
```
./helloworld
```Notice the presence of ./ in front of the actual executable file name.

**5. A simple "Hello World" to get you started**

No introduction would be complete without one of these classics:
```
#include <iostream>

int main()
{
    std::cout << "Hello World!" << std::endl;

    return 0;
}
```

---

### Post by [pl]ice on 2007-09-15
thanks guys, thats make sense, i'll look into gtkmm, and yes i haven't thought about the automake. I just was wondering what options were there :)
  ok, wish me happy learning, couse at my age it does not come easy!

thanks again.

---

### Post by gnusci on 2007-09-15
> any one does any C++ in linux?

Just start your course and post any question and problem here...

---

### Post by pmasiar on 2007-09-15
> **'[pl]ice said:**
> 
  ok, wish me happy learning, couse at my age it does not come easy!

find some local user group. Sometimes the best help can be obtained by pointing on something on a screen, or observing how gurus do it.

---

### Post by gnusci on 2007-09-15
a nice link:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html)

---

### Post by Ticus on 2007-09-15
hi! we use ms in college but I'd like to use g++ for my programs, can any body paste a example about saving data in text files??? 
Thanks!

---

### Post by dwhitney67 on 2007-09-15
If in MS or in Gedit or other IDE editor, Ctlr-A (to select everything), Ctlr-C (to copy), and Ctrl-V (to paste).

If you are dealing with an xterms, manually select the text you want to copy, Shift-Ctrl-C (to copy), and Shift-Ctrl-V (to paste).

Your text files should have either a .h or a .cpp extension (if dealing with C++).  When in MS, create a new file association such that either VS or WordPad is used to open files with such extensions.

I do not use MS anymore.  And probably never will again if I can avoid it.  If you have a notebook PC, you should inquire with your college professor if it is ok to do your assignments in Linux.  Generally all they want is the source code when an assignment is due.  If they need to observe the runtime binary, then bring your notebook PC into class.

P.S.  I'm sure there are other ways to copy text or files from one source to another.  Shame on you for not doing the research on how to do this.

---

### Post by Ticus on 2007-09-15
Hi again. Thanks for the comment, that's what I want to do because the profesor said that we can use any compiler. 
But I mean how can i save data in text files. For example how do yo write this lines in c++??? which extencion I use instead of .txt?

#include <iostream>
#include <fstream>
using namespace std;

int main () {
  ofstream myfile;
**  myfile.open ("example.txt");**
  myfile << "Writing this to a file.\n";
  myfile.close();
  return 0;
}

---

### Post by ryno519 on 2007-09-15
> **Ticus said:**
> Hi again. Thanks for the comment, that's what I want to do because the profesor said that we can use any compiler. 
But I mean how can i save data in text files. For example how do yo write this lines in c++??? which extencion I use instead of .txt?

#include <iostream>
#include <fstream>
using namespace std;

int main () {
  ofstream myfile;
**  myfile.open ("example.txt");**
  myfile << "Writing this to a file.\n";
  myfile.close();
  return 0;
}

The convention I like to follow are the following

.cpp for source files
.hpp for header files

Some people use .cc for source and .hh for headers. Some simply use .h for their C++ headers, although I consider that a poor convention.

So I'd suggest saving that file as main.cpp

---

### Post by nonewmsgs on 2007-09-15
use anjuta.  it's great.  it complains about some build dependencies when you makea  new project so you have to apt-get them, but once you get started it's great.

---

### Post by theBee on 2007-09-16
> **samjh said:**
> 
**1. Install your compiler**

Open up your terminal (you should at least be familiar with the Linux command-line), and type this:
```
sudo apt-get install build-essential
```This will give you the GNU C++ compiler and related utilities for developing applications and packages in Ubuntu.


Thanks!!!  This nugget should be in a FAQ.  (Maybe it is... I'm new here.)

I searched everywhere for g++.  I expected it to be available from the Applications | Add/Remove menu.  Why isn't it there?

(I'm an experienced C/C++ developer, but new to Linux.)

Anyhow, thanks for this tip.  Now I can run the compiler!

---

### Post by samjh on 2007-09-16
> **theBee said:**
> Thanks!!!  This nugget should be in a FAQ.  (Maybe it is... I'm new here.)

I searched everywhere for g++.  I expected it to be available from the Applications | Add/Remove menu.  Why isn't it there?

(I'm an experienced C/C++ developer, but new to Linux.)

Anyhow, thanks for this tip.  Now I can run the compiler!

The Add/Remove menu only lists the most commonly used stuff.

To dig deeper, you need to go System | Administration | Synaptic Package Manager.  From there, you can use the Search function to look for things like g++.

---

### Post by Ticus on 2007-10-03
[INDENT]The convention I like to follow are the following

.cpp for source files
.hpp for header files

Some people use .cc for source and .hh for headers. Some simply use .h for their C++ headers, although I consider that a poor convention.

So I'd suggest saving that file as main.cpp
__________________[/INDENT]

Thanks a lot guys!

---

### Post by Armadillo Kilr on 2007-10-03
you are welcome

---

