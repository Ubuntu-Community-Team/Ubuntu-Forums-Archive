---
title: "libcurlpp linking problems"
date: 2016-03-08
forum: Packaging and Compiling Programs
---

### Post by Bakerconspiracy on 2016-03-08
Hey hows it going?

I'm trying to compile a simple program with libcurlpp and I'm running into a linker error. I've tried compiling my own libcurl and libcurlpp and installing those to no avail. Lot's of includes and custom -L flags. Here's what it looks like:
```

g++ -std=c++11 -I/usr/local/include -L/usr/local/lib/libcurlpp.so -L/usr/lib/i386-linux-gnu -lstdc++ -lcurl -lcurlpp -lssl -lcrypto leetapi.cpp -o leetapi
leetapi.cpp:(.text+0xb55): undefined reference to `curlpp::Cleanup::Cleanup()'
leetapi.cpp:(.text+0xb63): undefined reference to `curlpp::Easy::Easy()'
leetapi.cpp:(.text+0xbea): undefined reference to `curlpp::Easy::setOpt(curlpp::OptionBase*)'
leetapi.cpp:(.text+0xc58): undefined reference to `curlpp::Easy::setOpt(curlpp::OptionBase*)'
leetapi.cpp:(.text+0xc9e): undefined reference to `curlpp::Easy::setOpt(curlpp::OptionBase*)'
leetapi.cpp:(.text+0xe04): undefined reference to `curlpp::Easy::setOpt(curlpp::OptionBase*)'
leetapi.cpp:(.text+0xe12): undefined reference to `curlpp::Easy::perform()'
leetapi.cpp:(.text+0xe3c): undefined reference to `curlpp::Easy::~Easy()'
leetapi.cpp:(.text+0xe4a): undefined reference to `curlpp::Cleanup::~Cleanup()'
leetapi.cpp:(.text+0x1041): undefined reference to `curlpp::Easy::~Easy()'
leetapi.cpp:(.text+0x1055): undefined reference to `curlpp::Cleanup::~Cleanup()'
/tmp/cc18kpNA.o:(.gcc_except_table+0x19c): undefined reference to `typeinfo for curlpp::LogicError'
/tmp/cc18kpNA.o:(.gcc_except_table+0x1a0): undefined reference to `typeinfo for curlpp::RuntimeError'
/tmp/cc18kpNA.o: In function `curlpp::Option<std::string>::~Option()':
leetapi.cpp:(.text._ZN6curlpp6OptionISsED2Ev[_ZN6curlpp6OptionISsED5Ev]+0x3b): undefined reference to `curlpp::OptionBase::~OptionBase()'
/tmp/cc18kpNA.o: In function `curlpp::Option<bool>::Option(CURLoption, bool const&)':
leetapi.cpp:(.text._ZN6curlpp6OptionIbEC2E10CURLoptionRKb[_ZN6curlpp6OptionIbEC5E10CURLoptionRKb]+0x15): undefined reference to `curlpp::OptionBase::OptionBase(CURLoption)'
leetapi.cpp:(.text._ZN6curlpp6OptionIbEC2E10CURLoptionRKb[_ZN6curlpp6OptionIbEC5E10CURLoptionRKb]+0x49): undefined reference to `curlpp::OptionBase::~OptionBase()'
/tmp/cc18kpNA.o: In function `curlpp::Option<bool>::~Option()':

```

Not sure what exactly is going wrong here, I've been banging my head against the wall for quite a while now. Used dpkg -S to find the libraries and try different things as well.
```

dpkg -S libcurlpp
libcurlpp0:i386: /usr/share/doc/libcurlpp0/copyright
libcurlpp-dev:i386: /usr/lib/i386-linux-gnu/libcurlpp.so
libcurlpp0:i386: /usr/share/doc/libcurlpp0/README
libcurlpp0:i386: /usr/share/doc/libcurlpp0/TODO
libcurlpp0:i386: /usr/share/doc/libcurlpp0/AUTHORS
libcurlpp0:i386: /usr/share/doc/libcurlpp0/changelog.Debian.gz
libcurlpp-dev:i386: /usr/share/doc/libcurlpp-dev
libcurlpp0:i386: /usr/share/doc/libcurlpp0
libcurlpp-dev:i386: /usr/lib/i386-linux-gnu/libcurlpp.a
libcurlpp0:i386: /usr/lib/i386-linux-gnu/libcurlpp.so.0.0.2
libcurlpp0:i386: /usr/lib/i386-linux-gnu/libcurlpp.so.0

```

Any ideas?

---

### Post by steeldriver on 2016-03-08
It's probably a matter of link order - if your .cpp file uses a object that's defined in libcurlpp then -lcurlpp needs to be to the RIGHT of leetapi.cpp 

Likewise, if libcurlcpp needs objects from libcurl

You shouldn't need to explicitly link libstdc++ if you're invoking the compiler as g++

Also -L is for specifying a search path, not a specific library

I would *guess *the command line should look more like

```

g++ -std=c++11 -I/usr/local/include leetapi.cpp -L/usr/local/lib -lcurlpp -lcurl -lssl -lcrypto -o leetapi

```

---

### Post by Bakerconspiracy on 2016-03-08
You da best. =d>

---

