---
title: "gcc c++ problems"
date: 2006-07-08
forum: Programming Talk
---

### Post by EndianX on 2006-07-08
I am having some problems with c++.

hw.cpp```
#include <iostream.h>

int main()
{
        cout << "Hello World!\n";
        return 0;
}
```

results of **gcc hw.cpp**
```
In file included from /usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/iostream.h:31,
                 from hw.cpp:1:
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/tmp/ccvhW2MI.o: In function `main':hw.cpp:(.text+0x27): undefined reference to `std::cout'
:hw.cpp:(.text+0x2c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccvhW2MI.o: In function `__tcf_0':hw.cpp:(.text+0x46): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccvhW2MI.o: In function `__static_initialization_and_destruction_0(int, int)':hw.cpp:(.text+0x6f): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccvhW2MI.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

I don't know much c++.  It seems to me these problems have to do with gcc not being set up properliy though.

Does anybody have any ideas?

- endianx -

---

### Post by EndianX on 2006-07-08
Also, if my c++ hello world program isn't right, could anybody post something that *should* compile?

---

### Post by Randomskk on 2006-07-08
You're using gcc, which is for C programs.
Use g++ for C++ programs.

---

### Post by asimon on 2006-07-08
... and to make you hw.cpp right, replace "iostream.h" with "iostream" and "cout" with "std::cout".

---

### Post by Randomskk on 2006-07-08
I don't know any C++, but could you also say namespace std at the start or something and then just use cout?

---

### Post by asimon on 2006-07-08
> **Randomskk said:**
> I don't know any C++, but could you also say namespace std at the start or something and then just use cout?

Yes, with
```

using namespace std;

```
but this is bad practice. Better only using-declare just the names you actually use, i.e.
```

using std::cout;

```

---

### Post by EndianX on 2006-07-10
Thank you all so much.  I was under the impression that gcc would compile all sorts of different languages.

I will give g++ a try.

Thanks again,

---

### Post by thumper on 2006-07-10
gcc will compile C++ as it determins type by extension, however the linker that it invokes by default can't link the object files into an executable. g++ invokes the correct linker.

---

### Post by QMario on 2006-07-10
Correct program:

hw.cpp

```

#include <iostream>

int main(int argc, char* argv[])
{
  std::cout << "Hello World!" << std::endl;
  return 0;
}

```

---

### Post by thumper on 2006-07-10
or...
```

#include <iostream>

int main()
{
   std::cout << "Hello World!\n";
   return 0;
}
```

Why declare command line args when you aren't going to use them, and it is also legal to have a main that doesn't take them.

Secondly why force a flush of standard out?  Over use of std::endl is one of my pet peeves.

---

