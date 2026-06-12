---
title: "gcc: error: unrecognized command line option '-V' and 'qversion'"
date: 2015-09-28
forum: Packaging and Compiling Programs
---

### Post by mohit9 on 2015-09-28
Dear team,

While configuring netopeer-master's server am getting below errors. 

[root]# ./configure
...
...
..
gcc version 4.8.3 20140911 (Red Hat 4.8.3-9) (GCC)
configure:3458: $? = 0
configure:3447: gcc -V >&5
gcc: [COLOR=#ff0000]error[/COLOR]: unrecognized command line option '-V'
gcc: fatal [COLOR=#ff0000]error[/COLOR]: no input files
compilation terminated.
configure:3458: $? = 4
configure:3447: gcc -qversion >&5
gcc: [COLOR=#ff0000]error[/COLOR]: unrecognized command line option '-qversion'
gcc: fatal [COLOR=#ff0000]error[/COLOR]: no input files
compilation terminated.
configure:3458: $? = 4
configure:3478: checking whether the C compiler works
configure:3500: gcc -Wall -Wextra -O3 /usr/local/bin  -DRCSID=\"$(IDNOGIT)\"  conftest.c /usr/local/bin  >&5
<command-line>:0:8: warning: missing terminating " character [enabled by default]
/usr/local/bin: file not recognized: Is a directory
collect2: [COLOR=#ff0000]error[/COLOR]: ld returned 1 exit status
configure:3504: $? = 1
configure:3542: result: no
...
...
..

Thanks in advance to get me out of these issues.

---

### Post by steeldriver on 2015-09-28
The first 4 of those look like part of the normal automake "probing" process

The last one looks more serious - what is your complete ./configure command? are you setting any relevant environment variables like CFLAGS or LDFLAGS?

---

