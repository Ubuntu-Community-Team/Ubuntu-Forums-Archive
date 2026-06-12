---
title: "What do I need to compile a cpp file?"
date: 2006-04-04
forum: Packaging and Compiling Programs
---

### Post by lumingzuiku on 2006-04-04
My source code is faily simple as below:

#include<iostream>

using namespace std;

int main(void)
{
        cout<<"Hello World!"<<endl;
        return 0;
}


But compiler gave me some error messages like this:
/tmp/ccNfUm8H.o: In function `main':
1.cpp:(.text+0x25): undefined reference to `std::cout'
1.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
...........

I used cpp to compile my code, is it the right thing to compile C++ files?
thx a lot!

---

### Post by JaspSoft on 2006-04-04
```

gcc <filename> -lstdc++

```

ought to do it...

---

### Post by xenmax on 2006-04-04
you can also try ```
g++ <filename>
```

---

### Post by lumingzuiku on 2006-04-04
god....can't start X now....

---

### Post by hod139 on 2006-04-04
Can't help you with X, but to compile make sure you have build-essential installed
```
sudo apt-get install build-essential
```
and then simply type
```
g++ file.cpp
```

---

