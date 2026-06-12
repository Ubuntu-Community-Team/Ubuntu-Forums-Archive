---
title: "Cout not a member of STD class? WTH?"
date: 2011-11-01
forum: Programming Talk
---

### Post by compiz addict on 2011-11-01
I'm trying to learn socket programming in C++ using a tutorial online. After giving up, I just copied every file from the website and ran make as instructed. It says cout is not a member of std... but cout is ALWAYS a member of std (as far as I know) so it's very frustrating.

g++    -c -o ServerSocket.o ServerSocket.cpp
g++    -c -o Socket.o Socket.cpp
Socket.cpp: In member function ‘int Socket::recv(std::string&) const’:
Socket.cpp:135:7: error: ‘cout’ is not a member of ‘std’
make: *** [Socket.o] Error 1

---

### Post by crdlb on 2011-11-02
I don't do C++, but I'm 99% sure you're missing:
```
#include <iostream>
```

---

### Post by 3Miro on 2011-11-02
What is the actual code? You are making us guess over here. You need to call cout with:

```
std::cout << " Hello Cruel World " << std::endl;
```

---

### Post by compiz addict on 2011-11-02
Yes, I have #include <iostream> in my code :P
Neither this code:
```

#include <iostream>

using namespace std;

int main() {

 cout << "test" << endl;
 return 0;
}

```
not this code:
```

#include <iostream>

int main() {

 std::cout << "test" << endl;
 return 0;
}

```

Seems to work . . .

Although, from that I get a slightly different error:
```


/tmp/cc4SNKht.o: In function `main':
test.cpp:(.text+0x14): undefined reference to `std::cout'
test.cpp:(.text+0x19): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
test.cpp:(.text+0x29): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cc4SNKht.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x51): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x56): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```

---

### Post by compiz addict on 2011-11-02
[SIZE="4"]WOW[/SIZE], I was using gcc, not g++! (well, the second time I was) Sorry for wasting your time everyone! lol

---

