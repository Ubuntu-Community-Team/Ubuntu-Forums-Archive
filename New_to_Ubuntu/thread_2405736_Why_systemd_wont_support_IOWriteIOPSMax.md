---
title: "Why systemd wont support IOWriteIOPSMax?"
date: 2018-11-10
forum: New to Ubuntu
---

### Post by rrll1977 on 2018-11-10
Hey community,

I apologize if this is not the right place to post this question, the problem is that I just installed Ubuntu 16.04.5 LTS and upgraded the kernel to 4.15.0-38-generic using the package linux-image-generic-hwe-16.04. Then when I try to start a service unit that uses the system directive IOReadIOPSMax, I get the error Unknown lvalue 'IOReadIOPSMax' in section 'Service'.

Also I can't use cpu.cfs_quota_us or cpu.cfs_period_us in cgconfig.conf, when I try to start the process cgconfig I get the error cpu.cfs_period_us:syntax error. This might be related to the issue I'm describing above.

I've get the system up and running on a KVM VPS following a bunch of tutorials I've found on the Internet, but now I cant find any information about where and how to get those functionalities enabled in my kernel.

Any help or comment is highly appreciated.

---

