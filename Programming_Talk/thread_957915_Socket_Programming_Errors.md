---
title: "Socket Programming Errors"
date: 2008-10-24
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-10-24
I wrote a simple port scanner. It compiles under ubuntu, g++. It does not compile under UNIX Solaris! I used g++, but i keep getting these errors:


Undefined                       first referenced
 symbol                             in file
__xnet_connect                      /var/tmp//ccidZvCu.o
__xnet_socket                       /var/tmp//ccidZvCu.o
getaddrinfo                         /var/tmp//ccidZvCu.o
freeaddrinfo                        /var/tmp//ccidZvCu.o
gai_strerror                        /var/tmp//ccidZvCu.o
ld: fatal: Symbol referencing errors. No output written to a.out
collect2: ld returned 1 exit status


Note: code is mixture of C/C++...

---

### Post by snova on 2008-10-24
Two possibilities:


[LIST=1]
[*]You didn't link with the library that contains these functions. They may also be in a different one for Solaris.
[*]Solaris doesn't have these functions.
[/LIST]

---

