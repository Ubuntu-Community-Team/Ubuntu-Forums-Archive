---
title: "Attempting to access RAM /dev/mem... says &quot;Operation not permitted&quot;"
date: 2013-03-07
forum: Programming Talk
---

### Post by KingNeil on 2013-03-07
Hi, I read the following tutorial on how to access the contents of RAM in Linux....

[http://www.rootninja.com/using-dd-to-search-for-strings-in-memory-or-devices/](http://www.rootninja.com/using-dd-to-search-for-strings-in-memory-or-devices/)

```
dd if=/dev/mem | hexdump -C | grep “string to search for”
```

So, I run the code... 

```
sudo dd if=/dev/mem | hexdump -C > NAMEOFOUTPUTFILEHERE.txt
```

And... it starts pumping out HEX code, until a few seconds later, where it says:

> 
dd: reading `/dev/mem': Operation not permitted
2056+0 records in
2056+0 records out
1052672 bytes (1.1 MB) copied, 0.44834 s, 2.3 MB/s


So basically.. I am able to get about 3.3 MB of RAM dump contents-- until the program stops, saying "Operation not permitted"

.... And so... I am wondering... why am I not able to dump the entire contents of RAM? Is this a deliberate limitation in Ubuntu, to stop malicious hackers..? Or, is it something else..? Does anybody know..? Thanks

---

### Post by KingNeil on 2013-03-07
OK... forget it... turns out Ubuntu has 1 MB limit on RAM extraction, as defined in the kernel.. and obviously, that's good security, because then a hacker can't extract your passwords from RAM etc... 

And so... yeah.... this thread is now SOLVED

Here is the full info, for anyone interested....

> 
if your kernel was compiled with STRICT_DEVMEM=y (see e.g. /boot/config-KERNELVERSION) then only the first 1MB is read from /dev/mem . This isn&#8217;t so much a kernel version issue, as a result of how your own machine&#8217;s kernel was compiled; most distro kernels will have this restriction in place for good reason.

You can download and insmod the forensic kernel module fmem to work around this; at your own risk! rmmod it as soon as possible afterwards. The fmem module provides a /dev/fmem device without any security restrictions.


---

