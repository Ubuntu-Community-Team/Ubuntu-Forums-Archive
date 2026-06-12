---
title: "[SOLVED] g++ -fshort-wchar option causes stack smashing"
date: 2008-09-04
forum: Programming Talk
---

### Post by Maxim P. Ruban on 2008-09-04
Hello,

I've faced with the following problem: 
If I use -fshort-wchar option, any instance of std::wofstream corrupts the stack and program aborts. 
This does not happen w/o -fshort-wchar.

You may use information below to reproduce this issue:

1. Code sample:

```

#include <fstream>

void smash_stack()
{
	std::wofstream file; 
}

int main()
{
	smash_stack();
	return 0;
}

```

2. Build string
to_compile# g++ -fshort-wchar test.cpp

3. Execution results
maxim@maxim-desktop:~/samples/scriptable/unix$ ./a.out
*** stack smashing detected ***: ./a.out terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d84138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7d840f0]
./a.out(__gxx_personality_v0+0x1e9)[0x8048711]
./a.out(__gxx_personality_v0+0x202)[0x804872a]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cad450]
./a.out(__gxx_personality_v0+0x39)[0x8048561]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:01 59614      /home/maxim/samples/scriptable/unix/a.out
08049000-0804a000 rw-p 00000000 08:01 59614      /home/maxim/samples/scriptable/unix/a.out
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
... (information useless at all)

4. Software versions
OS: Ubuntu 8.04 Hardy Heron
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
C++ (STL) stuff: 4.2

Could anyone, please, kindly address this issue to corresponding persons who are in charge of g++/STL library development?

Thank you in advance,
Maxim.

---

### Post by Zugzwang on 2008-09-04
Looks like this is normal behaviour. See [this bug report]("http://www.mail-archive.com/gcc-bugs@gcc.gnu.org/msg191931.html") and its answers for details.

In summary: The libraries you link against have a  w_char size of 4. If you change it for your programs, you mustn't link against it. However, when using std::wofstream you are using these functions, so the whole thing fails. See also the warning in the GCC documentation w.r.t -fshort-wchar.

---

### Post by Maxim P. Ruban on 2008-09-04
Zugzwang, 

Thank you so much!

I am generally Windows developer, and STL implementation resides in header-files there, so I didnt expect that implementation is in libraries under Linux.


Kind Regards,
Maxim.

---

