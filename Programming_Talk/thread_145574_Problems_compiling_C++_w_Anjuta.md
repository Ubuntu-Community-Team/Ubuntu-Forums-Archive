---
title: "Problems compiling C++ w/ Anjuta"
date: 2006-03-16
forum: Programming Talk
---

### Post by Joshuwa on 2006-03-16
Hi,

I've just installed Ubuntu and Anjunta, and no matter what c++ code I try to compile, I get a pretty good sized list of errors.

I even tried to compile everyone's favorite:
```
#include <iostream>
using namespace std;

int main()
{ 
	cout << "Hello World!" << endl;
	
	return 0;
}
```

And that failed as well, producing the errors below :-k 

I'm pretty new to C++, but I know the above program should have no problems. I've installed gcc & g++... what's going wrong?

Any help is greatly appreciated - thanks in advance!

(I had to shorten the error list - it was too long to post)
```
Compiling file: test.cpp ...
g++       -c "test.cpp" -o "test.o"
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from test.cpp:1:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2072: error: ‘tm’ has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2089: error: ‘tm’ has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function ‘virtual _InIter std::time_get<_CharT, _InIter>::do_get_weekday(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2123: error: request for member ‘tm_wday’ in ‘__tm->’, which is of non-class type ‘int’
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2134: error: ‘tm’ has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function ‘virtual _InIter std::time_get<_CharT, _InIter>::do_get_monthname(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2169: error: request for member ‘tm_mon’ in ‘__tm->’, which is of non-class type ‘int’
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2180: error: ‘tm’ has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function ‘virtual _InIter std::time_get<_CharT, _InIter>::do_get_year(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2196: error: request for member ‘tm_year’ in ‘__tm->’, which is of non-class type ‘int’
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2207: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2208: error: redefinition of ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const’
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const’ previously declared here
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2212: error: ‘__beg’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2212: error: ‘__end’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2232: error: ‘__tm’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2242: error: expected ‘,’ or ‘...’ before ‘*’ token
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function ‘virtual _OutIter std::time_put<_CharT, _OutIter>::do_put(_OutIter, std::ios_base&, _CharT, int) const’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2262: error: ‘__mod’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2264: error: ‘__format’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2270: error: ‘__format’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2274: error: ‘__tm’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h: In instantiation of ‘std::time_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2509:   instantiated from here
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = char, _OutIter = std::ostreambuf_iterator<char, std::char_traits<char> >]’ cannot be overloaded
/usr/include/c++/4.0.2/bits/locale_facets.h:3364: error: with ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = char, _OutIter = std::ostreambuf_iterator<char, std::char_traits<char> >]’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2516: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2516: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2521: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2521: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.h: In instantiation of ‘std::time_put<wchar_t, std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> > >’:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2636:   instantiated from here
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = wchar_t, _OutIter = std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> >]’ cannot be overloaded
/usr/include/c++/4.0.2/bits/locale_facets.h:3364: error: with ‘_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = wchar_t, _OutIter = std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> >]’
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2643: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2643: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/ostream: In instantiation of ‘std::basic_ostream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/bits/ostream.tcc:680:   instantiated from here
/usr/include/c++/4.0.2/ostream:64: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/ostream: In instantiation of ‘std::basic_ostream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/bits/ostream.tcc:692:   instantiated from here
/usr/include/c++/4.0.2/ostream:62: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/ostream:64: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/istream:580:   instantiated from here
/usr/include/c++/4.0.2/istream:65: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream:569: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/istream:596:   instantiated from here
/usr/include/c++/4.0.2/istream:63: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:65: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:272: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:427: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:438: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:569: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_iostream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/bits/istream.tcc:1273:   instantiated from here
/usr/include/c++/4.0.2/istream:757: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >::sentry’:
/usr/include/c++/4.0.2/bits/istream.tcc:1276:   instantiated from here
/usr/include/c++/4.0.2/istream:630: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_iostream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/bits/istream.tcc:1281:   instantiated from here
/usr/include/c++/4.0.2/istream:755: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:757: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
Completed ... unsuccessful
Total time taken: 7 secs

```

---

### Post by gord on 2006-03-16
```
sudo apt-get install build-essential
```
that installs all the relivant files to be able to compile c/c++ programs

---

### Post by Joshuwa on 2006-03-16
^ worked like a charm!

Thanks a lot!

---

