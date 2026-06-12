---
title: "[Netbeans] Unable to resolve identifier std::xxx"
date: 2013-05-28
forum: Programming Talk
---

### Post by giane on 2013-05-28
Hi all,
I hope that is the right section to post this problem.
I'm developing an aplication using zeromq framework boost library and std library v11. For the first two library (zmq and boost) i have no problem but std library give me some problem.
the following function/type give me the error "Unable to resolve identifier" in netbeans ide.
```

std::stol
std::stoi
std::thread
std::mutex

```
Netbeans is not the only one that give me this problem. I have the same problem but with different name in eclipse.
I control the code assistance Tool->Options->C/C++->Code Assistance but i think that the include directorys are right.
```

/usr/include/c++/4.8
/usr/include/i386-linux-gnu/c++/4.8
/usr/include/c++/4.8/backward
/usr/lib/gcc/i686-linux-gnu/4.8/include
/usr/local/include
/usr/lib/gcc/i686-linux-gnu/4.8/include-fixed
/usr/include/i386-linux-gnu
/usr/include
/usr/include/i386-linux-gnu/c++/4.8/bits

```

Someone can help me? I'll try some solutions that i found in internet but not work :confused:
thank you

---

### Post by dwhitney67 on 2013-05-28
Add -std=c++0x to your compiler options.  The "standard" class types you are trying to use were not introduced until a couple of years ago.  No doubt your compiler is defaulting to the 1999 standards.

---

### Post by vertago1 on 2013-11-20
I use netbeans and have the same problem and haven't found a fix yet.

My code compiles fine, but netbeans doesn't recognize several of the c++11 additions, even with the Code Assistance changed to the C++11 standard.

It is possible the order of the include directories needs to be changed for c++11, but I don't know how to tell which directory should be listed first for C++11.

---

### Post by dwhitney67 on 2013-11-21
> **vertago1 said:**
> I use netbeans and have the same problem and haven't found a fix yet.

My code compiles fine, but netbeans doesn't recognize several of the c++11 additions, even with the Code Assistance changed to the C++11 standard.

It is possible the order of the include directories needs to be changed for c++11, but I don't know how to tell which directory should be listed first for C++11.

I was unaware that Netbeans provided a C++ compiler.  I was under the impression that it used the system's native GCC (g++) compiler.

I have never used (nor will I ever use) Netbeans for C++ development, so I'm not quite sure how to help.

I suggest that you try to compile a simple source code file using 'g++' from the command line.  For instance:
```

#include <mutex>

int main()
{
    std::mutex m;
}

```
To compile this file:
```

g++ -std=c++0x file.cpp

```

---

