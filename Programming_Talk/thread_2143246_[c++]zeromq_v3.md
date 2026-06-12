---
title: "[c++]zeromq v3"
date: 2013-05-08
forum: Programming Talk
---

### Post by giane on 2013-05-08
Hi all i'm new on the international form but i write some message on italian ubuntu forum.
I'm learning the zeromq framework but i have some problem when i'm testing the examples in c++.
I already test the correct installation using the example in c and java. But when i try to compile the c++ example i obtain the folowing error
```
/usr/lib/gcc/i686-linux-gnu/4.7/include/stddef.h:213:23: note:   ‘size_t’
In file included from /usr/include/c++/4.7/ext/new_allocator.h:34:0,
                 from /usr/include/i386-linux-gnu/c++/4.7/./bits/c++allocator.h:34,
                 from /usr/include/c++/4.7/bits/allocator.h:48,
                 from /usr/include/c++/4.7/string:43,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/new:113:42: error: expected primary-expression before ‘void’
In file included from /usr/include/i386-linux-gnu/c++/4.7/./bits/c++allocator.h:34:0,
                 from /usr/include/c++/4.7/bits/allocator.h:48,
                 from /usr/include/c++/4.7/string:43,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/ext/new_allocator.h:42:14: error: ‘std::size_t’ has not been declared
/usr/include/c++/4.7/ext/new_allocator.h:43:14: error: ‘std::ptrdiff_t’ has not been declared
/usr/include/c++/4.7/ext/new_allocator.h:58:15: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.7/string:43:0,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/allocator.h:72:15: error: ‘ptrdiff_t’ does not name a type
/usr/include/c++/4.7/bits/allocator.h:93:15: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.7/string:46:0,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/ostream_insert.h:45:26: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/ostream_insert.h: In function ‘void std::__ostream_write(std::basic_ostream<_CharT, _Traits>&, const _CharT*, int)’:
/usr/include/c++/4.7/bits/ostream_insert.h:50:13: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ostream_insert.h:51:11: error: ‘__put’ was not declared in this scope
/usr/include/c++/4.7/bits/ostream_insert.h: At global scope:
/usr/include/c++/4.7/bits/ostream_insert.h:57:59: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/ostream_insert.h:77:27: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/ostream_insert.h: In function ‘std::basic_ostream<_CharT, _Traits>& std::__ostream_insert(std::basic_ostream<_CharT, _Traits>&, const _CharT*, int)’:
/usr/include/c++/4.7/bits/ostream_insert.h:87:14: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ostream_insert.h:88:12: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.7/bits/ostream_insert.h: At global scope:
/usr/include/c++/4.7/bits/ostream_insert.h:118:68: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/ostream_insert.h:122:11: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.7/string:55:0,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/basic_string.tcc: In function ‘std::basic_istream<_CharT, _Traits>& std:operator>>(std::basic_istream<_CharT, _Traits>&, std::basic_string<_CharT, _Traits, _Alloc>&)’:
/usr/include/c++/4.7/bits/basic_string.tcc:1020:14: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/basic_string.tcc:1021:32: error: ‘__w’ was not declared in this scope
In file included from /usr/include/c++/4.7/string:54:0,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/basic_string.h: In instantiation of ‘class std::basic_string<char>’:
/usr/include/c++/4.7/bits/basic_string.tcc:1134:25:   required from here
/usr/include/c++/4.7/bits/basic_string.h:119:61: error: no type named ‘difference_type’ in ‘std::basic_string<char>::_CharT_alloc_type {aka class std::allocator<char>}’
/usr/include/c++/4.7/bits/basic_string.h: In instantiation of ‘class std::basic_string<wchar_t>’:
/usr/include/c++/4.7/bits/basic_string.tcc:1149:25:   required from here
/usr/include/c++/4.7/bits/basic_string.h:119:61: error: no type named ‘difference_type’ in ‘std::basic_string<wchar_t>::_CharT_alloc_type {aka class std::allocator<wchar_t>}’
In file included from /usr/include/c++/4.7/ios:43:0,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/ios_base.h: At global scope:
/usr/include/c++/4.7/bits/ios_base.h:454:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ios_base.h:455:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ios_base.h:622:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ios_base.h:631:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ios_base.h:645:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/ios_base.h:654:5: error: ‘streamsize’ does not name a type
In file included from /usr/include/c++/4.7/ios:44:0,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/streambuf:51:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:144:14: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:236:33: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/streambuf:280:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:353:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:446:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:588:26: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/streambuf:645:15: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:661:15: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:738:15: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:791:20: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/streambuf:794:20: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/streambuf:812:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/streambuf:817:5: error: ‘streamsize’ does not name a type
In file included from /usr/include/c++/4.7/streambuf:825:0,
                 from /usr/include/c++/4.7/ios:44,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/streambuf.tcc:45:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf.tcc:79:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf.tcc:116:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf.tcc:139:12: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf.tcc:152:5: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.7/bits/streambuf.tcc:153:5: error: expected ‘;’ before ‘__copy_streambufs’
/usr/include/c++/4.7/bits/streambuf.tcc:156:5: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.7/bits/streambuf.tcc:157:5: error: expected ‘;’ before ‘__copy_streambufs_eof’
/usr/include/c++/4.7/bits/streambuf.tcc:163:5: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.7/bits/streambuf.tcc:164:5: error: expected ‘;’ before ‘__copy_streambufs’
/usr/include/c++/4.7/bits/streambuf.tcc:167:5: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.7/bits/streambuf.tcc:168:5: error: expected ‘;’ before ‘__copy_streambufs_eof’
In file included from /usr/include/c++/4.7/bits/locale_facets.h:50:0,
                 from /usr/include/c++/4.7/bits/basic_ios.h:39,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/streambuf_iterator.h:59:16: error: wrong number of template arguments (5, should be 3)
In file included from /usr/include/c++/4.7/bits/stl_algobase.h:66:0,
                 from /usr/include/c++/4.7/bits/char_traits.h:41,
                 from /usr/include/c++/4.7/string:42,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/stl_iterator_base_types.h:119:12: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
In file included from /usr/include/c++/4.7/bits/locale_facets.h:50:0,
                 from /usr/include/c++/4.7/bits/basic_ios.h:39,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/streambuf_iterator.h:219:66: error: wrong number of template arguments (5, should be 3)
In file included from /usr/include/c++/4.7/bits/stl_algobase.h:66:0,
                 from /usr/include/c++/4.7/bits/char_traits.h:41,
                 from /usr/include/c++/4.7/string:42,
                 from hwserver.cpp:7:
/usr/include/c++/4.7/bits/stl_iterator_base_types.h:119:12: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
In file included from /usr/include/c++/4.7/bits/locale_facets.h:50:0,
                 from /usr/include/c++/4.7/bits/basic_ios.h:39,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/streambuf_iterator.h:281:34: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char<_CharT>::__value, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> > >::__type std::__copy_move_a2(_CharT*, _CharT*, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> >)’:
/usr/include/c++/4.7/bits/streambuf_iterator.h:315:13: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf_iterator.h:316:11: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.7/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char<_CharT>::__value, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> > >::__type std::__copy_move_a2(const _CharT*, const _CharT*, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> >)’:
/usr/include/c++/4.7/bits/streambuf_iterator.h:327:13: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf_iterator.h:328:11: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.7/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char<_CharT>::__value, _CharT*>::__type std::__copy_move_a2(std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, _CharT*)’:
/usr/include/c++/4.7/bits/streambuf_iterator.h:350:14: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/streambuf_iterator.h:351:12: error: ‘__n’ was not declared in this scope
/usr/include/c++/4.7/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char<_CharT2>::__value, std::istreambuf_iterator<_CharT> >::__type std::find(std::istreambuf_iterator<_CharT>, std::istreambuf_iterator<_CharT>, const _CharT2&)’:
/usr/include/c++/4.7/bits/streambuf_iterator.h:387:8: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/streambuf_iterator.h:387:19: error: expected ‘;’ before ‘__n’
/usr/include/c++/4.7/bits/streambuf_iterator.h:388:12: error: ‘__n’ was not declared in this scope
In file included from /usr/include/c++/4.7/bits/basic_ios.h:39:0,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/locale_facets.h: At global scope:
/usr/include/c++/4.7/bits/locale_facets.h:94:29: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/locale_facets.h:94:50: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.7/bits/basic_ios.h:39:0,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/locale_facets.h:2448:32: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.7/bits/locale_facets.h:2607:0,
                 from /usr/include/c++/4.7/bits/basic_ios.h:39,
                 from /usr/include/c++/4.7/ios:45,
                 from /usr/include/c++/4.7/ostream:40,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/locale_facets.tcc:777:27: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/locale_facets.tcc: In member function ‘_OutIter std::num_put<_CharT, _OutIter>::_M_insert_int(_OutIter, std::ios_base&, _CharT, _ValueT) const’:
/usr/include/c++/4.7/bits/locale_facets.tcc:918:8: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/locale_facets.tcc:919:6: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:919:24: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:919:24: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:919:24: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:919:24: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:920:4: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.7/bits/locale_facets.tcc: In member function ‘_OutIter std::num_put<_CharT, _OutIter>::_M_insert_float(_OutIter, std::ios_base&, _CharT, char, _ValueT) const’:
/usr/include/c++/4.7/bits/locale_facets.tcc:981:8: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/locale_facets.tcc:998:19: error: ‘__prec’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1056:6: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1056:17: error: expected ‘;’ before ‘__off’
/usr/include/c++/4.7/bits/locale_facets.tcc:1059:3: error: ‘__off’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1065:45: error: ‘__off’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1073:8: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/locale_facets.tcc:1074:6: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1074:24: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1074:24: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1074:24: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1074:24: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1075:4: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.7/bits/locale_facets.tcc: In member function ‘virtual _OutIter std::num_put<_CharT, _OutIter>::do_put(std::num_put<_CharT, _OutIter>::iter_type, std::ios_base&, std::num_put<_CharT, _OutIter>::char_type, bool) const’:
/usr/include/c++/4.7/bits/locale_facets.tcc:1111:10: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/locale_facets.tcc:1112:8: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1112:26: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1112:26: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1112:26: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.7/bits/locale_facets.tcc:1112:26: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/locale_facets.tcc:1113:6: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.7/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.7/bits/locale_facets.tcc:1195:8: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/locale_facets.tcc:1195:29: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.7/iostream:40:0,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/ostream:309:38: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/ostream:333:35: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/ostream: In member function ‘void std::basic_ostream<_CharT, _Traits>::_M_write(const char_type*, int)’:
/usr/include/c++/4.7/ostream:311:8: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/ostream:312:6: error: ‘__put’ was not declared in this scope
/usr/include/c++/4.7/ostream: In function ‘std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)’:
/usr/include/c++/4.7/ostream:517:17: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.7/ostream:517:17: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.7/ostream:517:17: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.7/ostream:517:17: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/ostream: In function ‘std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)’:
/usr/include/c++/4.7/ostream:534:17: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.7/ostream:534:17: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.7/ostream:534:17: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.7/ostream:534:17: error: ‘streamsize’ was not declared in this scope
In file included from /usr/include/c++/4.7/ostream:607:0,
                 from /usr/include/c++/4.7/iostream:40,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/ostream.tcc: At global scope:
/usr/include/c++/4.7/bits/ostream.tcc:185:30: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.7/iostream:41:0,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/istream:80:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/istream:266:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/istream:341:27: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:352:27: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:414:31: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:425:31: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:449:7: error: expected ‘;’ at end of member declaration
/usr/include/c++/4.7/istream:449:25: error: expected ‘)’ before ‘__n’
/usr/include/c++/4.7/istream:452:7: error: expected ‘;’ at end of member declaration
/usr/include/c++/4.7/istream:452:14: error: redeclaration of ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.7/istream:449:14: note: previous declaration ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.7/istream:452:25: error: expected ‘)’ before ‘__n’
/usr/include/c++/4.7/istream:455:14: error: ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore()’ conflicts with a previous declaration
/usr/include/c++/4.7/istream:449:14: note: previous declaration ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.7/istream:484:28: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:502:7: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/istream: In constructor ‘std::basic_istream<_CharT, _Traits>::basic_istream(std::basic_istream<_CharT, _Traits>::__streambuf_type*)’:
/usr/include/c++/4.7/istream:92:9: error: class ‘std::basic_istream<_CharT, _Traits>’ does not have any field named ‘_M_gcount’
/usr/include/c++/4.7/istream:92:31: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available [-fpermissive]
/usr/include/c++/4.7/istream:92:31: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/include/c++/4.7/istream: In destructor ‘virtual std::basic_istream<_CharT, _Traits>::~basic_istream()’:
/usr/include/c++/4.7/istream:102:9: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/istream:102:33: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available [-fpermissive]
/usr/include/c++/4.7/istream: In constructor ‘std::basic_istream<_CharT, _Traits>::basic_istream()’:
/usr/include/c++/4.7/istream:605:9: error: class ‘std::basic_istream<_CharT, _Traits>’ does not have any field named ‘_M_gcount’
/usr/include/c++/4.7/istream:605:31: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available [-fpermissive]
/usr/include/c++/4.7/istream: In instantiation of ‘class std::basic_istream<char>’:
/usr/include/c++/4.7/istream:616:24:   required from here
/usr/include/c++/4.7/istream:449:14: error: ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore() [with _CharT = char; _Traits = std::char_traits<char>; std::basic_istream<_CharT, _Traits>::__istream_type = std::basic_istream<char>]’ conflicts with a previous declaration
/usr/include/c++/4.7/istream:449:14: note: previous declaration ‘std::basic_istream<char>::__istream_type& std::basic_istream<char>::ignore’
/usr/include/c++/4.7/istream: At global scope:
/usr/include/c++/4.7/istream:617:29: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:622:12: error: ‘std::basic_istream<char>& std::basic_istream<char>::ignore’ is not a static member of ‘class std::basic_istream<char>’
/usr/include/c++/4.7/istream:622:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/istream:627:12: error: ‘std::basic_istream<char>& std::basic_istream<char>::ignore’ is not a static member of ‘class std::basic_istream<char>’
/usr/include/c++/4.7/istream:627:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/istream:627:37: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.7/istream:627:44: error: expression list treated as compound expression in initializer [-fpermissive]
/usr/include/c++/4.7/istream: In instantiation of ‘class std::basic_istream<wchar_t>’:
/usr/include/c++/4.7/istream:632:27:   required from here
/usr/include/c++/4.7/istream:449:14: error: ‘std::basic_istream<_CharT, _Traits>::__istream_type& std::basic_istream<_CharT, _Traits>::ignore() [with _CharT = wchar_t; _Traits = std::char_traits<wchar_t>; std::basic_istream<_CharT, _Traits>::__istream_type = std::basic_istream<wchar_t>]’ conflicts with a previous declaration
/usr/include/c++/4.7/istream:449:14: note: previous declaration ‘std::basic_istream<wchar_t>::__istream_type& std::basic_istream<wchar_t>::ignore’
/usr/include/c++/4.7/istream:633:29: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/istream:638:12: error: ‘std::basic_istream<wchar_t>& std::basic_istream<wchar_t>::ignore’ is not a static member of ‘class std::basic_istream<wchar_t>’
/usr/include/c++/4.7/istream:638:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/istream:643:12: error: ‘std::basic_istream<wchar_t>& std::basic_istream<wchar_t>::ignore’ is not a static member of ‘class std::basic_istream<wchar_t>’
/usr/include/c++/4.7/istream:643:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/istream:643:37: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.7/istream:643:44: error: expression list treated as compound expression in initializer [-fpermissive]
In file included from /usr/include/c++/4.7/istream:873:0,
                 from /usr/include/c++/4.7/iostream:41,
                 from hwserver.cpp:8:
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>::int_type std::basic_istream<_CharT, _Traits>::get()’:
/usr/include/c++/4.7/bits/istream.tcc:242:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(std::basic_istream<_CharT, _Traits>::char_type&)’:
/usr/include/c++/4.7/bits/istream.tcc:276:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: At global scope:
/usr/include/c++/4.7/bits/istream.tcc:311:25: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(std::basic_istream<_CharT, _Traits>::char_type*, int, std::basic_istream<_CharT, _Traits>::char_type)’:
/usr/include/c++/4.7/bits/istream.tcc:313:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(std::basic_istream<_CharT, _Traits>::__streambuf_type&, std::basic_istream<_CharT, _Traits>::char_type)’:
/usr/include/c++/4.7/bits/istream.tcc:360:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: At global scope:
/usr/include/c++/4.7/bits/istream.tcc:402:29: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(std::basic_istream<_CharT, _Traits>::char_type*, int, std::basic_istream<_CharT, _Traits>::char_type)’:
/usr/include/c++/4.7/bits/istream.tcc:404:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore()’:
/usr/include/c++/4.7/bits/istream.tcc:464:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: At global scope:
/usr/include/c++/4.7/bits/istream.tcc:495:12: error: ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’ is not a static member of ‘class std::basic_istream<_CharT, _Traits>’
/usr/include/c++/4.7/bits/istream.tcc:495:12: error: template definition of non-template ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.7/bits/istream.tcc:495:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:557:12: error: ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’ is not a static member of ‘class std::basic_istream<_CharT, _Traits>’
/usr/include/c++/4.7/bits/istream.tcc:557:12: error: template definition of non-template ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.7/bits/istream.tcc:557:12: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:557:37: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>::int_type std::basic_istream<_CharT, _Traits>::peek()’:
/usr/include/c++/4.7/bits/istream.tcc:625:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: At global scope:
/usr/include/c++/4.7/bits/istream.tcc:652:26: error: ‘streamsize’ has not been declared
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::read(std::basic_istream<_CharT, _Traits>::char_type*, int)’:
/usr/include/c++/4.7/bits/istream.tcc:654:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: At global scope:
/usr/include/c++/4.7/bits/istream.tcc:679:5: error: ‘streamsize’ does not name a type
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::putback(std::basic_istream<_CharT, _Traits>::char_type)’:
/usr/include/c++/4.7/bits/istream.tcc:717:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::unget()’:
/usr/include/c++/4.7/bits/istream.tcc:752:7: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc: In function ‘std::basic_istream<_CharT, _Traits>& std::operator>>(std::basic_istream<_CharT, _Traits>&, _CharT2*)’:
/usr/include/c++/4.7/bits/istream.tcc:965:7: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:965:18: error: expected ‘;’ before ‘__extracted’
/usr/include/c++/4.7/bits/istream.tcc:973:19: error: expected ‘;’ before ‘__num’
/usr/include/c++/4.7/bits/istream.tcc:974:12: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:975:49: error: type/value mismatch at argument 1 in template parameter list for ‘template<class _Value> struct __gnu_cxx::__numeric_traits’
/usr/include/c++/4.7/bits/istream.tcc:975:49: error:   expected a type, got ‘streamsize’
/usr/include/c++/4.7/bits/istream.tcc:983:15: error: ‘__extracted’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:983:29: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.7/bits/istream.tcc:1008:12: error: ‘__extracted’ was not declared in this scope
hwserver.cpp: In function ‘int main()’:
hwserver.cpp:17:5: error: ‘zmq’ has not been declared
hwserver.cpp:17:20: error: expected ‘;’ before ‘context’
hwserver.cpp:18:5: error: ‘zmq’ has not been declared
hwserver.cpp:18:19: error: expected ‘;’ before ‘socket’
hwserver.cpp:19:5: error: ‘socket’ was not declared in this scope
hwserver.cpp:22:9: error: ‘zmq’ has not been declared
hwserver.cpp:22:24: error: expected ‘;’ before ‘request’
hwserver.cpp:25:23: error: ‘request’ was not declared in this scope
hwserver.cpp:36:9: error: ‘zmq’ has not been declared
hwserver.cpp:36:24: error: expected ‘;’ before ‘reply’
hwserver.cpp:37:26: error: ‘reply’ was not declared in this scope
hwserver.cpp:37:51: error: ‘memcpy’ was not declared in this scope
```
I'm using g++ version 4.7 and ubuntu 12.04 for compile i'm using the following command.
```

g++ hwserver.cpp -o hwserver -lzmq

```
Thanks in advance and sorry for my english. i hope that someone help me.

