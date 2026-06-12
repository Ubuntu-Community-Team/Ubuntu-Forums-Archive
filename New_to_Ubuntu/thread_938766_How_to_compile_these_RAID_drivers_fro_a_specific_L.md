---
title: "How to compile these RAID drivers fro a specific LinuxPE kernel?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by EddieBarzoon on 2008-10-05
Hi there,

I need to add the RAID drivers for ServRAID IBM 4mx to a LinuxPE boot image.

The drivers are here:

[https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5072186&brandind=5000008](https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5072186&brandind=5000008)

or at least these are the SUSE ones that I hope I can use. I wanted to compile these for my kernel which is 2.6.18.8.

I hoped to get the .c and .h files and then run a make -c pathtomykernel and the build the required .ko file.

However when I mount the img file from the site I have an ips.o file which I believe is precompiled for that kernel (not sure I am new to this!)

So how would I get the correct IBM ServRAID 4mx drivers and compile for my LinuxPE boot image?

Thanks in advance for any help anyone can give.

---

### Post by stmiller on 2008-10-05
That sounds like an ips module. Is it possible to just to Linux software RAID instead? Or it is very likely that a modern Linux distro already has this ips module built-in. Most certainly the Redhat/CentOS ones would.

---

### Post by EddieBarzoon on 2008-10-06
Thanks. I'm going to have to use hardware RAID for these servers.

Sorry for the newbie questions but how could I pull this ips module out of another distro to add it to my LinuxPE. Basically I think just need the ips.c and ips.h files for the latest version which I can then compile.

However all i can download is the pr-compiled ips.o file.

I think this is more a newbie error on my part than anything.

---

