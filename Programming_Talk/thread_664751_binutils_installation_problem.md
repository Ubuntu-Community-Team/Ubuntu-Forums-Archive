---
title: "binutils installation problem"
date: 2008-01-11
forum: Programming Talk
---

### Post by oguzhana on 2008-01-11
Hi everybody,
I recently trying to install GNU binutils on my Xubuntu machine. I need them for programming avr microcontrollers. Anyway, I downloaded file binutils-2.15.tar.bz2, extracted it with "tar jxvf" command, and I typed following commands:

cd binutils-2.15/
mkdir obj-avr
cd obj-avr
../configure --target=avr --prefix=/usr/local/avr --disable-nls,

after the last command (../configure etc etc) I took the following message and it stops
[I]
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... avr-unknown-none
checking build system type... i686-pc-linux-gnulibc1
checking for a BSD compatible install... /usr/bin/install -c
*** This configuration is not supported in the following subdirectories:
target-libiberty
(Any other directories should still work fine.)
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
*** The command 'gcc -o conftest -g -O2 conftest.c' failed.
*** You must set the environment variable CC to a working compiler.[/I]

My personal idea is that it is looking for the file in the wrong place. Can anyone tell me what is wrong and what is the solution. Thanks in advance and sorry if it is not the right place to post such a topic.

---

### Post by geirha on 2008-01-11
Seems your problem is that you lack a c compiler (there's no c compiler installed by default). Install the build-essential package which will install the make program, a compiler and some other necessities.

Running the following in a terminal should set you up.
```
sudo aptitude install build-essential
```

---

### Post by geraldm on 2008-01-12
binutils-2.15 has its fourth birthday in May.  I suggest that most of the work in modern microcontrollers is in the newer binutils, the most recent is 2.18 in August, 2007.  It is best to use a more recent version than 2.15.

gierha's  suggestion should get you on the correct path.

Gerald

---

