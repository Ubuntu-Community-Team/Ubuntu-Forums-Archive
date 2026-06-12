---
title: "Boken Compiler?"
date: 2007-03-05
forum: Programming Talk
---

### Post by Mars8082686 on 2007-03-05
Hi, I am trying to compile a basic C++ program and I am getting a funny error. I have compiled C++ programs on this machine before, but now it being weird. I think there is a problem with my linker. Here is my C++ code ```

#include <iostream>
 using namespace std;

 int main () 
 {
   cout << "Hello World!";
   return 0;
  }
```
and here is the error I'm getting
```

/usr/bin/ld: Undefined symbols:
std::ios_base::Init::Init()
std::ios_base::Init::~Init()
std::cout
std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)
___gxx_personality_v0
collect2: ld returned 1 exit status

```

any ideas?

---

### Post by hod139 on 2007-03-05
make sure you are using g++ to compile C++ code, not gcc.

---

### Post by Wybiral on 2007-03-05
Have you installed "build-essential"?

If not, type this in the command line:
```

sudo apt-get install build-essential

```

That tends to be a VERY VERY common problem so it's worth a shot.

---

### Post by Mars8082686 on 2007-03-05
> **hod139 said:**
> make sure you are using g++ to compile C++ code, not gcc.

I now feel like a complete and absolute noob... V.V
I'm going to go cut my self

---

