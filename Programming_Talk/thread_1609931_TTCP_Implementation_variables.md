---
title: "T/TCP Implementation variables"
date: 2010-10-31
forum: Programming Talk
---

### Post by jamesbon on 2010-10-31
Hi,
I had try to read man page but there are no such entries on my system and the Googled [links ]("http://www.google.com/search?hl=en&&sa=X&ei=7v_MTJyMOoSgvQP82szFDw&ved=0CBEQvgUoAA&q=cc_send&nfpr=1")do not seem to give me any useful information.I am trying to understand the implementation of T/TCP in kernel.The Network Programming Vol 3 of Richard Stevens Chapter 2 of that book deals with these.
It talks of tcp_ccgen,tao_cc,tao_ccsent,I searched on [http://lxr.linux.no/#linux+v2.6.36/](http://lxr.linux.no/#linux+v2.6.36/)
for these functions but I got zero results.
I am trying to understand implementation of T/TCP in linux kernel can someone point me to a useful link?

---

### Post by saulgoode on 2010-10-31
TTCP never made it into the Linux kernel owing to its security vulnerabilities. There was a short-lived unofficial patch for the 2.4 series ([http://ttcplinux.sourceforge.net/]("http://ttcplinux.sourceforge.net/")).

---

### Post by jamesbon on 2010-10-31
Thanks for this information.

---

