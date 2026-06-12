---
title: "C++ Variable types that handle strings"
date: 2010-02-19
forum: Programming Talk
---

### Post by Kenny_Strawn on 2010-02-19
How do I create a C++ variable type that is capable of handling a string?

Is there a variable type that handles strings, say in the "Cstring" library, and how is its syntax?

Specifically: I want to imitate Linux's "PATH" variable in C++, for the purpose of creating a program that serves as a hardware abstraction layer (and the basis for a hybrid kernel) that transforms GNOME into a new Unix-like OS (with one key element: GNOME as a UI in kernel space).

Boot Stage 1:

```

devkit-disks --mount /dev/sda1 --mount-fstype ext4 /

```

Boot Stage 2:

Scan hardware and attempt to automatically search for C++ functions in the Kernel API that enable its functionality, using them like a puzzle to enable the devices.

Boot Stage 3:

```
startx
```

One word of note: The device drivers will really be configuration files in /etc/kern that function very much like xorg.conf, but with a more C++-like syntax.

---

### Post by CptPicard on 2010-02-20
> 
Is there a variable type that handles strings, say in the "Cstring" library, and how is its syntax?

[http://tinyurl.com/yhkdf2h](http://tinyurl.com/yhkdf2h)

> GNOME as a UI in kernel space).

Sounds like a [horrible idea]("http://en.wikipedia.org/wiki/Windows_95"). Why?

> 
Scan hardware and attempt to automatically search for C++ functions in the Kernel API that enable its functionality, using them like a puzzle to enable the devices.

Funny, there are no C++ functions in the kernel API at all... and this kind of "trying to fit pieces together like a puzzle" is still just another way to say "automated programming", which is still pretty much the holy grail of open research problems, and very likely to be impossible for a lot of reasons.

What you're suggesting isn't getting any more possible...

---

### Post by nvteighen on 2010-02-20
I won't discuss your project, I'll just limit myself to answer your C++ question. But, having read your devicekit code at Launchpad and having read this post, I really recommend you to a look on a C++ tutorial and to study how a modern OS works.

That said, the C++ Standard Library's string class works like this:

```

#include <iostream>
#include <string>

int main(void)
{
    std::string myString("This is a compile-time string!");
    std::cout << myString << std::endl;

    std::string anotherString;
    std::cout << "Write something: ";
    std::cin >> anotherString;
    std::cout << "You wrote: \'" << anotherString << "\'" << std::endl;
    std::cout << anotherString.length() << " characters long!" << std::endl;

    return 0;
}

```

Of course, there are lots of methods for the std::string class for lots of things. There's plenty of information on them on the web.

---

### Post by sharpdust on 2010-02-20
> **Kenny_Strawn said:**
> 
Specifically: I want to imitate Linux's "PATH" variable in C++, for the purpose of creating a program that serves as a hardware abstraction layer (and the basis for a hybrid kernel) that transforms GNOME into a new Unix-like OS (with one key element: GNOME as a UI in kernel space).

GNOME is a window manager, not an OS. All it is just a GUI overlay to a terminal and what you're requesting just doesn't make sense.

---

