---
title: "Compiling Net::Packet fails"
date: 2010-02-03
forum: Packaging and Compiling Programs
---

### Post by payload101 on 2010-02-03
I am trying to compile the Net::Packet and it fails due to it can not find libdnet. It seems that due to what has been refereed to as the pollution of Ubuntu libraries by the decnet libraries that libdnet has been moved to dumbnet1. I have installed the dumbnet libraries and have enven gone to sourceforge and complied the lastest version of libdnet and tried to install Net::Libdnet but it also fails.

Has anyone been able to get Net::Packet to compile in karmic Koala 9.10. Any help would be appreciated.

Net-Libdnet-0.92$ perl Makefile.PL
Checking if your kit is complete...
Looks good
Writing Makefile for Net::Libdnet
bhartson@DataServer-1:~/Downloads/Net-Libdnet-0.92$ make
Skip blib/lib/Net/Libdnet/Entry/Intf.pm (unchanged)
Skip blib/lib/Net/Libdnet.pm (unchanged)
Skip blib/lib/Net/Libdnet/Intf.pm (unchanged)
Skip blib/lib/Net/Libdnet/Ip.pm (unchanged)
Skip blib/lib/Net/Libdnet/Eth.pm (unchanged)
Skip blib/lib/Net/Libdnet/Tun.pm (unchanged)
Skip blib/lib/Net/Libdnet/Route.pm (unchanged)
Skip blib/lib/Net/Libdnet/Fw.pm (unchanged)
Skip blib/lib/Net/Libdnet/Arp.pm (unchanged)
/usr/bin/perl /usr/share/perl/5.10/ExtUtils/xsubpp  -typemap /usr/share/perl/5.10/ExtUtils/typemap -typemap typemap  Libdnet.xs > Libdnet.xsc && mv Libdnet.xsc Libdnet.c
cc -c  -I/usr/include -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"0.92\" -DXS_VERSION=\"0.92\" -fPIC "-I/usr/lib/perl/5.10/CORE"   Libdnet.c
Libdnet.xs:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘TunHandle’
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_open’:
Libdnet.c:1963: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:1963: error: (Each undeclared identifier is reported only once
Libdnet.c:1963: error: for each function it appears in.)
Libdnet.c:1963: error: ‘RETVAL’ undeclared (first use in this function)
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_fileno’:
Libdnet.c:1994: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:1994: error: ‘handle’ undeclared (first use in this function)
Libdnet.c:2000: error: expected expression before ‘)’ token
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_name’:
Libdnet.c:2028: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:2028: error: ‘handle’ undeclared (first use in this function)
Libdnet.c:2034: error: expected expression before ‘)’ token
Libdnet.xs:1208: warning: assignment makes pointer from integer without a cast
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_send’:
Libdnet.c:2062: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:2062: error: ‘handle’ undeclared (first use in this function)
Libdnet.c:2070: error: expected expression before ‘)’ token
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_recv’:
Libdnet.c:2098: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:2098: error: ‘handle’ undeclared (first use in this function)
Libdnet.c:2108: error: expected expression before ‘)’ token
Libdnet.c: In function ‘XS_Net__Libdnet_dnet_tun_close’:
Libdnet.c:2142: error: ‘TunHandle’ undeclared (first use in this function)
Libdnet.c:2142: error: ‘handle’ undeclared (first use in this function)
Libdnet.c:2143: error: ‘RETVAL’ undeclared (first use in this function)
Libdnet.c:2147: error: expected expression before ‘)’ token
make: *** [Libdnet.o] Error 1

---

### Post by SevenMachines on 2010-02-05
hi, the compilation above is trying to use dumbnet instead of the, as you mentioned, deprecated in debian dnet. dumbnet compilation works fine but you need to change #includes in Net::Libdnet from dnet to dumbnet. 

specifically, in the Net::Libdnet files:
Libdnet.c
Libdnet.xs

change the 
#include <dnet.h>
to
#include <dumbnet.h>

---

