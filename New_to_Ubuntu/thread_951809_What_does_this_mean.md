---
title: "What does this mean?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jstocky on 2008-10-18
Please help a newbie! :)

what does this mean?

stocky@Nick:~$ dir
airsnort-0.2.7e  Documents  Music     Public	 Videos
Desktop		 Examples   Pictures  Templates  weplab-0.1.5
stocky@Nick:~$ cd weplab-0.1.5
stocky@Nick:~/weplab-0.1.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
stocky@Nick:~/weplab-0.1.5$

---

### Post by tjwoosta on 2008-10-18
do you have build-essential installed?

---

### Post by jstocky on 2008-10-18
NO, how do i get and install that?

---

### Post by schauerlich on 2008-10-18
> **jstocky said:**
> NO, how do i get and install that?

```
sudo apt-get install build-essential
```

---

### Post by jstocky on 2008-10-18
it's downloading, then what?

---

### Post by Keen101 on 2008-10-18
> sudo apt-get install build-essential

try this command in the terminal. It should install all GCC stuff for compiling and other stuff.

---

### Post by jstocky on 2008-10-18
Setting up build-essential (11.3ubuntu1) ...
stocky@Nick:~$ dir
airsnort-0.2.7e  Documents  Music     Public	 Videos
Desktop		 Examples   Pictures  Templates  weplab-0.1.5
stocky@Nick:~$ weplab-0.1.5
bash: weplab-0.1.5: command not found
stocky@Nick:~$ cd weplab-0.1.5
stocky@Nick:~/weplab-0.1.5$ sh ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pcap.h usability... no
checking pcap.h presence... no
checking for pcap.h... no
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... no
ERROR: You need libpcap-dev!
stocky@Nick:~/weplab-0.1.5$

---

### Post by Keen101 on 2008-10-18
search for "libpcap-dev" or maybe even just "libpcap" in synaptic package manager, then install it, and try to compile your program again.

---

### Post by Xiong Chiamiov on 2008-10-18
> **jstocky said:**
> 
what does this mean?


It means that you don't have the software installed to compile, which is the process of converting human-readable code into machine language.

More importantly, I see you're trying to install weplab manually; it's [in the repos]("http://packages.ubuntu.com/hardy/weplab"), so you should be installing it through Synaptic instead, unless you have some specific reason not to.

There used to be an excellent guide for installing software, but unfortunately that site went down.  You should still read [this guide]("http://www.psychocats.net/ubuntu/installingsoftware") though.

---

### Post by etusha on 2009-01-21
im have simalr problem wxweplab 0.1.6
i have install build-essential libpcap
```
weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
```

```
/weplab# make
make: Nothing to be done for `all'.
```

---

### Post by hyper_ch on 2009-01-21
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by snova on 2009-01-21
> **etusha said:**
> im have simalr problem wxweplab 0.1.6
i have install build-essential libpcap

<snip>

```
/weplab# make
make: Nothing to be done for `all'.
```

Try '**make install**', paste the output (if it doesn't work).

Alternatively, just install the 'weblab' package from Synaptic, it's a lot easier.

> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

A little late. :)

---

