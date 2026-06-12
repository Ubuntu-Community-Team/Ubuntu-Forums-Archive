---
title: "errors making binutils"
date: 2010-11-25
forum: Programming Talk
---

### Post by Søren on 2010-11-25
been trying to work out this for about 6 hours now. any genius able to weigh in?

```
ciberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/concat.c -o pic/concat.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/concat.c -o concat.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/cp-demint.c -o pic/cp-demint.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/cp-demint.c -o cp-demint.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/dyn-string.c -o pic/dyn-string.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/dyn-string.c -o dyn-string.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/fdmatch.c -o pic/fdmatch.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/fdmatch.c -o fdmatch.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/fibheap.c -o pic/fibheap.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/fibheap.c -o fibheap.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/filename_cmp.c -o pic/filename_cmp.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/filename_cmp.c -o filename_cmp.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/floatformat.c -o pic/floatformat.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/floatformat.c -o floatformat.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/fnmatch.c -o pic/fnmatch.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/fnmatch.c -o fnmatch.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/fopen_unlocked.c -o pic/fopen_unlocked.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/fopen_unlocked.c -o fopen_unlocked.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/getopt.c -o pic/getopt.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/getopt.c -o getopt.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/getopt1.c -o pic/getopt1.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/getopt1.c -o getopt1.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/getpwd.c -o pic/getpwd.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/getpwd.c -o getpwd.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/getruntime.c -o pic/getruntime.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/getruntime.c -o getruntime.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/hashtab.c -o pic/hashtab.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/hashtab.c -o hashtab.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/hex.c -o pic/hex.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/hex.c -o hex.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/lbasename.c -o pic/lbasename.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/lbasename.c -o lbasename.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/lrealpath.c -o pic/lrealpath.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/lrealpath.c -o lrealpath.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/make-relative-prefix.c -o pic/make-relative-prefix.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/make-relative-prefix.c -o make-relative-prefix.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/make-temp-file.c -o pic/make-temp-file.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/make-temp-file.c -o make-temp-file.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/objalloc.c -o pic/objalloc.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/objalloc.c -o objalloc.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/obstack.c -o pic/obstack.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/obstack.c -o obstack.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/partition.c -o pic/partition.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/partition.c -o partition.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/pexecute.c -o pic/pexecute.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/pexecute.c -o pexecute.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/physmem.c -o pic/physmem.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/physmem.c -o physmem.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/pex-common.c -o pic/pex-common.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/pex-common.c -o pex-common.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/pex-one.c -o pic/pex-one.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/pex-one.c -o pex-one.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c -o pic/pex-unix.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c -o pex-unix.o
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c: In function 'pex_child_error':
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:343: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:344: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:345: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:346: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:347: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:348: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:349: warning: ignoring return value of 'write', declared with attribute warn_unused_result
/mnt/lfs/sources/binutils-2.18/libiberty/pex-unix.c:350: warning: ignoring return value of 'write', declared with attribute warn_unused_result
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/safe-ctype.c -o pic/safe-ctype.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/safe-ctype.c -o safe-ctype.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/sort.c -o pic/sort.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/sort.c -o sort.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/spaces.c -o pic/spaces.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/spaces.c -o spaces.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/splay-tree.c -o pic/splay-tree.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/splay-tree.c -o splay-tree.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/strerror.c -o pic/strerror.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/strerror.c -o strerror.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/strsignal.c -o pic/strsignal.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/strsignal.c -o strsignal.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/unlink-if-ordinary.c -o pic/unlink-if-ordinary.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/unlink-if-ordinary.c -o unlink-if-ordinary.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xatexit.c -o pic/xatexit.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xatexit.c -o xatexit.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xexit.c -o pic/xexit.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xexit.c -o xexit.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xmalloc.c -o pic/xmalloc.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xmalloc.c -o xmalloc.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xmemdup.c -o pic/xmemdup.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xmemdup.c -o xmemdup.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xstrdup.c -o pic/xstrdup.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xstrdup.c -o xstrdup.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xstrerror.c -o pic/xstrerror.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xstrerror.c -o xstrerror.o
if [ x"" != x ]; then \
	  gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic   /mnt/lfs/sources/binutils-2.18/libiberty/xstrndup.c -o pic/xstrndup.o; \
	else true; fi
gcc -c -DHAVE_CONFIG_H -g -O2 -I. -I/mnt/lfs/sources/binutils-2.18/libiberty/../include  -W -Wall -Wwrite-strings -Wc++-compat -Wstrict-prototypes -pedantic  /mnt/lfs/sources/binutils-2.18/libiberty/xstrndup.c -o xstrndup.o
rm -f ./libiberty.a pic/./libiberty.a
ar rc ./libiberty.a \
	  ./regex.o ./cplus-dem.o ./cp-demangle.o ./md5.o ./alloca.o ./argv.o ./choose-temp.o ./concat.o ./cp-demint.o ./dyn-string.o ./fdmatch.o ./fibheap.o ./filename_cmp.o ./floatformat.o ./fnmatch.o ./fopen_unlocked.o ./getopt.o ./getopt1.o ./getpwd.o ./getruntime.o ./hashtab.o ./hex.o ./lbasename.o ./lrealpath.o ./make-relative-prefix.o ./make-temp-file.o ./objalloc.o ./obstack.o ./partition.o ./pexecute.o ./physmem.o ./pex-common.o ./pex-one.o ./pex-unix.o ./safe-ctype.o ./sort.o ./spaces.o ./splay-tree.o ./strerror.o ./strsignal.o ./unlink-if-ordinary.o ./xatexit.o ./xexit.o ./xmalloc.o ./xmemdup.o ./xstrdup.o ./xstrerror.o ./xstrndup.o  
ranlib ./libiberty.a
if [ x"" != x ]; then \
	  cd pic; \
	  ar rc ./libiberty.a \
	    ./regex.o ./cplus-dem.o ./cp-demangle.o ./md5.o ./alloca.o ./argv.o ./choose-temp.o ./concat.o ./cp-demint.o ./dyn-string.o ./fdmatch.o ./fibheap.o ./filename_cmp.o ./floatformat.o ./fnmatch.o ./fopen_unlocked.o ./getopt.o ./getopt1.o ./getpwd.o ./getruntime.o ./hashtab.o ./hex.o ./lbasename.o ./lrealpath.o ./make-relative-prefix.o ./make-temp-file.o ./objalloc.o ./obstack.o ./partition.o ./pexecute.o ./physmem.o ./pex-common.o ./pex-one.o ./pex-unix.o ./safe-ctype.o ./sort.o ./spaces.o ./splay-tree.o ./strerror.o ./strsignal.o ./unlink-if-ordinary.o ./xatexit.o ./xexit.o ./xmalloc.o ./xmemdup.o ./xstrdup.o ./xstrerror.o ./xstrndup.o  ; \
	  ranlib ./libiberty.a; \
	  cd ..; \
	else true; fi
rm -f needed-list; touch needed-list; \
	for f in atexit calloc memchr memcmp memcpy memmove memset rename strchr strerror strncmp strrchr strstr strtol strtoul tmpnam vfprintf vprintf vfork waitpid bcmp bcopy bzero; do \
	  for g in  ; do \
	    case "$g" in \
	      *$f*) echo $g >> needed-list ;; \
	    esac; \
	  done; \
	done
echo ./regex.o ./cplus-dem.o ./cp-demangle.o ./md5.o ./alloca.o ./argv.o ./choose-temp.o ./concat.o ./cp-demint.o ./dyn-string.o ./fdmatch.o ./fibheap.o ./filename_cmp.o ./floatformat.o ./fnmatch.o ./fopen_unlocked.o ./getopt.o ./getopt1.o ./getpwd.o ./getruntime.o ./hashtab.o ./hex.o ./lbasename.o ./lrealpath.o ./make-relative-prefix.o ./make-temp-file.o ./objalloc.o ./obstack.o ./partition.o ./pexecute.o ./physmem.o ./pex-common.o ./pex-one.o ./pex-unix.o ./safe-ctype.o ./sort.o ./spaces.o ./splay-tree.o ./strerror.o ./strsignal.o ./unlink-if-ordinary.o ./xatexit.o ./xexit.o ./xmalloc.o ./xmemdup.o ./xstrdup.o ./xstrerror.o ./xstrndup.o > required-list
make[3]: Entering directory `/mnt/lfs/sources/binutils-build/libiberty/testsuite'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/mnt/lfs/sources/binutils-build/libiberty/testsuite'
make[2]: Leaving directory `/mnt/lfs/sources/binutils-build/libiberty'
make[2]: Entering directory `/mnt/lfs/sources/binutils-build/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/mnt/lfs/sources/binutils-build/intl'
make[2]: Entering directory `/mnt/lfs/sources/binutils-build/bfd'
Making info in doc
make[3]: Entering directory `/mnt/lfs/sources/binutils-build/bfd/doc'
make chew
make[4]: Entering directory `/mnt/lfs/sources/binutils-build/bfd/doc'
gcc -o chew.$$ /mnt/lfs/sources/binutils-2.18/bfd/doc/chew.c \
	  -g -O2   \
	  -I.. -I/mnt/lfs/sources/binutils-2.18/bfd/doc/.. -I/mnt/lfs/sources/binutils-2.18/bfd/doc/../../include -I/mnt/lfs/sources/binutils-2.18/bfd/doc/../../intl -I../../intl; \
	/bin/bash /mnt/lfs/sources/binutils-2.18/bfd/doc/../../move-if-change chew.$$ chew
make[4]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd/doc'
./chew -f /mnt/lfs/sources/binutils-2.18/bfd/doc/doc.str </mnt/lfs/sources/binutils-2.18/bfd/doc/../elf.c >elf.tmp
/bin/bash /mnt/lfs/sources/binutils-2.18/bfd/doc/../../move-if-change elf.tmp elf.texi
restore=: && backupdir=".am$$" && \
	rm -rf $backupdir && mkdir $backupdir && \
	if (/mnt/lfs/sources/binutils-2.18/missing makeinfo --split-size=5000000 --split-size=5000000 --version) >/dev/null 2>&1; then \
	  for f in bfd.info bfd.info-[0-9] bfd.info-[0-9][0-9] bfd.i[0-9] bfd.i[0-9][0-9]; do \
	    if test -f $f; then mv $f $backupdir; restore=mv; else :; fi; \
	  done; \
	else :; fi && \
	if /mnt/lfs/sources/binutils-2.18/missing makeinfo --split-size=5000000 --split-size=5000000   -I /mnt/lfs/sources/binutils-2.18/bfd/doc \
	 -o bfd.info `test -f 'bfd.texinfo' || echo '/mnt/lfs/sources/binutils-2.18/bfd/doc/'`bfd.texinfo; \
	then \
	  rc=0; \
	else \
	  rc=$?; \
	  $restore $backupdir/* `echo "./bfd.info" | sed 's|[^/]*$||'`; \
	fi; \
	rm -rf $backupdir; exit $rc
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [bfd.info] Error 1
make[3]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd/doc'
Making info in po
make[3]: Entering directory `/mnt/lfs/sources/binutils-build/bfd/po'
( if test 'x/mnt/lfs/sources/binutils-2.18/bfd/po' != 'x.'; then \
	    posrcprefix='/mnt/lfs/sources/binutils-2.18/bfd/'; \
	  else \
	    posrcprefix="../"; \
	  fi; \
	  rm -f SRC-POTFILES-t SRC-POTFILES \
	    && (sed -e '/^#/d' \
	            -e '/^[ 	]*$/d' \
		    -e "s@.*@	$posrcprefix& \\\\@" < /mnt/lfs/sources/binutils-2.18/bfd/po/SRC-POTFILES.in \
		| sed -e '$s/\\$//') > SRC-POTFILES-t \
	    && chmod a-w SRC-POTFILES-t \
	    && mv SRC-POTFILES-t SRC-POTFILES )
