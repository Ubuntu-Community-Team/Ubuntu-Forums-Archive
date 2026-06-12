---
title: "Need Help Installing MIT SCHEME"
date: 2016-01-17
forum: New to Ubuntu
---

### Post by balls_mahoney2 on 2016-01-17
So I run the top command and all goes well until I get the error  message at the end, and then I try to compile the microcode and I just  can't get it to work. Any help would be greatly appreciated. Thank you  very much.
  superuser@superuser-MS-7817:~/~6.945/mit-scheme-9.2/src$ ./configure --prefix=$SCHEME_INSTALL
  checking for sysconf... yes
  checking for times... yes
  checking for truncate... yes
  checking for uname... yes
  checking for utime... yes
  checking for waitpid... yes
  checking for X... no
  checking for special C compiler options needed for large files... no
  checking for _FILE_OFFSET_BITS value needed for large files... no
  checking for long file names... yes
  checking ncurses.h usability... no
  checking ncurses.h presence... no
  checking for ncurses.h... no
  checking curses.h usability... no
  checking curses.h presence... no
  checking for curses.h... no
  checking term.h usability... no
  checking term.h presence... no
  checking for term.h... no
  checking termcap.h usability... no
  checking termcap.h presence... no
  checking for termcap.h... no
  checking for tgetent in -lncurses... no
  checking for tparm in -lncurses... no
  checking for tparam in -lncurses... no
  checking for tgetent in -lcurses... no
  checking for tparm in -lcurses... no
  checking for tparam in -lcurses... no
  checking for tgetent in -ltermcap... no
  checking for tparm in -ltermcap... no
  checking for tparam in -ltermcap... no
  configure: WARNING: No termcap library found; will emulate it
  checking openssl/blowfish.h usability... no
  checking openssl/blowfish.h presence... no
  checking for openssl/blowfish.h... no
  checking openssl/md5.h usability... no
  checking openssl/md5.h presence... no
  checking for openssl/md5.h... no
  checking mhash.h usability... no
  checking mhash.h presence... no
  checking for mhash.h... no
  checking mcrypt.h usability... no
  checking mcrypt.h presence... no
  checking for mcrypt.h... no
  checking gdbm.h usability... no
  checking gdbm.h presence... no
  checking for gdbm.h... no
  checking db.h usability... no
  checking db.h presence... no
  checking for db.h... no
  checking for pg_config... no
  checking libpq-fe.h usability... no
  checking libpq-fe.h presence... no
  checking for libpq-fe.h... no
  checking for dlopen... no
  checking for dlopen in -ldl... yes
  checking for m4... no
  configure: error: m4 not found
  configure: error: ./configure failed for microcode
  superuser@superuser-MS-7817:~/~6.945/mit-scheme-9.2/src$ sudo make -j9  compile-microcode
  [sudo] password for superuser: 
  (cd microcode && make all)
  make[1]: Entering directory `/home/superuser/~6.945/mit-scheme-9.2/src /microcode'
  make[1]: *** No rule to make target `all'.  Stop.
  make[1]: Leaving directory `/home/superuser/~6.945/mit-scheme-9.2/src /microcode'
  make: *** [compile-microcode] Error 2

---

### Post by sandyd on 2016-01-17
m4 package is missing.

Run
```

sudo apt-get install m4
```
to install.

---

