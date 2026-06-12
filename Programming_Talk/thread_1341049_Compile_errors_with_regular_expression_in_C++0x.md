---
title: "Compile errors with regular expression in C++0x"
date: 2009-11-29
forum: Programming Talk
---

### Post by sbarakat on 2009-11-29
I am trying to compile a regular expression example that uses the upcoming C++0x standard, but it keeps failing with a rather unhelpful error message:

```
g++ -Wall -std=c++0x -o "test_regex" "test_regex.cpp"
/tmp/ccGSTlxF.o: In function `std::tr1::basic_regex<char, std::tr1::regex_traits<char> >::basic_regex(char const*, unsigned int)':
test_regex.cpp:(.text._ZNSt3tr111basic_regexIcNS_12regex_traitsIcEEEC1EPKcj[std::tr1::basic_regex<char, std::tr1::regex_traits<char> >::basic_regex(char const*, unsigned int)]+0x75): undefined reference to `std::tr1::basic_regex<char, std::tr1::regex_traits<char> >::_M_compile()'
/tmp/ccGSTlxF.o: In function `bool std::tr1::regex_match<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, char, std::tr1::regex_traits<char> >(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::tr1::basic_regex<char, std::tr1::regex_traits<char> > const&, std::bitset<11ul>)':
test_regex.cpp:(.text._ZNSt3tr111regex_matchIN9__gnu_cxx17__normal_iteratorIPcSsEEcNS_12regex_traitsIcEEEEbT_S7_RKNS_11basic_regexIT0_T1_EESt6bitsetILm11EE[bool std::tr1::regex_match<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, char, std::tr1::regex_traits<char> >(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::tr1::basic_regex<char, std::tr1::regex_traits<char> > const&, std::bitset<11ul>)]+0x79): undefined reference to `bool std::tr1::regex_match<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::tr1::sub_match<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >, char, std::tr1::regex_traits<char> >(__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, __gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::tr1::match_results<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::tr1::sub_match<__gnu_cxx::__normal_iterator<char*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > > >&, std::tr1::basic_regex<char, std::tr1::regex_traits<char> > const&, std::bitset<11ul>)'
collect2: ld returned 1 exit status
Compilation failed.

```Somewhere in there it says
... undefined reference to `bool std::tr1::regex_match ...

This is the example code I'm working with, sourced from [http://www.johndcook.com/cpp_regex.html](http://www.johndcook.com/cpp_regex.html)
```
#include <tr1/regex>
#include <iostream>
#include <string>

int main()
{
    std::string str = "Hello world";
    std::tr1::regex rx("ello");

    if (regex_match(str.begin(), str.end(), rx))
    {
       std::cout << "WORKS";
    }

    return 0;
}
```I have tried [several]("http://stackoverflow.com/questions/992176/c-tokenize-a-string-using-a-regular-expression") [other]("http://www.codeguru.com/cpp/cpp/cpp_mfc/stl/article.php/c15339/") [examples]("http://www.codeproject.com/KB/string/TR1Regex.aspx") I have found across the net but they all result with a similar error. I have installed build-essential and running gcc 4.4.1 (which should have TR1).

Can anyone shed any light on the problem?? I am still very new to C++ but come from a PHP background.

---

### Post by Zugzwang on 2009-11-29
It might have to do with the fact that the libstdc++ support for TR1 regular expressions isn't considered to be fully done yet: [http://gcc.gnu.org/onlinedocs/libstdc++/manual/status.html#status.iso.tr1](http://gcc.gnu.org/onlinedocs/libstdc++/manual/status.html#status.iso.tr1)

Apart from that, your example code compiles (&links) fine here (on GCC 4.3.3).

---

### Post by sbarakat on 2009-11-29
I have tried several other examples as well though, even tried these [examples]("http://flavio.castelli.name/regexp-with-boost") from the Boost libraries. They all result in the similar compile issues, 'undefined reference to ...'.
I can compile simple examples like Hello World etc but as soon as I try anything with <tr1/regex> or <boost/regex.hpp> it fails. I'm sure its an issue with my setup or lack of, maybe a library I'm missing. I've been rattling my brain over this for the better part of a couple of days now and still cant figure it out.

If it helps I've got these packages installed on Ubuntu 9.10
g++-4.4
libstdc++6
libstdc++6-4.4-dev

---

### Post by MadCow108 on 2009-11-29
for boost regex you have to have the library installed and have to link with it:
g++ -lboost_regex file.cc

tr1 regex of gcc does not seem to be finished yet, so no point in trying to use it.

---

### Post by sbarakat on 2009-11-29
> **MadCow108 said:**
> for boost regex you have to have the library installed and have to link with it:
g++ -lboost_regex file.cc

tr1 regex of gcc does not seem to be finished yet, so no point in trying to use it.

Sweet that works! Yeah I guess I will give up on C++0x. I just remember reading somewhere that the standard would be finalized late 2009 or 2010. And since this project I'm working on is going to take at least a year or two to become stable I thought I would starting writing with it. But its probably a better idea to stick with Boost for now.

Thanks a lot for the help!

---

### Post by MadCow108 on 2009-11-29
even when the standard is finalized in near future (end of 2010 I guess), it will take years until the compilers have implemented it all in a stable fashion.
the c++98 standard isn't even fully implemented yet by most compilers [ok, the missing part is broken by design, but it still counts as not implemented :) ]

also the tr1 regex is based on boost regex, so there won't be much difference between standard and boost anyway

---

### Post by grayrainbow on 2009-11-29
Some parts of mine tr1_impl/regex file

explicit
basic_regex(const _Ch_type* __p,
  flag_type __f = regex_constants::ECMAScript)
  : _M_flags(__f), _M_pattern(__p), _M_mark_count(0)
  { _M_compile(); }

/**
 * @brief Compiles a regular expression pattern into a NFA.
 * @todo Implement this function.
 */
void _M_compile();

typedef basic_regex<char>    regex;

Btw, if you go in your c++ include directory and grep for "todo Implement this function", you could save yourself a lot of frustration with not implemented stuff. You can try installing include files which are known to work or try gcc 4.5 with -std=c++0x option, but don't be too optimistic(my build of it doesn't fix this issue).

Edit: Just grep it, seems "todo" is found only in tr1_impl/regex

---

### Post by koyeung on 2009-12-04
the implemenation status would be useful too:
[http://gcc.gnu.org/onlinedocs/libstdc++/manual/status.html#status.iso.tr1](http://gcc.gnu.org/onlinedocs/libstdc++/manual/status.html#status.iso.tr1)

---

