---
title: "Compiling a 32 bits program with libcurl on Ubuntu 10.10a 64 bits"
date: 2011-02-02
forum: Packaging and Compiling Programs
---

### Post by toffubu on 2011-02-02
Hi,

I'm trying to compile a program in 32 bits mode on a 64 bits Ubuntu 10.10 but I'm having the following error :

In file included from /usr/include/curl/curl.h:35,
                 from prog.c:2:
/usr/include/curl/curlrules.h:143: error: size of array &#8216;__curl_rule_01__&#8217; is negative
/usr/include/curl/curlrules.h:153: error: size of array &#8216;__curl_rule_02__&#8217; is negative

I'm using :
gcc -g -std=c99 -Wall -m32 $(curl-config --cflags) $(curl-config --libs) -o prog prog.c
which resolve to :
gcc -g -std=c99 -Wall -m32 -lcurl -Wl,-Bsymbolic-functions -o prog prog.c

I've also installed multilib and libcurl 32 bits library version with :
./getlibs -l libcurl.so.4

Any idea ?

---

### Post by SevenMachines on 2011-02-03
Hi, can you post the program or an example program that gives you this error?

---

### Post by toffubu on 2011-02-03
Something very simple :
```

#include <stdio.h>
#include <curl/curl.h>

int main(void)
{
  printf("sizeof(int) = %lu\n", sizeof(int));
  printf("sizeof(long int) = %lu\n", sizeof(long int));

  CURL *curl = curl_easy_init();
  if(curl) {
    curl_easy_setopt(curl, CURLOPT_URL, "http://www.google.com");
    curl_easy_perform(curl);
    curl_easy_cleanup(curl);
  }

  return 0;
}

```

---

### Post by SevenMachines on 2011-02-03
On building, the curl library gets definitions of the sizes of various primitives, 'long' being one of them, and puts it into a header file called curlbuild.h. Usually, on i386 the size is 4, on amd64 its 8. 

Therefore, to cross compile you need not only the targets libraries but also its headers.
i wouldn't use getlibs or these kind of things, instead, download the curl source and ./configure & make install with --prefix=/usr/local/i386 or something like that. You could also download the packages from [http://ie.archive.ubuntu.com/ubuntu/pool/main/c/curl/](http://ie.archive.ubuntu.com/ubuntu/pool/main/c/curl/) and extract them with 'dpkg -x ./' too

For some reason the aclocal check_sizeof macros werent working for me though, there supposed to work cross compiling but... maybe i'm missing something :) In the end i just changed the define myself and the program compiled fine

include/curlbuild.h:
```
 #define CURL_SIZEOF_LONG 4
```This,
```
 error: size of array ‘__curl_rule_01__’ is negative
fail because of the mismatch. 
```is because the sizeof(long) as compared to when the curl library was compiled is different, ie, in
include/curlrules.h:
```
 typedef char  __curl_rule_01__   [CurlchkszEQ(long, CURL_SIZEOF_LONG)];
```long != CURL_SIZEOF_LONG

---

### Post by toffubu on 2011-02-03
Ok, thanks for your answer.
I thought there would be an easier way.

Too bad there is no "include32" like "lib" have "lib32". This way it would be very easy to switch just by using the -m32 flag and you could use the 32 bits packages.

---

### Post by SevenMachines on 2011-02-03
I dont think i've seen a 32/64 bit cross compile thats needed separate headers before this one to be honest. i would have though headers should be applicable across architectures with defines and so on but i'm sure the curl people have done it this way for a reason.

Generally to cross compile i'd tend towards a virtual machine compile, a chroot, locally installed libs, in that order. Virtual machines especially avoid the quirks and the messing about that can happen.

Note in this case, if you just wanted a quick and dirty fix. You could do something like
```
# Make some local directory for headers
$ mkdir -p /usr/local/i386/include/

# Copy 32bit headers across
$ sudo cp  -rf /usr/include/curl/ /usr/local/i386/include/

# Replace the long size definition
$ sudo sed -i 's/#define CURL_SIZEOF_LONG 8/#define CURL_SIZEOF_LONG 4/g' /usr/local/i386/include/curl/curlbuild.h

# Point at the new headers
$ gcc -I/usr/local/i386/include -g -std=c99 -Wall -m32 -lcurl -Wl,-Bsymbolic-functions -o prog prog.c
```

---

### Post by mike.heffner on 2011-02-22
I wonder if the package could handle it like Fedora does:

$ ls /usr/include/curl/curlbuild*
/usr/include/curl/curlbuild-32.h  /usr/include/curl/curlbuild-64.h  /usr/include/curl/curlbuild.h

$ cat /usr/include/curl/curlbuild.h
#include <bits/wordsize.h>

#if __WORDSIZE == 32
#include "curlbuild-32.h"
#elif __WORDSIZE == 64
#include "curlbuild-64.h"
#else
#error "Unknown word size"
#endif

---

### Post by mike.heffner on 2011-02-23
Created bug for this issue here: [https://bugs.launchpad.net/ubuntu/+bug/723739](https://bugs.launchpad.net/ubuntu/+bug/723739)

---

### Post by SevenMachines on 2011-02-23
Good idea. header workaround might be ok. it'd be nice if there was a view on it upstream though

---

