---
title: "Cannot compile Hello World C++ file"
date: 2007-04-17
forum: Programming Talk
---

### Post by LegolasV on 2007-04-17
I'm using Ubuntu 6.10. I have installed packet build-essential successfully.
I have the following simple C++ Hello World program: 

#include <iostream>
#include <string>
using namespace std;

inline void pr_message(string s= "Hello World!")
{
	count << s << endl;
}

int main()
{
	pr_message();
}

I saved it under the name hello.cpp . I then type the following command to compile the program:
g++ hello.cpp

I then got the following error message:

hello.cpp: In function &#8216;void pr_message(std::string)&#8217;:
hello.cpp:7: error: no match for &#8216;operator<<&#8217; in &#8216;std::count << s&#8217;
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/basic_string.h:2395: note: candidates are: std::basic_ostream<_CharT, _Traits>& std:: operator<<(std::basic_ostream<_CharT, _Traits>&, const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]

Can somebody tell me what the problem is? Thank you very much in advance!

---

### Post by kpatz on 2007-04-17
It should be **cout**, not **count**.

```
cout << s << endl;
```

---

### Post by LegolasV on 2007-04-17
Found the solution already. SOrry for troubling u guys

---

### Post by LegolasV on 2007-04-17
thank u kpatz for your quick reply

---

