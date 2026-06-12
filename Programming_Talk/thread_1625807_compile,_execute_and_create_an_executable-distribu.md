---
title: "compile, execute and create an executable-distributable C++"
date: 2010-11-19
forum: Programming Talk
---

### Post by Rahul Sudhakaran V on 2010-11-19
Hi friends and fellow Ubuntuians,
I am new to ubuntu programming and development. I am trying to compile, execute and create an executable-distributable application.
Im starting here with a simple c++ program : Test1.cpp:
--------------------------------------------------------------------------------------------------------------
#include <iostream>
using namespace std;
int main()
{
    std::cout << "Welcome to the wonderful world of C++!!!\n";

    return 0;

}
--------------------------------------------------------------------------------------------------------------

Now i want to compile and execute and create a distributable for the same. BUT how to do it?
Please help.

Thanks.

---

### Post by santosh83 on 2010-11-19
> **Rahul Sudhakaran V said:**
> Hi friends and fellow Ubuntuians,
I am new to ubuntu programming and development. I am trying to compile, execute and create an executable-distributable application.
Im starting here with a simple c++ program : Test1.cpp:
--------------------------------------------------------------------------------------------------------------
#include <iostream>
using namespace std;
int main()
{
    std::cout << "Welcome to the wonderful world of C++!!!\n";

    return 0;

}
--------------------------------------------------------------------------------------------------------------

Now i want to compile and execute and create a distributable for the same. BUT how to do it?
Please help.

Thanks.

This post might be more appropriate on the general programming talk forum. Since you're seemingly a newbie you might first learn to compile, execute and debug your program before trying to package and distribute it. The standard C++ (and C) compiler on Linux is g++ (gcc.) Check the package repository for your version with Synaptic and install gcc and g++ at a minimum. You might also install gdb for commandline debugging. All these tool are pretty steep to learn initially, but worth the effort, as even sophisticated IDEs like Eclipse depend on these CLI tools to get the job done behind the screen. For editing, while each prefer their own editor, nevertheless some very powerful programming editors are Vim (gvim for graphical interface), and Emacs. I use Vim.

The basic command to compile would be:
$ g++ -Wall -Wextra -ansi -o Test Test.cpp

Then you can run it:
$ ./Test

---

### Post by lisati on 2010-11-19
Agreed: if you're a beginner programmer, the "programming talk" section might be more appropriate.

*Thread moved to **Programming Talk**.*

---