---

### Post by SledgeHammer_999 on 2013-05-08
Can you post the hwserver.cpp?

---

### Post by giane on 2013-05-08
yes but i  don't think that the problem is the program because is a standard example 
```

[COLOR=#000000][FONT=Andale Mono][COLOR=#BC7A00]//
//  Hello World server in C++
//  Binds REP socket to tcp://*:5555
//  Expects "Hello" from client, replies with "World"
//
#include <zmq.hpp>
#include <string>
#include <iostream>
#include <unistd.h>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono][COLOR=#B00040]int[/COLOR] main () {
    [COLOR=#408080]*//  Prepare our context and socket*[/COLOR]
    zmq[COLOR=#666666]::[/COLOR]context_t context ([COLOR=#666666]1[/COLOR]);
    zmq[COLOR=#666666]::[/COLOR]socket_t socket (context, ZMQ_REP);
    socket.bind ([COLOR=#BA2121]"tcp://*:5555"[/COLOR]);[/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono]    [COLOR=#008000]**while**[/COLOR] ([COLOR=#008000]**true**[/COLOR]) {
        zmq[COLOR=#666666]::[/COLOR]message_t request;[/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono]        [COLOR=#408080]*//  Wait for next request from client*[/COLOR]
        socket.recv ([COLOR=#666666]&[/COLOR]request);
        std[COLOR=#666666]::[/COLOR]cout [COLOR=#666666]<<[/COLOR] [COLOR=#BA2121]"Received Hello"[/COLOR] [COLOR=#666666]<<[/COLOR] std[COLOR=#666666]::[/COLOR]endl;[/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono]        [COLOR=#408080]*//  Do some 'work'*[/COLOR]
        sleep ([COLOR=#666666]1[/COLOR]);[/FONT][/COLOR]
[COLOR=#000000][FONT=Andale Mono]        [COLOR=#408080]*//  Send reply back to client*[/COLOR]
        zmq[COLOR=#666666]::[/COLOR]message_t reply ([COLOR=#666666]5[/COLOR]);
        memcpy (([COLOR=#B00040]void[/COLOR] [COLOR=#666666]*[/COLOR]) reply.data (), [COLOR=#BA2121]"World"[/COLOR], [COLOR=#666666]5[/COLOR]);
        socket.send (reply);
    }
    [COLOR=#008000]**return**[/COLOR] [COLOR=#666666]0[/COLOR];
}

```[/FONT][/COLOR]

