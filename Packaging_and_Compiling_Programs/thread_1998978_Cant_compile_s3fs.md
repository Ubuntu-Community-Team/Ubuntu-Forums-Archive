---
title: "Cant compile s3fs"
date: 2012-06-07
forum: Packaging and Compiling Programs
---

### Post by yaazz on 2012-06-07
I am trying to compile s3fs using the steps in the link below

[https://forums.aws.amazon.com/thread.jspa?messageID=210136&tstart=0]("https://forums.aws.amazon.com/thread.jspa?messageID=210136&tstart=0")

but even though I have installed libcurl4-openssl-dev, the makefile can't seem to locate the library.

here is the makefile included
```
all:
        g++ -ggdb -Wall $(shell pkg-config fuse --cflags --libs) $(shell pkg-config libcurl --cflags --libs) $(shell xml2-config --cflags --libs) -lcrypto s3fs.cpp -o s3fs
        @echo ok!

install: all
        cp -f s3fs /usr/bin

dist: all
        tar -cvzf s3fs.tar.gz -C .. s3fs/COPYING s3fs/Makefile s3fs/s3fs.cpp

clean:
        rm -f s3fs s3fs.o

```


This is the output of the makefile
```
DIRNAME@ip-10-242-197-133:~/s3fs$ sudo make install
g++ -ggdb -Wall -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse  -pthread -lfuse -lrt -ldl    -lcurl   -I/usr/include/libxml2 -L/usr/lib/x86_64-linux-gnu -lxml2 -lcrypto s3fs.cpp -o s3fs
s3fs.cpp: In function ‘std::string calc_signature(std::string, std::string, std::string, curl_slist*, std::string)’:
s3fs.cpp:426:18: warning: value computed is not used [-Wunused-value]
s3fs.cpp: In function ‘int put_local_fd(const char*, headers_t, int)’:
s3fs.cpp:759:63: warning: format ‘%llu’ expects argument of type ‘long long unsigned int’, but argument 4 has type ‘__off_t {aka long int}’ [-Wformat]
s3fs.cpp: In function ‘int s3fs_readlink(const char*, char*, size_t)’:
s3fs.cpp:852:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
s3fs.cpp: At global scope:
s3fs.cpp:440:1: warning: ‘size_t readCallback(void*, size_t, size_t, void*)’ defined but not used [-Wunused-function]
/tmp/ccNw3kXH.o: In function `alloc_curl_handle':
/home/DIRNAME/s3fs/s3fs.cpp:159: undefined reference to `curl_easy_init'
/home/DIRNAME/s3fs/s3fs.cpp:164: undefined reference to `curl_easy_reset'
/home/DIRNAME/s3fs/s3fs.cpp:166: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:172: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:174: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:175: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:176: undefined reference to `curl_easy_setopt'
/tmp/ccNw3kXH.o: In function `my_curl_easy_peDIRNAME':
/home/DIRNAME/s3fs/s3fs.cpp:295: undefined reference to `curl_easy_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:302: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:310: undefined reference to `curl_easy_strerror'
/tmp/ccNw3kXH.o: In function `calc_signature(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, curl_slist*, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/DIRNAME/s3fs/s3fs.cpp:420: undefined reference to `HMAC'
/home/DIRNAME/s3fs/s3fs.cpp:422: undefined reference to `BIO_f_base64'
/home/DIRNAME/s3fs/s3fs.cpp:422: undefined reference to `BIO_new'
/home/DIRNAME/s3fs/s3fs.cpp:423: undefined reference to `BIO_s_mem'
/home/DIRNAME/s3fs/s3fs.cpp:423: undefined reference to `BIO_new'
/home/DIRNAME/s3fs/s3fs.cpp:424: undefined reference to `BIO_push'
/home/DIRNAME/s3fs/s3fs.cpp:425: undefined reference to `BIO_write'
/home/DIRNAME/s3fs/s3fs.cpp:426: undefined reference to `BIO_ctrl'
/home/DIRNAME/s3fs/s3fs.cpp:428: undefined reference to `BIO_ctrl'
/home/DIRNAME/s3fs/s3fs.cpp:433: undefined reference to `BIO_free_all'
/tmp/ccNw3kXH.o: In function `get_headers(char const*, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&)':
/home/DIRNAME/s3fs/s3fs.cpp:513: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:514: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:515: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:516: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:517: undefined reference to `curl_easy_setopt'
/tmp/ccNw3kXH.o:/home/DIRNAME/s3fs/s3fs.cpp:520: more undefined references to `curl_easy_setopt' follow
/tmp/ccNw3kXH.o: In function `get_local_fd(char const*)':
/home/DIRNAME/s3fs/s3fs.cpp:571: undefined reference to `MD5_Init'
/home/DIRNAME/s3fs/s3fs.cpp:576: undefined reference to `MD5_Update'
/home/DIRNAME/s3fs/s3fs.cpp:580: undefined reference to `MD5_Final'
/home/DIRNAME/s3fs/s3fs.cpp:620: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:621: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:622: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:627: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:633: undefined reference to `curl_easy_setopt'
/tmp/ccNw3kXH.o:/home/DIRNAME/s3fs/s3fs.cpp:660: more undefined references to `curl_easy_setopt' follow
/tmp/ccNw3kXH.o: In function `s3fs_getattr':
/home/DIRNAME/s3fs/s3fs.cpp:814: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:820: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:826: undefined reference to `curl_easy_getinfo'
/tmp/ccNw3kXH.o: In function `s3fs_mknod':
/home/DIRNAME/s3fs/s3fs.cpp:901: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:902: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:903: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:904: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:905: undefined reference to `curl_easy_setopt'
/tmp/ccNw3kXH.o:/home/DIRNAME/s3fs/s3fs.cpp:919: more undefined references to `curl_easy_setopt' follow
/tmp/ccNw3kXH.o: In function `s3fs_readdir':
/home/DIRNAME/s3fs/s3fs.cpp:1278: undefined reference to `xmlReadMemory'
/home/DIRNAME/s3fs/s3fs.cpp:1323: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1324: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1325: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1326: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1327: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1331: undefined reference to `curl_slist_append'
/home/DIRNAME/s3fs/s3fs.cpp:1332: undefined reference to `curl_slist_append'
/home/DIRNAME/s3fs/s3fs.cpp:1333: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1336: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1337: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1346: undefined reference to `xmlFreeDoc'
/home/DIRNAME/s3fs/s3fs.cpp:1351: undefined reference to `curl_multi_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:1364: undefined reference to `curl_multi_timeout'
/home/DIRNAME/s3fs/s3fs.cpp:1373: undefined reference to `curl_multi_fdset'
/home/DIRNAME/s3fs/s3fs.cpp:1379: undefined reference to `curl_multi_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:1386: undefined reference to `curl_multi_info_read'
/home/DIRNAME/s3fs/s3fs.cpp:1390: undefined reference to `curl_easy_strerror'
/home/DIRNAME/s3fs/s3fs.cpp:1401: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:1409: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:1414: undefined reference to `curl_easy_getinfo'
/tmp/ccNw3kXH.o: In function `s3fs_init':
/home/DIRNAME/s3fs/s3fs.cpp:1467: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1468: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1470: undefined reference to `CRYPTO_set_locking_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1471: undefined reference to `CRYPTO_set_id_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1472: undefined reference to `curl_global_init'
/tmp/ccNw3kXH.o: In function `s3fs_destroy':
/home/DIRNAME/s3fs/s3fs.cpp:1499: undefined reference to `CRYPTO_set_id_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1500: undefined reference to `CRYPTO_set_locking_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1501: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1505: undefined reference to `curl_global_cleanup'
/tmp/ccNw3kXH.o: In function `main':
/home/DIRNAME/s3fs/s3fs.cpp:1588: undefined reference to `fuse_opt_parse'
/home/DIRNAME/s3fs/s3fs.cpp:1648: undefined reference to `fuse_main_real'
/tmp/ccNw3kXH.o: In function `__static_initialization_and_destruction_0':
/home/DIRNAME/s3fs/s3fs.cpp:370: undefined reference to `EVP_sha1'
/tmp/ccNw3kXH.o: In function `curl_multi_remove_handle_functor::operator()(void*)':
/home/DIRNAME/s3fs/s3fs.cpp:243: undefined reference to `curl_multi_remove_handle'
/tmp/ccNw3kXH.o: In function `auto_curl_multi':
/home/DIRNAME/s3fs/s3fs.cpp:252: undefined reference to `curl_multi_init'
/tmp/ccNw3kXH.o: In function `~auto_curl_multi':
/home/DIRNAME/s3fs/s3fs.cpp:255: undefined reference to `curl_multi_cleanup'
/tmp/ccNw3kXH.o: In function `auto_curl_multi::add_curl(void*)':
/home/DIRNAME/s3fs/s3fs.cpp:262: undefined reference to `curl_multi_add_handle'
/tmp/ccNw3kXH.o: In function `~auto_curl_slist':
/home/DIRNAME/s3fs/s3fs.cpp:272: undefined reference to `curl_slist_free_all'
/tmp/ccNw3kXH.o: In function `auto_curl_slist::append(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
/home/DIRNAME/s3fs/s3fs.cpp:278: undefined reference to `curl_slist_append'
/tmp/ccNw3kXH.o: In function `cleanup_stuff::operator()(std::pair<void*, stuff_t>)':
/home/DIRNAME/s3fs/s3fs.cpp:1209: undefined reference to `curl_slist_free_all'
collect2: ld returned 1 exit status
make: *** [all] Error 1
DIRNAME@ip-10-242-197-133:~/s3fs$ make
g++ -ggdb -Wall -D_FILE_OFFSET_BITS=64 -I/usr/include/fuse  -pthread -lfuse -lrt -ldl    -lcurl   -I/usr/include/libxml2 -L/usr/lib/x86_64-linux-gnu -lxml2 -lcrypto s3fs.cpp -o s3fs
s3fs.cpp: In function ‘std::string calc_signature(std::string, std::string, std::string, curl_slist*, std::string)’:
s3fs.cpp:426:18: warning: value computed is not used [-Wunused-value]
s3fs.cpp: In function ‘int put_local_fd(const char*, headers_t, int)’:
s3fs.cpp:759:63: warning: format ‘%llu’ expects argument of type ‘long long unsigned int’, but argument 4 has type ‘__off_t {aka long int}’ [-Wformat]
s3fs.cpp: In function ‘int s3fs_readlink(const char*, char*, size_t)’:
s3fs.cpp:852:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
s3fs.cpp: At global scope:
s3fs.cpp:440:1: warning: ‘size_t readCallback(void*, size_t, size_t, void*)’ defined but not used [-Wunused-function]
/tmp/cc4ThZa0.o: In function `alloc_curl_handle':
/home/DIRNAME/s3fs/s3fs.cpp:159: undefined reference to `curl_easy_init'
/home/DIRNAME/s3fs/s3fs.cpp:164: undefined reference to `curl_easy_reset'
/home/DIRNAME/s3fs/s3fs.cpp:166: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:172: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:174: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:175: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:176: undefined reference to `curl_easy_setopt'
/tmp/cc4ThZa0.o: In function `my_curl_easy_peDIRNAME':
/home/DIRNAME/s3fs/s3fs.cpp:295: undefined reference to `curl_easy_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:302: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:310: undefined reference to `curl_easy_strerror'
/tmp/cc4ThZa0.o: In function `calc_signature(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, curl_slist*, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
/home/DIRNAME/s3fs/s3fs.cpp:420: undefined reference to `HMAC'
/home/DIRNAME/s3fs/s3fs.cpp:422: undefined reference to `BIO_f_base64'
/home/DIRNAME/s3fs/s3fs.cpp:422: undefined reference to `BIO_new'
/home/DIRNAME/s3fs/s3fs.cpp:423: undefined reference to `BIO_s_mem'
/home/DIRNAME/s3fs/s3fs.cpp:423: undefined reference to `BIO_new'
/home/DIRNAME/s3fs/s3fs.cpp:424: undefined reference to `BIO_push'
/home/DIRNAME/s3fs/s3fs.cpp:425: undefined reference to `BIO_write'
/home/DIRNAME/s3fs/s3fs.cpp:426: undefined reference to `BIO_ctrl'
/home/DIRNAME/s3fs/s3fs.cpp:428: undefined reference to `BIO_ctrl'
/home/DIRNAME/s3fs/s3fs.cpp:433: undefined reference to `BIO_free_all'
/tmp/cc4ThZa0.o: In function `get_headers(char const*, std::map<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&)':
/home/DIRNAME/s3fs/s3fs.cpp:513: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:514: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:515: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:516: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:517: undefined reference to `curl_easy_setopt'
/tmp/cc4ThZa0.o:/home/DIRNAME/s3fs/s3fs.cpp:520: more undefined references to `curl_easy_setopt' follow
/tmp/cc4ThZa0.o: In function `get_local_fd(char const*)':
/home/DIRNAME/s3fs/s3fs.cpp:571: undefined reference to `MD5_Init'
/home/DIRNAME/s3fs/s3fs.cpp:576: undefined reference to `MD5_Update'
/home/DIRNAME/s3fs/s3fs.cpp:580: undefined reference to `MD5_Final'
/home/DIRNAME/s3fs/s3fs.cpp:620: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:621: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:622: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:627: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:633: undefined reference to `curl_easy_setopt'
/tmp/cc4ThZa0.o:/home/DIRNAME/s3fs/s3fs.cpp:660: more undefined references to `curl_easy_setopt' follow
/tmp/cc4ThZa0.o: In function `s3fs_getattr':
/home/DIRNAME/s3fs/s3fs.cpp:814: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:820: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:826: undefined reference to `curl_easy_getinfo'
/tmp/cc4ThZa0.o: In function `s3fs_mknod':
/home/DIRNAME/s3fs/s3fs.cpp:901: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:902: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:903: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:904: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:905: undefined reference to `curl_easy_setopt'
/tmp/cc4ThZa0.o:/home/DIRNAME/s3fs/s3fs.cpp:919: more undefined references to `curl_easy_setopt' follow
/tmp/cc4ThZa0.o: In function `s3fs_readdir':
/home/DIRNAME/s3fs/s3fs.cpp:1278: undefined reference to `xmlReadMemory'
/home/DIRNAME/s3fs/s3fs.cpp:1323: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1324: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1325: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1326: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1327: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1331: undefined reference to `curl_slist_append'
/home/DIRNAME/s3fs/s3fs.cpp:1332: undefined reference to `curl_slist_append'
/home/DIRNAME/s3fs/s3fs.cpp:1333: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1336: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1337: undefined reference to `curl_easy_setopt'
/home/DIRNAME/s3fs/s3fs.cpp:1346: undefined reference to `xmlFreeDoc'
/home/DIRNAME/s3fs/s3fs.cpp:1351: undefined reference to `curl_multi_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:1364: undefined reference to `curl_multi_timeout'
/home/DIRNAME/s3fs/s3fs.cpp:1373: undefined reference to `curl_multi_fdset'
/home/DIRNAME/s3fs/s3fs.cpp:1379: undefined reference to `curl_multi_peDIRNAME'
/home/DIRNAME/s3fs/s3fs.cpp:1386: undefined reference to `curl_multi_info_read'
/home/DIRNAME/s3fs/s3fs.cpp:1390: undefined reference to `curl_easy_strerror'
/home/DIRNAME/s3fs/s3fs.cpp:1401: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:1409: undefined reference to `curl_easy_getinfo'
/home/DIRNAME/s3fs/s3fs.cpp:1414: undefined reference to `curl_easy_getinfo'
/tmp/cc4ThZa0.o: In function `s3fs_init':
/home/DIRNAME/s3fs/s3fs.cpp:1467: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1468: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1470: undefined reference to `CRYPTO_set_locking_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1471: undefined reference to `CRYPTO_set_id_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1472: undefined reference to `curl_global_init'
/tmp/cc4ThZa0.o: In function `s3fs_destroy':
/home/DIRNAME/s3fs/s3fs.cpp:1499: undefined reference to `CRYPTO_set_id_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1500: undefined reference to `CRYPTO_set_locking_callback'
/home/DIRNAME/s3fs/s3fs.cpp:1501: undefined reference to `CRYPTO_num_locks'
/home/DIRNAME/s3fs/s3fs.cpp:1505: undefined reference to `curl_global_cleanup'
/tmp/cc4ThZa0.o: In function `main':
/home/DIRNAME/s3fs/s3fs.cpp:1588: undefined reference to `fuse_opt_parse'
/home/DIRNAME/s3fs/s3fs.cpp:1648: undefined reference to `fuse_main_real'
/tmp/cc4ThZa0.o: In function `__static_initialization_and_destruction_0':
/home/DIRNAME/s3fs/s3fs.cpp:370: undefined reference to `EVP_sha1'
/tmp/cc4ThZa0.o: In function `curl_multi_remove_handle_functor::operator()(void*)':
/home/DIRNAME/s3fs/s3fs.cpp:243: undefined reference to `curl_multi_remove_handle'
/tmp/cc4ThZa0.o: In function `auto_curl_multi':
/home/DIRNAME/s3fs/s3fs.cpp:252: undefined reference to `curl_multi_init'
/tmp/cc4ThZa0.o: In function `~auto_curl_multi':
/home/DIRNAME/s3fs/s3fs.cpp:255: undefined reference to `curl_multi_cleanup'
/tmp/cc4ThZa0.o: In function `auto_curl_multi::add_curl(void*)':
/home/DIRNAME/s3fs/s3fs.cpp:262: undefined reference to `curl_multi_add_handle'
/tmp/cc4ThZa0.o: In function `~auto_curl_slist':
/home/DIRNAME/s3fs/s3fs.cpp:272: undefined reference to `curl_slist_free_all'
/tmp/cc4ThZa0.o: In function `auto_curl_slist::append(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
/home/DIRNAME/s3fs/s3fs.cpp:278: undefined reference to `curl_slist_append'
/tmp/cc4ThZa0.o: In function `cleanup_stuff::operator()(std::pair<void*, stuff_t>)':
/home/DIRNAME/s3fs/s3fs.cpp:1209: undefined reference to `curl_slist_free_all'
collect2: ld returned 1 exit status
make: *** [all] Error 1


```

---

### Post by mikaelcrocker on 2012-06-07
Hey, I don't know what guide you're using, but I've set it up on multiple servers.  I use this guide as a reference

[http://code.google.com/p/s3fs/wiki/FuseOverAmazon](http://code.google.com/p/s3fs/wiki/FuseOverAmazon)

It's worked well for me, and I just ensure that I have all the dependencies installed

---

### Post by MadCow108 on 2012-06-07
libraries must be placed after objects needing their symbols

moving the s3fs.cpp in the makefile after the g++ should do it

---

### Post by yaazz on 2012-06-08
MadCow, that did it for me, thanks!

---

