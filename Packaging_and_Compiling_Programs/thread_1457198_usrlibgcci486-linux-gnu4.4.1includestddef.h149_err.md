---
title: "/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stddef.h:149: error"
date: 2010-04-18
forum: Packaging and Compiling Programs
---

### Post by Fabzil on 2010-04-18
Hello everyone !


Im doing a project with friends for the university, and the programm compile just fine on their computer, but on mine, I got some really fancy errors...

```

$ make
rm -rf *.o
g++ -o PartieGTP.o -c ./Expertbot/GTP/PartieGTP.cpp 
g++ -o IaUTC.o -c ./UTC/IaUTC.cpp -lpthread
./UTC/IaUTC.cpp: In constructor ‘IaUTC::IaUTC(Goban*, char)’:
./UTC/IaUTC.cpp:19: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
./UTC/IaUTC.cpp:19: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
./UTC/IaUTC.cpp: In constructor ‘IaUTC::IaUTC(Goban*, char, int)’:
./UTC/IaUTC.cpp:46: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
./UTC/IaUTC.cpp:46: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
g++ -o Goban.o -c ./Expertbot/Goban.cpp
g++ -o arbreUTC.o -c ./UTC/arbreUTC.cpp
g++ -o noeudUTC.o -c ./UTC/noeudUTC.cpp
g++ -o Groupe.o -c ./Expertbot/Groupe.cpp
g++ -o all2.o -c ./Expertbot/all2.cpp
g++ -o all3.o -c ./UTC/all3.cpp
g++ -o bordel.o -c ./Expertbot/bordel.cpp
g++ -o Intersection.o -c ./Expertbot/Intersection.cpp
g++ -o listeChaineeUTC.o -c ./UTC/listeChaineeUTC.cpp
In file included from /usr/include/c++/4.4/cstddef:44,
                 from /usr/include/c++/4.4/bits/stl_algobase.h:61,
                 from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stddef.h:149: error: expected constructor, destructor, or type conversion before ‘typedef’
In file included from /usr/include/c++/4.4/bits/stl_algobase.h:61,
                 from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/cstddef:51: error: ‘::ptrdiff_t’ has not been declared
In file included from /usr/include/c++/4.4/bits/stl_algobase.h:67,
                 from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:102: error: expected type-specifier before ‘ptrdiff_t’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:102: error: expected ‘>’ before ‘ptrdiff_t’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:113: error: ‘_Pointer’ does not name a type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:115: error: ‘_Reference’ does not name a type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:139: error: ‘ptrdiff_t’ does not name a type
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:149: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/bits/stl_algobase.h:69,
                 from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_iterator.h:95: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
/usr/include/c++/4.4/bits/stl_iterator.h:390: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
/usr/include/c++/4.4/bits/stl_iterator.h:474: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
/usr/include/c++/4.4/bits/stl_iterator.h:561: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
In file included from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_algobase.h: In static member function ‘static _Tp* std::__copy_move_backward<_IsMove, true, std::random_access_iterator_tag>::__copy_move_b(const _Tp*, const _Tp*, _Tp*)’:
/usr/include/c++/4.4/bits/stl_algobase.h:574: error: ‘ptrdiff_t’ does not name a type
/usr/include/c++/4.4/bits/stl_algobase.h:575: error: ‘_Num’ was not declared in this scope
In file included from /usr/include/c++/4.4/i486-linux-gnu/bits/c++allocator.h:34,
                 from /usr/include/c++/4.4/bits/allocator.h:48,
                 from /usr/include/c++/4.4/vector:62,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/ext/new_allocator.h: At global scope:
/usr/include/c++/4.4/ext/new_allocator.h:40: error: ‘std::ptrdiff_t’ has not been declared
/usr/include/c++/4.4/ext/new_allocator.h:55: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/vector:62,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/allocator.h:68: error: ‘ptrdiff_t’ does not name a type
/usr/include/c++/4.4/bits/allocator.h:90: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/vector:65,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_vector.h:192: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/vector:66,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_bvector.h:108: error: template argument 3 is invalid
/usr/include/c++/4.4/bits/stl_bvector.h:137: error: ‘ptrdiff_t’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘void std::_Bit_iterator_base::_M_incr(int)’:
/usr/include/c++/4.4/bits/stl_bvector.h:139: error: ‘difference_type’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h:139: error: expected ‘;’ before ‘__n’
/usr/include/c++/4.4/bits/stl_bvector.h:140: error: ‘__n’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h: At global scope:
/usr/include/c++/4.4/bits/stl_bvector.h:179: error: expected initializer before ‘operator’
/usr/include/c++/4.4/bits/stl_bvector.h:231: error: declaration of ‘operator+=’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:231: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/bits/stl_bvector.h:237: error: expected ‘;’ before ‘iterator’
/usr/include/c++/4.4/bits/stl_bvector.h:238: error: declaration of ‘operator-=’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:238: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/bits/stl_bvector.h:244: error: expected ‘;’ before ‘iterator’
/usr/include/c++/4.4/bits/stl_bvector.h:245: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h:252: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h:259: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘std::_Bit_iterator std::_Bit_iterator::operator+(int) const’:
/usr/include/c++/4.4/bits/stl_bvector.h:248: error: no match for ‘operator+=’ in ‘__tmp += __i’
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘std::_Bit_iterator std::_Bit_iterator::operator-(int) const’:
/usr/include/c++/4.4/bits/stl_bvector.h:255: error: no match for ‘operator-=’ in ‘__tmp -= __i’
/usr/include/c++/4.4/bits/stl_bvector.h: At global scope:
/usr/include/c++/4.4/bits/stl_bvector.h:264: error: declaration of ‘operator+’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:264: error: ‘ptrdiff_t’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h:264: error: expected primary-expression before ‘const’
/usr/include/c++/4.4/bits/stl_bvector.h:317: error: declaration of ‘operator+=’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:317: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/bits/stl_bvector.h:323: error: expected ‘;’ before ‘const_iterator’
/usr/include/c++/4.4/bits/stl_bvector.h:324: error: declaration of ‘operator-=’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:324: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/bits/stl_bvector.h:330: error: expected ‘;’ before ‘const_iterator’
/usr/include/c++/4.4/bits/stl_bvector.h:331: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h:338: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h:345: error: ‘difference_type’ has not been declared
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘std::_Bit_const_iterator std::_Bit_const_iterator::operator+(int) const’:
/usr/include/c++/4.4/bits/stl_bvector.h:334: error: no match for ‘operator+=’ in ‘__tmp += __i’
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘std::_Bit_const_iterator std::_Bit_const_iterator::operator-(int) const’:
/usr/include/c++/4.4/bits/stl_bvector.h:341: error: no match for ‘operator-=’ in ‘__tmp -= __i’
/usr/include/c++/4.4/bits/stl_bvector.h: At global scope:
/usr/include/c++/4.4/bits/stl_bvector.h:350: error: declaration of ‘operator+’ as non-function
/usr/include/c++/4.4/bits/stl_bvector.h:350: error: ‘ptrdiff_t’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h:350: error: expected primary-expression before ‘const’
/usr/include/c++/4.4/bits/stl_bvector.h:481: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/bits/stl_algobase.h:67,
                 from /usr/include/c++/4.4/vector:61,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_iterator_base_types.h: In instantiation of ‘std::iterator_traits<std::_Bit_iterator>’:
/usr/include/c++/4.4/bits/stl_iterator.h:103:   instantiated from ‘std::reverse_iterator<std::_Bit_iterator>’
/usr/include/c++/4.4/bits/stl_bvector.h:622:   instantiated from here
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:127: error: no type named ‘iterator_category’ in ‘struct std::_Bit_iterator’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:128: error: no type named ‘value_type’ in ‘struct std::_Bit_iterator’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:129: error: no type named ‘difference_type’ in ‘struct std::_Bit_iterator’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h: In instantiation of ‘std::iterator_traits<std::_Bit_const_iterator>’:
/usr/include/c++/4.4/bits/stl_iterator.h:103:   instantiated from ‘std::reverse_iterator<std::_Bit_const_iterator>’
/usr/include/c++/4.4/bits/stl_bvector.h:626:   instantiated from here
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:127: error: no type named ‘iterator_category’ in ‘struct std::_Bit_const_iterator’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:128: error: no type named ‘value_type’ in ‘struct std::_Bit_const_iterator’
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:129: error: no type named ‘difference_type’ in ‘struct std::_Bit_const_iterator’
In file included from /usr/include/c++/4.4/vector:66,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘size_t std::vector<bool, _Alloc>::max_size() const’:
/usr/include/c++/4.4/bits/stl_bvector.h:662: error: ‘difference_type’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h:662: error: template argument 1 is invalid
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘std::_Bit_iterator std::vector<bool, _Alloc>::insert(std::_Bit_iterator, const bool&)’:
/usr/include/c++/4.4/bits/stl_bvector.h:775: error: ‘difference_type’ does not name a type
/usr/include/c++/4.4/bits/stl_bvector.h:781: error: ‘__n’ was not declared in this scope
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘void std::vector<bool, _Alloc>::resize(size_t, bool)’:
/usr/include/c++/4.4/bits/stl_bvector.h:826: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/stl_bvector.h:826: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
/usr/include/c++/4.4/bits/stl_bvector.h: In member function ‘void std::vector<bool, _Alloc>::_M_initialize(size_t)’:
/usr/include/c++/4.4/bits/stl_bvector.h:863: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
In file included from /usr/include/c++/4.4/vector:69,
                 from ./UTC/listeChaineeUTC.h:2,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/vector.tcc: In member function ‘void std::vector<bool, _Alloc>::_M_fill_insert(std::_Bit_iterator, size_t, bool)’:
/usr/include/c++/4.4/bits/vector.tcc:591: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc:592: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc:593: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc:602: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc:604: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc: In member function ‘void std::vector<bool, _Alloc>::_M_insert_range(std::_Bit_iterator, _ForwardIterator, _ForwardIterator, std::forward_iterator_tag)’:
/usr/include/c++/4.4/bits/vector.tcc:627: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
/usr/include/c++/4.4/bits/vector.tcc:629: error: there are no arguments to ‘difference_type’ that depend on a template parameter, so a declaration of ‘difference_type’ must be available
In file included from /usr/include/c++/4.4/iosfwd:42,
                 from /usr/include/c++/4.4/ios:39,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/postypes.h: At global scope:
/usr/include/c++/4.4/bits/postypes.h:98: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.4/string:46,
                 from /usr/include/c++/4.4/bits/locale_classes.h:42,
                 from /usr/include/c++/4.4/bits/ios_base.h:43,
                 from /usr/include/c++/4.4/ios:43,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/ostream_insert.h:43: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/ostream_insert.h: In function ‘void std::__ostream_write(std::basic_ostream<_CharT, _Traits>&, const _CharT*, int)’:
/usr/include/c++/4.4/bits/ostream_insert.h:48: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ostream_insert.h:49: error: ‘__put’ was not declared in this scope
/usr/include/c++/4.4/bits/ostream_insert.h: At global scope:
/usr/include/c++/4.4/bits/ostream_insert.h:55: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/ostream_insert.h:75: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/ostream_insert.h: In function ‘std::basic_ostream<_CharT, _Traits>& std::__ostream_insert(std::basic_ostream<_CharT, _Traits>&, const _CharT*, int)’:
/usr/include/c++/4.4/bits/ostream_insert.h:85: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ostream_insert.h:86: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.4/bits/ostream_insert.h: At global scope:
/usr/include/c++/4.4/bits/ostream_insert.h:117: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/ostream_insert.h:121: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/string:56,
                 from /usr/include/c++/4.4/bits/locale_classes.h:42,
                 from /usr/include/c++/4.4/bits/ios_base.h:43,
                 from /usr/include/c++/4.4/ios:43,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/basic_string.tcc: In function ‘std::basic_istream<_CharT, _Traits>& std::operator>>(std::basic_istream<_CharT, _Traits>&, std::basic_string<_CharT, _Traits, _Alloc>&)’:
/usr/include/c++/4.4/bits/basic_string.tcc:996: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/basic_string.tcc:997: error: ‘__w’ was not declared in this scope
In file included from /usr/include/c++/4.4/string:53,
                 from /usr/include/c++/4.4/bits/locale_classes.h:42,
                 from /usr/include/c++/4.4/bits/ios_base.h:43,
                 from /usr/include/c++/4.4/ios:43,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/basic_string.h: At global scope:
/usr/include/c++/4.4/bits/basic_string.h: In instantiation of ‘std::basic_string<char, std::char_traits<char>, std::allocator<char> >’:
/usr/include/c++/4.4/bits/basic_string.tcc:1111:   instantiated from here
/usr/include/c++/4.4/bits/basic_string.h:114: error: no type named ‘difference_type’ in ‘class std::allocator<char>’
/usr/include/c++/4.4/bits/basic_string.h: In instantiation of ‘std::basic_string<wchar_t, std::char_traits<wchar_t>, std::allocator<wchar_t> >’:
/usr/include/c++/4.4/bits/basic_string.tcc:1126:   instantiated from here
/usr/include/c++/4.4/bits/basic_string.h:114: error: no type named ‘difference_type’ in ‘class std::allocator<wchar_t>’
In file included from /usr/include/c++/4.4/ios:43,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/ios_base.h:464: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ios_base.h:465: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ios_base.h:624: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ios_base.h:633: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ios_base.h:647: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/ios_base.h:656: error: ‘streamsize’ does not name a type
In file included from /usr/include/c++/4.4/ios:44,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/streambuf:50: error: expected constructor, destructor, or type conversion before ‘__copy_streambufs_eof’
/usr/include/c++/4.4/streambuf:141: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:234: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/streambuf:260: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:333: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:425: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:567: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/streambuf:624: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:640: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:717: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/streambuf:784: error: expected constructor, destructor, or type conversion before ‘__copy_streambufs_eof’
/usr/include/c++/4.4/streambuf:789: error: expected constructor, destructor, or type conversion before ‘__copy_streambufs_eof’
In file included from /usr/include/c++/4.4/streambuf:796,
                 from /usr/include/c++/4.4/ios:44,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/streambuf.tcc:44: error: expected constructor, destructor, or type conversion before ‘basic_streambuf’
/usr/include/c++/4.4/bits/streambuf.tcc:78: error: expected constructor, destructor, or type conversion before ‘basic_streambuf’
/usr/include/c++/4.4/bits/streambuf.tcc:115: error: expected constructor, destructor, or type conversion before ‘__copy_streambufs_eof’
/usr/include/c++/4.4/bits/streambuf.tcc:138: error: expected initializer before ‘__copy_streambufs’
/usr/include/c++/4.4/bits/streambuf.tcc:151: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.4/bits/streambuf.tcc:152: error: expected ‘;’ before ‘__copy_streambufs’
/usr/include/c++/4.4/bits/streambuf.tcc:155: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.4/bits/streambuf.tcc:156: error: expected ‘;’ before ‘__copy_streambufs_eof’
/usr/include/c++/4.4/bits/streambuf.tcc:162: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.4/bits/streambuf.tcc:163: error: expected ‘;’ before ‘__copy_streambufs’
/usr/include/c++/4.4/bits/streambuf.tcc:166: error: explicit instantiation of non-template ‘int std::streamsize’
/usr/include/c++/4.4/bits/streambuf.tcc:167: error: expected ‘;’ before ‘__copy_streambufs_eof’
In file included from /usr/include/c++/4.4/bits/locale_facets.h:50,
                 from /usr/include/c++/4.4/bits/basic_ios.h:39,
                 from /usr/include/c++/4.4/ios:45,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/streambuf_iterator.h:47: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
/usr/include/c++/4.4/bits/streambuf_iterator.h:200: error: wrong number of template arguments (5, should be 3)
/usr/include/c++/4.4/bits/stl_iterator_base_types.h:104: error: provided for ‘template<class _Category, class _Tp, class _Distance> struct std::iterator’
/usr/include/c++/4.4/bits/streambuf_iterator.h:262: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char::__value, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> > >::__type std::__copy_move_a2(_CharT*, _CharT*, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> >)’:
/usr/include/c++/4.4/bits/streambuf_iterator.h:296: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/streambuf_iterator.h:297: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.4/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char::__value, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> > >::__type std::__copy_move_a2(const _CharT*, const _CharT*, std::ostreambuf_iterator<_CharT, std::char_traits<_CharT> >)’:
/usr/include/c++/4.4/bits/streambuf_iterator.h:308: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/streambuf_iterator.h:309: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.4/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char::__value, _CharT*>::__type std::__copy_move_a2(std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, _CharT*)’:
/usr/include/c++/4.4/bits/streambuf_iterator.h:331: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/streambuf_iterator.h:332: error: ‘__n’ was not declared in this scope
/usr/include/c++/4.4/bits/streambuf_iterator.h: In function ‘typename __gnu_cxx::__enable_if<std::__is_char::__value, std::istreambuf_iterator<_CharT, std::char_traits<_CharT> > >::__type std::find(std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, std::istreambuf_iterator<_CharT, std::char_traits<_CharT> >, const _CharT2&)’:
/usr/include/c++/4.4/bits/streambuf_iterator.h:368: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/streambuf_iterator.h:368: error: expected ‘;’ before ‘__n’
/usr/include/c++/4.4/bits/streambuf_iterator.h:369: error: ‘__n’ was not declared in this scope
In file included from /usr/include/c++/4.4/bits/basic_ios.h:39,
                 from /usr/include/c++/4.4/ios:45,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/locale_facets.h: At global scope:
/usr/include/c++/4.4/bits/locale_facets.h:92: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/locale_facets.h:92: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/bits/basic_ios.h:39,
                 from /usr/include/c++/4.4/ios:45,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/locale_facets.h:2440: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/bits/locale_facets.h:2599,
                 from /usr/include/c++/4.4/bits/basic_ios.h:39,
                 from /usr/include/c++/4.4/ios:45,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/locale_facets.tcc:760: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/locale_facets.tcc: In member function ‘_OutIter std::num_put<_CharT, _OutIter>::_M_insert_int(_OutIter, std::ios_base&, _CharT, _ValueT) const’:
/usr/include/c++/4.4/bits/locale_facets.tcc:901: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/locale_facets.tcc:902: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:902: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:902: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:902: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:902: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:903: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.4/bits/locale_facets.tcc: In member function ‘_OutIter std::num_put<_CharT, _OutIter>::_M_insert_float(_OutIter, std::ios_base&, _CharT, char, _ValueT) const’:
/usr/include/c++/4.4/bits/locale_facets.tcc:964: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/locale_facets.tcc:981: error: ‘__prec’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1039: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1039: error: expected ‘;’ before ‘__off’
/usr/include/c++/4.4/bits/locale_facets.tcc:1042: error: ‘__off’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1048: error: ‘__off’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1056: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/locale_facets.tcc:1057: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1057: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1057: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1057: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1057: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1058: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.4/bits/locale_facets.tcc: In member function ‘virtual _OutIter std::num_put<_CharT, _OutIter>::do_put(_OutIter, std::ios_base&, _CharT, bool) const’:
/usr/include/c++/4.4/bits/locale_facets.tcc:1094: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/locale_facets.tcc:1095: error: ‘__w’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1095: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1095: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1095: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.4/bits/locale_facets.tcc:1095: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/locale_facets.tcc:1096: error: expected ‘)’ before ‘{’ token
/usr/include/c++/4.4/bits/locale_facets.tcc: At global scope:
/usr/include/c++/4.4/bits/locale_facets.tcc:1178: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/locale_facets.tcc:1178: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/ostream:287: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/ostream:311: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/ostream: In member function ‘void std::basic_ostream<_CharT, _Traits>::_M_write(const _CharT*, int)’:
/usr/include/c++/4.4/ostream:289: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/ostream:290: error: ‘__put’ was not declared in this scope
/usr/include/c++/4.4/ostream: In function ‘std::basic_ostream<_CharT, _Traits>& std::operator<<(std::basic_ostream<_CharT, _Traits>&, const _CharT*)’:
/usr/include/c++/4.4/ostream:494: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.4/ostream:494: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.4/ostream:494: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.4/ostream:494: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/ostream: In function ‘std::basic_ostream<char, _Traits>& std::operator<<(std::basic_ostream<char, _Traits>&, const char*)’:
/usr/include/c++/4.4/ostream:511: error: expected type-specifier before ‘streamsize’
/usr/include/c++/4.4/ostream:511: error: expected ‘>’ before ‘streamsize’
/usr/include/c++/4.4/ostream:511: error: expected ‘(’ before ‘streamsize’
/usr/include/c++/4.4/ostream:511: error: ‘streamsize’ was not declared in this scope
In file included from /usr/include/c++/4.4/ostream:565,
                 from /usr/include/c++/4.4/iostream:40,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/ostream.tcc: At global scope:
/usr/include/c++/4.4/bits/ostream.tcc:183: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/iostream:41,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/istream:79: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/istream:247: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/istream:321: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:332: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:394: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:405: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:432: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/istream:435: error: expected ‘;’ before ‘(’ token
/usr/include/c++/4.4/istream:464: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:482: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/istream: In constructor ‘std::basic_istream<_CharT, _Traits>::basic_istream(std::basic_streambuf<_CharT, _Traits>*)’:
/usr/include/c++/4.4/istream:92: error: class ‘std::basic_istream<_CharT, _Traits>’ does not have any field named ‘_M_gcount’
/usr/include/c++/4.4/istream:92: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available
/usr/include/c++/4.4/istream: In destructor ‘virtual std::basic_istream<_CharT, _Traits>::~basic_istream()’:
/usr/include/c++/4.4/istream:102: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/istream:102: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available
/usr/include/c++/4.4/istream: In constructor ‘std::basic_istream<_CharT, _Traits>::basic_istream()’:
/usr/include/c++/4.4/istream:582: error: class ‘std::basic_istream<_CharT, _Traits>’ does not have any field named ‘_M_gcount’
/usr/include/c++/4.4/istream:582: error: there are no arguments to ‘streamsize’ that depend on a template parameter, so a declaration of ‘streamsize’ must be available
/usr/include/c++/4.4/istream: At global scope:
/usr/include/c++/4.4/istream:594: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:599: error: ‘std::basic_istream<char, std::char_traits<char> >& std::basic_istream<char, std::char_traits<char> >::ignore’ is not a static member of ‘struct std::basic_istream<char, std::char_traits<char> >’
/usr/include/c++/4.4/istream:599: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/istream:604: error: ‘std::basic_istream<char, std::char_traits<char> >& std::basic_istream<char, std::char_traits<char> >::ignore’ is not a static member of ‘struct std::basic_istream<char, std::char_traits<char> >’
/usr/include/c++/4.4/istream:604: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/istream:604: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.4/istream:604: error: initializer expression list treated as compound expression
/usr/include/c++/4.4/istream:610: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/istream:615: error: ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >& std::basic_istream<wchar_t, std::char_traits<wchar_t> >::ignore’ is not a static member of ‘struct std::basic_istream<wchar_t, std::char_traits<wchar_t> >’
/usr/include/c++/4.4/istream:615: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/istream:620: error: ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >& std::basic_istream<wchar_t, std::char_traits<wchar_t> >::ignore’ is not a static member of ‘struct std::basic_istream<wchar_t, std::char_traits<wchar_t> >’
/usr/include/c++/4.4/istream:620: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/istream:620: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.4/istream:620: error: initializer expression list treated as compound expression
In file included from /usr/include/c++/4.4/istream:830,
                 from /usr/include/c++/4.4/iostream:41,
                 from ./UTC/listeChaineeUTC.h:3,
                 from ./UTC/listeChaineeUTC.cpp:6:
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘typename std::basic_istream<_CharT, _Traits>::int_type std::basic_istream<_CharT, _Traits>::get()’:
/usr/include/c++/4.4/bits/istream.tcc:190: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(_CharT&)’:
/usr/include/c++/4.4/bits/istream.tcc:224: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: At global scope:
/usr/include/c++/4.4/bits/istream.tcc:259: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(_CharT*, int, _CharT)’:
/usr/include/c++/4.4/bits/istream.tcc:261: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::get(std::basic_streambuf<_CharT, _Traits>&, _CharT)’:
/usr/include/c++/4.4/bits/istream.tcc:308: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: At global scope:
/usr/include/c++/4.4/bits/istream.tcc:350: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::getline(_CharT*, int, _CharT)’:
/usr/include/c++/4.4/bits/istream.tcc:352: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore()’:
/usr/include/c++/4.4/bits/istream.tcc:412: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: At global scope:
/usr/include/c++/4.4/bits/istream.tcc:443: error: ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’ is not a static member of ‘class std::basic_istream<_CharT, _Traits>’
/usr/include/c++/4.4/bits/istream.tcc:443: error: template definition of non-template ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.4/bits/istream.tcc:443: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:505: error: ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’ is not a static member of ‘class std::basic_istream<_CharT, _Traits>’
/usr/include/c++/4.4/bits/istream.tcc:505: error: template definition of non-template ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::ignore’
/usr/include/c++/4.4/bits/istream.tcc:505: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:505: error: expected primary-expression before ‘__delim’
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘typename std::basic_istream<_CharT, _Traits>::int_type std::basic_istream<_CharT, _Traits>::peek()’:
/usr/include/c++/4.4/bits/istream.tcc:573: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: At global scope:
/usr/include/c++/4.4/bits/istream.tcc:600: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::read(_CharT*, int)’:
/usr/include/c++/4.4/bits/istream.tcc:602: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: At global scope:
/usr/include/c++/4.4/bits/istream.tcc:628: error: expected constructor, destructor, or type conversion before ‘basic_istream’
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::putback(_CharT)’:
/usr/include/c++/4.4/bits/istream.tcc:665: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: In member function ‘std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::unget()’:
/usr/include/c++/4.4/bits/istream.tcc:698: error: ‘_M_gcount’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc: In function ‘std::basic_istream<_CharT, _Traits>& std::operator>>(std::basic_istream<_CharT, _Traits>&, _CharT2*)’:
/usr/include/c++/4.4/bits/istream.tcc:893: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:893: error: expected ‘;’ before ‘__extracted’
/usr/include/c++/4.4/bits/istream.tcc:901: error: expected ‘;’ before ‘__num’
/usr/include/c++/4.4/bits/istream.tcc:902: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:903: error: ‘streamsize’ cannot appear in a constant-expression
/usr/include/c++/4.4/bits/istream.tcc:903: error: template argument 1 is invalid
/usr/include/c++/4.4/bits/istream.tcc:911: error: ‘__extracted’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:911: error: ‘__num’ was not declared in this scope
/usr/include/c++/4.4/bits/istream.tcc:936: error: ‘__extracted’ was not declared in this scope
In file included from /usr/include/c++/4.4/fstream:44,
                 from ./UTC/arbreUTCtrace.h:6,
                 from ./UTC/listeChaineeUTC.cpp:7:
/usr/include/c++/4.4/i486-linux-gnu/bits/basic_file.h: At global scope:
/usr/include/c++/4.4/i486-linux-gnu/bits/basic_file.h:86: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/i486-linux-gnu/bits/basic_file.h:89: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/i486-linux-gnu/bits/basic_file.h:93: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/i486-linux-gnu/bits/basic_file.h:102: error: ‘streamsize’ does not name a type
In file included from ./UTC/arbreUTCtrace.h:6,
                 from ./UTC/listeChaineeUTC.cpp:7:
/usr/include/c++/4.4/fstream:156: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/fstream:301: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/fstream:328: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/fstream:343: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/fstream:363: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/fstream:366: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/fstream:386: error: ‘streamsize’ has not been declared
In file included from /usr/include/c++/4.4/fstream:915,
                 from ./UTC/arbreUTCtrace.h:6,
                 from ./UTC/listeChaineeUTC.cpp:7:
/usr/include/c++/4.4/bits/fstream.tcc: In member function ‘void std::basic_filebuf<_CharT, _Traits>::_M_destroy_internal_buffer()’:
/usr/include/c++/4.4/bits/fstream.tcc:72: error: ‘_M_ext_buf_size’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc: In constructor ‘std::basic_filebuf<_CharT, _Traits>::basic_filebuf()’:
/usr/include/c++/4.4/bits/fstream.tcc:84: error: class ‘std::basic_filebuf<_CharT, _Traits>’ does not have any field named ‘_M_ext_buf_size’
/usr/include/c++/4.4/bits/fstream.tcc: At global scope:
/usr/include/c++/4.4/bits/fstream.tcc:177: error: expected constructor, destructor, or type conversion before ‘basic_filebuf’
/usr/include/c++/4.4/bits/fstream.tcc: In member function ‘virtual typename std::basic_filebuf<_CharT, _Traits>::int_type std::basic_filebuf<_CharT, _Traits>::underflow()’:
/usr/include/c++/4.4/bits/fstream.tcc:224: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:224: error: expected ‘;’ before ‘__ilen’
/usr/include/c++/4.4/bits/fstream.tcc:228: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:228: error: ‘class std::__basic_file<char>’ has no member named ‘xsgetn’
/usr/include/c++/4.4/bits/fstream.tcc:238: error: expected ‘;’ before ‘__blen’
/usr/include/c++/4.4/bits/fstream.tcc:239: error: expected ‘;’ before ‘__rlen’
/usr/include/c++/4.4/bits/fstream.tcc:241: error: ‘__blen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:241: error: ‘__rlen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:244: error: ‘__blen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:245: error: ‘__rlen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:247: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/fstream.tcc:248: error: ‘__rlen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:248: error: ‘__remainder’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:257: error: ‘_M_ext_buf_size’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:257: error: ‘__blen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:281: error: ‘_M_ext_buf_size’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:287: error: expected ‘;’ before ‘__elen’
/usr/include/c++/4.4/bits/fstream.tcc:288: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:292: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:304: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:311: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:321: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:324: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc: At global scope:
/usr/include/c++/4.4/bits/fstream.tcc:464: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/fstream.tcc: In member function ‘bool std::basic_filebuf<_CharT, _Traits>::_M_convert_to_external(_CharT*, int)’:
/usr/include/c++/4.4/bits/fstream.tcc:467: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:467: error: expected ‘;’ before ‘__elen’
/usr/include/c++/4.4/bits/fstream.tcc:468: error: expected ‘;’ before ‘__plen’
/usr/include/c++/4.4/bits/fstream.tcc:471: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:471: error: ‘class std::__basic_file<char>’ has no member named ‘xsputn’
/usr/include/c++/4.4/bits/fstream.tcc:472: error: ‘__plen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:478: error: expected ‘;’ before ‘__blen’
/usr/include/c++/4.4/bits/fstream.tcc:479: error: ‘__blen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:499: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:499: error: ‘class std::__basic_file<char>’ has no member named ‘xsputn’
/usr/include/c++/4.4/bits/fstream.tcc:500: error: ‘__plen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:506: error: expected ‘;’ before ‘__rlen’
/usr/include/c++/4.4/bits/fstream.tcc:508: error: ‘__rlen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:513: error: ‘class std::__basic_file<char>’ has no member named ‘xsputn’
/usr/include/c++/4.4/bits/fstream.tcc:521: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:521: error: ‘__plen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc: At global scope:
/usr/include/c++/4.4/bits/fstream.tcc:526: error: expected constructor, destructor, or type conversion before ‘basic_filebuf’
/usr/include/c++/4.4/bits/fstream.tcc:609: error: expected constructor, destructor, or type conversion before ‘basic_filebuf’
/usr/include/c++/4.4/bits/fstream.tcc:657: error: ‘streamsize’ has not been declared
/usr/include/c++/4.4/bits/fstream.tcc: In member function ‘bool std::basic_filebuf<_CharT, _Traits>::_M_terminate_output()’:
/usr/include/c++/4.4/bits/fstream.tcc:798: error: ‘streamsize’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:798: error: expected ‘;’ before ‘__ilen’
/usr/include/c++/4.4/bits/fstream.tcc:810: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:813: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/fstream.tcc:814: error: ‘__elen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:819: error: ‘__ilen’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc: In member function ‘virtual void std::basic_filebuf<_CharT, _Traits>::imbue(const std::locale&)’:
/usr/include/c++/4.4/bits/fstream.tcc:886: error: ‘streamsize’ does not name a type
/usr/include/c++/4.4/bits/fstream.tcc:887: error: ‘__remainder’ was not declared in this scope
/usr/include/c++/4.4/bits/fstream.tcc:891: error: ‘__remainder’ was not declared in this scope
make: *** [listeChaineeUTC.o] Erreur 1


```