---

### Post by dwhitney67 on 2013-05-08
> **giane said:**
> 
I'm using g++ version 4.7 and ubuntu 12.04 for compile i'm using the following command.
```

g++ hwserver.cpp -o hwserver -lzmq

```
Thanks in advance and sorry for my english. i hope that someone help me.

I had no trouble compiling the example source code program you provided.

I tried on both a 64-bit and 32-bit system, each running Kubuntu 12.04 with GCC version 4.6.3, and with ZeroMQ 2.1.11-1ubuntu1 (this correlates with library with version 1.0.0).

---

### Post by giane on 2013-05-09
sorry i don't specify wich version of zmq i'm using.
I use the last version of zmq downloaded from zmq site and i install it whit the command
```

./configure --prefix=/usr/ --whit-cpp
make
sudo make install
sudo ldconfig

```

---

### Post by spjackson on 2013-05-09
I note that the errors you are getting are in the g++ 4.7 headers. How did you install g++ 4.7?


Can you build the simplest "hello world" using iostream? If you can, then possibly try moving 
```

#include <zmq.hpp>

```
after the compiler headers.

---

### Post by giane on 2013-05-09
I solved the problem, I'm an idiot when i download zmq.hpp from github i'm using "Save link as" option from the browser that download zmq.hpp with html tag ](*,)
I download the zip file and copy zmq.hpp in /usr/include/ folder and now all work.
thank you for the support.

---

