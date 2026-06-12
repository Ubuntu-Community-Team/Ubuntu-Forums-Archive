---
title: "Problems compiling Jpcap"
date: 2006-03-10
forum: Programming Talk
---

### Post by cybrid on 2006-03-10
Hello, I'm trying to compile [Jpcap]("http://netresearch.ics.uci.edu/kfujii/jpcap/doc/index.html") to be able to use it in conjunction with netbeans, but I get a ton of errors from gcc. This is the list:

```
gcc -G -I/usr/local/java/include -I/usr/local/java/include/solaris\
         -I/usr/include\
        Jpcap.c Jpcap_ipaddr.c JpcapSender.c JpcapWriter.c\
          packet_arp.c packet_datalink.c packet_icmp.c packet_ip.c\
          packet_ipv6.c packet_tcp.c packet_udp.c\
        -o libjpcap.so -lpcap
gcc: opción '-G' no reconocida
In file included from Jpcap.c:57:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
Jpcap.c: En la función 'Java_jpcap_Jpcap_getDeviceList':
Jpcap.c:248: aviso: declaración implícita incompatible de la función interna 'malloc'
Jpcap.c:263: aviso: declaración implícita incompatible de la función interna 'strchr'
Jpcap.c:270: aviso: declaración implícita incompatible de la función interna 'memset'
Jpcap.c:271: aviso: declaración implícita incompatible de la función interna 'strncpy'
Jpcap.c:283: aviso: declaración implícita incompatible de la función interna 'strcpy'
Jpcap.c: En la función 'get_packet':
Jpcap.c:687: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
Jpcap.c:693: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
In file included from Jpcap_ipaddr.c:14:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
In file included from JpcapSender.c:25:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
JpcapSender.c: En la función 'Java_jpcap_JpcapSender_sendPacket':
JpcapSender.c:156: aviso: declaración implícita incompatible de la función interna 'memset'
JpcapSender.c:179: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
JpcapSender.c:231:2: aviso: no hay caractér de fin de línea al final del ficheroIn file included from JpcapWriter.c:5:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
JpcapWriter.c: En la función 'Java_jpcap_JpcapWriter_writeDumpFile':
JpcapWriter.c:63: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
JpcapWriter.c:64: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
JpcapWriter.c:66: aviso: el puntero que apunta en el paso del argumento 3 de 'pcap_dump' difiere en signo
In file included from packet_arp.c:16:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_arp.c: En la función 'analyze_arp':
packet_arp.c:32: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_arp.c:34: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_arp.c:36: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_arp.c:38: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_datalink.c:4:20: error: net/bpf.h: No existe el fichero o el directorio
In file included from packet_datalink.c:16:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_datalink.c: En la función 'set_ether':
packet_datalink.c:56: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
packet_datalink.c:57: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
In file included from packet_icmp.c:16:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_icmp.c: En la función 'analyze_icmp':
packet_icmp.c:45: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_icmp.c: En la función 'set_icmp':
packet_icmp.c:126: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
In file included from packet_ip.c:15:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_ip.c: En la función 'analyze_ip':
packet_ip.c:39: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_ip.c:40: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_ip.c:67: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_ip.c: En la función 'set_ip':
packet_ip.c:97: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
packet_ip.c:98: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
In file included from packet_ipv6.c:15:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
In file included from packet_tcp.c:16:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_tcp.c: En la función 'analyze_tcp':
packet_tcp.c:55: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->SetByteArrayRegion' difiere en signo
packet_tcp.c: En la función 'set_tcp':
packet_tcp.c:101: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
In file included from packet_udp.c:17:
Jpcap_sub.h:6: error: syntax error before 'HAVE_SA_LEN'
Jpcap_sub.h:52: error: syntax error before 'pcap_t'
packet_udp.c: En la función 'set_udp':
packet_udp.c:54: aviso: el puntero que apunta en el paso del argumento 5 de '(*env)->GetByteArrayRegion' difiere en signo
make: *** [libjpcap.so] Error 1
```

Can anybody help me, please?

Thanks in advance.

---

### Post by gord on 2006-03-11
its kinda hard, seing as all thats in a diffirent language. but i'll give it a shot. first of all make sure you have the right versions of all your dependancys (ie; uptodate versions), also try using an earlyer version of gcc, ubuntu comes with  gcc4, ```
sudo apt-get install gcc-3.4
```
and then doing 
```
export CC=gcc-3.4
```
before ./configure will set make to use gcc-3.4

---

### Post by hod139 on 2006-03-13
First, did you install libpcap0.8-dev?

Second, from their website: [COLOR=#FF0000]Note: Jpcap ver.0.5 requres libpcap 0.9.4 or later.  [/COLOR]Depending on the version of Jpcap you are trying to build, the version of libpcap in the breezy repos may be out of date.
[COLOR=#FF0000]

[/COLOR]

---

### Post by Zhukov on 2006-11-29
Any news here?
I also need to get this running...

---

### Post by dignan on 2009-01-16
Hey, I'm working on a .deb for jpcap so hopefully I'll be able to get that out soon.  My development PC is currently attached to an external hard drive as I dig the files off it though!

---

### Post by Zhukov on 2009-01-17
Hi there!

There is already a deb at their webpage, i dont think you need to work on that.

I've tested it and it works like a charm!

---

