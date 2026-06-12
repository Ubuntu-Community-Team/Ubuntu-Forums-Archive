---
title: "&quot;undefined reference&quot; with g++ compiler in 12.04"
date: 2013-08-24
forum: Packaging and Compiling Programs
---

### Post by mamboknave on 2013-08-24
I'm setting up a new desktop with Ubuntu 12.04, 64b and I'm encountering serious linker problems with g++.

My C++ applications I'm normally compiling in Ubuntu 10.04 64b are NOT compiling anylonger within 12.04.

The failures are all of type "undefined reference".

Here below is a shrunk summary of the compiler output, which is gcc version 4.6.3

The command line, which works perfectly with 10.04, is:

>> g++ -g -Wall -lre2 -lcurl *.cpp ../Repository/*.cpp -std=c++0x

The libraries of curl and re2 were compiled and installed with no evident problems.

I'd be very glad to receive hints and directions for resolving this.

Thank You in advance.

```

/tmp/ccVyfLiu.o: In function `downloadData(int*, char*)':
/home/GetOptionData/getNprepEasy.cpp:124: undefined reference to `curl_slist_append'
.
.
.
/tmp/ccVyfLiu.o: In function `downloadData(int*, char*)':
/home/GetOptionData/getNprepEasy.cpp:137: undefined reference to `curl_global_init'
/home/GetOptionData/getNprepEasy.cpp:140: undefined reference to `curl_easy_init'
/home/GetOptionData/getNprepEasy.cpp:144: undefined reference to `curl_easy_setopt'
.
.
.
/tmp/ccVyfLiu.o: In function `downloadData(int*, char*)':
/home/GetOptionData/getNprepEasy.cpp:164: undefined reference to `curl_easy_perform'
/home/GetOptionData/getNprepEasy.cpp:181: undefined reference to `curl_easy_setopt'
/home/GetOptionData/getNprepEasy.cpp:272: undefined reference to `curl_easy_cleanup'
/home/GetOptionData/getNprepEasy.cpp:274: undefined reference to `curl_global_cleanup'
.
.
.
/tmp/ccvRI9PF.o: In function `parseYC()':
/home/GetOptionData/parseHtmls.cpp:70: undefined reference to `re2::RE2::RE2(char const*)'
/home/GetOptionData/parseHtmls.cpp:73: undefined reference to `re2::RE2::FindAndConsume'
/home/GetOptionData/parseHtmls.cpp:165: undefined reference to `re2::RE2::~RE2()'
.
.
.
/tmp/ccvRI9PF.o: In function `Arg':
/usr/local/include/re2/re2.h:762: undefined reference to `re2::RE2::Arg::parse_char(char const*, int, void*)'
/usr/local/include/re2/re2.h:767: undefined reference to `re2::RE2::Arg::parse_int(char const*, int, void*)'
/usr/local/include/re2/re2.h:774: undefined reference to `re2::RE2::Arg::parse_double(char const*, int, void*)'
/usr/local/include/re2/re2.h:775: undefined reference to `re2::RE2::Arg::parse_string(char const*, int, void*)'

/tmp/ccvRI9PF.o: In function `re2::VariadicFunction2<bool, re2::StringPiece*, re2::RE2 const&, re2::RE2::Arg, &(re2::RE2::FindAndConsumeN(re2::StringPiece*, re2::RE2 const&, re2::RE2::Arg const* const*, int))>::operator()(re2::StringPiece*, re2::RE2 const&, re2::RE2::Arg const&, re2::RE2::Arg const&, re2::RE2::Arg const&) const':
/usr/local/include/re2/variadic_function.h:33: undefined reference to `re2::RE2::FindAndConsumeN(re2::StringPiece*, re2::RE2 const&, re2::RE2::Arg const* const*, int)'
.
.
.

collect2: ld returned 1 exit status

```

---

### Post by steeldriver on 2013-08-24
Try changing the link order - the subordinate libraries need to go AFTER the modules that use them e.g.

```
g++ -g -Wall -std=c++0x *.cpp ../Repository/*.cpp -lcurl -lre2
```

You may need to swap -lcurl and -lre2 - I'm guessing about that

> 
-l library

Search the library named library when linking.  (The second alternative with the library as a separate argument is only for POSIX compliance and is not recommended.)       

It makes a difference where in the command you write this option; the linker searches and processes libraries and object files in the order they are specified.  Thus, ‘foo.o -lz bar.o’ searches library ‘z’ after file foo.o but before bar.o.  If bar.o refers to functions in ‘z’, those functions may not be loaded.


[http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html)

---

### Post by mamboknave on 2013-08-24
Steeldriver: Thanks a lot.
I made it working following your directions.
That's a novelty in 12.04 as in the 10.04 version the gcc didn't care about the position of the arguments in the command line.

---

