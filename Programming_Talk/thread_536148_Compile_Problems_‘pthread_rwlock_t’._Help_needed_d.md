---
title: "Compile Problems: ‘pthread_rwlock_t’. Help needed desperately"
date: 2007-08-27
forum: Programming Talk
---

### Post by Qazi on 2007-08-27
Hi all,
       I am  a newbie to the Linux community :) and working on a project where I have to compile this code, I am using a Ubuntu kernel version 2.6.16 (drapper drake). Now I have been  helplessly trying to compile but I keep getting the following errors. 


root@enable-laptop:/home/enable/FMIPv6/src/fmipv6_GSABA# make
make  all-recursive
make[1]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA'
Making all in libnetlink
make[2]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA/libnetlink'make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA/libnetlink'
Making all in libmissing
make[2]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA/libmissing'make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA/libmissing'
Making all in src
make[2]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src'
Making all in fmipv6-ar
make[3]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src/fmipv6-ar'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src/fmipv6-ar'
Making all in fmipv6-mn
make[3]: Entering directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src/fmipv6-mn'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I../../src/common   -isystem /usr/src/linux-2.6.16/include/ -Wall -std=gnu99 -g -O2 -MT hokey.o -MD -MP -MF ".deps/hokey.Tpo" -c -o hokey.o hokey.c; \
        then mv -f ".deps/hokey.Tpo" ".deps/hokey.Po"; else rm -f ".deps/hokey.Tpo"; exit 1; fi
In file included from hover_manage.h:36,
                 from hokey.c:5:
listener_list.h:54: error: syntax error before ‘pthread_rwlock_t’
listener_list.h:54: warning: no semicolon at end of struct or union
listener_list.h:56: error: syntax error before ‘}’ token
hokey.c:36: error: syntax error before ‘fmip6_mn_hk_lock’
hokey.c:36: warning: type defaults to ‘int’ in declaration of ‘fmip6_mn_hk_lock’
hokey.c:36: warning: data definition has no type or storage class
hokey.c: In function ‘send_hkreq_tran’:
hokey.c:177: warning: implicit declaration of function ‘pthread_rwlock_wrlock’
hokey.c:187: warning: implicit declaration of function ‘pthread_rwlock_unlock’
hokey.c:73: warning: unused variable ‘mac_authvalue’
hokey.c: In function ‘hokey_mn_recv_hkrsp’:
hokey.c:310: warning: pointer targets in initialisation differ in signedness
hokey.c:390: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
hokey.c:390: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
hokey.c:401: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
hokey.c:406: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
hokey.c:406: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
hokey.c:447: warning: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
hokey.c:447: warning: pointer targets in passing argument 2 of ‘__builtin_strncpy’ differ in signedness
hokey.c:462: warning: ‘return’ with no value, in function returning non-void
hokey.c:307: warning: unused variable ‘i’
hokey.c:298: warning: unused variable ‘pcoa’
hokey.c:295: warning: unused variable ‘auth_value_calc’
hokey.c:293: warning: unused variable ‘auth_value_rece’
hokey.c:291: warning: unused variable ‘lla’
hokey.c: In function ‘hokey_get_timestamp’:
hokey.c:561: warning: assignment makes pointer from integer without a cast
hokey.c:562: warning: assignment from incompatible pointer type
hokey.c:573: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
hokey.c:574: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
hokey.c:574: warning: pointer targets in passing argument 2 of ‘strcat’ differ in signedness
hokey.c:575: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
hokey.c:576: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
hokey.c:576: warning: pointer targets in passing argument 2 of ‘strcat’ differ in signedness
hokey.c:577: warning: pointer targets in passing argument 1 of ‘sprintf’ differ in signedness
hokey.c:578: warning: pointer targets in passing argument 1 of ‘strcat’ differ in signedness
hokey.c:578: warning: pointer targets in passing argument 2 of ‘strcat’ differ in signedness
hokey.c:580: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
hokey.c:580: warning: pointer targets in passing argument 2 of ‘strcpy’ differ in signedness
make[3]: *** [hokey.o] Error 1
make[3]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src/fmipv6-mn'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/enable/FMIPv6/src/fmipv6_GSABA'
make: *** [all] Error 2
root@enable-laptop:/home/enable/FMIPv6/src/fmipv6_GSABA#

