---
title: "Kdevelop makefile error??"
date: 2008-06-17
forum: Programming Talk
---

### Post by tacotanker271 on 2008-06-17
Hey guys, I'm new to ubuntu, but have been fooling around with it for a few weeks so I have somewhat of a hold on using it. I ran into a problem when running Kdevelop C++. I write a simple Hello World program and click compile file and I get an error that says 

"/home/fechter/Firstproject/debug
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?"

I click Run them and I get another error that says 

"cd '/home/fechter/Firstproject' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && cd '/home/fechter/Firstproject/debug' && CXXFLAGS="-O0 -g3" "/home/fechter/Firstproject/configure" --enable-debug=full && cd '/home/fechter/Firstproject/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k firstproject.lo
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***"

Anyone know a fix for this problem?

---

