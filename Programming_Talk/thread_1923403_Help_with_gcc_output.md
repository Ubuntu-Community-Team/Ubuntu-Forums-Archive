---
title: "Help with gcc output"
date: 2012-02-10
forum: Programming Talk
---

### Post by ibrahimtawbe on 2012-02-10
i'm trying 
```
gcc -Wall -Wstrict-prototypes -ansi -pedantic -g 3.3.c -o 3.3
```
```

#include <arpa/inet.h>
#include <netinet/in.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int 
inet_pton_loose(int family, const char *strptr, void *addrptr)
{
    int ret = -1;
    if (family == AF_INET) {
        if (inet_pton(family, strptr, addrptr) == 0) {
            return inet_aton(strptr, addrptr);
        }
    }
    else if (family == AF_INET6) {
        if (inet_pton(family, strptr, addrptr) == 0)
            if (inet_aton(strptr, addrptr) == 1) {
                char * ipv4_mapped_ipv6 = 
                    malloc(strlen(strptr) + 7 ); /* 7= ::FFFF: */
                strcpy(ipv4_mapped_ipv6, "::FFFF:");
                strcpy((ipv4_mapped_ipv6 + 7), strptr);
                ret = inet_pton(family, ipv4_mapped_ipv6, addrptr); 
                free(ipv4_mapped_ipv6);
                return ret;
            }
    }
    return ret;
}

```
getting this warning what is it ? 
```
3.3.c:13: warning: implicit declaration of function ‘inet_aton’
```

---

### Post by Arndt on 2012-02-10
> **ibrahimtawbe said:**
> i'm trying 
```
gcc -Wall -Wstrict-prototypes -ansi -pedantic -g 3.3.c -o 3.3
```
```

#include <arpa/inet.h>
#include <netinet/in.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int 
inet_pton_loose(int family, const char *strptr, void *addrptr)
{
    int ret = -1;
    if (family == AF_INET) {
        if (inet_pton(family, strptr, addrptr) == 0) {
            return inet_aton(strptr, addrptr);
        }
    }
    else if (family == AF_INET6) {
        if (inet_pton(family, strptr, addrptr) == 0)
            if (inet_aton(strptr, addrptr) == 1) {
                char * ipv4_mapped_ipv6 = 
                    malloc(strlen(strptr) + 7 ); /* 7= ::FFFF: */
                strcpy(ipv4_mapped_ipv6, "::FFFF:");
                strcpy((ipv4_mapped_ipv6 + 7), strptr);
                ret = inet_pton(family, ipv4_mapped_ipv6, addrptr); 
                free(ipv4_mapped_ipv6);
                return ret;
            }
    }
    return ret;
}

```
getting this warning what is it ? 
```
3.3.c:13: warning: implicit declaration of function ‘inet_aton’
```

Judging from the manual page for 'inet_aton', you should add -D_BSD_SOURCE to the compiler arguments, or -D_SVID_SOURCE.

---

### Post by ibrahimtawbe on 2012-02-10
thanks , it works 
> 
 Feature Test Macro Requirements for glibc (see feature_test_macros(7)):

       inet_aton(), inet_ntoa(): _BSD_SOURCE || _SVID_SOURCE


---

