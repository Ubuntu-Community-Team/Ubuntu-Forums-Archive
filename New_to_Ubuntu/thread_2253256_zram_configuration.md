---
title: "zram configuration"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by prpsarathy on 2014-11-18
Does ubuntu has the feature of compressed computing similar to that of osx yesomite.

---

### Post by grahammechanical on 2014-11-18
It will all depend on the version of Ubuntu and the Linux kernel being used. zRAM became part of the Linux kernel with version 3.14.

[http://en.wikipedia.org/wiki/Zram](http://en.wikipedia.org/wiki/Zram)

I do not think that is enabled by default. This page might be useful

[http://askubuntu.com/questions/174579/how-do-i-use-zram](http://askubuntu.com/questions/174579/how-do-i-use-zram)

There is a package in the Ubuntu Software Centre (at least for 14.10) called zram-config that is described: "A simple Upstart job to enable zram support on kernels that have the module available."

Upstart is used by Ubuntu to start and stop processes as necessary. The developers are in the process of changing from Upstart to SystemD. To see if zRAM kernel support is enabled run

```
cat /proc/swaps
```

This is what I get on my machine and I am running the development branch of the next release of Ubuntu 15.04.

> cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda8                               partition    2046540    44200    -1
/dev/sdb6                               partition    2135036    0    -2





EDIT: This is what we see with zRAM support enabled

> cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	2046540	0	-1
/dev/sdb6                               partition	2135036	0	-2
/dev/zram0                              partition	254156	0	5
/dev/zram1                              partition	254156	0	5


So, I guess zRAM support is not enabled by default but yes Ubuntu can do it because the Linux kernel can do it.

But can I see any noticeable improvement? We will see.
Regards.

---

### Post by prpsarathy on 2014-11-18
hi,

Thanks, i always believed that linux is the first innovator but might not be presenting itself well and also made easy to use.  You statement has proved my belief right. I will try to use it with the current version and wait for the new version.

---

### Post by prpsarathy on 2014-11-18
Hi,

I understand that zram supports compression. Kindly advice whether the default configuration makes the zram compressed. If not the command to make it use.  ihave done it in the current version of xubunut. does cacheing get enabled once zram is enabled. If yes, how do we see  like what i coudl see in the osx yesomite

---

