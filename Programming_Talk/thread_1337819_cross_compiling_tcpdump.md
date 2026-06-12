---
title: "cross compiling tcpdump"
date: 2009-11-25
forum: Programming Talk
---

### Post by nagileon on 2009-11-25
Hi there

I'm compiling tcpdump for my Linksys WRT54GL router. 
libcap compiles fine but compiling tcpdump gives me a bunch of errors. 

I'm dooing this: 

wget [http://www.tcpdump.org/release/libpcap-1.0.0.tar.gz](http://www.tcpdump.org/release/libpcap-1.0.0.tar.gz) 

wget [http://www.tcpdump.org/release/tcpdump-4.0.0.tar.gz](http://www.tcpdump.org/release/tcpdump-4.0.0.tar.gz) 

wget [ftp://ftp.dd-wrt.com/others/sourcecode/toolchains/toolchains.x86.debian.sp1.tar.bz2](ftp://ftp.dd-wrt.com/others/sourcecode/toolchains/toolchains.x86.debian.sp1.tar.bz2) 

tar -xvf libpcap-1.0.0.tar.gz 

tar -xvf tcpdump-4.0.0.tar.gz 

tar -xvf toolchains.x86.debian.sp1.tar.bz2

apt-get install flex

apt-get install bison

export PATH=~/toolchains/4.1.0-uclibc-0.9.28/bin:$PATH 

cd /root/libpcap-1.0.0 

CC=mipsel-linux-uclibc-gcc ac_cv_linux_vers=2 ./configure --host=mipsel-linux --with-pcap=linux 

make 

cd ../tcpdump-4.0.0 

CC=mipsel-linux-uclibc-gcc ac_cv_linux_vers=2 ./configure --host=mipsel-linux --with-pcap=linux 

make 
```

... 
./../libpcap-1.0.0/libpcap.a(pcap.o): In function `pcap_datalink_name_to_val': 
pcap.c:(.text+0x1b8): multiple definition of `pcap_datalink_name_to_val' 
dlnames.o:dlnames.c:(.text+0xe8): first defined here 
./../libpcap-1.0.0/libpcap.a(pcap.o): In function `pcap_datalink_val_to_name': 
pcap.c:(.text+0x26c): multiple definition of `pcap_datalink_val_to_name' 
dlnames.o:dlnames.c:(.text+0x0): first defined here 
./../libpcap-1.0.0/libpcap.a(pcap.o): In function `pcap_datalink_val_to_description': 
pcap.c:(.text+0x2d4): multiple definition of `pcap_datalink_val_to_description' 
dlnames.o:dlnames.c:(.text+0x68): first defined here 
./../libpcap-1.0.0/libpcap.a(pcap.o): In function `pcap_list_datalinks': 
pcap.c:(.text+0xfbc): multiple definition of `pcap_list_datalinks' 
datalinks.o:datalinks.c:(.text+0x0): first defined here 
./../libpcap-1.0.0/libpcap.a(savefile.o): In function `pcap_dump_ftell': 
savefile.c:(.text+0xd8): multiple definition of `pcap_dump_ftell' 
pcap_dump_ftell.o:pcap_dump_ftell.c:(.text+0x0): first defined here 
print-enc.o: In function `enc_if_print': 
print-enc.c:(.text+0x1e0): undefined reference to `ip6_print' 
./../libpcap-1.0.0/libpcap.a(grammar.o): In function `pcap_parse': 
grammar.c:(.text+0x5e0): undefined reference to `pcap_lex' 
collect2: ld returned 1 exit status 
make: *** [tcpdump] Error 1 

```
Anyone knows how to sort it out ? 

Regards 

Peter

---

