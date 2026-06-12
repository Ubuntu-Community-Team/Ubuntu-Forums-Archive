---
title: "Path to the C++ libraries"
date: 2005-07-16
forum: Programming Talk
---

### Post by csalinas on 2005-07-16
I can compile helloworld.cpp with #include <iostream> and everything works fine.

However, when I try to add #include "random.h" and a function that uses Randomize()
I get a compile-time error, no referenece to Randomize.

I am using namespace std; 

Where does Ubuntu/Synaptic put the C++ library?
Do I have to set the path to that directory?
Are libraries from boost only looked at at compile-time?  I tried to grep the .h files for "Randomize()"

Thanks in advance to anyone who can help me with this.

Chad

---

### Post by LordHunter317 on 2005-07-16
I'm not 100% certain, but I'm pretty sure Randomize() isn't part of the C standard, C++ standard, or POSIX, so it wouldn't be provided by Ubuntu.

If it's your own function, you'll have to provide the header yourself.

And a file named "random.h" would certianly not be part of the C++ standard, and isn't in the C one, so...

---

### Post by vintem on 2005-07-17
on my computer (with hoary) the C++ header file are in:
/usr/include/c++/3.3

there you have cstdlib (the new name of stdlib.h). If you #include this, you can use rand(), which returns an int. This program prints 5 random integers:

#include <iostream>
#include <cstdlib>
using namespace std;
int main() {
  for (int i = 0; i < 5; ++i){
    cout << rand() << endl;
     }
   return 0;
 }

---

### Post by csalinas on 2005-07-17
Thanks so much,  I now see that I have been using a lot of non-standard libraries in .Net C++ projects so porting them will invovle re-writing some of the .h or finding an appropriate standard .h and then changing my code.

Chad Salinas

---

### Post by csalinas on 2005-07-26
Chad Salinas at stanford : g++
Chad Salinas at stanford : emacs
Chad Salinas at stanford : /usr/include
Chad Salinas at stanford : GNOME
Chad Salinas at stanford : Dual boot Windows XP / Ubuntu 
Chad Salinas at stanford : AHA vs AHCI
Chad Salinas at stanford : USB Wireless
Chad Salinas at stanford : Synaptic Package Manager
Chad Salinas at stanford : /usr/bin
Chad Salinas at stanford : gcb
Chad Salinas at stanford : .xsession file
Chad Salinas at stanford : .emacs file
Chad Salinas at stanford : .bash-profile
Chad Salinas at stanford : Dinkum C++ library conforms to Standard C++ library
Chad Salinas at stanford : C++ callbacks
Chad Salinas at stanford : cluster algorithmChad Salinas at stanford : g++
Chad Salinas at stanford : function pointer tutorials
Chad Salinas at stanford : SGI Standard Template Library
Chad Salinas at stanford : Arithmetic on void pointer
Chad Salinas at stanford : heap advantages
Chad Salinas at stanford : heap disadvantages
Chad Salinas at stanford : activation protocol
Chad Salinas at stanford : RV register
Chad Salinas at stanford : Call and Return

---