I have tried to install a hell lot of librairies but it doesn't change anything. I remove and then re install g++ but still the same errors...
ANY IDEAS ? :(


Thxing in advance for your time and consideration ;)

---

### Post by MadCow108 on 2010-04-18
can you post some code?
especially
UTC/IaUTC.cpp
UTC/listeChaineeUTC.h
UTC/listeChaineeUTC.cpp

does the code really require c++0x features?
if yes you have to compile with -std=c++0x or -std=gnu++0x

btw this:
rm -rf *.o
does not belong in the default make target, it should be in the make clean target

---

### Post by Fabzil on 2010-04-18
- I tried deleting all the .o bedore compiling, and I get the same errors.

- does the code really require c++0x features?
=> I have no idea, dunno what is c++0x. The thing is that this code is on a SVN, it means that every person working with me on the project got the exact same files and makefile, and just do as me the "$:make". But just on my computer it doesn't work...

(well i'm back from wikipedia where i saw what is c++0x and I really dont know how can this be related with my issues)

---

### Post by MadCow108 on 2010-04-18
its hard to tell the problem without any source...
do your colleges use the sames compiler and library version?

./UTC/IaUTC.cpp:19: warning: extended initializer lists only available with -std=c++0x or -std=gnu++0x
this line either means your code uses some feature of c++0x (the unfinished new standard) or that you have some syntax error which fools gcc into thinking it uses it.
either way it is very likely a bug in the makefile or sourcefile

have the look at this output:
g++ ./UTC/listeChaineeUTC.cpp -E

and look to what the macro _PTRDIFF_TYPE__ expands to in the ptrdiff_t typedef:
typedef __PTRDIFF_TYPE__ ptrdiff_t;

maybe that helps finding the problem

---

### Post by Fabzil on 2010-04-19
*do your colleges use the sames compiler and library version?*
=> well we have checked and it seems that yes.


*this line either means your code uses some feature of c++0x (the unfinished new standard) or that you have some syntax error which fools gcc into thinking it uses it.*
=> Oh ! now i see, thx for your explanation


[I]and look to what the macro _PTRDIFF_TYPE__ expands to in the ptrdiff_t typedef:
typedef __PTRDIFF_TYPE__ ptrdiff_t;[/I]
=> I understand that i must see what the macro stand for, but I really dont know where to look :/



*its hard to tell the problem without any source...*
=> Alles das habt ihr gefragt steht hier : [http://fabzil.free.fr/PROJET/IA/debug/](http://fabzil.free.fr/PROJET/IA/debug/)


**Thx you for your time ! :KS**

---

### Post by MadCow108 on 2010-04-19
soule // HEURISTIQUE
what is this doing in the first line of listeChaineeUTC.cpp ...?

in IaUTC.cpp I am not sure what happens, you should investigate it. Are you including <pthread.h>?
A solution would be to change the code to this:
pthread_mutex_init(&tableMutex[i], NULL);
it does the same but avoids the macro

---

### Post by MadCow108 on 2010-04-20
I would care about the c++0x issues.
They show there is some kind of problem in your code, as the PTHREAD_INITIALIZE macro has nothing to do with c++0x
and you don't want anything to happen to your mutixes/mutexes!
If they get initialized wrong it may produce very ugly bugs much later on.

I recommend investigating what exactly causes it. Maybe one of your headers sets a define which messes it up
If that is to much work at least replace it with the function call (which seems safe in the particular files).

---

