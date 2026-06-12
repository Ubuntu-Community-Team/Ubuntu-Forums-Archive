---
title: "Need help configuring/fixing Geany"
date: 2009-06-06
forum: Programming Talk
---

### Post by Mirge on 2009-06-06
[IMG]http://www.infinitywebcreations.com/geany.png[/IMG]

The code completion / code hinting / intellisense is wrong... I went to new -> C++ source... when I type getline(... I'd use it like:

```

string name;

cout << "Enter your name please: ";
getline(cin, name);

cout << "Hi there, " << name << endl;

```

But the syntax it shows is not the right C++ syntax. Any idea how to adjust this? Pretty crucial to me... not just for this specific function, but I'd like it to be as accurate as possible in general for C++. Thanks!

---

### Post by Mirge on 2009-06-06
Looks like I need to create a new c99.tags file & move it to ~/.config/geany, but I have no idea how to create a tags file.. I try running:

```

mike@mike-kubuntu:/usr/include/c++/4.3$ geany -g c99.tags ./iostream
Unknown filetype extension for "c99.tags".

```

And... well, you can see the result above.

---

### Post by Mirge on 2009-06-06
Solved it on my own... ls -la my /usr/include/c++/4.3 dir... used the -P flag in geany to disable preprocessing commands (ie: #include)... wrote a quick PHP script to generate the command i needed.. ran it, moved my new c99.tags file to /usr/share/geany/c99.tags (after backing up original)... solved.

In case others need to update their tags file, here's the command I used:

```

geany -g -P c99.tags /usr/include/c++/4.3/algorithm /usr/include/c++/4.3/array /usr/include/c++/4.3/bitset /usr/include/c++/4.3/c++0x_warning.h /usr/include/c++/4.3/cassert /usr/include/c++/4.3/ccomplex /usr/include/c++/4.3/cctype /usr/include/c++/4.3/cerrno /usr/include/c++/4.3/cfenv /usr/include/c++/4.3/cfloat /usr/include/c++/4.3/cinttypes /usr/include/c++/4.3/ciso646 /usr/include/c++/4.3/climits /usr/include/c++/4.3/clocale /usr/include/c++/4.3/cmath /usr/include/c++/4.3/complex /usr/include/c++/4.3/complex.h /usr/include/c++/4.3/csetjmp /usr/include/c++/4.3/csignal /usr/include/c++/4.3/cstdarg /usr/include/c++/4.3/cstdbool /usr/include/c++/4.3/cstddef /usr/include/c++/4.3/cstdint /usr/include/c++/4.3/cstdio /usr/include/c++/4.3/cstdlib /usr/include/c++/4.3/cstring /usr/include/c++/4.3/ctgmath /usr/include/c++/4.3/ctime /usr/include/c++/4.3/cwchar /usr/include/c++/4.3/cwctype /usr/include/c++/4.3/cxxabi-forced.h /usr/include/c++/4.3/cxxabi.h /usr/include/c++/4.3/deque /usr/include/c++/4.3/exception /usr/include/c++/4.3/exception_defines.h /usr/include/c++/4.3/fenv.h /usr/include/c++/4.3/fstream /usr/include/c++/4.3/functional /usr/include/c++/4.3/iomanip /usr/include/c++/4.3/ios /usr/include/c++/4.3/iosfwd /usr/include/c++/4.3/iostream /usr/include/c++/4.3/istream /usr/include/c++/4.3/iterator /usr/include/c++/4.3/limits /usr/include/c++/4.3/list /usr/include/c++/4.3/locale /usr/include/c++/4.3/map /usr/include/c++/4.3/memory /usr/include/c++/4.3/new /usr/include/c++/4.3/numeric /usr/include/c++/4.3/ostream /usr/include/c++/4.3/queue /usr/include/c++/4.3/random /usr/include/c++/4.3/regex /usr/include/c++/4.3/set /usr/include/c++/4.3/sstream /usr/include/c++/4.3/stack /usr/include/c++/4.3/stdexcept /usr/include/c++/4.3/streambuf /usr/include/c++/4.3/string /usr/include/c++/4.3/tgmath.h /usr/include/c++/4.3/tuple /usr/include/c++/4.3/typeinfo /usr/include/c++/4.3/type_traits /usr/include/c++/4.3/unordered_map /usr/include/c++/4.3/unordered_set /usr/include/c++/4.3/utility /usr/include/c++/4.3/valarray /usr/include/c++/4.3/vector

```

---

