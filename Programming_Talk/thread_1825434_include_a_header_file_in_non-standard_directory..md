---
title: "include a header file in non-standard directory."
date: 2011-08-15
forum: Programming Talk
---

### Post by wujj123456 on 2011-08-15
Hello everyone, 

I am trying to compile telex ([https://telex.cc](https://telex.cc)) on Ubuntu 11.04 and I am getting the following error:

```
cc -O3 -Wall -I./req/local/include   -c -o listener.o listener.c
In file included from listener.h:7:0,
                 from listener.c:11:
state.h:7:25: fatal error: openssl/ssl.h: No such file or directory
compilation terminated.
```The required header is a modified openssl/ssl.h in ./req/openssl-1.0.0d/include, and I tried
```
cc -O3 -Wall -I./req/local/include -I./req/openssl-1.0.0d/include  -c -o listener.o listener.c
```but it still didn't work. 

What's the correct way to add a folder for gcc to search for headers? Btw, how do I know the default folders that gcc will search for? 

Thanks.

Solution: My bad. It's not the compiler problem, but a broken link indeed.

---

### Post by dwhitney67 on 2011-08-15
The correct way is the way you have it, using the -I option.

Question... where is this modified ssl.h file?  Is it in ./req/openssl-1.0.0d/include, or in ./req/openssl-1.0.0d/include/openssl?

The source file that is being compiled expects the header file to be in openssl, which is a sub-directory relative to one of the system header file directories (eg. /usr/include) or within one of the paths that you specified using the -I option.

---

### Post by Bachstelze on 2011-08-15
This should work, are you sure that the header file is ./req/openssl-1.0.0d/include/openssl/ssl.h and not e.g. ./req/openssl-1.0.0d/include/ssl.h?

Also you are using gcc, not g++.

---

### Post by wujj123456 on 2011-08-15
> **dwhitney67 said:**
> The correct way is the way you have it, using the -I option.

Question... where is this modified ssl.h file?  Is it in ./req/openssl-1.0.0d/include, or in ./req/openssl-1.0.0d/include/openssl?

The source file that is being compiled expects the header file to be in openssl, which is a sub-directory relative to one of the system header file directories (eg. /usr/include) or within one of the paths that you specified using the -I option.
It's ./req/openssl-1.0.0d/include/openssl/ssl.h. 

Actually I just found the problem. I only used "find . -name ssl.h" to locate ssl.h, but ./req/openssl-1.0.0d/include/openssl/ssl.h is a broken link...

---

