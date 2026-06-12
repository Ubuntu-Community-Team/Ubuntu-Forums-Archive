---
title: "problem with a class"
date: 2007-02-18
forum: Programming Talk
---

### Post by the_nomad on 2007-02-18
im trying to compile the next code but i get _a whole bunch_ of errors...

```

#include <iostream>
using namespace std;

class CRectangle {
    int x, y;
  public:
    void set_values (int,int);
    int area () {return (x*y);}
};

void CRectangle::set_values (int a, int b) {
  x = a;
  y = b;
}

int main () {
  CRectangle rect;
  rect.set_values (3,4);
  cout << "area: " << rect.area();
  return 0;
}

```

i got this example from a tutorial on cplusplus.com and it should work.... does anyone have any ideea on what am i doing bad? i've just installed g++ through 'sudo apt-get install g++'...
thanx in advance.

---

### Post by WW on 2007-02-18
It works for me.  How did you compile it, and what errors did you get?

---

### Post by the_nomad on 2007-02-18
first i changed the directory to the one the file is and then 'g++ file.cpp'
and i got these errs:
```
/usr/include/c++/4.0.2/bits/codecvt.h:458: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/codecvt.h:458: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:1708: error: expected `)' before &#8216;__cloc&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:1865: error: &#8216;__c_locale&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:1876: error: variable or field &#8216;_M_initialize_numpunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:1876: error: &#8216;int std::numpunct<char>::_M_initialize_numpunct&#8217; is not a static member of &#8216;class std::numpunct<char>&#8217;/usr/include/c++/4.0.2/bits/locale_facets.h:1876: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:1884: error: variable or field &#8216;_M_initialize_numpunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:1884: error: &#8216;int std::numpunct<wchar_t>::_M_initialize_numpunct&#8217; is not a static member of &#8216;class std::numpunct<wchar_t>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:1884: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: In constructor &#8216;std::numpunct_byname<_CharT>::numpunct_byname(const char*, size_t)&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:1899: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:1899: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:1901: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:1901: error: expected `;' before &#8216;__tmp&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:1902: error: &#8216;__tmp&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:2479: error: &#8216;__c_locale&#8217; does not name a type
/usr/include/c++/4.0.2/bits/locale_facets.h:2507: error: expected `)' before &#8216;__cloc&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h: In constructor &#8216;std::collate<_CharT>::collate(size_t)&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:2494: error: class &#8216;std::collate<_CharT>&#8217; does not have any field named &#8216;_M_c_locale_collate&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:2494: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.h: In destructor &#8216;virtual std::collate<_CharT>::~collate()&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:2571: error: &#8216;_M_c_locale_collate&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: In constructor &#8216;std::collate_byname<_CharT>::collate_byname(const char*, size_t)&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:2655: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:2655: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:2809: error: &#8216;__c_locale&#8217; does not name a type
/usr/include/c++/4.0.2/bits/locale_facets.h:2833: error: expected `)' before &#8216;__cloc&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:2839: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.h:2940: error: &#8216;__c_locale&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:2949: error: variable or field &#8216;_M_initialize_timepunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:2949: error: &#8216;int std::__timepunct<char>::_M_initialize_timepunct&#8217; is not a static member of &#8216;class std::__timepunct<char>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:2949: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:2953: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.h:2958: error: variable or field &#8216;_M_initialize_timepunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:2958: error: &#8216;int std::__timepunct<wchar_t>::_M_initialize_timepunct&#8217; is not a static member of &#8216;class std::__timepunct<wchar_t>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:2958: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:2963: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h: In constructor &#8216;std::__timepunct<_CharT>::__timepunct(size_t)&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h:39: error: class &#8216;std::__timepunct<_CharT>&#8217; does not have any field named &#8216;_M_c_locale_timepunct&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h: In constructor &#8216;std::__timepunct<_CharT>::__timepunct(std::__timepunct_cache<_CharT>*, size_t)&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h:45: error: class &#8216;std::__timepunct<_CharT>&#8217; does not have any field named &#8216;_M_c_locale_timepunct&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h: At global scope:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h:50: error: expected constructor, destructor, or type conversion before &#8216;(&#8217; token
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h: In destructor &#8216;virtual std::__timepunct<_CharT>::~__timepunct()&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/time_members.h:67: error: &#8216;_M_c_locale_timepunct&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:3046: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3071: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3099: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3128: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3154: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3192: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3211: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3230: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3249: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3268: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3286: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3363: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.h:3410: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.h: In member function &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:3385: error: &#8216;__tm&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3385: error: &#8216;__format&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3385: error: &#8216;__mod&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:3596: error: expected `)' before &#8216;__cloc&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3883: error: &#8216;__c_locale&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.h:3901: error: variable or field &#8216;_M_initialize_moneypunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:3901: error: &#8216;int std::moneypunct<char, true>::_M_initialize_moneypunct&#8217; is not a static member of &#8216;class std::moneypunct<char, true>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3901: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3901: error: expected primary-expression before &#8216;const&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3901: error: initializer expression list treated as compound expression
/usr/include/c++/4.0.2/bits/locale_facets.h:3905: error: variable or field &#8216;_M_initialize_moneypunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:3905: error: &#8216;int std::moneypunct<char, false>::_M_initialize_moneypunct&#8217; is not a static member of &#8216;class std::moneypunct<char, false>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3905: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3905: error: expected primary-expression before &#8216;const&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3905: error: initializer expression list treated as compound expression
/usr/include/c++/4.0.2/bits/locale_facets.h:3916: error: variable or field &#8216;_M_initialize_moneypunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:3916: error: &#8216;int std::moneypunct<wchar_t, true>::_M_initialize_moneypunct&#8217; is not a static member of &#8216;class std::moneypunct<wchar_t, true>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3916: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3917: error: expected primary-expression before &#8216;const&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3917: error: initializer expression list treated as compound expression
/usr/include/c++/4.0.2/bits/locale_facets.h:3921: error: variable or field &#8216;_M_initialize_moneypunct&#8217; declared void
/usr/include/c++/4.0.2/bits/locale_facets.h:3921: error: &#8216;int std::moneypunct<wchar_t, false>::_M_initialize_moneypunct&#8217; is not a static member of &#8216;class std::moneypunct<wchar_t, false>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3921: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3922: error: expected primary-expression before &#8216;const&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3922: error: initializer expression list treated as compound expression
/usr/include/c++/4.0.2/bits/locale_facets.h: In constructor &#8216;std::moneypunct_byname<_CharT, _Intl>::moneypunct_byname(const char*, size_t)&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.h:3939: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3939: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3941: error: &#8216;__c_locale&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h:3941: error: expected `;' before &#8216;__tmp&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3942: error: &#8216;__tmp&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h:4271: error: &#8216;__c_locale&#8217; does not name a type
/usr/include/c++/4.0.2/bits/locale_facets.h:4300: error: expected `)' before &#8216;__cloc&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h: In constructor &#8216;std::messages<_CharT>::messages(size_t)&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:39: error: class &#8216;std::messages<_CharT>&#8217; does not have any field named &#8216;_M_c_locale_messages&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:39: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h: At global scope:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:44: error: expected constructor, destructor, or type conversion before &#8216;(&#8217; token
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h: In destructor &#8216;virtual std::messages<_CharT>::~messages()&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:69: error: &#8216;_M_c_locale_messages&#8217; was not declared in this scope
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h: In constructor &#8216;std::messages_byname<_CharT>::messages_byname(const char*, size_t)&#8217;:
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:95: error: &#8216;strlen&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:96: error: &#8216;strcpy&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:99: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/i486-linux-gnu/bits/messages_members.h:99: error: &#8216;strcmp&#8217; is not a member of &#8216;std&#8217;
/usr/include/c++/4.0.2/bits/basic_ios.h: At global scope:
/usr/include/c++/4.0.2/bits/basic_ios.h: In instantiation of &#8216;std::basic_ios<char, std::char_traits<char> >&#8217;:
/usr/include/c++/4.0.2/bits/basic_ios.tcc:192:   instantiated from here
/usr/include/c++/4.0.2/bits/basic_ios.h:68: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/bits/basic_ios.h: In instantiation of &#8216;std::basic_ios<wchar_t, std::char_traits<wchar_t> >&#8217;:
/usr/include/c++/4.0.2/bits/basic_ios.tcc:195:   instantiated from here
/usr/include/c++/4.0.2/bits/basic_ios.h:66: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/bits/basic_ios.h:68: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, float&) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:750: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, double&) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:763: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, long double&) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:776: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;_OutIter std::num_put<_CharT, _OutIter>::_M_insert_float(_OutIter, std::ios_base&, _CharT, char, _ValueT) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1066: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1074: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::money_get<_CharT, _InIter>::do_get(_InIter, _InIter, bool, std::ios_base&, std::_Ios_Iostate&, long double&) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1479: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _OutIter std::money_put<_CharT, _OutIter>::do_put(_OutIter, bool, std::ios_base&, _CharT, long double) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1688: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1695: error: there are no arguments to &#8216;_S_get_c_locale&#8217; that depend on a template parameter, so a declaration of &#8216;_S_get_c_locale&#8217; must be available
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1735: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;_InIter std::time_get<_CharT, _InIter>::_M_extract_via_format(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*, const _CharT*) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1760: error: request for member &#8216;tm_wday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1767: error: request for member &#8216;tm_wday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1775: error: request for member &#8216;tm_mon&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1782: error: request for member &#8216;tm_mon&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1794: error: request for member &#8216;tm_mday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1801: error: request for member &#8216;tm_mday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1804: error: request for member &#8216;tm_mday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1816: error: request for member &#8216;tm_hour&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1821: error: request for member &#8216;tm_hour&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1829: error: request for member &#8216;tm_mon&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1833: error: request for member &#8216;tm_min&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1853: error: request for member &#8216;tm_sec&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1889: error: request for member &#8216;tm_year&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:1897: error: request for member &#8216;tm_year&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2055: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2072: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2089: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::time_get<_CharT, _InIter>::do_get_weekday(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2123: error: request for member &#8216;tm_wday&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2134: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::time_get<_CharT, _InIter>::do_get_monthname(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2169: error: request for member &#8216;tm_mon&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2180: error: &#8216;tm&#8217; has not been declared
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _InIter std::time_get<_CharT, _InIter>::do_get_year(_InIter, _InIter, std::ios_base&, std::_Ios_Iostate&, int*) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2196: error: request for member &#8216;tm_year&#8217; in &#8216;__tm->&#8217;, which is of non-class type &#8216;int&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2207: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2208: error: redefinition of &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const&#8217; previously declared here
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2212: error: &#8216;__beg&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2212: error: &#8216;__end&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2232: error: &#8216;__tm&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2242: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;*&#8217; token
/usr/include/c++/4.0.2/bits/locale_facets.tcc: In member function &#8216;virtual _OutIter std::time_put<_CharT, _OutIter>::do_put(_OutIter, std::ios_base&, _CharT, int) const&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2262: error: &#8216;__mod&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2264: error: &#8216;__format&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2270: error: &#8216;__format&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2274: error: &#8216;__tm&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.h: At global scope:
/usr/include/c++/4.0.2/bits/locale_facets.h: In instantiation of &#8216;std::time_put<char, std::ostreambuf_iterator<char, std::char_traits<char> > >&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2509:   instantiated from here
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = char, _OutIter = std::ostreambuf_iterator<char, std::char_traits<char> >]&#8217; cannot be overloaded
/usr/include/c++/4.0.2/bits/locale_facets.h:3364: error: with &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = char, _OutIter = std::ostreambuf_iterator<char, std::char_traits<char> >]&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2516: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2516: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2521: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2521: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2522: error: template-id &#8216;use_facet<<expression error> >&#8217; for &#8216;const int& std::use_facet(const std::locale&)&#8217; does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2578: error: template-id &#8216;has_facet<<expression error> >&#8217; for &#8216;bool std::has_facet(const std::locale&)&#8217; does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.h: In instantiation of &#8216;std::time_put<wchar_t, std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> > >&#8217;:
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2636:   instantiated from here
/usr/include/c++/4.0.2/bits/locale_facets.h:3384: error: &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = wchar_t, _OutIter = std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> >]&#8217; cannot be overloaded
/usr/include/c++/4.0.2/bits/locale_facets.h:3364: error: with &#8216;_OutIter std::time_put<_CharT, _OutIter>::put(_OutIter, std::ios_base&, _CharT, int) const [with _CharT = wchar_t, _OutIter = std::ostreambuf_iterator<wchar_t, std::char_traits<wchar_t> >]&#8217;
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2643: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2643: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template-id &#8216;use_facet<<expression error> >&#8217; for &#8216;const int& std::use_facet(const std::locale&)&#8217; does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: &#8216;mbstate_t&#8217; was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template-id &#8216;has_facet<<expression error> >&#8217; for &#8216;bool std::has_facet(const std::locale&)&#8217; does not match any template declaration
/usr/include/c++/4.0.2/ostream: In instantiation of &#8216;std::basic_ostream<char, std::char_traits<char> >&#8217;:
/usr/include/c++/4.0.2/bits/ostream.tcc:680:   instantiated from here
/usr/include/c++/4.0.2/ostream:64: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/ostream: In instantiation of &#8216;std::basic_ostream<wchar_t, std::char_traits<wchar_t> >&#8217;:
/usr/include/c++/4.0.2/bits/ostream.tcc:692:   instantiated from here
/usr/include/c++/4.0.2/ostream:62: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/ostream:64: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream: In instantiation of &#8216;std::basic_istream<char, std::char_traits<char> >&#8217;:
/usr/include/c++/4.0.2/istream:580:   instantiated from here
/usr/include/c++/4.0.2/istream:65: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/istream:569: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/istream: In instantiation of &#8216;std::basic_istream<wchar_t, std::char_traits<wchar_t> >&#8217;:
/usr/include/c++/4.0.2/istream:596:   instantiated from here
/usr/include/c++/4.0.2/istream:63: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:65: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:272: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:427: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:438: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:569: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream: In instantiation of &#8216;std::basic_iostream<char, std::char_traits<char> >&#8217;:
/usr/include/c++/4.0.2/bits/istream.tcc:1273:   instantiated from here
/usr/include/c++/4.0.2/istream:757: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<char>&#8217;
/usr/include/c++/4.0.2/istream: In instantiation of &#8216;std::basic_istream<wchar_t, std::char_traits<wchar_t> >::sentry&#8217;:
/usr/include/c++/4.0.2/bits/istream.tcc:1276:   instantiated from here
/usr/include/c++/4.0.2/istream:630: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream: In instantiation of &#8216;std::basic_iostream<wchar_t, std::char_traits<wchar_t> >&#8217;:
/usr/include/c++/4.0.2/bits/istream.tcc:1281:   instantiated from here
/usr/include/c++/4.0.2/istream:755: error: no type named &#8216;int_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;
/usr/include/c++/4.0.2/istream:757: error: no type named &#8216;off_type&#8217; in &#8216;struct std::char_traits<wchar_t>&#8217;

``` ... and many many many others :(

---

### Post by jvc26 on 2007-02-18
Does:
```

 g++ -o encoded file.cpp

```
Work?
Il

---

### Post by the_nomad on 2007-02-18
no ... the same thing :confused: :confused:

---

### Post by WW on 2007-02-18
Wow.  I hope someone else can figure that out.

I have only one suggestion--really a shot in the dark.  I installed g++ indirectly, by installing the package build-essential.  Installing this package will install gcc, g++, some basic libraries, the "make" command, and a couple other things.  *Maybe* you are missing a library (or something) that is necessary for compiling g++ programs.  (But I would expect g++ to depend on whatever it is that might be missing, so this idea is probably nonsense.)  You could try installing build-essential:
> $ sudo apt-get install build-essential
and then try to compile your program again.

---

### Post by jvc26 on 2007-02-18
Thats bizarre - I just compiled it fine with the command:
```

g++ -o testoutput test.cpp

```
(Where I called your source test.cpp) It compiled no issues - maybe try what WW suggested - I find it very odd as your code is fine to compile (no compiling errors) not sure I'm afraid
Il

---

### Post by the_nomad on 2007-02-18
awesome! thanx alot dudes :) it was from that build-essential pkg :)

---

### Post by WW on 2007-02-18
Cu pl&#259;cere. :)

---

