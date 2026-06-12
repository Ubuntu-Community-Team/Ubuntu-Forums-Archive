---
title: "libboost-1.55 problem in boost/assert.hpp"
date: 2014-06-30
forum: Programming Talk
---

### Post by DaveCat on 2014-06-30
Hello!
I'm quite a newbie as a programmer, but I think this is strange enough to post a thread here.
I'm working on a software project for university, I may tell more about it if needed, but I think the real problem lies in libboost-1.55.
In the many code files of the project, those boost headers are included:
```

#include <boost/tokenizer.hpp>
#include <boost/algorithm/string/predicate.hpp>
#include <boost/algorithm/string.hpp>
#include <boost/foreach.hpp>
#include <boost/shared_ptr.hpp>
```

but, when compiling, an error in boost/assert.hpp comes out (actually a lot of errors, of course):
(First error)
```

/usr/include/boost/assert.hpp|102|error: ‘BOOST_NOINLINE’ does not name a type| 
```

(Quasi-complete output - I'm using Code::Blocks on Ubuntu 14.04 LTS)
```

||=== Build: Release in buildingCASPplugin (compiler: GNU GCC Compiler) ===|
/usr/local/include/dlvhex2/ExtSourceProperties.h|45|warning: #warning TODO what is the difference/intended usage of ExtSourceProperty vs ExtSourceProperties? (the names are not very intuitive) [-Wcpp]|
/usr/local/include/dlvhex2/Atoms.h|217|warning: #warning inputMask seems to be duplicated in parts of ExternalAtomMask [-Wcpp]|
/usr/local/include/dlvhex2/Predicate.h|57|warning: #warning see warning in PredicateTable.h [-Wcpp]|
/usr/local/include/dlvhex2/PredicateTable.h|160|warning: #warning this looks fishy, and PREDICATE_FAIL is not used anywhere else, when can this happen and if it is intended to fail, why don't we return a pointer or throw an exception? [-Wcpp]|
/usr/include/boost/assert.hpp|102|error: ‘BOOST_NOINLINE’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|339|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|339|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|345|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|345|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|397|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|397|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|414|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|432|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|439|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|505|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|505|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|514|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|568|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|568|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|584|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|592|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|592|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|599|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|609|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|609|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|617|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|617|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|666|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|666|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/detail/operator_bool.hpp|11|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/detail/operator_bool.hpp|11|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/detail/operator_bool.hpp|60|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/detail/operator_bool.hpp|60|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|674|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|674|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|679|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|679|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|684|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|684|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|690|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|695|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|700|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|700|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|705|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|705|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|710|error: expected ‘;’ at end of member declaration|
/usr/include/boost/smart_ptr/shared_ptr.hpp|710|error: ‘BOOST_NOEXCEPT’ does not name a type|
/usr/include/boost/smart_ptr/shared_ptr.hpp|733|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|738|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|756|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|761|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|766|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|771|error: expected initializer before ‘BOOST_NOEXCEPT’|
/usr/include/boost/smart_ptr/shared_ptr.hpp|778|error: expected initializer before ‘BOOST_NOEXCEPT’|
||More errors follow but not being shown.|
||Edit the max errors limit in compiler options...|
||=== Build failed: 50 error(s), 4 warning(s) (0 minute(s), 19 second(s)) ===|


```

the main file of the project (which actually do not contain any main function for the project is a plugin, and you can imagine how happy I am with this being my first software development experience... ok I stop complaining.)
the main source contains the macro
```
#define NDEBUG
```

which, I read, is related to the assert.hpp header.

I've googled a little bit and I think those are about it:
[https://svn.boost.org/trac/boost/ticket/10043](https://svn.boost.org/trac/boost/ticket/10043)
[https://svn.boost.org/trac/boost/query?status=!closed&page=24&desc=1&order=type&row=description](https://svn.boost.org/trac/boost/query?status=!closed&page=24&desc=1&order=type&row=description)

Well, I think I wrote all I've found out so far.
Hope someone helps!

Thanks in advance,
Davide

---

### Post by spjackson on 2014-06-30
Can you provide a minimal compilable sample that produces this error, in particular one that does not involve [COLOR=#000000][FONT=Ubuntu Mono]/usr/local/include/dlvhex2 ?[/FONT][/COLOR]

The following works fine for me.
```

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"
$ uname -a
Linux xxxxxxxx 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
$ cat btest.cpp
#include <boost/tokenizer.hpp>
#include <boost/algorithm/string/predicate.hpp>
#include <boost/algorithm/string.hpp>
#include <boost/foreach.hpp>
#include <boost/shared_ptr.hpp>
#include <boost/assert.hpp>
#include <boost/version.hpp>


#include <iostream>


int main()
{
  std::cout << "Boost version: " << BOOST_LIB_VERSION << "\n";
}



$ make btest && ./btest
g++     btest.cpp   -o btest
Boost version: 1_55

```

---

### Post by DaveCat on 2014-06-30
Thanks for the answer!
Your code works fine also for me, as well as in all experiments I made isolating pieces of my code - they do work!
Problem is i'm working on codes which was made by someone else, so it's a bit complicated finding the minimal compileble and still nonworking code example.
I will try some more experiments tomorrow, looking for that minimal reason for error.

By the way, dlvhex is the program of which the program I'm working on is a plugin (if someone is really bored: [http://www.kr.tuwien.ac.at/research/systems/dlvhex/](http://www.kr.tuwien.ac.at/research/systems/dlvhex/) ).
What happened is that the currently available code was built some years ago, so with older boost (and older Gecode).
I rearranged part of it to get rid of errors caused by changes in Gecode namespaces, but after that the compiler, even if no longer complaining about Gecode stuff, started to report kind-of-impossible errors in an other (and apparently Gecode-independent) part of the code, errors like 
error: no match for 'operator*' (operand type is 'boost::tokenizer<boost::char_separator<char> >::iterator
 (see code below).
So I tried linking all the project in a codeblocks one, and started finding this other error, the one in asserts.hpp.
(Partial output of "make" made after ./configure in the source package of the plugin -- don't even know if this is worth reading!)
```
In file included from /usr/include/c++/4.8/map:60:0,
                 from ../include/casp/gecodesolver.h:9,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_tree.h:927:5: note: template<class _Key, class _Val, class _KeyOfValue, class _Compare, class _Alloc> bool std::operator!=(const std::_Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>&, const std::_Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>&)
     operator!=(const _Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>& __x,
     ^
/usr/include/c++/4.8/bits/stl_tree.h:927:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::_Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/map:60:0,
                 from ../include/casp/gecodesolver.h:9,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_tree.h:316:5: note: template<class _Val> bool std::operator!=(const std::_Rb_tree_iterator<_Tp>&, const std::_Rb_tree_const_iterator<_Val>&)
     operator!=(const _Rb_tree_iterator<_Val>& __x,
     ^
/usr/include/c++/4.8/bits/stl_tree.h:316:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::_Rb_tree_iterator<_Tp>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/vector:64:0,
                 from /usr/local/include/gecode/kernel/array.hpp:47,
                 from /usr/local/include/gecode/kernel.hh:160,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_vector.h:1428:5: note: template<class _Tp, class _Alloc> bool std::operator!=(const std::vector<_Tp, _Alloc>&, const std::vector<_Tp, _Alloc>&)
     operator!=(const vector<_Tp, _Alloc>& __x, const vector<_Tp, _Alloc>& __y)
     ^
/usr/include/c++/4.8/bits/stl_vector.h:1428:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::vector<_Tp, _Alloc>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/iterator:66:0,
                 from /usr/local/include/gecode/kernel/array.hpp:46,
                 from /usr/local/include/gecode/kernel.hh:160,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stream_iterator.h:137:5: note: template<class _Tp, class _CharT, class _Traits, class _Dist> bool std::operator!=(const std::istream_iterator<_Tp, _CharT, _Traits, _Dist>&, const std::istream_iterator<_Tp, _CharT, _Traits, _Dist>&)
     operator!=(const istream_iterator<_Tp, _CharT, _Traits, _Dist>& __x,
     ^
/usr/include/c++/4.8/bits/stream_iterator.h:137:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::istream_iterator<_Tp, _CharT, _Traits, _Dist>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/bits/locale_facets.h:48:0,
                 from /usr/include/c++/4.8/bits/basic_ios.h:37,
                 from /usr/include/c++/4.8/ios:44,
                 from /usr/include/c++/4.8/ostream:38,
                 from /usr/include/c++/4.8/iostream:39,
                 from /usr/local/include/gecode/support/bitset-offset.hpp:46,
                 from /usr/local/include/gecode/support.hh:117,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/streambuf_iterator.h:210:5: note: template<class _CharT, class _Traits> bool std::operator!=(const std::istreambuf_iterator<_CharT, _Traits>&, const std::istreambuf_iterator<_CharT, _Traits>&)
     operator!=(const istreambuf_iterator<_CharT, _Traits>& __a,
     ^
/usr/include/c++/4.8/bits/streambuf_iterator.h:210:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::istreambuf_iterator<_CharT, _Traits>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/string:52:0,
                 from /usr/include/c++/4.8/bits/locale_classes.h:40,
                 from /usr/include/c++/4.8/bits/ios_base.h:41,
                 from /usr/include/c++/4.8/ios:42,
                 from /usr/include/c++/4.8/ostream:38,
                 from /usr/include/c++/4.8/iostream:39,
                 from /usr/local/include/gecode/support/bitset-offset.hpp:46,
                 from /usr/local/include/gecode/support.hh:117,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/basic_string.h:2556:5: note: template<class _CharT, class _Traits, class _Alloc> bool std::operator!=(const std::basic_string<_CharT, _Traits, _Alloc>&, const _CharT*)
     operator!=(const basic_string<_CharT, _Traits, _Alloc>& __lhs,
     ^
/usr/include/c++/4.8/bits/basic_string.h:2556:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::basic_string<_CharT, _Traits, _Alloc>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/string:52:0,
                 from /usr/include/c++/4.8/bits/locale_classes.h:40,
                 from /usr/include/c++/4.8/bits/ios_base.h:41,
                 from /usr/include/c++/4.8/ios:42,
                 from /usr/include/c++/4.8/ostream:38,
                 from /usr/include/c++/4.8/iostream:39,
                 from /usr/local/include/gecode/support/bitset-offset.hpp:46,
                 from /usr/local/include/gecode/support.hh:117,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/basic_string.h:2544:5: note: template<class _CharT, class _Traits, class _Alloc> bool std::operator!=(const _CharT*, const std::basic_string<_CharT, _Traits, _Alloc>&)
     operator!=(const _CharT* __lhs,
     ^
/usr/include/c++/4.8/bits/basic_string.h:2544:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   mismatched types 'const _CharT*' and 'boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/string:52:0,
                 from /usr/include/c++/4.8/bits/locale_classes.h:40,
                 from /usr/include/c++/4.8/bits/ios_base.h:41,
                 from /usr/include/c++/4.8/ios:42,
                 from /usr/include/c++/4.8/ostream:38,
                 from /usr/include/c++/4.8/iostream:39,
                 from /usr/local/include/gecode/support/bitset-offset.hpp:46,
                 from /usr/local/include/gecode/support.hh:117,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/basic_string.h:2532:5: note: template<class _CharT, class _Traits, class _Alloc> bool std::operator!=(const std::basic_string<_CharT, _Traits, _Alloc>&, const std::basic_string<_CharT, _Traits, _Alloc>&)
     operator!=(const basic_string<_CharT, _Traits, _Alloc>& __lhs,
     ^
/usr/include/c++/4.8/bits/basic_string.h:2532:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::basic_string<_CharT, _Traits, _Alloc>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/iosfwd:40:0,
                 from /usr/include/c++/4.8/ios:38,
                 from /usr/include/c++/4.8/ostream:38,
                 from /usr/include/c++/4.8/iostream:39,
                 from /usr/local/include/gecode/support/bitset-offset.hpp:46,
                 from /usr/local/include/gecode/support.hh:117,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/postypes.h:221:5: note: template<class _StateT> bool std::operator!=(const std::fpos<_StateT>&, const std::fpos<_StateT>&)
     operator!=(const fpos<_StateT>& __lhs, const fpos<_StateT>& __rhs)
     ^
/usr/include/c++/4.8/bits/postypes.h:221:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::fpos<_StateT>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/ext/alloc_traits.h:38:0,
                 from /usr/include/c++/4.8/bits/stl_construct.h:61,
                 from /usr/include/c++/4.8/bits/stl_tempbuf.h:60,
                 from /usr/include/c++/4.8/bits/stl_algo.h:62,
                 from /usr/include/c++/4.8/algorithm:62,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/allocator.h:143:5: note: template<class _Tp> bool std::operator!=(const std::allocator<_Tp1>&, const std::allocator<_Tp1>&)
     operator!=(const allocator<_Tp>&, const allocator<_Tp>&)
     ^
/usr/include/c++/4.8/bits/allocator.h:143:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::allocator<_Tp1>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/ext/alloc_traits.h:38:0,
                 from /usr/include/c++/4.8/bits/stl_construct.h:61,
                 from /usr/include/c++/4.8/bits/stl_tempbuf.h:60,
                 from /usr/include/c++/4.8/bits/stl_algo.h:62,
                 from /usr/include/c++/4.8/algorithm:62,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/allocator.h:138:5: note: template<class _T1, class _T2> bool std::operator!=(const std::allocator<_Tp1>&, const std::allocator<_T2>&)
     operator!=(const allocator<_T1>&, const allocator<_T2>&)
     ^
/usr/include/c++/4.8/bits/allocator.h:138:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::allocator<_Tp1>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/bits/stl_algobase.h:67:0,
                 from /usr/include/c++/4.8/algorithm:61,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_iterator.h:353:5: note: template<class _IteratorL, class _IteratorR> bool std::operator!=(const std::reverse_iterator<_Iterator>&, const std::reverse_iterator<_IteratorR>&)
     operator!=(const reverse_iterator<_IteratorL>& __x,
     ^
/usr/include/c++/4.8/bits/stl_iterator.h:353:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::reverse_iterator<_Iterator>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/bits/stl_algobase.h:67:0,
                 from /usr/include/c++/4.8/algorithm:61,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_iterator.h:303:5: note: template<class _Iterator> bool std::operator!=(const std::reverse_iterator<_Iterator>&, const std::reverse_iterator<_Iterator>&)
     operator!=(const reverse_iterator<_Iterator>& __x,
     ^
/usr/include/c++/4.8/bits/stl_iterator.h:303:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::reverse_iterator<_Iterator>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/utility:70:0,
                 from /usr/include/c++/4.8/algorithm:60,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_pair.h:227:5: note: template<class _T1, class _T2> bool std::operator!=(const std::pair<_T1, _T2>&, const std::pair<_T1, _T2>&)
     operator!=(const pair<_T1, _T2>& __x, const pair<_T1, _T2>& __y)
     ^
/usr/include/c++/4.8/bits/stl_pair.h:227:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const std::pair<_T1, _T2>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/x86_64-linux-gnu/c++/4.8/bits/c++allocator.h:33:0,
                 from /usr/include/c++/4.8/bits/allocator.h:46,
                 from /usr/include/c++/4.8/ext/alloc_traits.h:38,
                 from /usr/include/c++/4.8/bits/stl_construct.h:61,
                 from /usr/include/c++/4.8/bits/stl_tempbuf.h:60,
                 from /usr/include/c++/4.8/bits/stl_algo.h:62,
                 from /usr/include/c++/4.8/algorithm:62,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/ext/new_allocator.h:144:5: note: template<class _Tp> bool __gnu_cxx::operator!=(const __gnu_cxx::new_allocator<_Tp>&, const __gnu_cxx::new_allocator<_Tp>&)
     operator!=(const new_allocator<_Tp>&, const new_allocator<_Tp>&)
     ^
/usr/include/c++/4.8/ext/new_allocator.h:144:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const __gnu_cxx::new_allocator<_Tp>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/bits/stl_algobase.h:67:0,
                 from /usr/include/c++/4.8/algorithm:61,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_iterator.h:823:5: note: template<class _Iterator, class _Container> bool __gnu_cxx::operator!=(const __gnu_cxx::__normal_iterator<_Iterator, _Container>&, const __gnu_cxx::__normal_iterator<_Iterator, _Container>&)
     operator!=(const __normal_iterator<_Iterator, _Container>& __lhs,
     ^
/usr/include/c++/4.8/bits/stl_iterator.h:823:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const __gnu_cxx::__normal_iterator<_Iterator, _Container>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
In file included from /usr/include/c++/4.8/bits/stl_algobase.h:67:0,
                 from /usr/include/c++/4.8/algorithm:61,
                 from /usr/local/include/gecode/support/heap.hpp:40,
                 from /usr/local/include/gecode/support.hh:106,
                 from /usr/local/include/gecode/kernel.hh:50,
                 from /usr/local/include/gecode/minimodel.hh:47,
                 from /usr/local/include/gecode/driver.hh:41,
                 from ../include/casp/gecodesolver.h:4,
                 from simpleparser.cpp:1:
/usr/include/c++/4.8/bits/stl_iterator.h:817:5: note: template<class _IteratorL, class _IteratorR, class _Container> bool __gnu_cxx::operator!=(const __gnu_cxx::__normal_iterator<_IteratorL, _Container>&, const __gnu_cxx::__normal_iterator<_IteratorR, _Container>&)
     operator!=(const __normal_iterator<_IteratorL, _Container>& __lhs,
     ^
/usr/include/c++/4.8/bits/stl_iterator.h:817:5: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:80: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'const __gnu_cxx::__normal_iterator<_IteratorL, _Container>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                ^
simpleparser.cpp:46:83: error: no match for 'operator++' (operand type is 'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}')
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                   ^
simpleparser.cpp:46:83: note: candidate is:
In file included from /usr/include/boost/iterator/iterator_adaptor.hpp:15:0,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:6:
/usr/include/boost/iterator/iterator_facade.hpp:722:3: note: template<class I, class V, class TC, class R, class D> typename boost::detail::postfix_increment_result<I, V, R, TC>::type boost::operator++(boost::iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, int)
   operator++(
   ^
/usr/include/boost/iterator/iterator_facade.hpp:722:3: note:   template argument deduction/substitution failed:
simpleparser.cpp:46:85: note:   'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}' is not derived from 'boost::iterator_facade<Derived1, V1, TC1, Reference1, Difference1>'
     for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
                                                                                     ^
simpleparser.cpp:47:11: error: no match for 'operator*' (operand type is 'boost::tokenizer<boost::char_separator<char> >::iterator {aka boost::token_iterator<boost::char_separator<char>, __gnu_cxx::__normal_iterator<const char*, std::basic_string<char> >, std::basic_string<char> >}')
   token = *tok_iter;
           ^
make[2]: *** [simpleparser.lo] Error 1
make[2]: Leaving directory `/home/dave/Build/caspnew/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dave/Build/caspnew/src'
make: *** [all-recursive] Error 1

```


Thanks again!
Bye!

---

### Post by dwhitney67 on 2014-06-30
Can you post the code within simpleparser.cpp?

---

### Post by DaveCat on 2014-07-01
Yep,  i can link them all, actually [https://github.com/DavGatto/caspplugin/tree/theorypropagation/src](https://github.com/DavGatto/caspplugin/tree/theorypropagation/src)
(i'd post it, but i'm from phone right now) 

I already tried isolating simpleparser.cpp adding an input-taking main, and it worked (no errors, at least)
If some of you want to try to compile gecodesolver and has  the newest release of libgecode, i'll post the modified code later, when i get to my pc (but i dont expect anyone to be that self-destructive to compile gecodesolver!) 
Thanks!

EDIT:
simpleparser.cpp:
```

#include "casp/gecodesolver.h"
#include "casp/simpleparser.h"

#include <stack>

#include <boost/tokenizer.hpp>
#include <boost/algorithm/string/predicate.hpp>

using namespace std;
using namespace boost;

SimpleParser::SimpleParser() {
}

int SimpleParser::priority(string s)
{
    if(s == "*" || s == "/" || s =="%")
        return 3;
    else if(s == "+" || s == "-")
        return 2;
    else if(s == "==" || s == ">" || s == "<" || s == "<=" || s == ">=" || s == "=" || s == "!=" || s == "!")
        return 1;

    return 0;
}


int SimpleParser::isOperator(string s)
{
    return priority(s) != 0;
}

string SimpleParser::convertToPostfix(string infix)
{
    string p;

    stack<string> x;

    vector<string> tokenList;
    string token = "";

    typedef tokenizer<char_separator<char> > tokenizer;
    char_separator<char> sep(" ", ",v.:-$%+-*/<>=()!", drop_empty_tokens);
    tokenizer tokens(infix, sep);

    for (tokenizer::iterator tok_iter = tokens.begin(); tok_iter != tokens.end(); ++tok_iter) {
        token = *tok_iter;
        tokenList.push_back(token);
    }

    string previousToken = "";
    for (int i = 0; i < tokenList.size(); i++) {
        string token = tokenList[i];

        if (token == "(") {
            if (isOperator(previousToken)) {
                x.push(token);
            }
            else {
                // If this is the case of predicate with parameters, read till closing bracket
                // for all parameters
                p = p.substr(0, p.length() - 1); // shuffle whitespace
                while (true) {
                    p += tokenList[i];

                    if (tokenList[i] == ")") break;

                    i++;
                }
                p += " "; // separate from next term
            }
        }
        else if (token == ")") {
            string n1 = x.top();
            x.pop();

            while (n1 != "(") {
                p += n1 + " ";
                n1 = x.top();
                x.pop();
            }
        }
        else if (isOperator(token)) {
            // check whether next token is also operator
            if (i < tokenList.size() - 1 && isOperator(tokenList[i+1])) {
                token += tokenList[i+1];
                i++;
            }

            if (x.empty())
                x.push(token);
            else {
                string n1 = x.top();

                while (priority(n1) >= priority(token)) {
                    x.pop();

                    p += n1 + " ";

                    if (x.empty()) break;

                    n1 = x.top();
                }
                x.push(token);
            }
        }
        else {
            p += token + " ";
        }

        previousToken = token;
    }

    while(!x.empty())
    {
        string n1 = x.top();
        x.pop();

        p += n1 + " ";
    }

    return p;
}

void SimpleParser::makeTree(string infix, struct ParseTree** root) {
    if (_cachedTrees.find(infix) != _cachedTrees.end()) {
        *root = new ParseTree(_cachedTrees[infix]);
        return;
    }

    string postfix = convertToPostfix(infix);

    stack<ParseTree*> elems;

    ParseTree *newTree, *left, *right;

    istringstream in(postfix);

    string s;
    while (in>>s) {
        if (isOperator(s)) {
            // Add new element
            right = elems.top();
            elems.pop();

            left = elems.top();
            elems.pop();

            newTree = new ParseTree;

            newTree->value = s;
            newTree->left = left;
            newTree->right = right;
            newTree->type = OPERATOR;

            elems.push(newTree);
        }

        else {
            newTree = new ParseTree;

            newTree->value = s;

            ElementType type = NUMBER;

            for (int i = 0; i < s.length(); i++)
                if (!isdigit(s[i])) type = CONSTRAINT_VARIABLE;

            newTree->type = type;

            elems.push(newTree);
        }
    }

    *root = elems.top();
    elems.pop();
}

set<string> SimpleParser::getConstraintVariables(struct ParseTree* root) {
    set<string> result;
    if (root->type == CONSTRAINT_VARIABLE) {
        result.insert(root->value);
    }
    else if (root->type == OPERATOR) {
        set<string> data = getConstraintVariables(root->left);
        result.insert(data.begin(), data.end());

        data = getConstraintVariables(root->right);
        result.insert(data.begin(), data.end());
    }
    return result;
}

void SimpleParser::deleteTree(ParseTree* root) {
    if (root->type == OPERATOR) {
        deleteTree(root->left);
        deleteTree(root->right);
    }
    delete root;
}

```

simpleparser.h:
```

#ifndef SIMPLEPARSER_H_
#define SIMPLEPARSER_H_

#include <string>
#include <map>
#include <set>

using namespace std;

enum ElementType {
    NUMBER, CONSTRAINT_VARIABLE, OPERATOR
};

struct ParseTree {
    string value;
    struct ParseTree *left, *right;
    ElementType type;
};

const int MAX = 500;

class SimpleParser {
private:
    map<string, ParseTree> _cachedTrees;

    int isOperator(string s);
    int priority(string s);
    string convertToPostfix(string infix);
public:
    SimpleParser();
    set<string> getConstraintVariables(struct ParseTree* root);
    void makeTree(string infix, struct ParseTree** root);
    void deleteTree(struct ParseTree* root);
};

#endif /* SIMPLEPARSER_H_ */

```

---

### Post by dwhitney67 on 2014-07-01
Thanks for the files.  I asked for them because .cpp file was popping up in the error messages that your compiler was producing.

Anyhow, I was able to compile the simpleparser.cpp (and associated header file) that you posted.  Of course, I had to make some cosmetic changes, but nothing really important.

Here are the changes to the .cpp file (see changes in bold text):
```

#include "casp/gecodesolver.h"
#include "casp/simpleparser.h"

#include <stack>
**#include <sstream>**

#include <boost/tokenizer.hpp>
#include <boost/algorithm/string/predicate.hpp>

...

string SimpleParser::convertToPostfix(string infix)
{
    ...

    string previousToken = "";
    for (**size_t** i = 0; i < tokenList.size(); i++) {
        string token = tokenList[i];
        ...
    }

    ...
}

void SimpleParser::makeTree(string infix, struct ParseTree** root) {
    ...

            for (**size_t** i = 0; i < s.length(); i++)
                if (!isdigit(s[i])) type = CONSTRAINT_VARIABLE;

    ...
}

```

Anyhow, the fact that you are getting errors compiling code indicates that either you have a bum installation of the boost libraries, or that you (err, CodeBlocks) is somehow building the project incorrectly.

On my 14.04 LTS system, I have boost-1.54 installed, which comes from the repos.  You indicated earlier that you have version 1.55; would it be possible for you to uninstall that version, and revert to the older version?

Btw, as for GCC (g++), I have this version:  g++ (Ubuntu 4.8.2-19ubuntu1) 4.8.2


P.S.  It considered bad programming practice to specify a 'using namespace' directive within a header file.  Consider removing the one from simpleparser.h, and instead use std:: where necessary.  You can Google for more insight as to why it is consider a bad practice.

---

### Post by DaveCat on 2014-07-02
I'm about to try using libboost 1.54, but, before that, I tried making your changes in simpleparser, and here is (part of) what I got:
```

In file included from /usr/include/boost/smart_ptr/shared_ptr.hpp:672:0,
                 from /usr/include/boost/shared_ptr.hpp:17,
                 from ../include/casp/gecodesolver.h:11,
                 from simpleparser.cpp:1:
/usr/include/boost/smart_ptr/detail/operator_bool.hpp:11:31: error: expected ';' at end of member declaration
     explicit operator bool () const BOOST_NOEXCEPT
                               ^
/usr/include/boost/smart_ptr/detail/operator_bool.hpp:11:37: error: 'BOOST_NOEXCEPT' does not name a type
     explicit operator bool () const BOOST_NOEXCEPT
                                     ^
/usr/include/boost/smart_ptr/detail/operator_bool.hpp:60:23: error: expected ';' at end of member declaration
     bool operator! () const BOOST_NOEXCEPT
                       ^
/usr/include/boost/smart_ptr/detail/operator_bool.hpp:60:29: error: 'BOOST_NOEXCEPT' does not name a type
     bool operator! () const BOOST_NOEXCEPT
                             ^
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from ../include/casp/gecodesolver.h:11,
                 from simpleparser.cpp:1:
/usr/include/boost/smart_ptr/shared_ptr.hpp:674:19: error: expected ';' at end of member declaration
     bool unique() const BOOST_NOEXCEPT
                   ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:674:25: error: 'BOOST_NOEXCEPT' does not name a type
     bool unique() const BOOST_NOEXCEPT
                         ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:679:22: error: expected ';' at end of member declaration
     long use_count() const BOOST_NOEXCEPT
                      ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:679:28: error: 'BOOST_NOEXCEPT' does not name a type
     long use_count() const BOOST_NOEXCEPT
                            ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:684:35: error: expected ';' at end of member declaration
     void swap( shared_ptr & other ) BOOST_NOEXCEPT
                                   ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:684:37: error: 'BOOST_NOEXCEPT' does not name a type
     void swap( shared_ptr & other ) BOOST_NOEXCEPT
                                     ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:690:76: error: expected initializer before 'BOOST_NOEXCEPT'
     template<class Y> bool owner_before( shared_ptr<Y> const & rhs ) const BOOST_NOEXCEPT
                                                                            ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:695:74: error: expected initializer before 'BOOST_NOEXCEPT'
     template<class Y> bool owner_before( weak_ptr<Y> const & rhs ) const BOOST_NOEXCEPT
                                                                          ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:700:75: error: expected ';' at end of member declaration
     void * _internal_get_deleter( boost::detail::sp_typeinfo const & ti ) const BOOST_NOEXCEPT
                                                                           ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:700:81: error: 'BOOST_NOEXCEPT' does not name a type
     void * _internal_get_deleter( boost::detail::sp_typeinfo const & ti ) const BOOST_NOEXCEPT
                                                                                 ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:705:44: error: expected ';' at end of member declaration
     void * _internal_get_untyped_deleter() const BOOST_NOEXCEPT
                                            ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:705:50: error: 'BOOST_NOEXCEPT' does not name a type
     void * _internal_get_untyped_deleter() const BOOST_NOEXCEPT
                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:710:50: error: expected ';' at end of member declaration
     bool _internal_equiv( shared_ptr const & r ) const BOOST_NOEXCEPT
                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:710:56: error: 'BOOST_NOEXCEPT' does not name a type
     bool _internal_equiv( shared_ptr const & r ) const BOOST_NOEXCEPT
                                                        ^
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from ../include/casp/gecodesolver.h:11,
                 from simpleparser.cpp:1:
/usr/include/boost/smart_ptr/shared_ptr.hpp: In constructor 'boost::shared_ptr<T>::shared_ptr(std::auto_ptr<_Tp1>)':
/usr/include/boost/smart_ptr/shared_ptr.hpp:459:45: error: 'r' was not declared in this scope
     shared_ptr( std::auto_ptr<Y> && r ): px(r.get()), pn()
                                             ^
/usr/include/boost/smart_ptr/shared_ptr.hpp: In member function 'boost::shared_ptr<T>& boost::shared_ptr<T>::operator=(std::auto_ptr<_Tp1>)':
/usr/include/boost/smart_ptr/shared_ptr.hpp:536:18: error: expected primary-expression before '(' token
         this_type( static_cast< std::auto_ptr<Y> && >( r ) ).swap( *this );
                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:536:50: error: expected '>' before '&&' token
         this_type( static_cast< std::auto_ptr<Y> && >( r ) ).swap( *this );
                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:536:50: error: expected '(' before '&&' token
/usr/include/boost/smart_ptr/shared_ptr.hpp:536:53: error: expected identifier before '>' token
         this_type( static_cast< std::auto_ptr<Y> && >( r ) ).swap( *this );
                                                     ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:536:56: error: 'r' was not declared in this scope
         this_type( static_cast< std::auto_ptr<Y> && >( r ) ).swap( *this );
                                                        ^
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from ../include/casp/gecodesolver.h:11,
                 from simpleparser.cpp:1:
/usr/include/boost/smart_ptr/shared_ptr.hpp: At global scope:
/usr/include/boost/smart_ptr/shared_ptr.hpp:733:101: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> inline bool operator==(shared_ptr<T> const & a, shared_ptr<U> const & b) BOOST_NOEXCEPT
                                                                                                     ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:738:101: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> inline bool operator!=(shared_ptr<T> const & a, shared_ptr<U> const & b) BOOST_NOEXCEPT
                                                                                                     ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:756:83: error: 'boost::detail::sp_nullptr_t' has not been declared
 template<class T> inline bool operator==( shared_ptr<T> const & p, boost::detail::sp_nullptr_t ) BOOST_NOEXCEPT
                                                                                   ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:756:98: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T> inline bool operator==( shared_ptr<T> const & p, boost::detail::sp_nullptr_t ) BOOST_NOEXCEPT
                                                                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:761:58: error: declaration of 'operator==' as non-function
 template<class T> inline bool operator==( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                          ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:761:43: error: 'sp_nullptr_t' is not a member of 'boost::detail'
 template<class T> inline bool operator==( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                           ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:761:86: error: expected primary-expression before 'const'
 template<class T> inline bool operator==( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                                                      ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:766:83: error: 'boost::detail::sp_nullptr_t' has not been declared
 template<class T> inline bool operator!=( shared_ptr<T> const & p, boost::detail::sp_nullptr_t ) BOOST_NOEXCEPT
                                                                                   ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:766:98: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T> inline bool operator!=( shared_ptr<T> const & p, boost::detail::sp_nullptr_t ) BOOST_NOEXCEPT
                                                                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:771:58: error: declaration of 'operator!=' as non-function
 template<class T> inline bool operator!=( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                          ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:771:43: error: 'sp_nullptr_t' is not a member of 'boost::detail'
 template<class T> inline bool operator!=( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                           ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:771:86: error: expected primary-expression before 'const'
 template<class T> inline bool operator!=( boost::detail::sp_nullptr_t, shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                                                      ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:778:100: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> inline bool operator<(shared_ptr<T> const & a, shared_ptr<U> const & b) BOOST_NOEXCEPT
                                                                                                    ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:783:74: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T> inline void swap(shared_ptr<T> & a, shared_ptr<T> & b) BOOST_NOEXCEPT
                                                                          ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:788:89: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> shared_ptr<T> static_pointer_cast( shared_ptr<U> const & r ) BOOST_NOEXCEPT
                                                                                         ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:798:88: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> shared_ptr<T> const_pointer_cast( shared_ptr<U> const & r ) BOOST_NOEXCEPT
                                                                                        ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:808:90: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> shared_ptr<T> dynamic_pointer_cast( shared_ptr<U> const & r ) BOOST_NOEXCEPT
                                                                                          ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:818:94: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T, class U> shared_ptr<T> reinterpret_pointer_cast( shared_ptr<U> const & r ) BOOST_NOEXCEPT
                                                                                              ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:830:102: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T> inline typename shared_ptr<T>::element_type * get_pointer(shared_ptr<T> const & p) BOOST_NOEXCEPT
                                                                                                      ^
In file included from /usr/include/boost/shared_ptr.hpp:17:0,
                 from ../include/casp/gecodesolver.h:11,
                 from simpleparser.cpp:1:
/usr/include/boost/smart_ptr/shared_ptr.hpp:890:77: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class D, class T> D * basic_get_deleter( shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                                             ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:914:49: error: expected initializer before 'BOOST_NOEXCEPT'
     template<typename D> D* get_deleter() const BOOST_NOEXCEPT
                                                 ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:928:71: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class D, class T> D * get_deleter( shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                                       ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:947:82: error: expected initializer before 'BOOST_NOEXCEPT'
 template<class T> inline bool atomic_is_lock_free( shared_ptr<T> const * /*p*/ ) BOOST_NOEXCEPT
                                                                                  ^
/usr/include/boost/smart_ptr/shared_ptr.hpp:1026:78: error: expected initializer before 'BOOST_NOEXCEPT'
 template< class T > std::size_t hash_value( boost::shared_ptr<T> const & p ) BOOST_NOEXCEPT
                                                                              ^
In file included from /usr/include/boost/type_traits/is_rvalue_reference.hpp:15:0,
                 from /usr/include/boost/type_traits/is_reference.hpp:17,
                 from /usr/include/boost/type_traits/intrinsics.hpp:206,
                 from /usr/include/boost/type_traits/is_convertible.hpp:15,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/is_rvalue_reference.hpp:21:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_PARTIAL_SPEC1_1(typename T,is_rvalue_reference,T&&,true)
 ^
In file included from /usr/include/boost/type_traits/intrinsics.hpp:207:0,
                 from /usr/include/boost/type_traits/is_convertible.hpp:15,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/is_volatile.hpp:60:35: error: template argument 1 is invalid
 struct is_volatile_rval_filter<T&&>
                                   ^
In file included from /usr/include/boost/type_traits/is_integral.hpp:15:0,
                 from /usr/include/boost/type_traits/is_arithmetic.hpp:13,
                 from /usr/include/boost/type_traits/is_convertible.hpp:21,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: 'char16_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: 'char16_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: 'char16_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: 'char16_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:77:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char16_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: 'char32_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: 'char32_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: 'char32_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: 'char32_t' was not declared in this scope
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
/usr/include/boost/type_traits/is_integral.hpp:80:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_CV_SPEC1(is_integral,char32_t,true)
 ^
In file included from /usr/include/boost/type_traits/add_lvalue_reference.hpp:9:0,
                 from /usr/include/boost/type_traits/is_convertible.hpp:26,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/add_reference.hpp:67:38: error: template argument 1 is invalid
 struct add_reference_rvalue_layer<T&&>
                                      ^
In file included from /usr/include/boost/type_traits/add_lvalue_reference.hpp:12:0,
                 from /usr/include/boost/type_traits/is_convertible.hpp:26,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/add_lvalue_reference.hpp:19:1: error: template argument 1 is invalid
 BOOST_TT_AUX_TYPE_TRAIT_PARTIAL_SPEC1_1(typename T,add_lvalue_reference,T&&,T&)
 ^
In file included from /usr/include/boost/type_traits/is_convertible.hpp:27:0,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/add_rvalue_reference.hpp:46:18: error: expected unqualified-id before '&&' token
         typedef T&&   type;
                  ^
In file included from /usr/include/boost/type_traits/is_function.hpp:26:0,
                 from /usr/include/boost/type_traits/is_convertible.hpp:28,
                 from /usr/include/boost/iterator/iterator_categories.hpp:20,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:14,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/is_function.hpp:104:1: error: template argument 1 is invalid
 BOOST_TT_AUX_BOOL_TRAIT_PARTIAL_SPEC1_1(typename T,is_function,T&&,false)
 ^
In file included from /usr/include/boost/iterator/detail/facade_iterator_category.hpp:17:0,
                 from /usr/include/boost/iterator/iterator_facade.hpp:14,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:15,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/is_const.hpp:69:34: error: template argument 1 is invalid
 struct is_const_rvalue_filter<T&&>
                                  ^
In file included from /usr/include/boost/type_traits/is_member_function_pointer.hpp:25:0,
                 from /usr/include/boost/type_traits/is_member_pointer.hpp:28,
                 from /usr/include/boost/type_traits/is_pointer.hpp:24,
                 from /usr/include/boost/detail/indirect_traits.hpp:9,
                 from /usr/include/boost/iterator/detail/facade_iterator_category.hpp:26,
                 from /usr/include/boost/iterator/iterator_facade.hpp:14,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:15,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/remove_cv.hpp:46:36: error: template argument 1 is invalid
 struct rvalue_ref_filter_rem_cv<T&&>
                                    ^
In file included from /usr/include/boost/detail/indirect_traits.hpp:16:0,
                 from /usr/include/boost/iterator/detail/facade_iterator_category.hpp:26,
                 from /usr/include/boost/iterator/iterator_facade.hpp:14,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:15,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/remove_reference.hpp:39:29: error: template argument 1 is invalid
 struct remove_rvalue_ref<T&&>
                             ^
In file included from /usr/include/boost/iterator/iterator_facade.hpp:23:0,
                 from /usr/include/boost/iterator/iterator_adaptor.hpp:15,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/type_traits/remove_const.hpp:63:29: error: template argument 1 is invalid
 struct remove_const_impl<T&&>
                             ^
In file included from /usr/include/boost/iterator/iterator_adaptor.hpp:10:0,
                 from /usr/include/boost/token_iterator.hpp:22,
                 from /usr/include/boost/tokenizer.hpp:20,
                 from simpleparser.cpp:7:
/usr/include/boost/iterator/detail/minimum_category.hpp:62:9: error: expected identifier before '(' token
         BOOST_STATIC_ASSERT((is_same<T1,T2>::value));
         ^
/usr/include/boost/iterator/detail/minimum_category.hpp:62:9: error: expected unqualified-id before ')' token
         BOOST_STATIC_ASSERT((is_same<T1,T2>::value));
         ^
/usr/include/boost/iterator/detail/minimum_category.hpp:62:9: error: expected ')' before ',' token
         BOOST_STATIC_ASSERT((is_same<T1,T2>::value));
         ^
/usr/include/boost/iterator/detail/minimum_category.hpp:62:9: error: expected unqualified-id before string constant
         BOOST_STATIC_ASSERT((is_same<T1,T2>::value));
         ^
/usr/include/boost/type_traits/make_unsigned.hpp:38:4: error: expected identifier before '(' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:38:4: error: expected unqualified-id before ')' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:38:4: error: expected ')' before ',' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:38:4: error: expected unqualified-id before string constant
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:41:4: error: expected identifier before '(' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:41:4: error: expected unqualified-id before ')' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:41:4: error: expected ')' before ',' token
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:41:4: error: 'int boost::detail::make_unsigned_imp<T>::static_assert(...)' cannot be overloaded
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:38:4: error: with 'int boost::detail::make_unsigned_imp<T>::static_assert(...)'
    BOOST_STATIC_ASSERT(
    ^
/usr/include/boost/type_traits/make_unsigned.hpp:41:4: error: expected unqualified-id before string constant
    BOOST_STATIC_ASSERT(
    ^
make[2]: *** [simpleparser.lo] Error 1
make[2]: Leaving directory `/home/dave/Build/csp3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dave/Build/csp3/src'
make: *** [all-recursive] Error 1

```

---

### Post by DaveCat on 2014-07-02
With boost 1.54 everithing goes just the same.
Trying 1.50

---

### Post by DaveCat on 2014-07-02
With 1.50 the error seem to disappear, but OTHER error come out (at least, I'm happy of my choice of being a maths student and not IT...).
I dont talk of the other errors as it would be off-topic.
Tomorrow I'll try 1.51, 52, 53.

Thanks!

---

### Post by DaveCat on 2014-07-06
Probably was a problem of compatibility between boost and gecode, as everything worked using Gecode 3.7 instead of 4.1 (and boost 1.54).
Thank you!

---

