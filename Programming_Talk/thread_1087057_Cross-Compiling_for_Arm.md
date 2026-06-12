---
title: "Cross-Compiling for Arm"
date: 2009-03-04
forum: Programming Talk
---

### Post by pocketchange on 2009-03-04
I'm trying to cross-compile a program for arm.  In the past, I've kind of cheated by using openembedded and bitbake, which automatically builds the toolchain for me.  OE/Bitbake, however, introduces a lot of overheard trying to sort through all of the build files to get anything done.  

My preferred IDE is emacs, but I'm not completely stuck to it.  Could anyone tell me how to cross-compile?  I've downloaded the gnuarm package and it seems to have unpacked just fine, but I guess the hang up is what do I do from here to make sure everything is compiled right?  As far as I can gather, I have to set some environment variables.  Which variables do I need to setup?  Do I need to pass any arguments to ./configure?

---

### Post by cabalas on 2009-03-04
These links should be useful 

[http://mcuprogramming.com/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/](http://mcuprogramming.com/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/)

[http://mcuprogramming.com/2008/09/30/build-your-own-arm-cross-compiler-toolchain-revision/](http://mcuprogramming.com/2008/09/30/build-your-own-arm-cross-compiler-toolchain-revision/)

---

### Post by pocketchange on 2009-03-04
I have the following program that I'm trying to build.  The target is an at91sam9263ek running angstrom.  Here is the code:

```
#include <stdio.h>

int main() {
        printf("Hello World\n");
        return(0);
}

```

The at91sam9263ek manual says the processor is an ARM926EJ-S.

I'm following the directions from the [gnuarm website]("http://gnuarm.com/")'s support section.

arm-elf-gcc -mcpu=arm926ej-s -O2 -g -c hello.c
arm-elf-gcc -mcpu=arm926ej-s -o hello hello.o -lc

I end up with this error:
/home/user/Projects/arm-toolchain/gnuarm-4.0.2/bin/../lib/gcc/arm-elf/4.0.2/../../../../arm-elf/bin/ld: ERROR: hello.o uses VFP instructions, whereas hello does not
/home/user/Projects/arm-toolchain/gnuarm-4.0.2/bin/../lib/gcc/arm-elf/4.0.2/../../../../arm-elf/bin/ld: failed to merge target specific data of file hello.o

Any idea why this would happen?  I've tried adding the option -mfp=fpa with no success and I've tried adding in -mthumb (not sure what that does) and it doesn't work.  


Shane

---

### Post by pocketchange on 2009-03-04
I checked the second link (the author says he couldn't get the process from the first link you provided to work).  I don't have an account to download the setup script.  I did find a post from a Debian developer (posted just today):

[http://www.hermann-uwe.de/blog/building-an-arm-cross-toolchain-with-binutils-gcc-newlib-and-gdb-from-source](http://www.hermann-uwe.de/blog/building-an-arm-cross-toolchain-with-binutils-gcc-newlib-and-gdb-from-source)

But I got an error building gdb.  Regardless of those tools (I'm sure I can get something built), I'm unclear of the next steps.  How do I get this to work with my IDE?  Which environment variables do I need for the ./configure and make to work?  Do I need to pass any special arguments to ./configure to make it work?

---

### Post by supirman on 2009-03-04
I really dislike building toolchains myself, so I'd recommend to use one that is available and pre-compiled.  However, you can compile your own and use it.

Generally, an arm cross compiler will give you all of the gnu tools (gcc, ld, readelf, objdump, strip, etc) prefixed with **arm-linux-**.

So, to cross compile an item by hand, it's usually of the form:
```
arm-linux-gcc somefile.c
```

When trying to cross compile packages which use autotools (and hence ./configure), you would generally pass **--target=arm-linux**.  Be forewarned, however, that not all packages and configure scripts support cross-compiling easily (since they often try to compile and run tests - which is impossible when you're cross compiling).

*edit* Also, you may need to set **CC=arm-linux-gcc** for some packages...

See if that's enough to get you started.

---

### Post by pocketchange on 2009-03-05
Ok, I think I'm making some progress here.  Still a few hangups:

I verified installation of the compilers (my name was slightly different in that it had the word "gnu" in it:

```
% which arm-linux-gnu-ar arm-linux-gnu-ranlib arm-linux-gnu-gcc
/usr/bin/arm-linux-gnu-ar
/usr/bin/arm-linux-gnu-ranlib
/usr/bin/arm-linux-gnu-gcc
```

So I run the following command:

```
% CC=arm-linux-gnu-gcc AR=arm-linux-gnu-ar RANLIB=arm-linux-ranlib ./configure --target=arm-linux
```

And get the following output:

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... arm-unknown-linux-gnu
checking target system type... (cached) arm-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... arm-linux-gnu-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.
zsh: exit 1     CC=arm-linux-gnu-gcc AR=arm-linux-gnu-ar RANLIB=arm-linux-ranlib ./configure
```

Is this because the resulting executable can't be run on my machine since it's built for the arm?

Shane

---

### Post by Simian Man on 2009-03-05
[Crosstool]("http://www.kegel.com/crosstool/") is the way to go.  Be sure to check their build matrix for versions that are or aren't working.

---

### Post by pocketchange on 2009-03-05
> **Simian Man said:**
> [Crosstool]("http://www.kegel.com/crosstool/") is the way to go.  Be sure to check their build matrix for versions that are or aren't working.

I'm trying out crosstool now to see if I can get something to work.  I'm guessing in whatever IDE I choose, I can set these environment variables:

CC=
RANLIB=
AR=

and then it should compile from my crosstool folder?  The processor type is an ARM926EJ-S, which implements ARM architecture version 5TEJ.  I'm trying to use the demo-arm.sh to build it.  I noticed an error: "These critical programs are missing or too old: gcc"

```
% gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

To fix this I had to try to build a gcc-4.0.2 or earlier because the compiler in ubuntu seems to be too old to build the gcc-4.1.0 or later.  

The build gets to this and fails:

```
In function ‘open’,
    inlined from ‘collect_execute’ at /home/user/Projects/arm-toolchain/crosstool-0.43/build/arm-unknown-linux-gnu/gcc-4.0.2-glibc-2.3.6/gcc-4.0.2/gcc/collect2.c:1580:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [collect2.o] Error 1
make[1]: Leaving directory `/home/user/Projects/arm-toolchain/crosstool-0.43/build/arm-unknown-linux-gnu/gcc-4.0.2-glibc-2.3.6/build-gcc-core/gcc'
make: *** [all-gcc] Error 2
zsh: exit 2     ./demo-arm.sh

```

*sigh*  I'll resume this tomorrow.  For all those who have contributed help, I am greatly appreciative.

Shane

---

### Post by mmix on 2009-03-07
[http://stackoverflow.com/questions/309292/how-to-compile-and-install-a-linux-kernel-into-an-arm-kit/310834#310834](http://stackoverflow.com/questions/309292/how-to-compile-and-install-a-linux-kernel-into-an-arm-kit/310834#310834)

---

### Post by yazdanbakhsh on 2009-08-07
[B][SIZE=4]Hello!
I'm working with a tool,ReSP(Reflective Simulation platform), as a MPSoC platform.It includes many cpu architectures, like arm, powerpc, MIPS,...
It comes with a arm cross compiler. It works good for simple programs like fact, helloworld,...
I have codes to benchmark network application. I wrote a makefile to compile these codes, as you say:[/SIZE][/B]
---------------------------------------------------------------------------------------------------------------------------
CC     = /home/amir/ReSP/arm/bin/arm-elf-gcc 
OPT    = -specs=/home/amir/ReSP/arm/arm-elf/lib/osemu.specs
OTHER  = -fdata-sections -ffunction-sections -mcpu=arm7tdmi
#DEBUG  = -g 

# MAKE SURE BENCHMARK FUNCTION IS DEFINED
OTHER1 = -DBENCHMARK_FUNCTION=ipv4routing

# Replace with appropriate paths to libraries at your site
INCDIR = /home/rramaswa/sscalar/arm-libpcap-0.7.1/include
LIBDIR = /home/rramaswa/sscalar/arm-libpcap-0.7.1/lib
LIBS   =  -lpcap

bench.o : bench.c
    $(CC) -g3 $(OPT) $(OTHER) $(OTHER1) bench.c -c -o bench.o

ipv4.o : ipv4.c
    $(CC) -g3 $(OPT) $(OTHER) ipv4.c -c -o ipv4.o  

trie.o : trie.c
    $(CC) -g3 $(OPT) $(OTHER) trie.c -c -o trie.o

qsort.o : qsort.c
    $(CC) -g3 $(OPT) $(OTHER) qsort.c -c -o qsort.o

clean:
    rm -f *.o *~ bench core* dump.raw drop.raw
---------------------------------------------------------------------------------------------------------------------------

[B][SIZE=4]but it encouters many errors. I'm mixed-up.I appreciate if anyone can help me. I need this ASAP, for my thesis.

the errors:[/SIZE][/B]  :(:(:(:(:(
--------------------------------------------------------------------------------------------------------------------------
/home/amir/ReSP/arm/bin/arm-elf-gcc  -g3 -specs=/home/amir/ReSP/arm/arm-elf/lib/osemu.specs -fdata-sections -ffunction-sections -mcpu=arm7tdmi -DBENCHMARK_FUNCTION=ipv4routing bench.c -c -o bench.o
In file included from bench.h:34,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘socklen_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inet_addr’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inet_lnaof’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:43: error: expected ‘)’ before ‘__net’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inet_netof’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inet_network’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inet_aton’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/arpa/inet.h:79: error: expected ‘)’ before ‘__net’
In file included from /home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/if_ether.h:65,
                 from bench.h:35,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/net/ethernet.h:35: error: expected specifier-qualifier-list before ‘u_int8_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/net/ethernet.h:41: error: expected specifier-qualifier-list before ‘u_int8_t’
In file included from /home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/if_ether.h:66,
                 from bench.h:35,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/net/if_arp.h:161: error: expected specifier-qualifier-list before ‘u_int32_t’
In file included from bench.h:35,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/if_ether.h:78: error: expected specifier-qualifier-list before ‘u_int8_t’
In file included from bench.h:36,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/in_systm.h:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘n_short’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/in_systm.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘n_long’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/in_systm.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘n_time’
In file included from bench.h:38,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/ip.h:31: error: expected specifier-qualifier-list before ‘u_int8_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/ip.h:47: error: expected specifier-qualifier-list before ‘u_int32_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/ip.h:79: error: expected specifier-qualifier-list before ‘u_int8_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/ip.h:145: error: expected specifier-qualifier-list before ‘u_int8_t’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/ip.h:164: error: expected specifier-qualifier-list before ‘u_int8_t’
In file included from bench.h:39,
                 from bench.c:19:
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/tcp.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘tcp_seq’
/home/amir/ReSP/arm/bin/../lib/gcc/arm-elf/4.2.2/../../../../arm-elf/include/netinet/tcp.h:52: error: expected specifier-qualifier-list before ‘u_int16_t’
bench.c: In function ‘write_packet_to_tcpdump_file’:
bench.c:98: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:99: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:100: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:101: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:102: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:103: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:105: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:106: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:107: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:108: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:109: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:110: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:115: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:116: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:117: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:118: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:119: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:120: error: ‘struct ether_header’ has no member named ‘ether_dhost’
bench.c:122: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:123: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:124: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:125: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:126: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:127: error: ‘struct ether_header’ has no member named ‘ether_shost’
bench.c:130: error: ‘struct ether_header’ has no member named ‘ether_type’
bench.c:130: error: ‘u_int16_t’ undeclared (first use in this function)
bench.c:130: error: (Each undeclared identifier is reported only once
bench.c:130: error: for each function it appears in.)
bench.c: In function ‘main’:
bench.c:451: error: ‘struct ether_header’ has no member named ‘ether_type’
bench.c:494: error: ‘struct ip’ has no member named ‘ip_len’
bench.c:501: error: ‘struct ip’ has no member named ‘ip_dst’
bench.c:509: error: ‘struct ip’ has no member named ‘ip_dst’
make: *** [bench.o] Error 1
--------------------------------------------------------------------------------------------------------------------------

**[SIZE=4]Best Regards,[/SIZE]**

---

### Post by slavik on 2009-08-07
deaad threads need to stay dead.

---

