---
title: "cant compile C++ files"
date: 2012-05-04
forum: Packaging and Compiling Programs
---

### Post by trttony on 2012-05-04
I type g++ helloworld.cpp -o helloworld to compile  the code

#include <iostream>

using namespace std;

int main()
{
            cout << "Hello World!";
            return 0;
}

and i get more pages of errors than my terminal will display...

a small chunk of it is 


/usr/include/c++/4.6/bits/istream.tcc:654:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc: At global scope:
/usr/include/c++/4.6/bits/istream.tcc:679:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.6/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::putback(std::basic_istream<_CharT, _Traits>::char_type)’:
/usr/include/c++/4.6/bits/istream.tcc:717:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::unget()’:
/usr/include/c++/4.6/bits/istream.tcc:752:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc: In function ‘std::basic_istream<_CharT, _Traits>& std::operator>>(std::basic_istream<_CharT, _Traits>&, _CharT2*)’:
/usr/include/c++/4.6/bits/istream.tcc:965:7: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc:965:18: error: expected ‘;’ before ‘__extracted’
/usr/include/c++/4.6/bits/istream.tcc:973:19: error: expected ‘;’ before ‘__num’
/usr/include/c++/4.6/bits/istream.tcc:974:12: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc:975:49: error: type/value mismatch at argument 1 in template parameter list for ‘template<class _Value> struct __gnu_cxx::__numeric_traits’
/usr/include/c++/4.6/bits/istream.tcc:975:49: error:   expected a type, got ‘streamsize’
/usr/include/c++/4.6/bits/istream.tcc:983:15: error: ‘__extracted’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc:983:29: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.6/bits/istream.tcc:1008:12: error: ‘__extracted’ was not declared in this scope

any help would be greatly appreciated new to c++

---

### Post by Bachstelze on 2012-05-04
Install build-essential. ;)

---

### Post by trttony on 2012-05-05
build-essential is installed... i even uninstalled it and reinstalled it... i have the libraries too. g++ is installed as well

---

### Post by Bachstelze on 2012-05-06
Then post the entire output, not just "a small chunk".

---

