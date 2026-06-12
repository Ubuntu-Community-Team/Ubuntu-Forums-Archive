---
title: "Linking trouble with libpHash c++ library"
date: 2010-10-23
forum: Packaging and Compiling Programs
---

### Post by burthawk101 on 2010-10-23
I'm trying to test out libpHash, a perceptual hashing library written in c++.

I've compiled and installed ffmpeg and libpHash from source because the official packages were giving me some trouble.


Here's the simple program:
```
#include <stdio.h>
#include <iostream>

using namespace std;
#if defined( _MSC_VER) || defined(_BORLANDC_)
typedef unsigned _uint64 ulong64;
typedef signed _int64 long64;
#else
typedef unsigned long long ulong64;
typedef signed long long long64;
#endif
extern int ph_dct_imagehash(const char *file, ulong64 &hash);

int main(){
	char path1[] = "blago1.jpg";
	
	ulong64 hash;
	ph_dct_imagehash(path1, hash);
	cout << "calculated hash: " << hash;
}
```

It looks like the linker can't find the ph_dct_imagehash function:

```

burt@gaeta:~/programming$ g++ test2.cpp -o testhash   -L /usr/local/lib/ -l pHash -Wall
/tmp/ccG4AuTO.o: In function `main':
test2.cpp:(.text+0x43): undefined reference to `ph_dct_imagehash(char const*, unsigned long long&)'
collect2: ld returned 1 exit status

```

The library definitely exists:
```
burt@gaeta:~/programming$ ls /usr/local/lib/ | grep libpHash
libpHash.a
libpHash.la
libpHash.so
libpHash.so.0
libpHash.so.0.0.0
```

I got the prototype from the official documentation here:
[http://phash.org/docs/howto.html](http://phash.org/docs/howto.html)

Any input is greatly appreciated.

---

### Post by SevenMachines on 2010-10-23
I imagine you're missing an include
> #include <pHash.h>

I'd get rid of the extern line too

---

### Post by burthawk101 on 2010-10-23
> **SevenMachines said:**
> I imagine you're missing an include

You were absolutely right. Once I made that change and added /usr/local/lib to LD_LIBRARY_PATH and it compiled and ran without a hitch. 

Thanks!

---

