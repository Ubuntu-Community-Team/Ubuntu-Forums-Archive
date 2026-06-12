---
title: "Cannot find -lssl but openssl is installed!"
date: 2011-07-25
forum: Packaging and Compiling Programs
---

### Post by rickrvo on 2011-07-25
Hi,

I'm trying to compile a Qt application to android with necessitas and I keep getting this error:

```
  p, li { white-space: pre-wrap; }  [COLOR=#be1414]/home/hormonde/necessitas/android-ndk-r5c/toolchains/arm-linux-androideabi-4.4.3/prebuilt/linux-x86/bin/../lib/gcc/arm-linux-androideabi/4.4.3/../../../../arm-linux-androideabi/bin/ld: skipping incompatible /usr/lib/libssl.so when searching for -lssl[/COLOR]
 [COLOR=#be1414]/home/hormonde/necessitas/android-ndk-r5c/toolchains/arm-linux-androideabi-4.4.3/prebuilt/linux-x86/bin/../lib/gcc/arm-linux-androideabi/4.4.3/../../../../arm-linux-androideabi/bin/ld: skipping incompatible /usr/lib/libssl.a when searching for -lssl[/COLOR]
 [COLOR=#be1414]/home/hormonde/necessitas/android-ndk-r5c/toolchains/arm-linux-androideabi-4.4.3/prebuilt/linux-x86/bin/../lib/gcc/arm-linux-androideabi/4.4.3/../../../../arm-linux-androideabi/bin/ld: cannot find -lssl[/COLOR]
 [COLOR=#be1414]collect2: ld returned 1 exit status[/COLOR]
 [COLOR=#3c3c3c]make[1]: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/libz-build-android'[/COLOR]
 [COLOR=#3c3c3c]make: Leaving directory `/home/hormonde/uni_net-student-android-tablet/uni_net-project/libz-build-android'[/COLOR]
 [COLOR=#be1414]make[1]: *** [liblibz.so.1.0.0] Error 1[/COLOR]
 [COLOR=#be1414]make: *** [release] Error 2[/COLOR]
 [COLOR=#be1414]The process "/usr/bin/make" exited with code 2.[/COLOR]
 [COLOR=#be1414]Error while building project libz (target: Android)[/COLOR]
 [COLOR=#be1414]When executing build step 'Make'[/COLOR]

```If I comment the -lssl line in the .pro file the same error occurs with the -lcrypto, -lnsl, and -lpthread...

here is the .pro code for that part:

```
unix:LIBS += -L../staticlib-build-android/ \
    -L../plugins/attendees-build-android \
    -L../libjpeg-build-android \
    -L/home/hormonde/necessitas/android-ndk-r5c/platforms/android-3/arch-arm/usr/lib \
    -L/usr/lib \
    -lz \
    -llibjpeg \
    -lssl \
    -lcrypto \
    -lnsl \
    -lpthread \
    -luni_net \
    -lattendees
```I have openssl installed as well as libssl-dev and libssl0.9.8.

I've already tried reinstalling these packages and nothing seems to work... Does any one know how to fix this?

---

### Post by MadCow108 on 2011-07-25
I have no experience with android but this line:
```
skipping incompatible /usr/lib/libssl.a when searching for -lssl
```
indicates that the ssl library available for linking is for the wrong architecture.
You seem to need an arm library

---

### Post by rickrvo on 2011-07-25
Any idea how I might get an arm library?

thx

---

### Post by rickrvo on 2011-07-26
I remember when I was trying to build this for maemo that I had this -lssl issue too, so I don't know if it has something to do with the architecture target...

Is there different ssl versions? (sorry but I don't understand whats the difference and what is an arm library, I'm kind of linux noob)

---

### Post by rickrvo on 2011-07-29
I fixed the "incompatible libssl.so" errors by abd pulling libssl.co and libcrypto.so from an Android's /system/lib folder.

Now it gives me this errors:

```
 [COLOR=#be1414]release/isd_connection.o: In function `dsaKey::~dsaKey()':[/COLOR]
 [COLOR=#be1414]isd_connection.cpp:(.text._ZN6dsaKeyD1Ev[dsaKey::~dsaKey()]+0x16): undefined reference to `DSA_free'[/COLOR]
 [COLOR=#be1414]release/isd_connection.o: In function `privateDSAKey::privateDSAKey(QString const&, QString const&)':[/COLOR]
 [COLOR=#be1414]isd_connection.cpp:(.text._ZN13privateDSAKeyC1ERK7QStringS2_[privateDSAKey::privateDSAKey(QString const&, QString const&)]+0x54): undefined reference to `DSA_free'[/COLOR]
 [COLOR=#be1414]release/dsa_key.o: In function `~dsaKey':[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/include/dsa_key.h:73: undefined reference to `DSA_free'[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/include/dsa_key.h:73: undefined reference to `DSA_free'[/COLOR]
 [COLOR=#be1414]release/dsa_key.o: In function `createNewDSA()':[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/src/dsa_key.cpp:684: undefined reference to `DSA_new'[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/src/dsa_key.cpp:690: undefined reference to `BN_new'[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/src/dsa_key.cpp:690: undefined reference to `BN_new'[/COLOR]
 [COLOR=#be1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/src/dsa_key.cpp:690: undefined reference to `BN_new'[/COLOR]
 [COLOR=#BE1414]/home/hormonde/uni_net-student-android-tablet/uni_net-project/staticlib-build-android/../staticlib/src/dsa_key.cpp:690: undefined reference to `BN_new'[/COLOR]
[COLOR=#BE1414]...[/COLOR]
[COLOR=#BE1414]...[/COLOR]
[COLOR=#be1414]...
[/COLOR]

```and it goes for every function that is included on #include <openssl/dsa.h>

as I think it has to do with this similar issue as Ó.Egilsson on his last post: [http://groups.google.com/group/android-ndk/browse_thread/thread/74cef4a7d6fec819/cce69b1d4e4dda49](http://groups.google.com/group/android-ndk/browse_thread/thread/74cef4a7d6fec819/cce69b1d4e4dda49) which there errors are supposed to go away if the correct libs are linked... (as the same code runs perfectly on a linux version of the application) 

Does anyone have a clue on how to bypass this issue?

---

### Post by rickrvo on 2011-08-01
please?

---

