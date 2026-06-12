---
title: "memory leak with getaddrinfo_a"
date: 2018-01-02
forum: Programming Talk
---

### Post by chuchi on 2018-01-02
Hi there!


I got a memory leak using the call 'getaddrinfo_a'. This is an example code taken from the Linux man pages:


```

#include <netdb.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main(int argc, char *argv[])
{
    int i, ret;
    struct gaicb * reqs[argc - 1];
    char host[NI_MAXHOST];
    struct addrinfo *res;


    if (argc < 2)
    {
        fprintf(stderr, "Usage: %s HOST...\n", argv[0]);
        exit(EXIT_FAILURE);
    }


    for (i = 0; i < argc - 1; i++)
    {
        reqs[i] = (gaicb*)malloc(sizeof (*reqs[0]));
        if (reqs[i] == NULL)
        {
            perror("malloc");
            exit(EXIT_FAILURE);
        }
        memset(reqs[i], 0, sizeof (*reqs[0]));
        reqs[i]->ar_name = argv[i + 1];
    }


    ret = getaddrinfo_a(GAI_WAIT, reqs, argc - 1, NULL);
    if (ret != 0)
    {
        fprintf(stderr, "getaddrinfo_a() failed: %s\n",
                gai_strerror(ret));
        exit(EXIT_FAILURE);
    }


    for (i = 0; i < argc - 1; i++)
    {
        printf("%s: ", reqs[i]->ar_name);
        ret = gai_error(reqs[i]);
        if (ret == 0)
        {
            res = reqs[i]->ar_result;


            ret = getnameinfo(res->ai_addr, res->ai_addrlen,
                    host, sizeof (host),
                    NULL, 0, NI_NUMERICHOST);
            if (ret != 0)
            {
                fprintf(stderr, "getnameinfo() failed: %s\n",
                        gai_strerror(ret));
                exit(EXIT_FAILURE);
            }
            puts(host);
            
            /*
             * Still got a memory leak with these lines
            freeaddrinfo(reqs[i]->ar_result);
            free (reqs[i]);
            */
        }
        else
        {
            puts(gai_strerror(ret));
        }
    }
    exit(EXIT_SUCCESS);
}

```


I added the commented lines, but still got the memory leak.


And these are the error messages showed by valgrind:


```

==8866== 272 bytes in 1 blocks are possibly lost in loss record 5 of 6
==8866==    at 0x4C2FB55: calloc (in /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so)
==8866==    by 0x40138A4: allocate_dtv (dl-tls.c:322)
==8866==    by 0x40138A4: _dl_allocate_tls (dl-tls.c:539)
==8866==    by 0x541026E: allocate_stack (allocatestack.c:588)
==8866==    by 0x541026E: pthread_create@@GLIBC_2.2.5 (pthread_create.c:539)
==8866==    by 0x4E3B49A: __gai_create_helper_thread (gai_misc.h:113)
==8866==    by 0x4E3B49A: __gai_enqueue_request (gai_misc.c:256)
==8866==    by 0x4E3BBB4: getaddrinfo_a (getaddrinfo_a.c:67)
==8866==    by 0x400AE4: main (getaddrinfo_a_example.cpp:31)
==8866==
==8866== LEAK SUMMARY:
==8866==    definitely lost: 0 bytes in 0 blocks
==8866==    indirectly lost: 0 bytes in 0 blocks
==8866==      possibly lost: 272 bytes in 1 blocks
==8866==    still reachable: 2,588 bytes in 9 blocks
==8866==         suppressed: 0 bytes in 0 blocks
==8866== Reachable blocks (those to which a pointer was found) are not shown.
==8866== To see them, rerun with: --leak-check=full --show-leak-kinds=all
==8866==
==8866== For counts of detected and suppressed errors, rerun with: -v
==8866== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)

```


Why am I having a memory leak with getaddrinfo_a?


Thanks a lot!

---

