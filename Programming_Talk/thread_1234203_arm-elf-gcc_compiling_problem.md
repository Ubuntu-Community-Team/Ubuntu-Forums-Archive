---
title: "arm-elf-gcc compiling problem"
date: 2009-08-07
forum: Programming Talk
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

the errors:[/SIZE][/B]  :sad::sad::sad::sad::sad:
--------------------------------------------------------------------------------------------------------------------------
/home/amir/ReSP/arm/bin/arm-elf-gcc -g3 -specs=/home/amir/ReSP/arm/arm-elf/lib/osemu.specs -fdata-sections -ffunction-sections -mcpu=arm7tdmi -DBENCHMARK_FUNCTION=ipv4routing bench.c -c -o bench.o
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

### Post by cmwslw on 2009-08-07
Well it this definitely looks like you're missing a header. Why do you need a custom makefile? The included makefile for the arm-elf-binutils worked fine for me.

-cory

---

### Post by mmix on 2009-08-08
This isn't compiling problem, this is environment problem.

use your own cross compiler

[http://wiki.openembedded.net/index.php/Main_Page](http://wiki.openembedded.net/index.php/Main_Page)

HTH

---

### Post by falconfalcon on 2010-06-07
i encountered with same kind of problem..
mcohw.c:261: error: expected '='™, ','™, '€˜;'€™, '˜asm'€™ or '__attribute__'™ before '{'€™ token

possible solutions are;
1: you have missed the [COLOR="Red"]__attribute__[/COLOR]
  say u have declared the function as,
 
 [COLOR="red"]void blah_blah (void) blahblah;[/COLOR]

and while using the function you have missed the [COLOR="red"](void)[/COLOR]

2:trust me, this works;
 use double parentheses in the place of single at the function
 say,
 
[COLOR="Red"]void blah_blah (void) blahblah {{
 ............
.........
.........
......
}}[/COLOR]

it works.. now reduce the double parentheses to single. it should work fine !! ya.. de arm-elf-gcc compiler is dumb :)

---

