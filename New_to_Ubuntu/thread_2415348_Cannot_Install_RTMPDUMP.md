---
title: "Cannot Install RTMPDUMP"
date: 2019-03-24
forum: New to Ubuntu
---

### Post by lukepen1998 on 2019-03-24
I am running Ubuntu 18.04 and I am trying to install rtmpdump in order to stream video to a server using FFmpeg. When making rtmpdump it fails, I was wondering if anyone has any idea why
```
git clone git://git.ffmpeg.org/rtmpdump
Cloning into 'rtmpdump'...
remote: Counting objects: 2604, done.
remote: Compressing objects: 100% (965/965), done.
remote: Total 2604 (delta 1962), reused 2148 (delta 1638)
Receiving objects: 100% (2604/2604), 806.24 KiB | 571.00 KiB/s, done.
Resolving deltas: 100% (1962/1962), done.
lukepenrose1@ubuntu:~$ cd rtmpdump
lukepenrose1@ubuntu:~/rtmpdump$ cd libtmp
bash: cd: libtmp: No such file or directory
lukepenrose1@ubuntu:~/rtmpdump$ cd librtmp
lukepenrose1@ubuntu:~/rtmpdump/librtmp$ make clean
rm -f *.o *.a *.so *.so.1 librtmp.pc
lukepenrose1@ubuntu:~/rtmpdump/librtmp$ sudo make install
gcc -Wall   -DRTMPDUMP_VERSION=\"v2.4\" -DUSE_OPENSSL  -O2 -fPIC   -c -o rtmp.o rtmp.c
In file included from handshake.h:86:0,
                 from rtmp.c:152:
dh.h: In function &#8216;DHInit&#8217;:
dh.h:256:12: error: dereferencing pointer to incomplete type &#8216;DH {aka struct dh_st}&#8217;
   MP_new(dh->g);
            ^
dh.h:171:19: note: in definition of macro &#8216;MP_new&#8217;
 #define MP_new(m) m = BN_new()
                   ^
In file included from rtmp.c:152:0:
handshake.h: In function &#8216;InitRC4Encryption&#8217;:
handshake.h:120:12: error: storage size of &#8216;ctx&#8217; isn&#8217;t known
   HMAC_CTX ctx;
            ^~~
In file included from rtmp.c:152:0:
handshake.h:72:35: warning: implicit declaration of function &#8216;HMAC_CTX_init&#8217;; did you mean &#8216;HMAC_CTX_new&#8217;? [-Wimplicit-function-declaration]
 #define HMAC_setup(ctx, key, len) HMAC_CTX_init(&ctx); HMAC_Init_ex(&ctx, key, len, EVP_sha256(), 0)
                                   ^
handshake.h:125:3: note: in expansion of macro &#8216;HMAC_setup&#8217;
   HMAC_setup(ctx, secretKey, 128);
   ^~~~~~~~~~
handshake.h:74:67: warning: implicit declaration of function &#8216;HMAC_CTX_cleanup&#8217;; did you mean &#8216;HMAC_CTX_get_md&#8217;? [-Wimplicit-function-declaration]
 #define HMAC_finish(ctx, dig, dlen) HMAC_Final(&ctx, dig, &dlen); HMAC_CTX_cleanup(&ctx)
                                                                   ^
handshake.h:127:3: note: in expansion of macro &#8216;HMAC_finish&#8217;
   HMAC_finish(ctx, digest, digestLen);
   ^~~~~~~~~~~
In file included from rtmp.c:152:0:
handshake.h:120:12: warning: unused variable &#8216;ctx&#8217; [-Wunused-variable]
   HMAC_CTX ctx;
            ^~~
handshake.h: In function &#8216;HMACsha256&#8217;:
handshake.h:269:12: error: storage size of &#8216;ctx&#8217; isn&#8217;t known
   HMAC_CTX ctx;
            ^~~
handshake.h:269:12: warning: unused variable &#8216;ctx&#8217; [-Wunused-variable]
rtmp.c: In function &#8216;RTMP_ReadPacket&#8217;:
rtmp.c:3555:7: warning: variable &#8216;didAlloc&#8217; set but not used [-Wunused-but-set-variable]
   int didAlloc = FALSE;
       ^~~~~~~~
At top level:
rtmp.c:2907:19: warning: &#8216;av_NetConnection_Connect_Rejected&#8217; defined but not used [-Wunused-const-variable=]
 static const AVal av_NetConnection_Connect_Rejected =
                   ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
rtmp.c:1559:35: warning: &#8216;av_record&#8217; defined but not used [-Wunused-const-variable=]
 #define SAVC(x) static const AVal av_##x = AVC(#x)
                                   ^
rtmp.c:1905:1: note: in expansion of macro &#8216;SAVC&#8217;
 SAVC(record);
 ^~~~
<builtin>: recipe for target 'rtmp.o' failed
make: *** [rtmp.o] Error 1

```

---

### Post by mc4man on 2019-03-26
```
sudo apt install rtmpdump
```
No reason to build. (may already be installed..

---

### Post by lukepen1998 on 2019-03-26
Im using it to stream to DaCast and when streaming it says the "librtmp" is not installed

---

### Post by mc4man on 2019-03-26
> **lukepen1998 said:**
> Im using it to stream to DaCast and when streaming it says the "librtmp" is not installed

If you install rtmpdump then librtmp (librtmp1 in 16.04+ or librtmp0 in 14.04) will be installed. The repo package is fully up to date as the last commit to rtmpdump was Wed, 23 Dec 2015
Or just install librtmp1

edit: if it's actually librtmp support in ffmpeg that you need then you'll need to build ffmpeg yourself as I doubt any ffmpeg packages (repo, ppa or standalone) include that support

---

