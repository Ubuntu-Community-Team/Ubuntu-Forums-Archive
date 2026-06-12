---
title: "python raw sockets"
date: 2014-02-23
forum: Programming Talk
---

### Post by fugu2 on 2014-02-23
I'm trying to create a simple raw socket python program, and it was my 
understanding that raw sockets do not transverse the netfilter tables 
when they are formed. But when I have an iptables rule like
```

-A OUTPUT -j NFQUEUE --queue-num 0

```
it seems to be grabbing the raw socket packet and sending it through
the iptables and it gets caught by this rule. My question is:
Can I create raw packets that will be sent 'as is' without being affected
by this iptables rule?

---

### Post by ian-weisser on 2014-02-25
A raw (non-TCP, non-UDP) packet should be ignored by iptables.
Are you unintentionally using TCP/UDP sockets? Python's socket module tends to expect that.

```
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)          # socket.AF_INET will use iptables

sock = socket.socket(socket.AF_UNIX, socket.SOCK_STREAM)          # socket.AF_UNIX won't use iptables
```

---

### Post by fugu2 on 2014-02-26
> **ian-weisser said:**
> A raw (non-TCP, non-UDP) packet should be ignored by iptables.
Are you unintentionally using TCP/UDP sockets? Python's socket module tends to expect that.

```
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)          # socket.AF_INET will use iptables

sock = socket.socket(socket.AF_UNIX, socket.SOCK_STREAM)          # socket.AF_UNIX won't use iptables
```

[FONT=system]Ah thank you, I think I was using (s[/FONT][FONT=system]ocket.AF_INET, socket.SOCK_RAW, socket.IPPROTO_IP[/FONT]) or something, thinking I was using using raw sockets. I will try AF_UNIX as soon as I get a chance! I also just read something about AF_PACKET which I'll need too look into as well.
Thank you again!

---

