---
title: "ubuntu10.10 multi-version linker"
date: 2010-10-13
forum: Programming Talk
---

### Post by melon1234 on 2010-10-13
There are two versions of gcc/g++ on my ubuntu10.10 x64 system.
One is native 4.4.5, the other is 4.1.2 installed from compiling source code. 
It seems each of them work fine because 

   cout<<"Hello"<<endl;

gives correct result.
However when I use g++4.1.2 to compile a bigger project, at the link stage, it complains that:
../../../lib/libXXX.so: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)@GLIBCXX_3.4
undefined reference to `typeinfo for int@CXXABI_1.3'
   ... many many errors about iostream linking failed.

libXXX.so is provided by third party, so I cannot rebuild libXXX.so. What's going on? I really have stdlibc++.so.6 in gcc-4.1.2/lib64. Why doesn't the linker still complain? Is it related to multi-version linker problem?

Thank you in advance.

--
ShenLei

---

