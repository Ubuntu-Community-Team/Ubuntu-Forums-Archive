---
title: "Problem in linking"
date: 2008-01-22
forum: Programming Talk
---

### Post by bargi on 2008-01-22
Hi,

I have the linking problem.........

I have compile the program but it is giving me linking error as follow:

[code]
Runtime.cpp:(.text+0x19f3): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
Runtime.cpp:(.text+0x1a03): undefined reference to `std::allocator<char>::~allocator()'
Runtime.cpp:(.text+0x1a16): undefined reference to `std::allocator<char>::~allocator()'
std::char_traits<char>, std::allocator<char> > const&)':
Runtime.cpp:(.text+0x1a78): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
Runtime.cpp:(.text+0x1a8b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
StringUtilities.cpp:(.text+0x1c): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
`__static_initialization_and_destruction_0(int, int)':
StringUtilities.cpp:(.text+0x57): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string()'

[code]



One more thing is that  I am using boost libraries...when I compile earlier it was giving error ,so I used -fpermissive to remove it. But now it is giving me linking error.

Can anybody help me in resolving this problem.

Thanks

---

### Post by LaRoza on 2008-01-22
How are you compiling? Give the code.

---

### Post by bargi on 2008-01-22
Thanks for Reply !

First of all I run autoreconf command which created the makefile.in.

After that I run projectconfigure command which is our custom command for creating makefile.

After that make....

I have set boost library path in LD_LIBRARY_PATH environment variable
and boost is install in /home/Project/lib/boost

When I first run the make command it give me error on some warnings...and instruction to use fpremissive, so I used it and it remove that error but give linking error....

Is there problem with gcc ?

Thanks


Thanks

---

### Post by LaRoza on 2008-01-22
> **bargi said:**
> 
Is there problem with gcc ?


Try "g++"

---

### Post by bargi on 2008-01-22
Hi !

How can I change gcc option ...?

Makefile is  generated automatically.......

Thanks

---

### Post by LaRoza on 2008-01-22
Oh, I don't know much about makefiles, and am not really good at C++.

Is everything you need installed?

---

### Post by hod139 on 2008-01-22
```

gcc foo.cpp -lstdc++

```

---

### Post by bargi on 2008-01-24
Thanks for reply.......

But in my project I have to compile with makefile which r generated from configure.ac file.........

How can I make changes so that it compile with libstdc++ libraries..
Or should I set environment variables for it....

Please give suggestion.........

Thanks a lot

Bargi

---

### Post by wolfbone on 2008-01-24
> **bargi said:**
> Thanks for reply.......

But in my project I have to compile with makefile which r generated from configure.ac file.........

How can I make changes so that it compile with libstdc++ libraries..
Or should I set environment variables for it....

Please give suggestion.........

Thanks a lot

Bargi

Did you put "AC_PROG_CXX" in your configure.ac or configure.in?

---

### Post by bargi on 2008-01-24
I have solved the problem........

I have to include "AC_PROG_CC" in my configure.ac file.......

But I can't understand that when I am using "AC_PROG_CXX" then why should I add "AC_PROG_CC" ??

I will be thankful for your reply ..........

Thanks

---

### Post by wolfbone on 2008-01-24
> **bargi said:**
> But I can't understand that when I am using "AC_PROG_CXX" then why should I add "AC_PROG_CC" ??
Thanks

No idea. It works fine for me. But I don't use any custom "projectconfigure" command. Perhaps that is the source of the problem?

---

