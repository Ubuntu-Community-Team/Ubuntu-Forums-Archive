---
title: "Error on running squid using make command"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by MicVP on 2013-01-03
Hi Everyone,

I'm new to ubuntu and I'm planning to run squid 3.1.10 on ubuntu server 12.04.1 LTS 64bit. I'm compiling it from a clean source from squid website. I got build-essentials installed and the compilation was successful. When I run the **make** command, I got this error  (these are the last lines) :

g++: warning: switch '-fhuge-objects' is no longer supported
User.cc: In static member function 'static void AuthUser::CachedACLsReset()':
User.cc:161:17: error: variable 'username' set but not used [-Werror=unused-but-set-variable]
cc1plus: all warnings being treated as errors

make[3]: *** [User.lo] Error 1
make[3]: Leaving directory `/root/squid-3.1.10/src/auth'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/squid-3.1.10/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/squid-3.1.10/src'
make: *** [all-recursive] Error 1
root@liklik:~/squid-3.1.10#

Please help me guys. I promise I'll help in return. Happy New Year to all of you.:)

---

### Post by MicVP on 2013-01-03
Please help me guys. Any suggestions? This is my code. I successfully compiled it but after that, when I use the **make** command, I got the error stated above.

**[FONT=&quot]./configure --prefix=/opt/squid/  --with-logdir=/var/log/squid/  --with-pidfile=/var/run/squid.pid  --enable-storeio=ufs, aufs  --enable-removal-policies=lru, heap  --enable-icmp  --enable-useragent-log  --enable-referer-log  --enable-cache-digests  --with-large-files [/FONT]****[FONT=&quot]--enable-delay-pools [/FONT]****[FONT=&quot]--enable-follow-x-forwarded-for[/FONT]****[FONT=&quot] --enable-auth [/FONT]**[B][FONT=&quot]--with-filedescriptors=8192 



[/FONT][/B][FONT=&quot]Help will be much appreciated.[/FONT]

---

### Post by steeldriver on 2013-01-03
I don't understand what you mean - if you "successfully compiled it" why are you running make now? for the install? or did you mean to say you successfully **configured** it? 

Bottom line is, if the makefile has the -Werror=unused-but-set-variable flag set, and the source code has and unused-but-set-variable, then the build is going to fail

Is there any particular reason you need that version? 3.1.19 is in the 12.04 repository

---

