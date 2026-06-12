---
title: "glibc on Ubuntu"
date: 2007-11-07
forum: Programming Talk
---

### Post by sriram.venkataramani on 2007-11-07
Hi,

I'm working on a checkpointing software and have problems running it on Ubuntu (6.10, 7.10). The same software works on other Linux distros (both fedora and debian) and the vanilla Linux kernel (2.6.22) itself. 

Now I have reason to believe that the problem might be with glibc (2.6.1) in Ubuntu. I am going to download and build the original glibc source and use that to link to my checkpointing software. 

But before doing that I'd like to know if anybody knows whether the glibc might be patched in Ubuntu or whether there is something in glibc that might have it behave differently in Ubuntu. 

Thanks!

---

### Post by hod139 on 2007-11-07
What's the error?

You can see the debian changelog:
[http://changelogs.ubuntu.com/changelogs/pool/main/g/glibc/glibc_2.6.1-1ubuntu9/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/g/glibc/glibc_2.6.1-1ubuntu9/changelog)

You can find other package information at:
[http://packages.ubuntu.com/gutsy/base/libc6](http://packages.ubuntu.com/gutsy/base/libc6)

---

### Post by sriram.venkataramani on 2007-11-07
I get a segmentation fault when a call to munmap is made. I printed out the memory maps and it showed that the memory upto the end of the head was unmapped. When it goes to unmap an unnamed area of memory after the heap, the program receives a SIGSEGV.

---

### Post by hod139 on 2007-11-07
Without posting actual code I can't really help.  How much older are the fedora and debian distros?  It might be the newer glibc and/or kernel is killing it, because it always should have been killed.

---

### Post by sriram.venkataramani on 2007-11-07
The code is available on Sourceforge if you are interested.

svn co [https://dmtcp.svn.sourceforge.net/svnroot/dmtcp](https://dmtcp.svn.sourceforge.net/svnroot/dmtcp) dmtcp

Thanks!

- Sri

---

### Post by sriram.venkataramani on 2007-11-07
Once you've downloaded the code, go to the dmtcp/mtcp folder and do

make check

---

