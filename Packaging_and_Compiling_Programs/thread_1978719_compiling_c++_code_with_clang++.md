---
title: "compiling c++ code with clang++"
date: 2012-05-12
forum: Packaging and Compiling Programs
---

### Post by t0rb3n on 2012-05-12
Hi,

when I try to compile

```
#include <memory>

int main()
{
	std::unique_ptr<double> test;
	return 1;
}
```

with clang++, I get the following error:
```
user@machine:~/tmp$ clang++ -std=c++0x test.cpp 
In file included from test.cpp:2:
In file included from /usr/include/c++/4.6/memory:63:
In file included from /usr/include/c++/4.6/bits/stl_algobase.h:65:
In file included from /usr/include/c++/4.6/bits/stl_pair.h:60:
In file included from /usr/include/c++/4.6/bits/move.h:53:
/usr/include/c++/4.6/type_traits:630:59: error: '_Tp' does not refer to a value
    : public integral_constant<bool, __is_standard_layout(_Tp)>
                                                          ^
/usr/include/c++/4.6/type_traits:628:21: note: declared here
  template<typename _Tp>
                    ^
/usr/include/c++/4.6/type_traits:631:8: error: expected class name
    { };
       ^
/usr/include/c++/4.6/type_traits:631:8: error: expected '{' after base class list
/usr/include/c++/4.6/type_traits:643:56: error: '_Tp' does not refer to a value
    : public integral_constant<bool, __is_literal_type(_Tp)>
                                                       ^
/usr/include/c++/4.6/type_traits:641:21: note: declared here
  template<typename _Tp>
                    ^
/usr/include/c++/4.6/type_traits:644:8: error: expected class name
    { };
       ^
/usr/include/c++/4.6/type_traits:644:8: error: expected '{' after base class list
/usr/include/c++/4.6/type_traits:647:56: error: expected function body after function declarator
    typename add_rvalue_reference<_Tp>::type declval() noexcept;
                                                       ^
/usr/include/c++/4.6/type_traits:654:30: error: use of undeclared identifier 'declval'
        static decltype(_Tp1(declval<_Args1>()...), __one()) __test(int);
                             ^
/usr/include/c++/4.6/type_traits:654:38: error: '_Args1' does not refer to a value
        static decltype(_Tp1(declval<_Args1>()...), __one()) __test(int);
                                     ^
/usr/include/c++/4.6/type_traits:653:43: note: declared here
      template<typename _Tp1, typename... _Args1>
                                          ^
/usr/include/c++/4.6/type_traits:654:46: error: expected expression
        static decltype(_Tp1(declval<_Args1>()...), __one()) __test(int);
                                             ^
/usr/include/c++/4.6/type_traits:654:62: error: C++ requires a type specifier for all declarations
        static decltype(_Tp1(declval<_Args1>()...), __one()) __test(int);
        ~~~~~~                                               ^
/usr/include/c++/4.6/type_traits:668:43: error: use of undeclared identifier 'declval'
        static decltype(static_cast<_Tp1>(declval<_Arg1>()), __one())
                                          ^
/usr/include/c++/4.6/type_traits:668:51: error: '_Arg1' does not refer to a value
        static decltype(static_cast<_Tp1>(declval<_Arg1>()), __one())
                                                  ^
/usr/include/c++/4.6/type_traits:667:40: note: declared here
      template<typename _Tp1, typename _Arg1>
                                       ^
/usr/include/c++/4.6/type_traits:668:58: error: expected expression
        static decltype(static_cast<_Tp1>(declval<_Arg1>()), __one())
                                                         ^
/usr/include/c++/4.6/type_traits:669:2: error: C++ requires a type specifier for all declarations
        __test(int);
        ^
/usr/include/c++/4.6/type_traits:694:48: error: use of undeclared identifier 'declval'
    { static const bool __value = noexcept(_Tp(declval<_Args>()...)); };
                                               ^
/usr/include/c++/4.6/type_traits:694:56: error: '_Args' does not refer to a value
    { static const bool __value = noexcept(_Tp(declval<_Args>()...)); };
                                                       ^
/usr/include/c++/4.6/type_traits:692:38: note: declared here
  template<typename _Tp, typename... _Args>
                                     ^
/usr/include/c++/4.6/type_traits:694:63: error: expected expression
    { static const bool __value = noexcept(_Tp(declval<_Args>()...)); };
                                                              ^
/usr/include/c++/4.6/type_traits:699:61: error: use of undeclared identifier 'declval'
      static const bool __value = noexcept(static_cast<_Tp>(declval<_Arg>()));
                                                            ^
fatal error: too many errors emitted, stopping now [-ferror-limit=]
20 errors generated.

```

I usually work with gcc, without any difficulties, so, what am I doing wrong here?

---

### Post by oldos2er on 2012-05-12
Moved to Packaging and Compiling Programs.

---

### Post by bregma on 2012-05-14
> **t0rb3n said:**
> 
I usually work with gcc, without any difficulties, so, what am I doing wrong here?
You're trying to use the GCC standard library with a different compiler.

Clang does not in fact support the current C++ standard as well as GCC.

That's one reason why they're completely re-implementing the standard library on their own.  Another reason, of course, is they don't like the GPL.

---

### Post by kingtaurus on 2012-05-14
I quickly tried to compile your code with the same command;
```

clang++ --std=c++0x test.cpp

```

It worked properly (however, when asking a question like this, it is usually best to give the following information: clang++ --version). My computer reports:

```

clang++ --version
Ubuntu clang version 3.0-6ubuntu3 (tags/RELEASE_30/final) (based on LLVM 3.0)
Target: x86_64-pc-linux-gnu
Thread model: posix

```

If you are using an older version of clang++ you might have to use boost or the tr1 headers (from GCC).

Cheers,

Greg

---

### Post by t0rb3n on 2012-05-15
Indeed, I got an older version.

```
user@machine:~$ clang++ --version
clang version 2.9 (tags/RELEASE_29/final)
Target: x86_64-pc-linux-gnu
Thread model: posix

```

Is there an apt repository where can I get their version of the stdlib and/or the 3.0.x version of clang?
Or do I have to compile it on my own?

Thank you for your help so far.

Edit: I just remembered, I did not yet upgrade to 12.04, is clang 3 in the new repositories?

---

### Post by kingtaurus on 2012-05-16
> **t0rb3n said:**
> Indeed, I got an older version.

```
user@machine:~$ clang++ --version
clang version 2.9 (tags/RELEASE_29/final)
Target: x86_64-pc-linux-gnu
Thread model: posix

```

Is there an apt repository where can I get their version of the stdlib and/or the 3.0.x version of clang?
Or do I have to compile it on my own?

Thank you for your help so far.

Edit: I just remembered, I did not yet upgrade to 12.04, is clang 3 in the new repositories?

Clang 3.0 is in the 12.04 LTS repositories (along with libclang).

Cheers,

---

