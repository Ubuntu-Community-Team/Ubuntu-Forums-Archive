---
title: "kernel compilation"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by maroofi on 2012-04-17
hi all
i have Ubuntu 11.10 installed on my pc runing under VMware workstation 8
and i downloaded kernel 2.6.35.13 from kernel.org and did:
unpack  & copy source to /usr/src
make gconfig
make
make modules_install
make install
update-grub
reboot
executed all above instructions and everything worked fine but now when i reboot my system and type "uname -r" in terminal i get "3.0.0-12-generic".
is it ok? i guess it should be 2.6.35.13 instead of 3.0.0.12-generic.is that right???

---

### Post by maroofi on 2012-04-17
problem soleved i just hold shift down while boot process and grub menu appeared then select older kernel version..

---

