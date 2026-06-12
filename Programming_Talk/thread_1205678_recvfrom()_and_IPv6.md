---
title: "recvfrom() and IPv6"
date: 2009-07-06
forum: Programming Talk
---

### Post by Schelm on 2009-07-06
I am writing a small ping program which works for IPv6. Unfortunately, according to the [ICMP6 man page]("http://manpages.ubuntu.com/manpages/hardy/man4/icmp6.4.html"), the IPv6 header is automatically cropped off when recvfrom() is used. I need to access the IPv6 header for incoming packets, since I want to read out the hop limit to find out how many hops a roundtrip took.
Is there a way to disable the removal of the IPv6 header or does anyone have another idea how I can access the hop count?
[]("http://manpages.ubuntu.com/manpages/hardy/man4/icmp6.4.html")__

---

### Post by dwhitney67 on 2009-07-06
The only thing I can think of is to setup a raw socket, and then enable the appropriate socket option (IP_HDRINCL).  You will need to have root-privileges to create the socket.

Something like:
```

// will need root-privileges for the following
int sd = socket(AF_INET6, SOCK_RAW, IPPROTO_UDP);

int opt = 1;

setsockopt(sd, IPPROTO_IPV6, IP_HDRINCL, opt, sizeof(opt));

// root-privilege are no longer required
setuid(getuid());

...

```
I have never dealt with IPv6, so I can only theorize that the code above will work.  Something similar does work with IPv4.

---

### Post by Schelm on 2009-07-07
Thanks for your help. The socket is raw, but IP_HDRINCL is not supported with IPv6.
I figured out a solution: Header flags can be read, if setsockopt is used to add additional header information. For the hop limit, this is IPV6_RECVHOPLIMIT. Data should be read with recvmsg(). Then, the message we received can be parsed. Looking for ancillary data header called IPV6_HOPLIMIT gives the desired result. Pretty tricky and a pain to code though :/

---

### Post by dwhitney67 on 2009-07-07
> **Schelm said:**
> Thanks for your help. The socket is raw, but IP_HDRINCL is not supported with IPv6.
I figured out a solution: Header flags can be read, if setsockopt is used to add additional header information. For the hop limit, this is IPV6_RECVHOPLIMIT. Data should be read with recvmsg(). Then, the message we received can be parsed. Looking for ancillary data header called IPV6_HOPLIMIT gives the desired result. Pretty tricky and a pain to code though :/

:-)  Oh, so that's how it is done.

A few months ago I augmented my Socket Library to support the sendmsg() and recvmsg() library functions when I was  attempting to set the DSCP (TOS) within the IP header.  But it is nice to know that my efforts can actually be used for other purposes.

---

### Post by maya80 on 2009-09-02
Hello
im some how new to ubuntu and IPV6, how can i send and receive IPv6 raw-sockets??

---

