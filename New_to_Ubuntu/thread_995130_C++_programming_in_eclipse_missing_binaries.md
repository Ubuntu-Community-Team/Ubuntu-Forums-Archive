---
title: "C++ programming in eclipse: missing binaries"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by eeeandrew on 2008-11-27
hi all, I've been trying to get the eclipse environment working for C++ coding. I have the IDE running as no more than a text editor(no auto formatting, no auto complete and no colour coding). When I try and run a simple program:

> #include <iostream>
using namespace std;

int main()
{
cout >> "hello world" >> "\n";
return 0;
}

I get an error message saying that there are missing binaries and the program is unable to run.

I attempted to the run the program by selecting my source code file, right-clicking and choosing run as C++.

Anyone know where I can get the binaries and if I'm attempting to run it correctly? I've heard its possible to compile from command line using a compiler that comes with ubuntu.

Thanks in advance,
Andrew

---

### Post by conscious on 2008-11-27
Are you sure you have installed the **eclipse-cdt** package?

And I believe you should use << in this code, not >>.

---

### Post by eeeandrew on 2008-11-29
thanks for pointing that out. I only started C++ recently at Uni and its getting irritating that I can't use my own laptop to work on stuff at home.

I did > sudo apt-get install eclipse-cdt and the terminal says its the latest version. Any other thoughts?

Thanks in advance,
Andrew

---

