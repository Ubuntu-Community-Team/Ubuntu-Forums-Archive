---
title: "A complete C++ beginner in need!"
date: 2010-11-13
forum: Programming Talk
---

### Post by pooke on 2010-11-13
Hello,

I'm a complete C++ beginner but I'd really like to get going.

I've been looking into some cryptography (just to test things out, of course I'm starting from level 1).

I use Geany if that makes sense in here. Whenever I compile and build some easy examples from, let's say Botan, I always get a:

#include botan/(header file here) not found or regognized

Compile error

...

It happens with basically any header files. When I do "#include <boost/math.h>" (or how u write it.. sorry).

The compiler says the header files cannot be found.

Something like that. And when I build a GTK application from an example, I get "gtk/ui_gtk.h not found" (just roughly from my memory). They are in the same directory! I don't get it.

I have all compilers installed.

Regards,
pooke

---

### Post by Arndt on 2010-11-13
> **pooke said:**
> Hello,

I'm a complete C++ beginner but I'd really like to get going.

I've been looking into some cryptography (just to test things out, of course I'm starting from level 1).

I use Geany if that makes sense in here. Whenever I compile and build some easy examples from, let's say Botan, I always get a:

#include botan/(header file here) not found or regognized

Compile error

...

It happens with basically any header files. When I do "#include <boost/math.h>" (or how u write it.. sorry).

The compiler says the header files cannot be found.

Something like that. And when I build a GTK application from an example, I get "gtk/ui_gtk.h not found" (just roughly from my memory). They are in the same directory! I don't get it.

I have all compilers installed.

Regards,
pooke

The compiler presumably should be told the place (or places) where to start looking for header files. That is typically done with the -I option.

Some packages come with a special script which outputs just what the compiler needs, but many don't.

---

### Post by pooke on 2010-11-13
Hello.

Thanks!

So basically I do this:

$ g++ -I example.cpp -o example.cpp (when I'm in that directory where the example is in)

??

Regards,
pooke

---

### Post by Arndt on 2010-11-13
> **pooke said:**
> Hello.

Thanks!

So basically I do this:

$ g++ -I example.cpp -o example.cpp (when I'm in that directory where the example is in)

??

Regards,
pooke

No, with -I you specify the directory relative to which the header files are looked up. Look at the manual page for g++.

If the code does #include on "inc1/f.hh" and "incl/g.hh", and tjose files are in /home/mary/src/incl/f.hh and /home/mary/src/incl/g.hh, you should say g++ -I/home/mary/src

Besides, -o example.cpp doesn't look like a good idea. -o specifies the output file.

---

### Post by pooke on 2010-11-13
Thanks a bunch, I'll try that. I'll return to you (here) if I get problems.

---

### Post by pooke on 2010-11-13
Hm.. check this;

I took an example from [http://botan.randombit.net/examples/](http://botan.randombit.net/examples/) (ca.cpp)

Tried compile it with g++ in shell. I get this;

ca.cpp:(.text._ZN5Botan19AlgorithmIdentifierD1Ev[Botan::AlgorithmIdentifier::~AlgorithmIdentifier()]+0xd): undefined reference to `vtable for Botan::AlgorithmIdentifier'
/tmp/ccmixNVo.o: In function `Botan::X509_Time::~X509_Time()':
ca.cpp:(.text._ZN5Botan9X509_TimeD1Ev[Botan::X509_Time::~X509_Time()]+0xb): undefined reference to `vtable for Botan::X509_Time'
/tmp/ccmixNVo.o: In function `Botan::X509_Certificate::~X509_Certificate()':
ca.cpp:(.text._ZN5Botan16X509_CertificateD1Ev[Botan::X509_Certificate::~X509_Certificate()]+0xd): undefined reference to `vtable for Botan::X509_Certificate'
/tmp/ccmixNVo.o: In function `Botan::PKCS10_Request::~PKCS10_Request()':
ca.cpp:(.text._ZN5Botan14PKCS10_RequestD1Ev[Botan::PKCS10_Request::~PKCS10_Request()]+0xd): undefined reference to `vtable for Botan::PKCS10_Request'
collect2: ld returned 1 exit status

That's just an extract. The shell is filled with those errors.

Rgds,
pooke

---

