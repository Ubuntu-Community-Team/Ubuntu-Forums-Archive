---
title: "[ C++ ] String error ( no match for ‘operator+’ in ‘std::operator+ )."
date: 2009-09-22
forum: Programming Talk
---

### Post by credobyte on 2009-09-22
[COLOR=Green]**imagePrefix**[/COLOR] is a string ( eg., "image", "picture" )
[COLOR=Green]**imageExtension**[/COLOR] is a string ( detected from the given file name, eg. ".jpg", ".png" )
[COLOR=Green]**i**[/COLOR] is an integer, incremented by a for loop

Any ideas, what this error means and how to avoid ( fix ) it ?

Ln 30:
```
string newImgName = imagePrefix + "_" + i + imageExtension;

```Error:
```
main.cpp: In function ‘int main(int, char**)’:
main.cpp:30: error: no match for ‘operator+’ in ‘std::operator+(const std::basic_string<_CharT, _Traits, _Alloc>&, const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const char*)"_")) + i’
/usr/include/c++/4.3/bits/stl_bvector.h:267: note: candidates are: std::_Bit_iterator std::operator+(ptrdiff_t, const std::_Bit_iterator&)
/usr/include/c++/4.3/bits/stl_bvector.h:353: note:                 std::_Bit_const_iterator std::operator+(ptrdiff_t, const std::_Bit_const_iterator&)
```

---

### Post by dwhitney67 on 2009-09-22
You cannot add an integer to an STL string; no such operator exists.  Use stringstream instead.

Something like:
```

#include <sstream>
#include <string>
#include <iostream>

int main()
{
   int i = 10;
   std::string str = "Hello";
   std::stringstream ss;
   ss << str << " " << i;
   std::cout << ss.str() << std::endl;
}

```

---

### Post by MadCow108 on 2009-09-22
the operator + is not overloaded for integers, only for strings
so you need to convert the integer to a string first

stringstreams can do that:
```

#include <sstream>
stringstream ss;
ss << string1 << integer1 << "_" << endl;
string str = ss.str();

```

edit to slow :)

---

### Post by credobyte on 2009-09-22
Thanks to you both - works like a charm :)

---

