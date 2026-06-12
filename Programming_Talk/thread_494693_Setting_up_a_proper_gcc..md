---
title: "Setting up a proper gcc."
date: 2007-07-07
forum: Programming Talk
---

### Post by heatman on 2007-07-07
So, I thought I'd go ahead and dig up my old programming hobby under Ubuntu. But after writting this really simple hello world sample and trying to compile it, gcc bails out tellimg me that: 

```

/tmp/ccPrb3VW.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccPrb3VW.o: In function `__tcf_0':
test.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccPrb3VW.o: In function `main':
test.cpp:(.text+0x8e): undefined reference to `std::cout'
test.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccPrb3VW.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

The code itself is:
```

#include <iostream>

using namespace std;

int main() {
  cout << "Hello world!\n";

  return 1;
}


```

This shouldn't happen and leads me to believe that something in the underlaying system is at fault, any helpers? :>

---

### Post by samjh on 2007-07-07
Are you sure you've installed g++?  It's not gcc, but g++ you should be using.

This will get you all the necessities for gcc and g++ compilation:
```
sudo apt-get install build-essential
```

---

### Post by xtacocorex on 2007-07-07
Returning one at the exit denotes failure or bad exit status, I'd return a zero.  As samjh said, use g++ to compile C++ code.

---

