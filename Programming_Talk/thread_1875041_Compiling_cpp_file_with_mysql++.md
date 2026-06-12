---
title: "Compiling cpp file with mysql++"
date: 2011-11-04
forum: Programming Talk
---

### Post by paulten on 2011-11-04
Hello all. 

After my upgrade to 11.10 I am unable to compile my cpp application which are using mysql++. 

This seems to be a common error, but I can't figure out what do to in my case.
I'm getting an error containing undefined references,
```

ilread.o: In function `nlines(std::basic_ifstream<char, std::char_traits<char> >&)':
ilread.cpp:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string()'
ilread.cpp:(.text+0x2d): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::getline<char, std::char_traits<char>, std::allocator<char> >(std::basic_istream<char, std::char_traits<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)'
ilread.cpp:(.text+0x3e): undefined reference to `std::basic_ios<char, std::char_traits<char> >::operator void*() const'
ilread.cpp:(.text+0x55): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
ilread.cpp:(.text+0x6a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
ilread.o: In function `main':
ilread.cpp:(.text+0xc0): undefined reference to `std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(char const*, std::_Ios_Openmode)'
ilread.cpp:(.text+0xd6): undefined reference to `mysqlpp::Connection::Connection(bool)'
ilread.cpp:(.text+0x10c): undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
......
ilread.o:(.rodata._ZTIN7mysqlpp5QueryE[typeinfo for mysqlpp::Query]+0x0): undefined reference to `vtable for __cxxabiv1::__vmi_class_type_info'
ilread.o:(.rodata._ZTIN7mysqlpp5QueryE[typeinfo for mysqlpp::Query]+0x10): undefined reference to `typeinfo for std::basic_ostream<char, std::char_traits<char> >'
ilread.o:(.rodata._ZTIN7mysqlpp10ComparableINS_8DateTimeEEE[typeinfo for mysqlpp::Comparable<mysqlpp::DateTime>]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
ilread.o:(.rodata._ZTIN7mysqlpp18OptionalExceptionsE[typeinfo for mysqlpp::OptionalExceptions]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'
ilread.o:(.eh_frame+0x1cb): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make: *** [ilread] Error 1

```


The beginning of my cpp program contains
```

#include </usr/include/mysql++/mysql++.h>
#include <sstream>
#include <fstream>
#include <limits>
#include <iostream>
using namespace std;
using namespace mysqlpp;

```
My program did compile previously, so I am certain there is no error in the code!
My makefile looks like this,
```

CXX := g++
CXXFLAGS := -I/usr/include/mysql -I/usr/include/mysql++
LDFLAGS := -L/usr/lib -lmysqlpp -lmysqlclient -lnsl -lz -lm
EXECUTABLE := main

all: ilread

clean:
        rm -f $(EXECUTABLE) *.o

```

My library files are indeed located in /usr/lib, 
```

# locate mysqlpp
/usr/lib/libmysqlpp.a
/usr/lib/libmysqlpp.so
# locate mysqlclient
/usr/lib/libmysqlclient.a
/usr/lib/libmysqlclient.so

```

As stated, I am using the latest version, 11.10.

I'm stuck...
Suggestions are highly appreciable! 

Kind regards
Paul

---

### Post by Zugzwang on 2011-11-04
Can you perform a "make clean" and post the complete output of running "make" here, including the gcc/g++ commands that are executed? I suspect that "gcc" is used instead of "g++" for linking.

---

### Post by paulten on 2011-11-04
Hello, thank you for replying.

Here is what you requested,

```

root@paul-XPS-M1330:~/Documents/fysikk/cpp_sqlite/read/app/ILread# g++ -I/usr/include/mysql -I/usr/local/include/mysql++ -L/usr/lib -lmysqlpp -lmysqlclient -lnsl -lz -lm -o ilread ilread.cpp 
/tmp/cc8vi8ds.o: In function `main':
ilread.cpp:(.text+0xd6): undefined reference to `mysqlpp::Connection::Connection(bool)'
ilread.cpp:(.text+0x10c): undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
ilread.cpp:(.text+0x152): undefined reference to `mysqlpp::Connection::select_db(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
ilread.cpp:(.text+0x18e): undefined reference to `mysqlpp::Connection::query(char const*)'
ilread.cpp:(.text+0x1b5): undefined reference to `mysqlpp::Query::parse()'
ilread.cpp:(.text+0x4ad): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4c5): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4dd): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4f5): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::DateTime const&)'
ilread.cpp:(.text+0x50b): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(int)'
ilread.cpp:(.text+0x5f4): undefined reference to `mysqlpp::Query::error() const'
ilread.cpp:(.text+0x64f): undefined reference to `mysqlpp::Connection::~Connection()'
ilread.cpp:(.text+0x76d): undefined reference to `mysqlpp::Connection::~Connection()'
/tmp/cc8vi8ds.o: In function `mysqlpp::DateTime::~DateTime()':
ilread.cpp:(.text._ZN7mysqlpp8DateTimeD2Ev[_ZN7mysqlpp8DateTimeD5Ev]+0xb): undefined reference to `vtable for mysqlpp::DateTime'
/tmp/cc8vi8ds.o: In function `mysqlpp::Query::execute(mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZN7mysqlpp5Query7executeERKNS_14SQLTypeAdapterES3_S3_S3_S3_[mysqlpp::Query::execute(mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&)]+0x74): undefined reference to `mysqlpp::Query::execute(mysqlpp::SQLQueryParms&)'
/tmp/cc8vi8ds.o: In function `mysqlpp::DateTime::DateTime<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
ilread.cpp:(.text._ZN7mysqlpp8DateTimeC2ISsEERKT_[_ZN7mysqlpp8DateTimeC5ISsEERKT_]+0x17): undefined reference to `vtable for mysqlpp::DateTime'
ilread.cpp:(.text._ZN7mysqlpp8DateTimeC2ISsEERKT_[_ZN7mysqlpp8DateTimeC5ISsEERKT_]+0x31): undefined reference to `mysqlpp::DateTime::convert(char const*)'
/tmp/cc8vi8ds.o: In function `__gnu_cxx::new_allocator<mysqlpp::SQLTypeAdapter>::construct(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZN9__gnu_cxx13new_allocatorIN7mysqlpp14SQLTypeAdapterEE9constructEPS2_RKS2_[__gnu_cxx::new_allocator<mysqlpp::SQLTypeAdapter>::construct(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)]+0x2d): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZNSt6vectorIN7mysqlpp14SQLTypeAdapterESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_[std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)]+0x5b): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
ilread.cpp:(.text._ZNSt6vectorIN7mysqlpp14SQLTypeAdapterESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_[std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)]+0xa4): undefined reference to `mysqlpp::SQLTypeAdapter::operator=(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `mysqlpp::SQLTypeAdapter* std::__copy_move_backward<false, false, std::random_access_iterator_tag>::__copy_move_b<mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*)':
ilread.cpp:(.text._ZNSt20__copy_move_backwardILb0ELb0ESt26random_access_iterator_tagE13__copy_move_bIPN7mysqlpp14SQLTypeAdapterES5_EET0_T_S7_S6_[mysqlpp::SQLTypeAdapter* std::__copy_move_backward<false, false, std::random_access_iterator_tag>::__copy_move_b<mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*)]+0x36): undefined reference to `mysqlpp::SQLTypeAdapter::operator=(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `void std::_Construct<mysqlpp::SQLTypeAdapter, mysqlpp::SQLTypeAdapter>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZSt10_ConstructIN7mysqlpp14SQLTypeAdapterES1_EvPT_RKT0_[void std::_Construct<mysqlpp::SQLTypeAdapter, mysqlpp::SQLTypeAdapter>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)]+0x2d): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
collect2: ld returned 1 exit status
root@paul-XPS-M1330:~

