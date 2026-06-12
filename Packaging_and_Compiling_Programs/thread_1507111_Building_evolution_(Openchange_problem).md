---
title: "Building evolution (Openchange problem)"
date: 2010-06-11
forum: Packaging and Compiling Programs
---

### Post by dlindend on 2010-06-11
Been using evolution 2.30 for some time now. I build this from source (GIT) using the Makefile from [http://mad-scientist.us/evolution.html](http://mad-scientist.us/evolution.html) (and changing the evolution version in the file to 2.30). Works very good.
Untill I wanted to update, which failed on compiling openchange.

I tried using the beta11 for SAMBA4 which is related, but that gave the same error. Latest test was with beta 9 of samba4 (which worked in my previous version). 
(I can't post in the openchange forum which is closed for new users)

> >>>>> Running build for openchange
make[1]: Map '/home/****/UN/Evolution/obj/openchange' wordt binnengegaan
Compiling libmapi++/src/attachment.cpp with -fPIC
Compiling libmapi++/src/folder.cpp with -fPIC
Compiling libmapi++/src/mapi_exception.cpp with -fPIC
Compiling libmapi++/src/message.cpp with -fPIC
Compiling libmapi++/src/object.cpp with -fPIC
Compiling libmapi++/src/session.cpp with -fPIC
Linking libmapipp.so.0.10
Linking sample application bin/libmapixx-test
libmapi.so.0.10: undefined reference to `smb_iconv_convenience_reinit'
collect2: ld returned 1 exit status
make[1]: *** [bin/libmapixx-test] Fout 1
make[1]: Map '/home/****/UN/Evolution/obj/openchange' wordt verlaten
make: *** [.stamp/openchange.build] Fout 2

---

### Post by edav on 2010-06-15
Hi,  this is because openchange has updated their code to match samba git-master, some functions changed, so if you want to compile latest trunk of libmapi you have two options:  1) update samba 4 to master  2) download the latest revision of libmapi that works with samba alpha 11 which is 1779.

-- Erik

---