-----------
I tried to fix the problems with line 54 and 56 (please see above), but the problem still remains. I think there is nothing wrong with the code. I assume its something to do with ‘pthread_rwlock_t’.I l also seem have pthread library installed as well. This what get when I look for it. 

root@enable-laptop:/home/enable/FMIPv6/src/fmipv6_GSABA# ls /usr/lib |grep pthread
libpthread.a
libpthread_nonshared.a
libpthread.so
root@enable-laptop:/home/enable/FMIPv6/src/fmipv6_GSABA#
-----
  I desperately need some help on this. Can someone PLEASE help me out here. It will well appreciated. Thanks alot. Kind Regards

Qazi Bouland Mussabbir

---

### Post by AlexThomson_NZ on 2007-08-27
I have a little experience with posix threads (no guru though), maybe pthread_rwlock_t has been depreciated or something (I hadn't heard of it)?

---

### Post by Qazi on 2007-08-28
Hi Alex,
         first of all,thanks alot for replying to my post. I was wanted to ask, what exactly do you mean by "pthread_rwlock_t has been depreciated or something" in your previous post.

Can some one please help me on this? 


Regards


Qazi Bouland Mussabbir

---

### Post by AlexThomson_NZ on 2007-08-28
Hi,

What I meant is that may be a fairly old program trying to use a function (pthread_rwlock_t) that is no longer available.  It's a stab in the dark, but was my first instinct.

Cheers

---

### Post by DMills on 2007-08-28
Looks to me like somewhere before hokey.c line 5 (or before you include <pthread.h>, whichever is earlier), you need to #define __USE_UNIX98 to something to get rwlocks defined. 


-D__USE_UNIX98 might not be a bad thing to add to the compiler options?

HTH.

Regards, Dan.

---

### Post by Qazi on 2007-08-29
Hi Dan,
        How do you mean? I tried to put the #define _USE_UNIX98 in the hokey.c file. But still I get the same old errors. I am copying initial part of the hokey.c code so that you have a look at it. If could please kindly  inform me what exactly I would need to type, it would be of help help. Thanks alot for your help. Kind Regards

Qazi Bouland Mussabbir
 

/*===========================================================================*/
/*********Added by yangting on 20070614 for hokey begin*************/

#include <errno.h>
#include "hover_manage.h"
#include "hokey.h"
#include "hmac-sha1.h"

#define FMIP6_MN_DEBUG_LEVEL 3

#if FMIP6_MN_DEBUG_LEVEL >= 1
#define FMDBG dbg
#else
#define FMDBG(x...)
#endif

#if FMIP6_MN_DEBUG_LEVEL >= 2
#define FMDBG2 dbg
#else
#define FMDBG2(x...)
#endif

#if FMIP6_MN_DEBUG_LEVEL >= 3
#define FMDBG3 dbg
#else
#define FMDBG3(x...)
#endif

#if FMIP6_MN_DEBUG_LEVEL >= 4
#define FMDBG4 dbg
#else
#define FMDBG4(x...)
#endif

/*Thread safety when sending HKREQ-s*/
pthread_rwlock_t fmip6_mn_hk_lock;

/**
 * Event dispatching list. Homng allows you to register listeners for 
 * events indicating for example the receipt of an fback or the failure of 
 * an fbu transaction for example
 */
//fmip6_event_listener_list * hokey_listeners = NULL;

uint8_t mn_nonce[16]; //global variable for generating the HK after recieving hkrsp msg
extern struct hk_para ar_hk_para;

---

### Post by DMills on 2007-08-29
Could you post the first 60 lines of listener_list.h?

Somewhere in there, there needs to be a 
#define __USE_UNIX98 1 
or similar, and somewhere after that there needs to be an 
#include <pthread.h>

Basically the required functions are defined in pthread.h if __USE_UNIX98 is defined prior to the inclusion of pthread.h.


HTH.

Regards, Dan.

---

