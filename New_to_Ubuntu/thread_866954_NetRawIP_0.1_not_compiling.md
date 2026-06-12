---
title: "Net::RawIP 0.1 not compiling"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-07-22
Net::RawIP as a fresh tarball download, version 0.1, isn't compiling. I'm on Hardy.

```
brad@brad-laptop-ubuntu:~/Desktop/Net-RawIP-0.1$ make
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.1\" -DXS_VERSION=\"0.1\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -D_LINUX_ -D_ETH_ -D_IFLIST_ -D_GLIBC_ RawIP.c
RawIP.xs: In function &#8216;XS_Net__RawIP_tcp_pkt_parse&#8217;:
RawIP.xs:758: error: lvalue required as left operand of assignment
RawIP.xs:784: error: lvalue required as left operand of assignment
RawIP.xs: In function &#8216;XS_Net__RawIP_icmp_pkt_parse&#8217;:
RawIP.xs:817: error: lvalue required as left operand of assignment
RawIP.xs: In function &#8216;XS_Net__RawIP_generic_pkt_parse&#8217;:
RawIP.xs:857: error: lvalue required as left operand of assignment
RawIP.xs: In function &#8216;XS_Net__RawIP_udp_pkt_parse&#8217;:
RawIP.xs:891: error: lvalue required as left operand of assignment
RawIP.xs: In function &#8216;XS_Net__RawIP_dispatch&#8217;:
RawIP.xs:1283: error: lvalue required as left operand of assignment
RawIP.xs: In function &#8216;XS_Net__RawIP_loop&#8217;:
RawIP.xs:1305: error: lvalue required as left operand of assignment
make: *** [RawIP.o] Error 1
brad@brad-laptop-ubuntu:~/Desktop/Net-RawIP-0.1$
```

---

### Post by unutbu on 2008-07-22
There is a libnet-rawip-perl package (version 0.21-1)
available for Hardy. Are you sure you don't want to use that?

[http://packages.ubuntu.com/hardy/perl/libnet-rawip-perl](http://packages.ubuntu.com/hardy/perl/libnet-rawip-perl)

---

