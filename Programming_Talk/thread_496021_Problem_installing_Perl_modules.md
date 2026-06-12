---
title: "Problem installing Perl modules"
date: 2007-07-08
forum: Programming Talk
---

### Post by Mahozamalcha on 2007-07-08
I have recurrent problems installing some perl modules (PadWalker for example). The same problems occur with the cpan shell and when compiling manually. When running make, I get a bunch of errors: some files not found, wrong type expected, and a horde of error: invalid type argument of "unary *" . I get this kind of problems on a lot of completely different modules. Has someone please got any idea of the reason why this happen or what I could try to solve the problem ?

---

### Post by Mr. C. on 2007-07-09
Attempt an install of one of the problematic packages, and show the actual output, starting with the first error messages.

MrC

---

### Post by Mahozamalcha on 2007-07-09
Here is a log of the make step of installation. I give the english translation of the french error messages behind #.

```

####@Niluge:~/perl/PadWalker-1.5$ make
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.5\" -DXS_VERSION=\"1.5\" -fPIC "-I/usr/lib/perl/5.8/CORE"   PadWalker.c
Dans le fichier inclus à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perl.h:420:24: erreur: sys/types.h : Aucun fichier ou répertoire de ce type     #No file or folder of this type
/usr/lib/perl/5.8/CORE/perl.h:451:19: erreur: ctype.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:463:23: erreur: locale.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:480:20: erreur: setjmp.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:486:26: erreur: sys/param.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:491:23: erreur: stdlib.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:496:23: erreur: unistd.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:776:23: erreur: string.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:925:27: erreur: netinet/in.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:929:26: erreur: arpa/inet.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:939:25: erreur: sys/stat.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:961:21: erreur: time.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:968:25: erreur: sys/time.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:975:27: erreur: sys/times.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:982:19: erreur: errno.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:997:25: erreur: sys/socket.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:1024:21: erreur: netdb.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:1127:24: erreur: sys/ioctl.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:1156:23: erreur: dirent.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
          à partir de /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
          à partir de /usr/lib/perl/5.8/CORE/perl.h:1510,
          à partir de PadWalker.xs:2:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: erreur: limits.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de /usr/lib/perl/5.8/CORE/perl.h:2120,
          à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/handy.h:136:25: erreur: inttypes.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de /usr/lib/perl/5.8/CORE/perl.h:2284,
          à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: erreur: signal.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perl.h:2421:33: erreur: pthread.h : Aucun fichier ou répertoire de ce type
In file included from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perl.h:2423: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «perl_os_thread"
/usr/lib/perl/5.8/CORE/perl.h:2424: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «perl_mutex"
/usr/lib/perl/5.8/CORE/perl.h:2425: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «perl_cond"
/usr/lib/perl/5.8/CORE/perl.h:2426: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «perl_key"
Dans le fichier inclus à partir de /usr/lib/perl/5.8/CORE/iperlsys.h:51,
          à partir de /usr/lib/perl/5.8/CORE/perl.h:2733,
          à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perlio.h:65:19: erreur: stdio.h : Aucun fichier ou répertoire de ce type
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perlio.h:259: erreur: expected «)" before «*" token
/usr/lib/perl/5.8/CORE/perlio.h:262: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/perlio.h:265: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/perlio.h:268: erreur: expected declaration specifiers or «..." before «FILE"
In file included from /usr/lib/perl/5.8/CORE/perl.h:2747,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/sv.h:389: erreur: expected specifier-qualifier-list before «DIR"
Dans le fichier inclus à partir de /usr/lib/perl/5.8/CORE/op.h:497,
          à partir de /usr/lib/perl/5.8/CORE/perl.h:2754,
          à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/reentr.h:72:20: erreur: pwd.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/reentr.h:75:20: erreur: grp.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/reentr.h:85:26: erreur: crypt.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/reentr.h:90:27: erreur: shadow.h : Aucun fichier ou répertoire de ce type
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/reentr.h:612: erreur: field «_crypt_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:620: erreur: field «_drand48_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:624: erreur: field «_grent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:635: erreur: field «_hostent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:654: erreur: field «_netent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:669: erreur: field «_protoent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:684: erreur: field «_pwent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:695: erreur: field «_servent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:710: erreur: field «_spent_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:721: erreur: field «_gmtime_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:724: erreur: field «_localtime_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:771: erreur: field «_random_struct" has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:772: erreur: expected specifier-qualifier-list before «int32_t"
In file included from /usr/lib/perl/5.8/CORE/perl.h:2756,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/av.h:13: erreur: expected specifier-qualifier-list before «ssize_t"
In file included from /usr/lib/perl/5.8/CORE/perl.h:2759,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/scope.h:232: erreur: expected specifier-qualifier-list before «sigjmp_buf"
In file included from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perl.h:2931: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «getuid"
/usr/lib/perl/5.8/CORE/perl.h:2932: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «geteuid"
/usr/lib/perl/5.8/CORE/perl.h:2933: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «getgid"
/usr/lib/perl/5.8/CORE/perl.h:2934: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «getegid"
Dans le fichier inclus à partir de PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perl.h:3238:22: erreur: math.h : Aucun fichier ou répertoire de ce type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3881,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/thrdvar.h:85: erreur: field «Tstatbuf" has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:86: erreur: field «Tstatcache" has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:91: erreur: field «Ttimesbuf" has incomplete type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3883,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: erreur: expected specifier-qualifier-list before «time_t"
In file included from /usr/lib/perl/5.8/CORE/perl.h:3950,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/proto.h:128: erreur: expected declaration specifiers or «..." before «mode_t"
/usr/lib/perl/5.8/CORE/proto.h:128: erreur: expected declaration specifiers or «..." before «uid_t"
/usr/lib/perl/5.8/CORE/proto.h:297: erreur: expected declaration specifiers or «..." before «off64_t"
/usr/lib/perl/5.8/CORE/proto.h:299: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_do_sysseek"
/usr/lib/perl/5.8/CORE/proto.h:300: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_do_tell"
/usr/lib/perl/5.8/CORE/proto.h:411: erreur: expected declaration specifiers or «..." before «gid_t"
/usr/lib/perl/5.8/CORE/proto.h:411: erreur: expected declaration specifiers or «..." before «uid_t"
/usr/lib/perl/5.8/CORE/proto.h:736: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_my_fork"
/usr/lib/perl/5.8/CORE/proto.h:1020: erreur: expected declaration specifiers or «..." before «pid_t"
/usr/lib/perl/5.8/CORE/proto.h:1300: erreur: expected declaration specifiers or «..." before «pid_t"
/usr/lib/perl/5.8/CORE/proto.h:1456: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/proto.h:2001: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_PerlIO_read"
/usr/lib/perl/5.8/CORE/proto.h:2002: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_PerlIO_write"
/usr/lib/perl/5.8/CORE/proto.h:2003: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_PerlIO_unread"
/usr/lib/perl/5.8/CORE/proto.h:2004: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «Perl_PerlIO_tell"
/usr/lib/perl/5.8/CORE/proto.h:2005: erreur: expected declaration specifiers or «..." before «off64_t"
In file included from /usr/lib/perl/5.8/CORE/perl.h:3988,
                 from PadWalker.xs:2:
/usr/lib/perl/5.8/CORE/perlvars.h:31: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «PL_thr_key"
/usr/lib/perl/5.8/CORE/perlvars.h:48: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «PL_op_mutex"
/usr/lib/perl/5.8/CORE/perlvars.h:52: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «PL_dollarzero_mutex"
/usr/lib/perl/5.8/CORE/perl.h:4485:24: erreur: sys/ipc.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:4486:24: erreur: sys/sem.h : Aucun fichier ou répertoire de ce type
/usr/lib/perl/5.8/CORE/perl.h:4611:24: erreur: sys/file.h : Aucun fichier ou répertoire de ce type
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:38,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from PadWalker.xs:3:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/intrpvar.h:237: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/intrpvar.h:238: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/intrpvar.h:239: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/intrpvar.h:240: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:39,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from PadWalker.xs:3:
/usr/lib/perl/5.8/CORE/perlvars.h:31: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/perlvars.h:48: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
/usr/lib/perl/5.8/CORE/perlvars.h:52: erreur: expected «=", «,", «;", «asm" or «__attribute__" before «*" token
PadWalker.xs: In function «dopoptosub":
PadWalker.xs:97: erreur: invalid type argument of «unary *"
PadWalker.xs:97: erreur: invalid type argument of «unary *"
PadWalker.xs: In function «upcontext":
PadWalker.xs:105: erreur: invalid type argument of «unary *"
PadWalker.xs:106: erreur: invalid type argument of «unary *"
PadWalker.xs:106: erreur: invalid type argument of «unary *"
PadWalker.xs:107: erreur: invalid type argument of «unary *"
PadWalker.xs:109: erreur: invalid type argument of «unary *"
PadWalker.xs:116: erreur: invalid type argument of «unary *"
PadWalker.xs:126: erreur: invalid type argument of «unary *"
PadWalker.xs:127: erreur: invalid type argument of «unary *"
PadWalker.xs:133: erreur: invalid type argument of «unary *"
PadWalker.xs: In function «fetch_from_stash":
PadWalker.xs:152: attention : incompatible implicit declaration of built-in function «strlen"
PadWalker.xs:153: attention : incompatible implicit declaration of built-in function «strcpy"
PadWalker.xs:154: attention : incompatible implicit declaration of built-in function «strcat"
PadWalker.xs:160: erreur: invalid type argument of «unary *"
PadWalker.xs:161: erreur: invalid type argument of «unary *"
PadWalker.xs:162: erreur: invalid type argument of «unary *"
PadWalker.xs: In function «pads_into_hash":
PadWalker.xs:183: erreur: invalid type argument of «unary *"
PadWalker.xs:184: erreur: invalid type argument of «unary *"
PadWalker.xs:211: erreur: invalid type argument of «unary *"
PadWalker.xs:212: erreur: invalid type argument of «unary *"
PadWalker.xs:213: attention : incompatible implicit declaration of built-in function «strlen"
PadWalker.xs:223: erreur: invalid type argument of «unary *"
PadWalker.xs:224: erreur: invalid type argument of «unary *"
PadWalker.xs:233: erreur: invalid type argument of «unary *"
PadWalker.xs:238: erreur: invalid type argument of «unary *"
PadWalker.xs:239: erreur: invalid type argument of «unary *"
PadWalker.xs:242: erreur: invalid type argument of «unary *"
PadWalker.xs:242: erreur: invalid type argument of «unary *"
PadWalker.xs: In function «padlist_into_hash":
PadWalker.xs:259: erreur: invalid type argument of «unary *"
PadWalker.xs:260: erreur: invalid type argument of «unary *"
PadWalker.xs: In function «do_peek":
PadWalker.xs:304: erreur: invalid type argument of «unary *"
PadWalker.xs:307: erreur: invalid type argument of «unary *"
PadWalker.xs:311: erreur: invalid type argument of «unary *"
PadWalker.xs:315: erreur: invalid type argument of «unary *"
PadWalker.xs:347: erreur: invalid type argument of «unary *"
PadWalker.xs:348: attention : incompatible implicit declaration of built-in function «exit"
PadWalker.xs:348: erreur: «EXIT_FAILURE" undeclared (first use in this function)
PadWalker.xs:348: erreur: (Each undeclared identifier is reported only once
PadWalker.xs:348: erreur: for each function it appears in.)
PadWalker.xs: In function «get_closed_over":
PadWalker.xs:358: erreur: invalid type argument of «unary *"
PadWalker.xs:359: erreur: invalid type argument of «unary *"
PadWalker.xs:363: erreur: invalid type argument of «unary *"
PadWalker.xs:364: erreur: invalid type argument of «unary *"
PadWalker.xs:369: attention : incompatible implicit declaration of built-in function «strlen"
PadWalker.xs:372: erreur: invalid type argument of «unary *"
PadWalker.xs:373: erreur: invalid type argument of «unary *"
PadWalker.xs:381: erreur: invalid type argument of «unary *"
PadWalker.xs:381: erreur: invalid type argument of «unary *"
PadWalker.xs:385: erreur: invalid type argument of «unary *"
PadWalker.xs:386: erreur: invalid type argument of «unary *"
PadWalker.xs:386: erreur: invalid type argument of «unary *"
PadWalker.xs:387: erreur: invalid type argument of «unary *"

```

Follows a lot of the same invalid type argument errors...
I can also tell you that I don't remember having this problem with Edgy Eft, and that I have this problem on two different computers.
Thanks for your help !

---

### Post by Mr. C. on 2007-07-09
The first error yields the answer:

> /usr/lib/perl/5.8/CORE/perl.h:420:24: erreur: sys/types.h : Aucun fichier ou répertoire de ce type     #No file or folder of this type


You are missing essential include files.  Do an 

```
apt get build-essentials
```

and try again.

MrC

---

### Post by Mahozamalcha on 2007-07-09
Thanks a bunch, that solved my problem ! I felt I was missing something, but didn't know enough about Ubuntu to know what it was. Again, thanks a lot for your help, everything compiles flawlessly now !

---

