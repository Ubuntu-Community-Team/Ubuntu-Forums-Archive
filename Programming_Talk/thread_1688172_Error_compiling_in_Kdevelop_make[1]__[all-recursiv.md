---
title: "Error compiling in Kdevelop make[1]: *** [all-recursive] Error 1"
date: 2011-02-15
forum: Programming Talk
---

### Post by kasparove on 2011-02-15
Hello all,
I'm having some problems when I'm compiling an application.
The messages I receive are:

cd '/home/xxxxxx/appname' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make 
make all-recursive
Entering directory /home/xxxxxx/appname
Making all in src
Entering directory /home/xxxxxx/appname/src
linking appname (g++)
linking appname (g++)
Leaving directory /home/xxxxxx/appname/src
Entering directory /home/xxxxxx/appname
/usr/local/boost_1_40_0/lib/libboost_regex.a(regex_traits_defaults.o):(.data+0x0): multiple definition of `boost::re_detail::def_coll_names'
/home/xxxxxx/appname/src/boost/libboost_regex.a(c_regex_traits_common.o):(.data+0x0): first defined here
/usr/local/boost_1_40_0/lib/libboost_regex.a(regex_traits_defaults.o):(.data+0x220): multiple definition of `boost::re_detail::def_multi_coll'
/home/xxxxxx/appname/src/boost/libboost_regex.a(c_regex_traits_common.o):(.data+0x220): first defined here
ftplib.o: In function `ftplib::Connect(char const*)':
ftplib.cpp:(.text+0x1472): warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
ftplib.cpp:(.text+0x1450): warning: Using 'getservbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
collect2: ld returned 1 exit status
Leaving directory /home/xxxxxx/appname
Entering directory /home/xxxxxx/appname
make[2]: *** [appname] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I hope anyone could help me!
Thanks a lot

---

