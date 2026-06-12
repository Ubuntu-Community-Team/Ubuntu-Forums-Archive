---
title: "Masses of compile errors, source c std libs?"
date: 2008-02-24
forum: Programming Talk
---

### Post by lucasl on 2008-02-24
Hi,
I'm getting hundreds of errors when trying to compile a game of mine that hasn't been changed since it compiled correctly last. However, I have reinstalled ubuntu since. I couldn't really determine anything from the errors, so here are the first however-many.
```
g++ *.cpp -Wall -o main -lchipmunk -lgl
In file included from /usr/include/c++/4.1.3/algorithm:68,
                 from /usr/include/c++/4.1.3/string:55,
                 from /usr/include/c++/4.1.3/bits/locale_classes.h:47,
                 from /usr/include/c++/4.1.3/bits/ios_base.h:47,
                 from /usr/include/c++/4.1.3/ios:48,
                 from /usr/include/c++/4.1.3/ostream:44,
                 from /usr/include/c++/4.1.3/iostream:44,
                 from game.h:1,
                 from game.cpp:1:
/usr/include/c++/4.1.3/bits/stl_algo.h:62:1: error: unterminated #ifndef
/usr/include/c++/4.1.3/bits/stl_algo.h:1948: error: ‘forward_iterator_’ has not been declared
/usr/include/c++/4.1.3/bits/basic_string.tcc:48: error: expected ‘,’ or ‘...’ before ‘namespace’
/usr/include/wctype.h:66: error: expected `)' before ‘;’ token
/usr/include/wctype.h:185: error: ‘wctype_t’ does not name a type
/usr/include/wctype.h:189: error: ‘wctype_t’ has not been declared
/usr/include/wctype.h:298: error: ‘wctype_t’ does not name a type
/usr/include/wctype.h:303: error: ‘wctype_t’ has not been declared
/usr/include/c++/4.1.3/cwctype:83: error: ‘::wctype_t’ has not been declared
/usr/include/c++/4.1.3/cwctype:84: error: ‘::wctrans_t’ has not been declared
/usr/include/c++/4.1.3/cwctype:86: error: ‘::iswalnum’ has not been declared
/usr/include/c++/4.1.3/cwctype:87: error: ‘::iswalpha’ has not been declared
/usr/include/c++/4.1.3/cwctype:89: error: ‘::iswblank’ has not been declared
/usr/include/c++/4.1.3/cwctype:91: error: ‘::iswcntrl’ has not been declared
/usr/include/c++/4.1.3/cwctype:92: error: ‘::iswctype’ has not been declared
/usr/include/c++/4.1.3/cwctype:93: error: ‘::iswdigit’ has not been declared
/usr/include/c++/4.1.3/cwctype:94: error: ‘::iswgraph’ has not been declared
/usr/include/c++/4.1.3/cwctype:95: error: ‘::iswlower’ has not been declared
/usr/include/c++/4.1.3/cwctype:96: error: ‘::iswprint’ has not been declared
/usr/include/c++/4.1.3/cwctype:97: error: ‘::iswpunct’ has not been declared
/usr/include/c++/4.1.3/cwctype:98: error: ‘::iswspace’ has not been declared
/usr/include/c++/4.1.3/cwctype:99: error: ‘::iswupper’ has not been declared
/usr/include/c++/4.1.3/cwctype:100: error: ‘::iswxdigit’ has not been declared
/usr/include/c++/4.1.3/cwctype:101: error: ‘::towctrans’ has not been declared
/usr/include/c++/4.1.3/cwctype:102: error: ‘::towlower’ has not been declared
/usr/include/c++/4.1.3/cwctype:103: error: ‘::towupper’ has not been declared
/usr/include/c++/4.1.3/cwctype:104: error: ‘::wctrans’ has not been declared
/usr/include/c++/4.1.3/cwctype:105: error: ‘::wctype’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:65: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:71: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:76: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:81: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:145: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::__ctype_abstract_base<_CharT>::__ctype_abstract_base(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:353: error: class ‘std::std::__ctype_abstract_base<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:614: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:663: error: expected constructor, destructor, or type conversion before ‘ctype’
/usr/include/c++/4.1.3/bits/locale_facets.h:675: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:697: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1198: error: specialisation of ‘template<class _Facet> const _Facet& std::use_facet(const std::locale&)’ in different namespace
/usr/include/c++/4.1.3/bits/localefwd.h:184: error:   from definition of ‘template<class _Facet> const _Facet& std::use_facet(const std::locale&)’
/usr/include/c++/4.1.3/bits/locale_facets.h:1219: error: ‘wctype_t’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1231: error: ‘__wmask_type’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1236: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1260: error: ‘__wmask_type’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1504: error: specialisation of ‘template<class _Facet> const _Facet& std::use_facet(const std::locale&)’ in different namespace
/usr/include/c++/4.1.3/bits/localefwd.h:184: error:   from definition of ‘template<class _Facet> const _Facet& std::use_facet(const std::locale&)’
/usr/include/c++/4.1.3/bits/codecvt.h:71: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/codecvt.h: In constructor ‘std::std::__codecvt_abstract_base<_InternT, _ExternT, _StateT>::__codecvt_abstract_base(size_t)’:
/usr/include/c++/4.1.3/bits/codecvt.h:226: error: expected class-name before ‘(’ token
/usr/include/c++/4.1.3/bits/codecvt.h: At global scope:
/usr/include/c++/4.1.3/bits/codecvt.h:285: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/codecvt.h:329: error: expected constructor, destructor, or type conversion before ‘codecvt’
/usr/include/c++/4.1.3/bits/codecvt.h:346: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/codecvt.h:404: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/codecvt.h: In constructor ‘std::std::codecvt_byname<_InternT, _ExternT, _StateT>::codecvt_byname(const char*, size_t)’:
/usr/include/c++/4.1.3/bits/codecvt.h:458: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/codecvt.h:458: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:1587: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::__numpunct_cache<_CharT>::__numpunct_cache(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1612: error: class ‘std::std::__numpunct_cache<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:1658: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:1673: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::numpunct<_CharT>::numpunct(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1681: error: class ‘std::std::numpunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::numpunct<_CharT>::numpunct(std::std::__numpunct_cache<_CharT>*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1695: error: class ‘std::std::numpunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::numpunct<_CharT>::numpunct(__locale_struct*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1709: error: class ‘std::std::numpunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:1869: error: expected constructor, destructor, or type conversion before ‘numpunct’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::numpunct_byname<_CharT>::numpunct_byname(const char*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1899: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h:1899: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:1928: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:1938: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:1975: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2011: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2016: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2021: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2026: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2032: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2037: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2070: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2075: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2080: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2112: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2120: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2125: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2144: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2148: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2151: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2155: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2159: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2164: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2168: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2173: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2177: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2187: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:2192: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::num_get<_CharT, _InIter>::num_get(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:1948: error: class ‘std::std::num_get<_CharT, _InIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:2205: error: expected constructor, destructor, or type conversion before ‘num_get’
/usr/include/c++/4.1.3/bits/locale_facets.h:2221: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:2231: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::num_put<_CharT, _OutIter>::num_put(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2241: error: class ‘std::std::num_put<_CharT, _OutIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:2477: error: expected constructor, destructor, or type conversion before ‘num_put’
/usr/include/c++/4.1.3/bits/locale_facets.h:2495: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:2511: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::collate<_CharT>::collate(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2522: error: class ‘std::std::collate<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h:2522: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.h:2522: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::collate<_CharT>::collate(__locale_struct*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2536: error: class ‘std::std::collate<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h:2536: error: there are no arguments to ‘_S_clone_c_locale’ that depend on a template parameter, so a declaration of ‘_S_clone_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.h: In destructor ‘virtual std::std::collate<_CharT>::~collate()’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2599: error: there are no arguments to ‘_S_destroy_c_locale’ that depend on a template parameter, so a declaration of ‘_S_destroy_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:2647: error: expected constructor, destructor, or type conversion before ‘collate’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::collate_byname<_CharT>::collate_byname(const char*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2683: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h:2683: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:2710: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::__timepunct_cache<_CharT>::__timepunct_cache(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:2772: error: class ‘std::std::__timepunct_cache<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:2828: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:2842: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:2972: error: expected constructor, destructor, or type conversion before ‘__timepunct’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h: In constructor ‘std::std::__timepunct<_CharT>::__timepunct(size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:39: error: class ‘std::std::__timepunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:40: error: there are no arguments to ‘_S_get_c_name’ that depend on a template parameter, so a declaration of ‘_S_get_c_name’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h: In constructor ‘std::std::__timepunct<_CharT>::__timepunct(std::std::__timepunct_cache<_CharT>*, size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:45: error: class ‘std::std::__timepunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:46: error: there are no arguments to ‘_S_get_c_name’ that depend on a template parameter, so a declaration of ‘_S_get_c_name’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h: In constructor ‘std::std::__timepunct<_CharT>::__timepunct(__locale_struct*, const char*, size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:52: error: class ‘std::std::__timepunct<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:55: error: ‘strlen’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:57: error: ‘memcpy’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h: In destructor ‘virtual std::std::__timepunct<_CharT>::~__timepunct()’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:72: error: there are no arguments to ‘_S_get_c_name’ that depend on a template parameter, so a declaration of ‘_S_get_c_name’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/time_members.h:75: error: there are no arguments to ‘_S_destroy_c_locale’ that depend on a template parameter, so a declaration of ‘_S_destroy_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3010: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:3022: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:3074: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3099: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3127: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3156: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3182: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3220: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3239: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3258: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3277: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3296: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3302: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3309: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:3314: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::time_get<_CharT, _InIter>::time_get(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3033: error: class ‘std::std::time_get<_CharT, _InIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3319: error: expected constructor, destructor, or type conversion before ‘time_get’
/usr/include/c++/4.1.3/bits/locale_facets.h:3352: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:3362: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::time_put<_CharT, _OutIter>::time_put(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3373: error: class ‘std::std::time_put<_CharT, _OutIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3443: error: expected constructor, destructor, or type conversion before ‘time_put’
/usr/include/c++/4.1.3/bits/locale_facets.h:3502: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::__moneypunct_cache<_CharT, _Intl>::__moneypunct_cache(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3525: error: class ‘std::std::__moneypunct_cache<_CharT, _Intl>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3568: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:3587: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::moneypunct<_CharT, _Intl>::moneypunct(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3597: error: class ‘std::std::moneypunct<_CharT, _Intl>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::moneypunct<_CharT, _Intl>::moneypunct(std::std::__moneypunct_cache<_CharT, _Intl>*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3610: error: class ‘std::std::moneypunct<_CharT, _Intl>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::moneypunct<_CharT, _Intl>::moneypunct(__locale_struct*, const char*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3625: error: class ‘std::std::moneypunct<_CharT, _Intl>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3916: error: expected constructor, destructor, or type conversion before ‘moneypunct’
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::moneypunct_byname<_CharT, _Intl>::moneypunct_byname(const char*, size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:3967: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h:3967: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:3999: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:4010: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:4051: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:4081: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:4104: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:4116: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h:4128: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::money_get<_CharT, _InIter>::money_get(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:4020: error: class ‘std::std::money_get<_CharT, _InIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:4132: error: expected constructor, destructor, or type conversion before ‘money_get’
/usr/include/c++/4.1.3/bits/locale_facets.h:4148: error: expected class-name before ‘{’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:4158: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h: In constructor ‘std::std::money_put<_CharT, _OutIter>::money_put(size_t)’:
/usr/include/c++/4.1.3/bits/locale_facets.h:4168: error: class ‘std::std::money_put<_CharT, _OutIter>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/bits/locale_facets.h: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.h:4284: error: expected constructor, destructor, or type conversion before ‘money_put’
/usr/include/c++/4.1.3/bits/locale_facets.h:4317: error: expected class-name before ‘,’ token
/usr/include/c++/4.1.3/bits/locale_facets.h:4335: error: ‘id’ in class ‘std::locale’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.h:4519: error: expected constructor, destructor, or type conversion before ‘messages’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h: In constructor ‘std::std::messages<_CharT>::messages(size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:39: error: class ‘std::std::messages<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:39: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:40: error: there are no arguments to ‘_S_get_c_name’ that depend on a template parameter, so a declaration of ‘_S_get_c_name’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h: In constructor ‘std::std::messages<_CharT>::messages(__locale_struct*, const char*, size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:46: error: class ‘std::std::messages<_CharT>’ does not have any field named ‘facet’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:48: error: ‘strlen’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:50: error: ‘memcpy’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:54: error: there are no arguments to ‘_S_clone_c_locale’ that depend on a template parameter, so a declaration of ‘_S_clone_c_locale’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h: In destructor ‘virtual std::std::messages<_CharT>::~messages()’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:70: error: there are no arguments to ‘_S_get_c_name’ that depend on a template parameter, so a declaration of ‘_S_get_c_name’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:72: error: there are no arguments to ‘_S_destroy_c_locale’ that depend on a template parameter, so a declaration of ‘_S_destroy_c_locale’ must be available
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h: In constructor ‘std::std::messages_byname<_CharT>::messages_byname(const char*, size_t)’:
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:96: error: ‘struct std::locale::facet’ has not been declared
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:98: error: ‘strlen’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:99: error: ‘strcpy’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:102: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:102: error: ‘strcmp’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/basic_ios.h: At global scope:
/usr/include/c++/4.1.3/bits/basic_ios.h:57: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/basic_ios.h:122: error: ‘iostate’ does not name a type
/usr/include/c++/4.1.3/bits/basic_ios.h:134: error: ‘iostate’ has not been declared
/usr/include/c++/4.1.3/bits/basic_ios.h:143: error: ‘iostate’ has not been declared
/usr/include/c++/4.1.3/bits/basic_ios.h:150: error: ‘iostate’ has not been declared
/usr/include/c++/4.1.3/bits/basic_ios.h:207: error: ‘iostate’ does not name a type
/usr/include/c++/4.1.3/bits/basic_ios.h:243: error: ‘iostate’ has not been declared
/usr/include/c++/4.1.3/bits/basic_ios.h:134: error: ‘goodbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h: In member function ‘void std::std::basic_ios<_CharT, _Traits>::_M_setstate(int)’:
/usr/include/c++/4.1.3/bits/basic_ios.h:154: error: ‘_M_streambuf_state’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h: In member function ‘bool std::std::basic_ios<_CharT, _Traits>::eof() const’:
/usr/include/c++/4.1.3/bits/basic_ios.h:177: error: ‘eofbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h: In member function ‘bool std::std::basic_ios<_CharT, _Traits>::fail() const’:
/usr/include/c++/4.1.3/bits/basic_ios.h:188: error: ‘badbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h:188: error: ‘failbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h: In member function ‘bool std::std::basic_ios<_CharT, _Traits>::bad() const’:
/usr/include/c++/4.1.3/bits/basic_ios.h:198: error: ‘badbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h: In member function ‘void std::std::basic_ios<_CharT, _Traits>::exceptions(int)’:
/usr/include/c++/4.1.3/bits/basic_ios.h:245: error: ‘_M_exception’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.h:246: error: ‘_M_streambuf_state’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc: At global scope:
/usr/include/c++/4.1.3/bits/basic_ios.tcc:44: error: variable or field ‘clear’ declared void
/usr/include/c++/4.1.3/bits/basic_ios.tcc:44: error: ‘int std::std::basic_ios<_CharT, _Traits>::clear’ is not a static member of ‘class std::std::basic_ios<_CharT, _Traits>’
/usr/include/c++/4.1.3/bits/basic_ios.tcc:44: error: template definition of non-template ‘int std::std::basic_ios<_CharT, _Traits>::clear’
/usr/include/c++/4.1.3/bits/basic_ios.tcc:44: error: ‘iostate’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:45: error: expected `;' before ‘{’ token
/usr/include/c++/4.1.3/bits/basic_ios.tcc: In member function ‘std::std::basic_ios<_CharT, _Traits>& std::std::basic_ios<_CharT, _Traits>::copyfmt(const std::std::basic_ios<_CharT, _Traits>&)’:
/usr/include/c++/4.1.3/bits/basic_ios.tcc:76: error: ‘_Words’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:76: error: ‘__words’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:76: error: ‘_S_local_word_size’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:77: error: ‘_M_local_word’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:77: error: expected type-specifier before ‘_Words’
/usr/include/c++/4.1.3/bits/basic_ios.tcc:77: error: expected `;' before ‘_Words’
/usr/include/c++/4.1.3/bits/basic_ios.tcc:80: error: ‘_Callback_list’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:80: error: ‘__cb’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:83: error: ‘erase_event’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:83: error: there are no arguments to ‘_M_call_callbacks’ that depend on a template parameter, so a declaration of ‘_M_call_callbacks’ must be available
/usr/include/c++/4.1.3/bits/basic_ios.tcc:84: error: ‘_M_word’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:89: error: there are no arguments to ‘_M_dispose_callbacks’ that depend on a template parameter, so a declaration of ‘_M_dispose_callbacks’ must be available
/usr/include/c++/4.1.3/bits/basic_ios.tcc:92: error: ‘_M_callbacks’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:95: error: ‘_M_word’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:96: error: ‘_M_word_size’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:103: error: ‘_M_ios_locale’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:106: error: ‘copyfmt_event’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:106: error: there are no arguments to ‘_M_call_callbacks’ that depend on a template parameter, so a declaration of ‘_M_call_callbacks’ must be available
/usr/include/c++/4.1.3/bits/basic_ios.tcc: In member function ‘std::locale std::std::basic_ios<_CharT, _Traits>::imbue(const std::locale&)’:
/usr/include/c++/4.1.3/bits/basic_ios.tcc:127: error: return type ‘struct std::locale’ is incomplete
/usr/include/c++/4.1.3/bits/basic_ios.tcc:130: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/basic_ios.tcc: In member function ‘void std::std::basic_ios<_CharT, _Traits>::init(std::basic_streambuf<_CharT, _Traits>*)’:
/usr/include/c++/4.1.3/bits/basic_ios.tcc:142: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/basic_ios.tcc:145: error: ‘_M_ios_locale’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:163: error: ‘_M_exception’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:163: error: ‘goodbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:165: error: ‘_M_streambuf_state’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc:165: error: ‘badbit’ was not declared in this scope
/usr/include/c++/4.1.3/bits/basic_ios.tcc: At global scope:
/usr/include/c++/4.1.3/bits/basic_ios.tcc:192: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.1.3/bits/basic_ios.h:56: error: provided for ‘template<class _CharT, class _Traits> class std::std::basic_ios’
/usr/include/c++/4.1.3/bits/basic_ios.tcc:195: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.1.3/bits/basic_ios.h:56: error: provided for ‘template<class _CharT, class _Traits> class std::std::basic_ios’
/usr/include/c++/4.1.3/ostream:337: error: ‘struct std::ios_base::seekdir’ has not been declared
/usr/include/c++/4.1.3/ostream: In member function ‘void std::std::basic_ostream<_CharT, _Traits>::_M_write(const _CharT*, std::streamsize)’:
/usr/include/c++/4.1.3/ostream:270: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/ostream: In destructor ‘std::std::basic_ostream<_CharT, _Traits>::sentry::~sentry()’:
/usr/include/c++/4.1.3/ostream:386: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/ostream:390: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:49: error: definition of ‘std::locale std::locale::combine(const std::locale&) const’ is not in namespace enclosing ‘std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:49: error: invalid use of undefined type ‘struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:49: error: template definition of non-template ‘std::locale std::locale::combine(const std::locale&) const’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘std::locale std::locale::combine(const std::locale&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:49: error: return type ‘struct std::locale’ is incomplete
/usr/include/c++/4.1.3/bits/locale_facets.tcc:51: error: ‘_Impl’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:51: error: ‘__tmp’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:51: error: expected type-specifier before ‘_Impl’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:51: error: expected `;' before ‘_Impl’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:54: error: invalid use of undefined type ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:67: error: definition of ‘bool std::locale::operator()(const std::basic_string<_CharT, _Traits, _Alloc>&, const std::basic_string<_CharT, _Traits, _Alloc>&) const’ is not in namespace enclosing ‘std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:67: error: invalid use of undefined type ‘struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:67: error: template definition of non-template ‘bool std::locale::operator()(const std::basic_string<_CharT, _Traits, _Alloc>&, const std::basic_string<_CharT, _Traits, _Alloc>&) const’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In function ‘bool std::std::has_facet(const std::locale&)’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:91: error: expected initializer before ‘*’ token
/usr/include/c++/4.1.3/bits/locale_facets.tcc:92: error: invalid use of undefined type ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:92: error: ‘__facets’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In function ‘const _Facet& std::std::use_facet(const std::locale&)’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:113: error: expected initializer before ‘*’ token
/usr/include/c++/4.1.3/bits/locale_facets.tcc:114: error: invalid use of undefined type ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:114: error: ‘__facets’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:116: error: ‘__facets’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘const std::std::__numpunct_cache<_CharT>* std::std::__use_cache<std::std::__numpunct_cache<_CharT> >::operator()(const std::locale&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:136: error: expected initializer before ‘*’ token
/usr/include/c++/4.1.3/bits/locale_facets.tcc:137: error: ‘__caches’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:150: error: invalid use of undefined type ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:152: error: ‘__caches’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘const std::std::__moneypunct_cache<_CharT, _Intl>* std::std::__use_cache<std::std::__moneypunct_cache<_CharT, _Intl> >::operator()(const std::locale&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:163: error: expected initializer before ‘*’ token
/usr/include/c++/4.1.3/bits/locale_facets.tcc:164: error: ‘__caches’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:177: error: invalid use of undefined type ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/localefwd.h:53: error: forward declaration of ‘const struct std::locale’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:180: error: ‘__caches’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:281: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘_InIter std::std::num_get<_CharT, _InIter>::_M_extract_float(_InIter, _InIter, std::ios_base&, int&, std::string&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:286: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:442: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:447: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:474: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘_InIter std::std::num_get<_CharT, _InIter>::_M_extract_int(_InIter, _InIter, std::ios_base&, int&, _ValueT&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:480: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:486: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:488: error: ‘__basefield’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:488: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:489: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:630: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:637: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:640: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:650: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _InIter std::std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, int&, bool&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:652: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:652: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:662: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:669: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:703: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:706: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:715: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:722: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:729: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:736: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:744: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:751: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:759: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _InIter std::std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, int&, float&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:764: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:772: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _InIter std::std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, int&, double&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:777: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:800: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _InIter std::std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, int&, long double&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:805: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:813: error: ‘struct std::ios_base::iostate’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _InIter std::std::num_get<_CharT, _InIter>::do_get(_InIter, _InIter, std::ios_base&, int&, void*&) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:816: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:817: error: ‘fmtflags’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:818: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:818: error: ‘__fmt’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:818: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:818: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:824: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:826: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:854: error: ‘struct std::ios_base::fmtflags’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In function ‘int std::std::__int_to_char(_CharT*, long int, const _CharT*, int)’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:857: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:858: error: ‘__basefield’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:858: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:859: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:867: error: ‘struct std::ios_base::fmtflags’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:874: error: ‘struct std::ios_base::fmtflags’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In function ‘int std::std::__int_to_char(_CharT*, long long int, const _CharT*, int)’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:877: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:878: error: ‘__basefield’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:878: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:879: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:887: error: ‘struct std::ios_base::fmtflags’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc:895: error: ‘struct std::ios_base::fmtflags’ has not been declared
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In function ‘int std::std::__int_to_char(_CharT*, _ValueT, const _CharT*, int, bool)’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:897: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:900: error: ‘__basefield’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:900: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:901: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:911: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:924: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘_OutIter std::std::num_put<_CharT, _OutIter>::_M_insert_int(_OutIter, std::ios_base&, _CharT, _ValueT) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:959: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:962: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:971: error: ‘__flags’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:988: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:989: error: ‘__basefield’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:989: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:990: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:995: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1002: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1004: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1009: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1018: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1026: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘_OutIter std::std::num_put<_CharT, _OutIter>::_M_insert_float(_OutIter, std::ios_base&, _CharT, char, _ValueT) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1077: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1081: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1099: error: ‘__convert_from_v’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1100: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1107: error: ‘__convert_from_v’ is not a member of ‘std::std’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1108: error: there are no arguments to ‘_S_get_c_locale’ that depend on a template parameter, so a declaration of ‘_S_get_c_locale’ must be available
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1174: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1182: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _OutIter std::std::num_put<_CharT, _OutIter>::do_put(_OutIter, std::ios_base&, _CharT, bool) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1194: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1195: error: ‘__flags’ was not declared in this scope
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1195: error: incomplete type ‘std::ios_base’ used in nested name specifier
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1204: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1212: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1221: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’
/usr/include/c++/4.1.3/bits/locale_facets.tcc: In member function ‘virtual _OutIter std::std::num_put<_CharT, _OutIter>::do_put(_OutIter, std::ios_base&, _CharT, const void*) const’:
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1282: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1283: error: ‘fmtflags’ in class ‘std::ios_base’ does not name a type
/usr/include/c++/4.1.3/bits/locale_facets.tcc:1286: error: invalid use of undefined type ‘struct std::ios_base’
/usr/include/c++/4.1.3/iosfwd:105: error: forward declaration of ‘struct std::ios_base’

```

---

### Post by dempl_dempl on 2008-02-24
I've had similar problem couple of weeks ago.

What's even funnier, it compiled under  Code::blocks , and not under Kdevelop.

Ask44  looked into my code and said the problem was in the naming of my files.

I had one called string.h [ the same name as one of c++ standard headers  ] .

It seems  that C++ compilers are not great fans of such naming conventions ,  and then they  go haywire with  a truck-load  of errors on console :-)  . 

See if there's any of your CPP/.H  files which have names conflicting with standard headers.

---

### Post by hod139 on 2008-02-24
If the source code isn't too large, could you post that.  If it is too much code, can you post a small fragment that also causes a compiler error.

---

### Post by Fbot1 on 2008-02-24
If nothing else works, try using chroot.

---

### Post by lucasl on 2008-02-25
filenames: game.cpp/.h physics.cpp/.h physicsobject.cpp/.h main.cpp
command to compile: g++ -Wall *.cpp -o main -lchipmunk -lglut
I doubt any of those file names conflict.
Ok, here is the source. The game uses Freeglut and [chipmunk.]("http://wiki.slembcke.net/main/published/Chipmunk") Chipmunk is a 2d physics library. I won't include game.h, physics.h and physicsobject.h.


```

main.cpp:
///////////////
////HEADERS////
///////////////


#include <iostream>
#include <sstream>
#include <GL/freeglut_std.h>
#include <GL/freeglut_ext.h>
#include <cstdlib>
#include <ctime>
#include <vector>
#include <string>
#include <cmath>
#include "chipmunk/chipmunk.h"
#include "game.h"
#include "physics.h"
#include "physicsobject.h"

using namespace std;

///////////////
///CONSTANTS///
///////////////

const int SCREEN_WIDTH = 800;
const int SCREEN_HEIGHT = 600;
const int FPS = 30;

///////////////
////GLOBALS////
///////////////

bool specialKeys[109];
bool keys[256];
extern int mousex, mousey;
int stage = 0;
Game *game;
Physics *physics;
PhysicsObject *man;

///////////////
///PROTOTYPES//
///////////////

void addObjects(void);
void cleanup(void);
void drawText(const unsigned char *text, GLfloat x, GLfloat y, GLfloat r = 55.0f, GLfloat g = 255.0f, GLfloat b = 255.0f, void *font = GLUT_BITMAP_HELVETICA_12);

///////////////
///MAIN LOOP///
///////////////

int main(int argc, char *argv[]) {
	game = new Game(&argc, argv, "Game", SCREEN_WIDTH, SCREEN_HEIGHT, FPS);
	addObjects();
	game->Begin();
	
	
	return 0;
}

///////////////
///FUNCTIONS///
///////////////

void addObjects(void) {
	PhysicsObject *staticObject = physics->CreateStaticObject();
	staticObject->AddLineShape(cpv(0, 0), cpv(SCREEN_WIDTH, 0));
	staticObject->AddLineShape(cpv(SCREEN_WIDTH, 0), cpv(SCREEN_WIDTH, SCREEN_HEIGHT));
	staticObject->AddLineShape(cpv(SCREEN_WIDTH, SCREEN_HEIGHT), cpv(0, SCREEN_HEIGHT));
	staticObject->AddLineShape(cpv(0, SCREEN_HEIGHT), cpv(0, 0));
	physics->InitObject(staticObject);
	if (stage == 0) {
		man = physics->CreateObject(cpv(5, 500), 45);
		man->AddSquareShape(15, 15);
		physics->InitObject(man);
		for (int j = 0; j < 20; j++) {
			for (int i = 0; i < 10; i++) {
				PhysicsObject *obj = physics->CreateObject(cpv(50+j*40, 100+i), 0.001f);
				obj->AddCircleShape(5);
				physics->InitObject(obj);
			}
		}
	} else if (stage == 1) {
	//nothing here yet	
	}
}

void drawText(const unsigned char *text, GLfloat x, GLfloat y, GLfloat r, GLfloat g, GLfloat b, void *font) {
	glPushMatrix();
	glDisable(GL_TEXTURE_2D);
	glColor3f(r, g, b);
    glutBitmapString(font, text);
	glEnable(GL_TEXTURE_2D);
    glPopMatrix();
}

void cleanup() {
	delete game;
	delete physics;
}

physics.cpp (my wrapper for chipmunk)
#include <iostream>
#include <sstream>
#include <GL/freeglut_std.h>
#include <GL/freeglut_ext.h>
#include <cstdlib>
#include <ctime>
#include <vector>
#include <string>
#include <cmath>
#include "chipmunk/chipmunk.h"
#include "physics.h"
#include "physicsobject.h"

using namespace std;

Physics::Physics(cpVect grav, int steps, int iter) {
	cpInitChipmunk();
	
	substeps = steps;
	delta = (1.0f/60.0f) / (cpFloat)substeps;
	
	space = cpSpaceNew();
	space->gravity = grav;
	space->iterations = iter;
}

Physics::~Physics(void) {
	for (unsigned int i = 0; i < objects.size(); i++) delete objects[i];
	//cpSpaceFreeChildren(space);
	cpSpaceFree(space);
}

PhysicsObject *Physics::CreateObject(cpVect pos, cpFloat mass, cpFloat frict, cpFloat elast, cpFloat rot, bool infinteMoment) {
	PhysicsObject *object = new PhysicsObject(false, pos, mass, frict, elast, rot, infinteMoment);
	objects.push_back(object);
	return object;
}

PhysicsObject *Physics::CreateStaticObject(cpVect pos, cpFloat frict, cpFloat elast, cpFloat rot) {
	PhysicsObject *object = new PhysicsObject(true, pos, INFINITY, frict, elast, rot);
	objects.push_back(object);
	return object;
}

void Physics::InitObject(PhysicsObject *object) {
	if (!object->isStatic) {
		if (object->body->i != INFINITY) cpBodySetMoment(object->body, object->moment);
		cpSpaceAddBody(space, object->body);
	}
	for (unsigned int i = 0; i < object->shapes.size(); i++) cpSpaceAddShape(space, object->shapes[i]);
	object->isInit = true;
}

void Physics::DestroyObject(PhysicsObject *object) {
	for (unsigned int i = 0; i < object->shapes.size(); i++) cpSpaceRemoveShape(space, object->shapes[i]);
	cpSpaceRemoveBody(space, object->body);
	delete object;
	for (unsigned int i = 0; i < objects.size(); i++) {
		if (object == objects[i]) {
			objects.erase(objects.begin()+i);
			break;
		}
		if (i == objects.size()-1) printf("Can't find object to be deleted in objects. Ignoring...\n");
	}
}

void Physics::ClearObjects(void) {
	for (unsigned int j = 0; j < objects.size(); j++) {
		PhysicsObject *object = objects[j];
		object->body->v = {0, 0};
		for (unsigned int i = 0; i < object->shapes.size(); i++) cpSpaceRemoveShape(space, object->shapes[i]);
		cpSpaceRemoveBody(space, object->body);
		delete object;
	}
	objects.clear();
	cpResetShapeIdCounter();
}

void Physics::Update(void) {
	for (int i = 0; i < substeps; i++) cpSpaceStep(space, delta);
	for (unsigned int i = 0; i < objects.size(); i++) objects[i]->Update();
}

void Physics::Draw(void) {
	for (unsigned int i = 0; i < objects.size(); i++) objects[i]->Draw();
}

physicsobject.cpp (more of my wrapper for chipmunk)
#include <iostream>
#include <sstream>
#include <GL/freeglut_std.h>
#include <GL/freeglut_ext.h>
#include <cstdlib>
#include <ctime>
#include <vector>
#include <string>
#include <cmath>
#include "chipmunk/chipmunk.h"
#include "physics.h"
#include "physicsobject.h"

using namespace std;

PhysicsObject::PhysicsObject(bool isStaticObj, cpVect pos, cpFloat mass, cpFloat frict, cpFloat elast, cpFloat rot, bool infiniteMoment) {
	isStatic = isStaticObj;
	friction = frict;
	elasticity = elast;
	if (!isStatic) body = cpBodyNew(mass, 0);
	else body = cpBodyNew(INFINITY, INFINITY);
	if (infiniteMoment) cpBodySetMoment(body, INFINITY);
	body->p = pos;
	if (!isStatic) cpBodySetAngle(body, rot);
	isInit = false;
	moment = 0;//this will be added to as shapes are added, then set on Physics::InitObject
}

PhysicsObject::~PhysicsObject(void) {
	for (unsigned int i = 0; i < shapes.size(); i++) cpShapeFree(shapes[i]);
	shapes.clear();
	cpBodyFree(body);
	body = NULL;
}

void PhysicsObject::AddCircleShape(cpFloat radius, cpVect offset) {
	cpShape *shape = cpCircleShapeNew(body, radius, offset);
	shape->e = elasticity;
	shape->u = friction;
	moment += cpMomentForCircle(body->m, radius, radius, offset);
	shapes.push_back(shape);
}

void PhysicsObject::AddSquareShape(cpFloat width, cpFloat height, cpVect offset) {
	cpVect verts[4] = {{width/2, height/2}, {width/2, -height/2}, {-width/2, -height/2}, {-width/2, height/2}};
	cpShape *shape = cpPolyShapeNew(body, 4, verts, offset);
	shape->e = elasticity;
	shape->u = friction;
	moment += cpMomentForPoly(body->m, 4, verts, offset);
	shapes.push_back(shape);
}

void PhysicsObject::AddLineShape(cpVect start, cpVect end, cpFloat thickness) {
	if (!isStatic) {
		printf("Can't add line shape to non-static object.\n");
		return;
	}
	cpShape *shape = cpSegmentShapeNew(body, start, end, thickness);
	shape->e = elasticity;
	shape->u = friction;
	shapes.push_back(shape);
}

void PhysicsObject::AddShape(int numVerts, cpVect *verts, cpVect offset) {
	cpShape *shape = cpPolyShapeNew(body, numVerts, verts, offset);
	shape->e = elasticity;
	shape->u = friction;
	moment += cpMomentForPoly(body->m, numVerts, verts, offset);
	shapes.push_back(shape);
}

void PhysicsObject::Update(void) {
	cpBodyResetForces(body);
}

void PhysicsObject::Draw(void) {
	for (unsigned int i = 0; i < shapes.size(); i++) {
		glPushMatrix();
		glColor3f(0.0f, 0.0f, 0.0f);
		glTranslatef(body->p.x, body->p.y, 0);
		glRotatef(body->a/M_PI*180, 0, 0, 1);
		if (shapes[i]->type == CP_CIRCLE_SHAPE) {
			glTranslatef(((cpCircleShape *)shapes[i])->c.x, ((cpCircleShape *)shapes[i])->c.y, 0);
			glBegin(GL_LINE_LOOP);
			for (int j = 0; j < 32; j++) glVertex2f(cos(2*M_PI/32*j)*((cpCircleShape *)shapes[i])->r, sin(2*M_PI/32*j)*((cpCircleShape *)shapes[i])->r);
		}
		if (shapes[i]->type == CP_SEGMENT_SHAPE) {
			glBegin(GL_LINES);
			glVertex2f(((cpSegmentShape *)shapes[i])->a.x, ((cpSegmentShape *)shapes[i])->a.y);
			glVertex2f(((cpSegmentShape *)shapes[i])->b.x, ((cpSegmentShape *)shapes[i])->b.y);
		}
		if (shapes[i]->type == CP_POLY_SHAPE) {
			glBegin(GL_LINE_LOOP);
			for (int j = 0; j < ((cpPolyShape *)shapes[i])->numVerts; j++) glVertex2f(((cpPolyShape *)shapes[i])->verts[j].x, ((cpPolyShape *)shapes[i])->verts[j].y);
		}
		glEnd();		
		glPopMatrix();
	}
}

game.cpp
#include "game.h"

#include <iostream>

#include <sstream>

#include <GL/freeglut_std.h>

#include <GL/freeglut_ext.h>

#include <cstdlib>

#include <ctime>

#include <vector>

#include <string>



using namespace std;



extern const int SCREEN_WIDTH;

extern const int SCREEN_HEIGHT;

extern const int FPS;

extern bool specialKeys[109];

extern bool keys[256];

extern int stage;

extern Game *game;

extern void cleanup(void);

extern PhysicsObject *man;

extern Physics *physics;

int mousex, mousey;



extern void addObjects(void);



Game::Game(int *argc, char *argv[], const char *title, int width, int height, int framesps, bool fullscreen) {

    glutInit(argc, argv);

	screenWidth = width;

	screenHeight = height;

	fps = framesps;

	windowTitle = title;

	fullScreen = false;//not fullscreenyet

	glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE);

	glutInitWindowSize(screenWidth, screenHeight);

	window = glutCreateWindow(title);

	atexit(cleanup);

	SetFullScreen(fullscreen);//SetFullScreen initializes GL

	physics = new Physics(cpv(0, 900), 5);

	mousex = mousey = 0;

}



Game::~Game(void) {

	if (fullScreen) glutLeaveGameMode();

}



void Game::UpdateCB(int value) {game->Update(value);}

void Game::DrawCB(void) {game->Draw();}

void Game::EventKeyDownCB(unsigned char key, int x, int y) {game->EventKeyDown(key, x, y);}

void Game::EventSpecialKeyDownCB(int key, int x, int y) {game->EventSpecialKeyDown(key, x, y);}

void Game::EventKeyUpCB(unsigned char key, int x, int y) {game->EventKeyUp(key, x, y);}

void Game::EventSpecialKeyUpCB(int key, int x, int y) {game->EventSpecialKeyUp(key, x, y);}

void Game::EventMouseMoveCB(int x, int y) {game->EventMouseMove(x, y);}



void Game::InitGL(int width, int height, int framesps) {

	glutDisplayFunc(DrawCB);

	glutKeyboardFunc(EventKeyDownCB);

	glutKeyboardUpFunc(EventKeyUpCB);

	glutTimerFunc(1000/fps, UpdateCB, 0);

	glutSpecialFunc(EventSpecialKeyDownCB);

	glutSpecialUpFunc(EventSpecialKeyUpCB);

	glutMotionFunc(EventMouseMoveCB);

	glutPassiveMotionFunc(EventMouseMoveCB);

	

	glClearColor(255.0f, 255.0f, 255.0f, 0.0f);

	glMatrixMode(GL_PROJECTION);

	glLoadIdentity();

	glOrtho(0, screenWidth, screenHeight, 0, -1, 0);

	glMatrixMode(GL_MODELVIEW);

	glLoadIdentity();

	glDisable(GL_DEPTH_TEST);

}



void Game::Begin(void) {

	glutMainLoop();

}



void Game::SetFullScreen(bool state) {

	if (fullScreen != state) {

		if (state == true) {

			if (glutGameModeGet(GLUT_GAME_MODE_POSSIBLE)) {

   				stringstream ss;

  				ss << screenWidth << "x" << screenHeight;

				string gameModeString;

				ss >> gameModeString;

				glutGameModeString(gameModeString.c_str());

				glutEnterGameMode();

		} else cout << "Can't enter game mode - Impossible." << endl;

		} else {

			glutLeaveGameMode();

			glutDestroyWindow(window);

			window = glutCreateWindow(windowTitle.c_str());

		}

	}

	fullScreen = state;

	InitGL(screenWidth, screenHeight, fps);

}



void Game::Draw(void) {

	glClear(GL_COLOR_BUFFER_BIT);

	physics->Draw();

	glutSwapBuffers();

}





void Game::EventKeyDown(unsigned char key, int x, int y) {

	keys[key] = true;

	if (key == 'q' or key == 27) {

		  glutDestroyWindow(window);

		  exit(0);

    }

    if (key == ' ') {

    	PhysicsObject *obj = physics->CreateObject(cpv(350, 100), 300);

		obj->AddSquareShape(100, 50);

		physics->InitObject(obj);

    }

    if (key == 'v') {

    	physics->ClearObjects();

    	addObjects();

    }

    if (key == 'c') {

    	for (int i = 0; i < 10; i++) {

			PhysicsObject *obj = physics->CreateObject(cpv(400, 100+i), 1);

			obj->AddCircleShape(5);

			physics->InitObject(obj);

		}

    }

    if (key == '1') stage = 0;

    if (key == '2') stage = 1;

}



void Game::EventKeyUp(unsigned char key, int x, int y) {

	keys[key] = false;

}



void Game::EventSpecialKeyDown(int key, int x, int y) {

	specialKeys[key] = true;

	if (key == GLUT_KEY_F1) SetFullScreen(!fullScreen);

}



void Game::EventSpecialKeyUp(int key, int x, int y) {

	specialKeys[key] = false;

}



void Game::EventMouseMove(int x, int y) {

	mousex = x;

	mousey = y;

}



void Game::Update(int value) {

	glutPostRedisplay();

	if (specialKeys[GLUT_KEY_LEFT]) man->Force(cpv(-1000*man->GetMass(), 0));

	if (specialKeys[GLUT_KEY_RIGHT]) man->Force(cpv(1000*man->GetMass(), 0));

	if (specialKeys[GLUT_KEY_UP] and man->GetVelocity().y < 0.1 and man->GetVelocity().y > -0.1) man->Impulse(cpv(0, -50000*man->GetMass()));

	physics->Update();

	glutTimerFunc(1000/fps, UpdateCB, 0);

}


```

I've probably made thousands of stylistic mistakes, but I've compiled the code without errors before.

Thanks!
Lucas

EDIT: I've just discovered that the compiler seems to think that the custom types and classes (eg. PhysicsObject) are part of the std namespace. Not sure why.

---

### Post by lucasl on 2008-02-25
After looking through my stl_alg.h file, I noticed it didn't end. Well it did, but with this line:
```
  template<typename _ForwardIterator, typename _Predicate>
    _ForwardIterator
    __partition(_ForwardIterator __first, _ForwardIterator __last,
		_Predicate __pred,
		forward_iterator_
```

I reinstalled libstdc++dev (or whatever it is called) and it now works like a charm.

---

