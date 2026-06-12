---
title: "What is *this*?"
date: 2007-08-08
forum: Programming Talk
---

### Post by phreakre on 2007-08-08
> /tmp/cc5vMbWT.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc5vMbWT.o: In function `__tcf_0':
helloworld.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc5vMbWT.o: In function `main':
helloworld.cpp:(.text+0x8e): undefined reference to `std::cout'
helloworld.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
helloworld.cpp:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
helloworld.cpp:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cc5vMbWT.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


I am a java guy trying to teach myself C++ and I am getting this output from this input :
> #include <iostream>

using namespace std;

int main() {
	cout << "Hello!" << endl;
	return 0;
}


..with the "gcc -x c++ helloworld.cpp" command.

---

### Post by CptPicard on 2007-08-08
Aren't you missing Java's fairly legible stack traces already? ;)

Your code seems fine, but I'm not sure if your command is linking anything (never called the compiler like that, myself). Try g++ yourfile.cpp -o outfile

---

### Post by phreakre on 2007-08-08
Thank you very much, Cpt. 

gcc --help says -x c++ enables the c++ compiler, but I guess it does not. g++ helloworld.cpp worked just fine. 

Thanks again.

---

### Post by CptPicard on 2007-08-08
Np,

It probably does enable the c++ compiler allright, but from the way the barf looks like, my guess is that the standard library is simply not linked in or something... would be curious to hear some guru actually explain what is going on ;)

---

### Post by xtacocorex on 2007-08-08
I would use g++ for C++ compiling.

---

### Post by hod139 on 2007-08-08
> **CptPicard said:**
> Np,

It probably does enable the c++ compiler allright, but from the way the barf looks like, my guess is that the standard library is simply not linked in or something... would be curious to hear some guru actually explain what is going on ;)

This is exactly right.  If you use the g++ command to compile cpp files, it will automatically link against libstdc++.  if you use gcc to compile a cpp file, you have to manually link.
```

gcc helloworld.cpp -lstdc++

```

As mentioned in another post, it's easiest to use gcc for c code and g++ for c++ code.

---

