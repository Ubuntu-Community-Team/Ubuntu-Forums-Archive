---
title: "Can't link against libcurl statically"
date: 2017-11-18
forum: Packaging and Compiling Programs
---

### Post by chuchi on 2017-11-18
Hi there!


I am trying to compile my program against libcurl statically, with no success. I have googled so much but found nothing.


I compiled libcurl with this configure instruction :


```

./configure --enable-static

```


This is the instruction I use to compile my program against libcurl :


```

g++ main.cpp -o main -I~/sources/curl-7.56.1/include -I~/sources/curl-7.56.1/lib ~/sources/curl-7.56.1/lib/.libs/libcurl.a

```


And this is the error output I get 


```

/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-version.o): In function `curl_version':
version.c:(.text+0x4b): undefined reference to `zlibVersion'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-version.o): In function `curl_version_info':
version.c:(.text+0x9d): undefined reference to `zlibVersion'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-content_encoding.o): In function `inflate_stream':
content_encoding.c:(.text+0x1bb): undefined reference to `inflate'
content_encoding.c:(.text+0x1d8): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x1f1): undefined reference to `inflateInit2_'
content_encoding.c:(.text+0x275): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x2d4): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x2f1): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x312): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x324): undefined reference to `inflateEnd'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-content_encoding.o): In function `Curl_unencode_deflate_write':
content_encoding.c:(.text+0x3bc): undefined reference to `inflateInit_'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-content_encoding.o): In function `Curl_unencode_gzip_write':
content_encoding.c:(.text+0x57f): undefined reference to `zlibVersion'
content_encoding.c:(.text+0x5b5): undefined reference to `inflateInit2_'
content_encoding.c:(.text+0x601): undefined reference to `inflateInit2_'
content_encoding.c:(.text+0x68b): undefined reference to `inflateEnd'
content_encoding.c:(.text+0x6ca): undefined reference to `inflateEnd'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-content_encoding.o): In function `Curl_unencode_cleanup':
content_encoding.c:(.text+0x7d8): undefined reference to `inflateEnd'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-curl_threads.o): In function `Curl_thread_create':
curl_threads.c:(.text+0x7e): undefined reference to `pthread_create'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-curl_threads.o): In function `Curl_thread_destroy':
curl_threads.c:(.text+0xcd): undefined reference to `pthread_detach'
/home/jesus/sources/curl-7.56.1/lib/.libs/libcurl.a(libcurl_la-curl_threads.o): In function `Curl_thread_join':
curl_threads.c:(.text+0x102): undefined reference to `pthread_join'
collect2: error: ld returned 1 exit status

```


What am I doing wrong? If I compile against the shared library of libcurl, then everything works fine. Why?




Thanks a lot!

---

### Post by steeldriver on 2017-11-18
I think you need to use the static-libs provided by the curl-config utility for the version you installed - based on this SO answer

[static compile of libcurl apps linux C (missing library)]("https://stackoverflow.com/a/9688669")

I was able to build the simple GET example from here

[simple.c]("https://curl.haxx.se/libcurl/c/simple.html")

using

```

gcc -pthread -static simple.c -o simple `~/bin/curl-config --cflags --static-libs` -ldl

```

You will need to change the path to `~/bin/curl-config` to reflect the `--prefix` that you configured/installed curl-7.56.1 to (in my case I used --prefix=$HOME)

---

### Post by chuchi on 2017-11-19
Hi, thanks for your response!


Found the solution, I had to compile also against zlib statically and pthreads. Now this line works :


```

g++ main.cpp -o main-I~/sources/curl-7.56.1/include -I~/sources/curl-7.56.1/lib~/sources/curl-7.56.1/lib/.libs/libcurl.a/home/jesus/sources/zlib-1.2.11/libz.a -lpthread

```


But now I have another problem : I can't access https urls. This sample https code :
[https://curl.haxx.se/libcurl/c/https.html](https://curl.haxx.se/libcurl/c/https.html)


Does not work for me. I get this errormessage:


```

curl_easy_perform() failed: Unsupportedprotocol

```


I am trying to build libcurl againstopenssl with no success. I installed openssl on my system (Ifollowed the instructions described here'[https://curl.haxx.se/docs/install.html](https://curl.haxx.se/docs/install.html)'and I installed openssl in the location /usr/local/ssl ) and configured libcurl with this:


```

./configure --with-ssl 
make

```


But my code still fails. How can Ibuild libcurl with openssl?


Thanks a lot!

---

### Post by chuchi on 2017-11-19
Hi steeldriver! Sorry I missed your -ldl option. Now this works for me:

```

#g++ main.cpp -o main -I~/sources/curl-7.56.1/include -I~/sources/curl-7.56.1/lib ~/sources/curl-7.56.1/lib/.libs/libcurl.a ~/sources/zlib-1.2.11/libz.a ~/sources/openssl-1.0.2m/libssl.a ~/sources/openssl-1.0.2m/libcrypto.a  -lpthread -ldl

```

thanks a lot!

---

