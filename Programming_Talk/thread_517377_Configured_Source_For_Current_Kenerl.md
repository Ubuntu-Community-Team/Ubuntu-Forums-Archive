---
title: "Configured Source For Current Kenerl?"
date: 2007-08-04
forum: Programming Talk
---

### Post by scrop on 2007-08-04
I'm doing some development work and I could really use the configured system headers. When I used to use gentoo, I had them because I built myself. On other systems I could get the source rpm and zcat /proc.config.gz to a file and have my "configured" sources which is enough for certain types of development.

How do I get this on ubuntu? 
I don't know what kernel ubuntu gives you has configuration wise because they didn't enable the /proc/config module. I got the source package but its not configured. Any help would be great.

---

### Post by jpkotta on 2007-08-04
.config is in the linux-headers package for your kernel.  I can't remember for sure, but I think installing the virtual package "linux-headers" will get the correct package for the running kernel.  Otherwise just get the one that matches the version of your kernel.

BTW, I agree that they should enable /proc/config.gz.

---