```

---

### Post by karlson on 2011-11-04
> **paulten said:**
> Hello, thank you for replying.

Here is what you requested,

```

root@paul-XPS-M1330:~/Documents/fysikk/cpp_sqlite/read/app/ILread# g++ -I/usr/include/mysql -I/usr/local/include/mysql++ -L/usr/lib -lmysqlpp -lmysqlclient -lnsl -lz -lm -o ilread ilread.cpp 
/tmp/cc8vi8ds.o: In function `main':
ilread.cpp:(.text+0xd6): undefined reference to `mysqlpp::Connection::Connection(bool)'
ilread.cpp:(.text+0x10c): undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
ilread.cpp:(.text+0x152): undefined reference to `mysqlpp::Connection::select_db(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
ilread.cpp:(.text+0x18e): undefined reference to `mysqlpp::Connection::query(char const*)'
ilread.cpp:(.text+0x1b5): undefined reference to `mysqlpp::Query::parse()'
ilread.cpp:(.text+0x4ad): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4c5): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4dd): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(double)'
ilread.cpp:(.text+0x4f5): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::DateTime const&)'
ilread.cpp:(.text+0x50b): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(int)'
ilread.cpp:(.text+0x5f4): undefined reference to `mysqlpp::Query::error() const'
ilread.cpp:(.text+0x64f): undefined reference to `mysqlpp::Connection::~Connection()'
ilread.cpp:(.text+0x76d): undefined reference to `mysqlpp::Connection::~Connection()'
/tmp/cc8vi8ds.o: In function `mysqlpp::DateTime::~DateTime()':
ilread.cpp:(.text._ZN7mysqlpp8DateTimeD2Ev[_ZN7mysqlpp8DateTimeD5Ev]+0xb): undefined reference to `vtable for mysqlpp::DateTime'
/tmp/cc8vi8ds.o: In function `mysqlpp::Query::execute(mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZN7mysqlpp5Query7executeERKNS_14SQLTypeAdapterES3_S3_S3_S3_[mysqlpp::Query::execute(mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&, mysqlpp::SQLTypeAdapter const&)]+0x74): undefined reference to `mysqlpp::Query::execute(mysqlpp::SQLQueryParms&)'
/tmp/cc8vi8ds.o: In function `mysqlpp::DateTime::DateTime<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
ilread.cpp:(.text._ZN7mysqlpp8DateTimeC2ISsEERKT_[_ZN7mysqlpp8DateTimeC5ISsEERKT_]+0x17): undefined reference to `vtable for mysqlpp::DateTime'
ilread.cpp:(.text._ZN7mysqlpp8DateTimeC2ISsEERKT_[_ZN7mysqlpp8DateTimeC5ISsEERKT_]+0x31): undefined reference to `mysqlpp::DateTime::convert(char const*)'
/tmp/cc8vi8ds.o: In function `__gnu_cxx::new_allocator<mysqlpp::SQLTypeAdapter>::construct(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZN9__gnu_cxx13new_allocatorIN7mysqlpp14SQLTypeAdapterEE9constructEPS2_RKS2_[__gnu_cxx::new_allocator<mysqlpp::SQLTypeAdapter>::construct(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)]+0x2d): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZNSt6vectorIN7mysqlpp14SQLTypeAdapterESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_[std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)]+0x5b): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
ilread.cpp:(.text._ZNSt6vectorIN7mysqlpp14SQLTypeAdapterESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_[std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> >::_M_insert_aux(__gnu_cxx::__normal_iterator<mysqlpp::SQLTypeAdapter*, std::vector<mysqlpp::SQLTypeAdapter, std::allocator<mysqlpp::SQLTypeAdapter> > >, mysqlpp::SQLTypeAdapter const&)]+0xa4): undefined reference to `mysqlpp::SQLTypeAdapter::operator=(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `mysqlpp::SQLTypeAdapter* std::__copy_move_backward<false, false, std::random_access_iterator_tag>::__copy_move_b<mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*)':
ilread.cpp:(.text._ZNSt20__copy_move_backwardILb0ELb0ESt26random_access_iterator_tagE13__copy_move_bIPN7mysqlpp14SQLTypeAdapterES5_EET0_T_S7_S6_[mysqlpp::SQLTypeAdapter* std::__copy_move_backward<false, false, std::random_access_iterator_tag>::__copy_move_b<mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter*)]+0x36): undefined reference to `mysqlpp::SQLTypeAdapter::operator=(mysqlpp::SQLTypeAdapter const&)'
/tmp/cc8vi8ds.o: In function `void std::_Construct<mysqlpp::SQLTypeAdapter, mysqlpp::SQLTypeAdapter>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)':
ilread.cpp:(.text._ZSt10_ConstructIN7mysqlpp14SQLTypeAdapterES1_EvPT_RKT0_[void std::_Construct<mysqlpp::SQLTypeAdapter, mysqlpp::SQLTypeAdapter>(mysqlpp::SQLTypeAdapter*, mysqlpp::SQLTypeAdapter const&)]+0x2d): undefined reference to `mysqlpp::SQLTypeAdapter::SQLTypeAdapter(mysqlpp::SQLTypeAdapter const&)'
collect2: ld returned 1 exit status
root@paul-XPS-M1330:~

```


