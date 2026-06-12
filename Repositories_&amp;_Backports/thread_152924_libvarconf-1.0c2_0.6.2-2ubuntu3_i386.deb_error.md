---
title: "libvarconf-1.0c2_0.6.2-2ubuntu3_i386.deb error"
date: 2006-03-30
forum: Repositories &amp; Backports
---

### Post by somerville32 on 2006-03-30
> 
Preconfiguring packages ...
(Reading database ... 122728 files and directories currently installed.)
Unpacking libvarconf-1.0c2 (from .../libvarconf-1.0c2_0.6.2-2ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libvarconf-1.0c2_0.6.2-2ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libvarconf-1.0.so.2.0.0', which is also in package libvarconf-1.0-2
Errors were encountered while processing:
 /var/cache/apt/archives/libvarconf-1.0c2_0.6.2-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I got this error while installing a whole wack of different packages through synaptics. My package list is just the default from the breezy installed with the disabled ones enabled.

I also got a similar error yesterday when trying to upgrade to dapper (I had to reinstall from cd). It was complaining about xfm4-themes trying to overwrite some README file that is in package xfm4. :-k

---

