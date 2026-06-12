---
title: "ofstream error (C++)"
date: 2008-10-15
forum: Programming Talk
---

### Post by Ddorda on 2008-10-15
Hey
this is just a little part of the program, but it's all the information needed (i think):
```

#include <fstream>
#include <iostream>
    // Save username and password
    ofstream myfile;
    myfile.open (homeDir + std::string("/users.log"));
    if (!myfile)
    {
    exit(1);
    }
    myfile << loginData->username << " " << loginData->password << " " << loginData->hostname << endl;
    myfile.close();
```

and it gives this error:
```
main.cpp: In function ‘void accountLogin(Network*, LoginData*)’:
main.cpp:497: error: no matching function for call to ‘std::basic_ofstream<char, std::char_traits<char> >::open(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)’
/usr/include/c++/4.2/fstream:648: note: candidates are: void std::basic_ofstream<_CharT, _Traits>::open(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]

```

I'm stuck on this like 2 days!
help!

TY - Ddorda

---

### Post by dribeas on 2008-10-15
> **Ddorda said:**
> ```

    myfile.open (homeDir + std::string("/users.log"));

```

and it gives this error:
```
main.cpp: In function &#8216;void accountLogin(Network*, LoginData*)&#8217;:
main.cpp:497: error: no matching function for call to &#8216;std::basic_ofstream<char, std::char_traits<char> >::open(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)&#8217;
/usr/include/c++/4.2/fstream:648: note: candidates are: void std::basic_ofstream<_CharT, _Traits>::open(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]

```

Class std:: ofstream does not take an std::string as argument, it takes a const char*. You should modify your code:

```

std::string tmp = homeDir + std::string( "/users.log" );
myfile.open ( tmp.c_str() );

// or
myfile.open( (homeDir+std::string( "/users.log" )).c_str() );

```

---

### Post by Ddorda on 2008-10-15
Thank you so much! i'm checking it now :D
the dubuger didn't say anything:KS

---