( rm -f BLD-POTFILES-t BLD-POTFILES \
	    && (sed -e '/^#/d' \
	            -e '/^[ 	]*$/d' \
		    -e "s@.*@	../& \\\\@" < /mnt/lfs/sources/binutils-2.18/bfd/po/BLD-POTFILES.in \
		| sed -e '$s/\\$//') > BLD-POTFILES-t \
	    && chmod a-w BLD-POTFILES-t \
	    && mv BLD-POTFILES-t BLD-POTFILES )
cd .. \
	  && CONFIG_FILES=po/Makefile.in:po/Make-in \
	     CONFIG_HEADERS= /bin/bash ./config.status
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing bfd_stdint.h commands
config.status: executing default commands
make[3]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd/po'
make[3]: Entering directory `/mnt/lfs/sources/binutils-build/bfd/po'
make[3]: Nothing to be done for `info'.
make[3]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd/po'
make[3]: Entering directory `/mnt/lfs/sources/binutils-build/bfd'
make[3]: Nothing to be done for `info-am'.
make[3]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd'
make[2]: *** [info-recursive] Error 1
make[2]: Leaving directory `/mnt/lfs/sources/binutils-build/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/mnt/lfs/sources/binutils-build'
make: *** [all] Error 2
lfs@xxx-desktop:/mnt/lfs/sources/binutils-build$ 
 
```

---