Do you have 2 version of mysqlpp installed?  One in /usr/<include, lib> and the other in /usr/local/<include, lib>?

Also, Put the libraries always after the sources or objects.

---

### Post by paulten on 2011-11-04
Sorry about that mixup, I copied that line from my old Makefile which I used in ubuntu 11.04, now in 11.10 I have the files in /usr/include/mysql++ .

But actually your last comment seemed to do the trick!

```


# g++ -I/usr/include/mysql -I/usr/include/mysql++ -L/usr/lib ilread.cpp -lmysqlpp -lmysqlclient -lnsl -lz -lm 

```
All good!
But when I list the libs before the source,
```
  
# make clean
rm -f main *.o
# g++ -I/usr/include/mysql -I/usr/include/mysql++ -L/usr/lib -lmysqlpp -lmysqlclient -lnsl -lz -lm ilread.cpp 
/tmp/ccJe6q88.o: In function `main':
ilread.cpp:(.text+0xd6): undefined reference to `mysqlpp::Connection::Connection(bool)'
ilread.cpp:(.text+0x10c): undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
ilread.cpp:(.text+0x152): undefined reference to `mysqlpp::Connection::select_db(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
ilread.cpp:(.text+0x18e): undefined reference to `mysqlpp::Connection::query(char const*)'


```

To sum it up, from g++: 
> 
Libraries are usually designated with an argument of the form -llibrary-name. In particular, -lg++ denotes a library of standard C++ routines and -lm denotes a library containing various mathematical routines (sine, cosine, arctan, square root, etc.) They must be listed after the object or source files that contain calls to their functions.


Thank you very much for helping me out here!


Thanks,

Paul

---

