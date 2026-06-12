---
title: "New to linux programming in C++ and need help"
date: 2009-02-05
forum: Programming Talk
---

### Post by jdoge13 on 2009-02-05
I'm trying to write out a very simple program (the one most people learn first that simply displays "Hello World") it works perfectly when I compile it in Dev C++ on my pc, however I'm getting a indecipherable (to me) error message below are the code and error. I think it must be some error with my compiler or with the iostream library. Any ideas?  Thanks for any help in advance.

Code:
#include <iostream>
using namespace std;

main(){
	cout << "Hello World." << endl;
}

(the only difference between this and the windows code is I used the system("pause"); command in the windows version)

---

### Post by jdoge13 on 2009-02-05
The Error:
```

/tmp/cc7tX0KZ.o: In function `main':
hello.cpp:(.text+0x1c): undefined reference to `std::cout'
hello.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
hello.cpp:(.text+0x29): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
hello.cpp:(.text+0x31): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cc7tX0KZ.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp:(.text+0x60): undefined reference to `std::ios_base::Init::Init()'
hello.cpp:(.text+0x65): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc7tX0KZ.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by croto on 2009-02-06
In ubuntu, you need to install the build-essential package in order to be able to compile anything:
```

sudo apt-get install build-essential

```

Also, make sure that you're using g++ to compile your C++ program (I mean, don't use gcc, which is the C compiler)

---

### Post by jdoge13 on 2009-02-06
Thanks a lot...had no idea about the g++ thing, makes a big difference. haha.

---

