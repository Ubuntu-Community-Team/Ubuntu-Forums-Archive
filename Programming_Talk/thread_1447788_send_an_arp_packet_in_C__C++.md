---
title: "send an arp packet in C / C++"
date: 2010-04-05
forum: Programming Talk
---

### Post by IdealVithVodka on 2010-04-05
Hi,


I'm looking for a way how to send an arp request / reply packet using C or C++. I've written an application that can send different crafted packages using jpcap (java), but I'm not a C expert (trying to learn). The reason for this is that I would like to port my java program to C to use it on a less powerful system that can't fully cope with the resource hungry VM.


Any suggestions ??


With Kind Regards

---

### Post by Cracauer on 2010-04-05
I would recommend studying the source code for dhclient(1).

A quick look uncovers:
```

        if ((sock = socket(AF_INET, SOCK_RAW, IPPROTO_UDP)) == -1)
                error("socket(SOCK_RAW): %m");
        if (setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &on,
            sizeof(on)) == -1)
                error("setsockopt(IP_HDRINCL): %m");
[...]
and then
sendmsg(sock, somemmem....);

```

---

### Post by ja660k on 2010-04-06
how do you see that source code?
what directory is it in

if i vim /sbin/dhclient 
it gives me some binary garbage ???

---

### Post by IdealVithVodka on 2010-04-06
@ja660k :


Your checking the binary of the dhclient. You need to get the source code of it and then view the code to get some more info.

I was looking around and found an interesting website with some useful code that is easy for me to understand (managed to get it working). 

[http://www.programming-pcap.aldabaknocking.com/codesamples.html](http://www.programming-pcap.aldabaknocking.com/codesamples.html)


Still, I couldn't find anything that would send an arp packet for me.


@Cracauer :

Thanks for the tip. I will try to view the source code. Hopefully with my low level of understanding C i will be able to find something useful.


Any further ideas anyone ?

---

### Post by Xyro on 2010-04-06
[Here]("http://beej.us/guide/bgnet/output/html/multipage/index.html") is a great starter guide to newtork programming in C

---

### Post by IdealVithVodka on 2010-04-06
@Xyro :

Thank, but isn't it networking via sockets ?? I'm no expect tho

Found something that actually sends an arp packet (its in C and uses libnet) :

[http://vafer.org/blog/20040905200347](http://vafer.org/blog/20040905200347)


is it a wrapper(libnet) for libpcap or a totally different stand alone network library ??


Thanks guys !!

---

