---
title: "ins mod results in invalid module format"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by jp9744 on 2012-07-20
Definitely a ubuntu/kernel newbie.  I'm working my way through a
series of texts (embedded linux development, linux device drivers,
and so on..) in linux device drivers I came across the most simple
hello-world example for a kernel module.  I coded the example
and built it (all went fine), but when I ran the command
>insmod hello.ko
I got back the following message:
insmod: error inserting 'hello.ko': -1 Invalid module format
I also tried
>dmesg
at the tail of this listing it indicated...
[ ####.####] hello: disagrees about version of symbol module_layout

My ubuntu install is 12.04 (I just downloaded it over the weekend).
The kernel I downloaded is 3.2.0.orig.tar off the ubuntu site.  My system
information is:
Linux machineName 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux

I am running this under a virtual box.

I assumed I had to write/compile/link my hello.c module against the same
kernel as my system is currently running.  When I went searching for 
the linux kernel for the 12.04 install of ubuntu I found the indirection to 
3.2.0.orig.

Any suggestions/answers are greatly appreciated.

---

