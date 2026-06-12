---
title: "Error compiling a simple program that use ip.h header"
date: 2006-05-22
forum: Programming Talk
---

### Post by frankabel on 2006-05-22
Hi all!

I install dapper (typing "server" on installer) . When I try to compile the following simple program:

#include <linux/ip.h>

int main(){
    char data[65535];
    struct iphdr *piphdr;
    piphdr = &data;
    return 0;
}

the following error accur:

In file included from test.c:1:
/usr/include/linux/ip.h:93:2: error: #error "Endian problem - this didn't happen"
test.c: In function ‘main’:
test.c:6: warning: assignment from incompatible pointer type

When I try to compile the same program into a Brezy Desktop the compilation is fine.

How can I solve the problem with the Dapper minimal installation?

Salute
Frank Abel

---

### Post by Harleen on 2006-05-22
I think an additional include before ip.h is needed, to set the defines for Big/Little Endian. Supposed you are on a little Endian machine (PC) try to add
#include <linux/byteorder/little_endian.h>

---

### Post by frankabel on 2006-05-22
Thanks

My solution was use <netinet/ip.h> header instead <linux/ip.h>

---

