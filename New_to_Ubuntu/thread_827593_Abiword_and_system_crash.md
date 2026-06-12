---
title: "Abiword and system crash"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by aimpau on 2008-06-12
Hi everyone,

Whenever I open Abiword and type something for a few minutes, it would automatically crash the whole system which I have to hard reset.

Any help?

Here's the dmesg part that really got me worried:

[   57.975640] audit(1213324838.965:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4682 profile="/usr/sbin/cupsd" namespace="default"


I think it has something to do with cupsd not being able to access /etc/cups/cupsd.conf

I checked and the file is in there.

---

### Post by powerpleb on 2008-06-12
I've never liked AbiWord, always found it buggy.

---

