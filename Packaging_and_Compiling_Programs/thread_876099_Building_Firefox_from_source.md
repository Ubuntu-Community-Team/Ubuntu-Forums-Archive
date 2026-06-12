---
title: "Building Firefox from source"
date: 2008-07-31
forum: Packaging and Compiling Programs
---

### Post by mlilien on 2008-07-31
I'm trying to build firefox from source in order to test some stuff I've been working with the javascript interpreter.  However, I've run into several problems.  

I've tried compiling the most recent build of FF3, but get this error message:
Cannot mmap file ../../../dist/bin/components/libmozgnome.so

I haven't been able to find any help anywhere about that, so I decided to try using FF2.  However, that gives me the following error message:
TestMinStringAPI.o: In function `test_adopt_sub()':
TestMinStringAPI.cpp:(.text+0x68a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
TestMinStringAPI.o: In function `test_adopt()':
TestMinStringAPI.cpp:(.text+0x73a): undefined reference to `nsMemory::Clone(void const*, unsigned int)'
/usr/bin/ld: TestMinStringAPI: hidden symbol `nsMemory::Clone(void const*, unsigned int)' isn't defined
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: ld returned 1 exit status


Do any of you have any idea what could be causing these errors?  I get them when I try compiling the source without my code as well, so it's nothing that I've added.

Thanks

---

### Post by LinuxRocks713 on 2008-07-31
install build-essential, c headers, libmozembed headers, blah, blah, ...

---

### Post by mlilien on 2008-07-31
I've got build-essential installed.  I'm pretty sure I've got c headers installed.

What package would I find c headers and libmozembed headers in?

Thanks

---

