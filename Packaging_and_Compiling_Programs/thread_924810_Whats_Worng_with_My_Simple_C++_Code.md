---
title: "Whats Worng with My Simple C++ Code?"
date: 2008-09-19
forum: Packaging and Compiling Programs
---

### Post by f.ben.isaac@gmail.com on 2008-09-19
#include<iostream>
using namespace std;

class CRectangle{
	int h, w;
	public:
		void getHW(int,int);
		int rect(){return(h*w);}
};

void CRectangle::getHW(int a, int b)
{
	h = a;
	w = b;
}

int main()
{
	CRectangle rectangle;
	rectangle.getHW(4,3);
	cout<<"Area is: " << rectangle.rect() << "\n";
	return 0;
}

It works fine under windows, but under Ubuntu, it gives me error while compiling! Why? Isn't C++ is C++?! Is there different C++ languages!

I'm newbie so bear with me

Sample of THE ERROR is 

*****************************************************************



/tmp/cc4JJ8lZ.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
cProg.cpp:(.text+0x24): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
cProg.cpp:(.text+0x6f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
cProg.cpp:(.text+0xad): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
cProg.cpp:(.text+0xf5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/cc4JJ8lZ.o: In function `__static_initialization_and_destruction_0(int, int)':
cProg.cpp:(.text+0x13f): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc4JJ8lZ.o: In function `__tcf_0':
cProg.cpp:(.text+0x18c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc4JJ8lZ.o: In function `main':
cProg.cpp:(.text+0x1d7): undefined reference to `std::cout'
cProg.cpp:(.text+0x1dc): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
cProg.cpp:(.text+0x1e8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
cProg.cpp:(.text+0x1f8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cc4JJ8lZ.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

*******************************************************
Thanks for Help!

---

### Post by jcwmoore on 2008-09-19
are you using the c++ compiler (g++) or the c compiler (gcc)?

i tried your code and all worked well with the command 
```
g++ file.cpp
```

but i got your exact output with
```
gcc file.cpp
```

---

### Post by f.ben.isaac@gmail.com on 2008-09-20
Yep worked with g++.
I used gcc ...

But why it did not work with gcc & worked with g++?!!!

---

### Post by jcwmoore on 2008-09-20
ok... gcc is the c compiler, so it will compile c, now c++ is basically an extension (or superset) of c, meaning that a c program will compile with a c++ complier but not necessarily the other way around.

---

