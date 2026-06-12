---
title: "SCTP module not supported / Chromebook with Ubuntu"
date: 2015-10-12
forum: Programming Talk
---

### Post by mohamed20 on 2015-10-12
Hi guys,

I have Ubuntu installed on an Acer Chromebook :

```
(trusty)root@localhost:/# uname -a
Linux localhost 3.8.11 #1 SMP Thu Sep 17 23:14:49 PDT 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I have the following installed as well :

```
(trusty)root@localhost:/# dpkg --get-selections | grep sctp
libsctp-dev                       install
libsctp1:i386                    install
lksctp-tools                    install

```
But when testing the SCTP support with checksctp I get the following :

```
(trusty)root@localhost:/# checksctp
checksctp: Protocol not supported

```

And of course when running a server test it fails as well :

```
(trusty)root@localhost:/# sctp_darn -H 0 -P 2500 -l
sctp_darn: failed to create socket:  Socket type not supported.

```

My question is : do the Ubuntu versions installed using Crouton don't come with sctp support by default or is there something wrong with my setup ? How to successfully load the sctp module in my case ?

Any help is really appreciated.

Thanks in advance,

---

