---
title: "helgrind reports strange errors"
date: 2017-12-24
forum: Programming Talk
---

### Post by chuchi on 2017-12-24
Hi everyone!


Using the valgrind tool helgrind, I geterror messages that, in my opinion, should not be reported. This isan example code :


```

#include <stdio.h>


#include <sys/socket.h>
#include <sys/types.h>
#include <netdb.h>
#include <strings.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <string.h>
#include <unistd.h>
#include <pthread.h>


#define NUM_THREADS 3


void* do_test(void *param)
{
    char *host = (char*) param;
    struct hostent *hp;
    struct sockaddr_in addr;


    if ((hp = gethostbyname(host)) ==NULL)
    {
        perror("gethostbyname");
        return NULL;
    }
    memcpy(&addr.sin_addr,hp->h_addr, hp->h_length);


    return NULL;
}


int main(int argc, char *argv[])
{
    pthread_t doRequests[NUM_THREADS];
    char ip[24];
    strcpy(ip, "127.0.0.1");


    for (size_t i = 0; i <NUM_THREADS; i++)
    {
        pthread_create(&doRequests[i],NULL, do_test, ip);
    }


    for (size_t i = 0; i <NUM_THREADS; i++)
    {
        pthread_join(doRequests[i],NULL);
    }


    return 1;
}

```


As you can see, each thread has its ownlocal variables in 'do_test', and there is no global variablesaccessed by different threads.


I used this command to execute theprevious code :


valgrind --tool=helgrind ./shellmain


And this is an excerpt from the errorshelgrind reported :


```

==5060== Possible data race duringwrite of size 1 at 0x658AE08 by thread #4
==5060== Locks held: none
==5060==    at 0x4C371C0: __GI_strcpy(in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5DCCEBC:__nss_hostname_digits_dots (digits_dots.c:164)
==5060==    by 0x5DBBCD6: gethostbyname(getXXbyYY.c:108)
==5060==    by 0x404274: do_test(void*)(shellmain.cpp:22)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060== 
==5060== This conflicts with a previouswrite of size 8 by thread #3
==5060== Locks held: none
==5060==    at 0x5D3126C: __GI_memset(memset.S:65)
==5060==    by 0x5DCCAF4:__nss_hostname_digits_dots (digits_dots.c:124)
==5060==    by 0x5DBBCD6: gethostbyname(getXXbyYY.c:108)
==5060==    by 0x404274: do_test(void*)(shellmain.cpp:22)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060==  Address 0x658ae08 is 40 bytesinside a block of size 1,024 alloc'd
==5060==    at 0x4C2EFAF: malloc (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5DBBE04: gethostbyname(getXXbyYY.c:102)
==5060==    by 0x404274: do_test(void*)(shellmain.cpp:22)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060==  Block was alloc'd by thread#2


==5060== Possible data race during readof size 8 at 0x658ADF0 by thread #4
==5060== Locks held: none
==5060==    at 0x4042A8: do_test(void*)(shellmain.cpp:27)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060== 
==5060== This conflicts with a previouswrite of size 8 by thread #3
==5060== Locks held: none
==5060==    at 0x5D31280: __GI_memset(memset.S:72)
==5060==    by 0x5DCCAF4:__nss_hostname_digits_dots (digits_dots.c:124)
==5060==    by 0x5DBBCD6: gethostbyname(getXXbyYY.c:108)
==5060==    by 0x404274: do_test(void*)(shellmain.cpp:22)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060==  Address 0x658adf0 is 16 bytesinside a block of size 1,024 alloc'd
==5060==    at 0x4C2EFAF: malloc (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5DBBE04: gethostbyname(getXXbyYY.c:102)
==5060==    by 0x404274: do_test(void*)(shellmain.cpp:22)
==5060==    by 0x4C34DB6: ??? (in/usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==5060==    by 0x5A8C6B9: start_thread(pthread_create.c:333)
==5060==    by 0x5DA93DC: clone(clone.S:109)
==5060==  Block was alloc'd by thread#2

```


Helgrind says there is a race conditionbetween the memory read in gethostbyname and the memory write inmemcpy. 


How is this possible? The functiondo_test is executed by each different thread, so each thread willhave different local variables, right?


Thanks a lot!

---

### Post by spjackson on 2017-12-24
gethostbyname() is not re-entrant. It has its own static struct into which it writes its result and it returns the result of that struct.

---

### Post by chuchi on 2017-12-24
Hi spjackson,


Thank you very much for your response!


Because I read in the man pages that gethostbyname is thread safe, I thought I would not have any problem. I also thought that reentrant and thread safe were the same things. But now I am reading in the man pages this function is not reentrant.


So it's time I start to study the differences between reentrant and thread safety.


Thanks again!


All the best

---

### Post by chuchi on 2017-12-24
Ok, after googling now I understand what reentracy is. Even more, the re-entrant alternative to gethostbyname is getaddrinfo. 

Thanks a lot!

---

