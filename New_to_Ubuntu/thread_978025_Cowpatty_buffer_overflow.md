---
title: "Cowpatty buffer overflow"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by mpow on 2008-11-10
Hi all, I was trying to get cowpatty to work to test my home's wireless since my dad got into a security craze. I get a buffer overflow error when I run ./cowpatty -f dict -r eap-test.dump -s Router'sSSID 
I was wondering if anyone could help me fix this so I can run cowpatty. I am not sure, but I think it might be the fact that the dictionary file has 10000+ lines of text, but I might be wrong. I don't know how all this stuff works too well, so I figured I'd ask the experts. Here is the output of when I run the command minus the memory map section (I wasn't sure what all to post).

cowpatty 4.3 - WPA-PSK dictionary attack. <jwright@hasborg.com>

Collected all necessary data to mount crack against WPA/PSK passphrase.
Starting dictionary attack.  Please be patient.
*** buffer overflow detected ***: ./cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d13558]
/lib/tls/i686/cmov/libc.so.6[0xb7d11680]
./cowpatty[0x804b307]
./cowpatty[0x804b5dc]
./cowpatty[0x804b708]
./cowpatty[0x8049e56]
./cowpatty[0x804a985]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c2f685]
./cowpatty[0x8048cb1]

Thanks in advance for the help,
mpow

---

### Post by Hex on 2008-12-04
I have the same problem, afte encountering the errors during installation in this thread here, [http://ubuntuforums.org/showthread.php?p=6305421#post6305421](http://ubuntuforums.org/showthread.php?p=6305421#post6305421)

---

### Post by ketek90 on 2008-12-10
i have the same problems

i have libssl-dev
and libpcap0.8 dev installed

```
cowpatty 4.3 - WPA-PSK dictionary attack. <jwright@hasborg.com>

Collected all necessary data to mount crack against WPA2/PSK passphrase.
Starting dictionary attack.  Please be patient.
*** buffer overflow detected ***: ./cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d59558]
/lib/tls/i686/cmov/libc.so.6[0xb7d57680]
./cowpatty[0x804b307]
./cowpatty[0x804b5dc]
./cowpatty[0x804b708]
./cowpatty[0x8049e56]
./cowpatty[0x804a985]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c75685]
./cowpatty[0x8048cb1]

```

---

### Post by B34ST1Y on 2008-12-23
*bump* - i'm having THE SAME ISSUE. doesn't ANYONE know how to fix this? Or even what's happening here? it seems to be crashing for no reason

---

### Post by Luinfana on 2009-01-04
I can confirm this as well. I additionally had problems with the latest (4.3) release of the included genpmk tool, but after compiling the oldest available version (4.1), that seems to work now. Unfortunately no version of coWPAtty itself works for me. I get:

```
*** stack smashing detected ***: cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d26558]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7d26510]
cowpatty[0x804a900]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c42685]
cowpatty[0x8048c91]

```

etc etc etc.

Any ideas at all?

---

### Post by almark on 2009-02-11
Try to  compile the cowpatty stuff with an older compiler gcc 4.2, I tried this myself on an ubuntu 8.04 and it works OK...

Regards
Mark

---

### Post by m4ddav3 on 2009-07-13
The buffer overflow is caused by an optimisation made by GCC, because it has the -O2 flag set in C_FLAGS. To fix, edit Makefile and comment out line 14 so it looks like:

```
...
# <dragorn> make is a twisted beast
##################################
LDLIBS          = -lpcap
[COLOR=black]CFLAGS          = -pipe -Wall -DOPENSSL[/COLOR]
[COLOR=DarkRed]#CFLAGS         += -O2[/COLOR]
LDLIBS          += -lcrypto
CFLAGS          += -g3 -ggdb
...
```To fix the other warning, edit genpmk.c, at line 215, the fopen statement should have its result assigned to fpout, like so:

```
                ...
                printf("File %s exists, appending new data.\n", opt.hashfile);
               [COLOR=DarkRed] fpout = fopen(opt.hashfile, "ab");[/COLOR]
                if (fopen == NULL) {
                ...
```A little bit of 'make clean && make' and you should be good to go :-\"

---

### Post by quiniola on 2011-07-09
Thanks m4d! You are the man!

---

