---
title: "Complete beginner needs help with fstream!"
date: 2011-03-04
forum: Programming Talk
---

### Post by Caleidoscope on 2011-03-04
Hello! I'm trying to get used to using ifstreams and ofstreams, so I'm writing a small program but get a massive error when compiling and I don't know what it is!

So I've got a header with this function in it :

```
#include <iostream>
#include <fstream>

bool information(std::ifstream a);

```That I defined in this .cc file :

```

#include "TheFile.h"
#include <iostream>
#include <string>
#include <fstream>

using namespace std;

bool information(ifstream a)
{    
    string info;
    
    cin >> ws;
    getline(cin, info);

    return true;
}
```The function doesn't really do anything yet but I can't get past this error...
Then I've got this file, where when I try and use this function it gives me a huge error!!

```
#include "TheFile.h"
#include <iostream>
#include <iomanip>
#include <fstream>
#include <string>


using namespace std;

ifstream file;

int main() {
        

    
    file.open("the_file.dat");

    information(file);

    return 0;
    
    }
```If I remove "information(file);" everything compiles!

The error is this (sorry for the loooong post!!!) :

```
In file included from /usr/include/c++/4.4/bits/localefwd.h:43,
                 from /usr/include/c++/4.4/string:45,
                 from TheFile.h:1,
                 from Key.cc:1:
/usr/include/c++/4.4/bits/ios_base.h: In copy constructor ‘std::basic_ios<char, std::char_traits<char> >::basic_ios(const std::basic_ios<char, std::char_traits<char> >&)’:
/usr/include/c++/4.4/bits/ios_base.h:790: error: ‘std::ios_base::ios_base(const std::ios_base&)’ is private
/usr/include/c++/4.4/iosfwd:47: error: within this context
/usr/include/c++/4.4/iosfwd: In copy constructor ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::basic_ifstream<char, std::char_traits<char> >&)’:
/usr/include/c++/4.4/iosfwd:81: note: synthesized method ‘std::basic_ios<char, std::char_traits<char> >::basic_ios(const std::basic_ios<char, std::char_traits<char> >&)’ first required here 
/usr/include/c++/4.4/streambuf: In copy constructor ‘std::basic_filebuf<char, std::char_traits<char> >::basic_filebuf(const std::basic_filebuf<char, std::char_traits<char> >&)’:
/usr/include/c++/4.4/streambuf:770: error: ‘std::basic_streambuf<_CharT, _Traits>::basic_streambuf(const std::basic_streambuf<_CharT, _Traits>&) [with _CharT = char, _Traits = std::char_traits<char>]’ is private
/usr/include/c++/4.4/iosfwd:78: error: within this context
/usr/include/c++/4.4/iosfwd: In copy constructor ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::basic_ifstream<char, std::char_traits<char> >&)’:
/usr/include/c++/4.4/iosfwd:81: note: synthesized method ‘std::basic_filebuf<char, std::char_traits<char> >::basic_filebuf(const std::basic_filebuf<char, std::char_traits<char> >&)’ first required here 
Key.cc: In function ‘int main()’:
Key.cc:31: note: synthesized method ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::basic_ifstream<char, std::char_traits<char> >&)’ first required here 
Key.cc:31: error:   initializing argument 1 of ‘bool information(std::ifstream)’
make: *** [Key.o] Error 1

```Could anybody help me out?

---

### Post by SevenMachines on 2011-03-04
I think you want to pass fstreams by reference, no copying to functions, ie
```
 bool information(std::ifstream & a);
```

---

