---
title: "valgrind reports race conditions when using libcurl"
date: 2021-06-29
forum: Programming Talk
---

### Post by chuchi on 2021-06-29
Hello everyone!


The Valgrind tool 'helgrind' is showing race conditions when I use libcurl in a multithread environment.


For example, if I run this multithread libcurl example under helgrind:


[https://curl.se/libcurl/c/multithread.html](https://curl.se/libcurl/c/multithread.html)


helgrind shows this output:

```


==376392== Helgrind, a thread error detector
==376392== Copyright (C) 2007-2015, and GNU GPL'd, by OpenWorks LLP et al.
==376392== Using Valgrind-3.11.0 and LibVEX; rerun with -h for copyright info
==376392== Command: ./main
==376392== 
Thread 0, gets https://curl.se/
Thread 1, gets ftp://cool.haxx.se/
Thread 2, gets https://www.cag.se/
==376392== ---Thread-Announcement------------------------------------------
==376392== 
==376392== Thread #7 was created
==376392==    at 0x536849E: clone (clone.S:74)
==376392==    by 0x4E46149: create_thread (createthread.c:102)
==376392==    by 0x4E47E83: pthread_create@@GLIBC_2.2.5 (pthread_create.c:679)
==376392==    by 0x4C34BB7: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==376392==    by 0x431461: Curl_thread_create (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x42A51D: Curl_resolver_getaddrinfo (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x43AEA9: Curl_resolv (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x422C0A: Curl_connect (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40F0E5: multi_runsingle (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40FF7D: curl_multi_perform (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x4052EA: curl_easy_perform (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x404D40: pull_one_url(void*) (main.cpp:29)
==376392== 
==376392== ----------------------------------------------------------------
==376392== 
==376392== Possible data race during read of size 4 at 0x8651A44 by thread #7
==376392== Locks held: none
==376392==    at 0x8442189: send_dg (res_send.c:1214)
==376392==    by 0x8442189: __libc_res_nsend (res_send.c:538)
==376392==    by 0x843FD61: __libc_res_nquery (res_query.c:227)
==376392==    by 0x84408F7: __libc_res_nquerydomain (res_query.c:597)
==376392==    by 0x84408F7: __libc_res_nsearch (res_query.c:381)
==376392==    by 0x7230B88: _nss_dns_gethostbyname4_r (dns-host.c:326)
==376392==    by 0x534CD17: gaih_inet (getaddrinfo.c:870)
==376392==    by 0x534FE1D: getaddrinfo (getaddrinfo.c:2425)
==376392==    by 0x430BB1: Curl_getaddrinfo_ex (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x429DAE: getaddrinfo_thread (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x4313FA: curl_thread_create_thunk (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x4C34DB6: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==376392==    by 0x4E476B9: start_thread (pthread_create.c:333)
==376392==  Address 0x8651a44 is 0 bytes inside data symbol "have_sendmmsg.12561"
==376392== 
Thread 3, gets www.haxx.se
==376392== ---Thread-Announcement------------------------------------------
==376392== 
==376392== Thread #6 was created
==376392==    at 0x536849E: clone (clone.S:74)
==376392==    by 0x4E46149: create_thread (createthread.c:102)
==376392==    by 0x4E47E83: pthread_create@@GLIBC_2.2.5 (pthread_create.c:679)
==376392==    by 0x4C34BB7: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==376392==    by 0x404DBD: main (main.cpp:54)
==376392== 
==376392== ---Thread-Announcement------------------------------------------
==376392== 
==376392== Thread #2 was created
==376392==    at 0x536849E: clone (clone.S:74)
==376392==    by 0x4E46149: create_thread (createthread.c:102)
==376392==    by 0x4E47E83: pthread_create@@GLIBC_2.2.5 (pthread_create.c:679)
==376392==    by 0x4C34BB7: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==376392==    by 0x404DBD: main (main.cpp:54)
==376392== 
==376392== ----------------------------------------------------------------
==376392== 
==376392== Possible data race during read of size 1 at 0x944B11 by thread #6
==376392== Locks held: none
==376392==    at 0x452760: ossl_seed (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x455415: ossl_connect_step1 (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x45742D: ossl_connect_common (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x427BF5: Curl_ssl_connect_nonblocking (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x43B285: https_connecting (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x43CB82: Curl_http_connect (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40EF0C: multi_runsingle (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40FF7D: curl_multi_perform (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x4052EA: curl_easy_perform (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x404D40: pull_one_url(void*) (main.cpp:29)
==376392==    by 0x4C34DB6: ??? (in /usr/lib/valgrind/vgpreload_helgrind-amd64-linux.so)
==376392==    by 0x4E476B9: start_thread (pthread_create.c:333)
==376392== 
==376392== This conflicts with a previous write of size 1 by thread #2
==376392== Locks held: none
==376392==    at 0x4527B0: ossl_seed (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x455415: ossl_connect_step1 (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x45742D: ossl_connect_common (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x427BF5: Curl_ssl_connect_nonblocking (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x43B285: https_connecting (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x43CB82: Curl_http_connect (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40EF0C: multi_runsingle (in /local/ae/proyects/cpp/libcurl/main)
==376392==    by 0x40FF7D: curl_multi_perform (in /local/ae/proyects/cpp/libcurl/main)
==376392==  Address 0x944b11 is 0 bytes inside data symbol "ssl_seeded.31922"
==376392== 
Thread 0 terminated
Thread 1 terminated
Thread 2 terminated
Thread 3 terminated
==376392== 
==376392== For counts of detected and suppressed errors, rerun with: -v
==376392== Use --history-level=approx or =none to gain increased speed, at
==376392== the cost of reduced accuracy of conflicting-access information
==376392== ERROR SUMMARY: 4 errors from 2 contexts (suppressed: 23964 from 253)


```

And this is my environment:

openssl-1.1.1k
curl-7.77.0
zlib-1.2.11

If I replace the URLs that use HTTPS shown in the libcurl example by URLs accessing HTTP ([http://locahost/index.html](http://locahost/index.html)), helgrind does not show any race condition at all.

How can I get rid of those race conditions?

Thank you so much!

---

### Post by norobro on 2021-07-03
> **chuchi said:**
> How can I get rid of those race conditions?Don't know if it's possible. Could be a false positive. 

There is an interesting discussion about this, with the curl [developer]("https://hackerone.com/bagder?type=user"), here: [https://hackerone.com/reports/1019457](https://hackerone.com/reports/1019457)

---

