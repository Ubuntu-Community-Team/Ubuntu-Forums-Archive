---
title: "Getting nothing but errors when trying to compile C++ program"
date: 2007-01-30
forum: Packaging and Compiling Programs
---

### Post by Scooter7 on 2007-01-30
Hi, I'm new to C++ programming and Ubuntu/Linux, and was trying to compile this code from a tutorial:

```
include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}
```

And I got these errors:

> cd '/home/scooter7/C++_Projects/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/scooter7/C++_Projects/test/debug' && cd '/home/scooter7/C++_Projects/test/debug' && CXXFLAGS="-O0 -g3" "/home/scooter7/C++_Projects/test/configure" --enable-debug=full && cd '/home/scooter7/C++_Projects/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

I have tried compiling this in both KDevelop and gcc, and get the same results.   The strange thing is I have successfully compiled that exact code in Windows using Dev-C++ (by the way, is that available for Linux somewhere?   On the website ([www.bloodshed.net](www.bloodshed.net)) it says it is, but I can't find it anywhere to download...).   Why is this?   I'm using Ubuntu 6.10 with both GNOME and KDE.   Also, I have tried KDevelop and gcc in both environments with the same (unsuccessful) results.

---

### Post by phossal on 2007-01-30
```
**#**include <iostream>


int main()
{
  **std::**cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  **std::**cin.get();

  return 1;
}**;**


```

[edit] Complied with g++. **[COLOR="DimGray"][SIZE="1"]You need a newline following the main method (in most cases).[/SIZE][/COLOR]** I removed the name space declaration because (as the *experts* will tell you) it's usually not a good idea. And I threw in the preceding pound sign for the include statement.

---

### Post by Scooter7 on 2007-01-30
Thank you, I tried that code but I got more errors, similar to the earlier ones:

> cd '/home/scooter7/C++_Projects/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/scooter7/C++_Projects/test/debug' && cd '/home/scooter7/C++_Projects/test/debug' && CXXFLAGS="-O0 -g3" "/home/scooter7/C++_Projects/test/configure" --enable-debug=full && cd '/home/scooter7/C++_Projects/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

---

### Post by phossal on 2007-01-30
What command are you using to compile it with: 
```
g++ source.cpp
```

---

### Post by Scooter7 on 2007-01-30
Sorry, I posted that before I saw your edit.

I was using KDevelop, but I tried that g++ command and got this:

> test.cpp:10:3: warning: no newline at end of file

---

### Post by phossal on 2007-01-30
Right. You need a blank line after the main method.

---

### Post by phossal on 2007-01-30
lol I figured you would have that problem, so I bolded it in my first post. And then I was embarrassed because I thought it was stupid. It's a common problem though. ;)

KDevelop is misconfigured, it seems like. I don't know anything about it. I use eclipse and CDT.

---

### Post by Scooter7 on 2007-01-30
Well, thanks for your help. :D 

I'll check out Eclipse.   And, btw, I'm using the Cprogramming.com tutorials ([http://www.cprogramming.com/tutorial/lesson1.html](http://www.cprogramming.com/tutorial/lesson1.html))... but seeing as I had to make those changes to my code... well, do you think I can use the code from the tutorials in Eclipse without getting those errors, or do I still need the changes?

---

### Post by phossal on 2007-01-30
I'm not one of the resident c, c++ experts. I'm surprised one of them hasn't jumped in yet. Regarding the IDE, if you're just beginning, I think a lot of us would recommend just using gedit, and then running the compiler manually. 

Learning an IDE is a big deal on its own, as you know from your experience with KDevelop. Just avoid them for now. 

As for compiling your original source, I couldn't at the command line, which is why I changed it. I've never been a fan of online tutorials, though. I learn best from books.

---

### Post by Scooter7 on 2007-01-30
Well, thanks again for your help.

This is really odd, I tried using gedit with the exact same code that you changed for me (except without the changes), and comiled it with g++ perfectly! O_o

---

### Post by phossal on 2007-01-30
Interesting. Technically, it *should* work. I'm not sure why the problems on my end. I'm glad you're up and running. Good luck. 
ps. Keep your eye out for Wybiral, jblerun, et. al. They're the guys who seem to really enjoy the minutia of the c languages.

---

### Post by hod139 on 2007-01-30
The errors are because KDevelop is trying to use automake to build the project, and not g++ directly as phossal showed.  Automake is part of [autoconf]("http://www.gnu.org/software/autoconf/"), which is a way to automate source code distributions.  For a single file this is super overkill, and my guess is that you can probably tell KDevelop not to use the autotools but instead to use g++ directly.

---

