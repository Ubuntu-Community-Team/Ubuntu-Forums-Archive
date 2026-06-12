---
title: "Black screen after FGLRX with 7970x2"
date: 2017-06-24
forum: New to Ubuntu
---

### Post by cs-deviance on 2017-06-24
Hi!

I got some problem with FGLRX.

Some info:
```
Linux pc 4.4.0-81-generic #104~14.04.1-Ubuntu SMP Wed Jun 14 12:45:52 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
X.Org X Server 1.15.1
```



Vga:
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
```


Xorg Log: [https://pastebin.com/gfmsZji9](https://pastebin.com/gfmsZji9)

I googled many but didn't find any solution.
(I can go back with open-source drivers but i want to fix fglrx. any other solution is good)

Thanks :)

---

### Post by ajgreeny on 2017-06-25
I assume from your kernel version that you are probably using 16.04 version of *ubuntu and if that is correct I am afraid there is no other choice for graphics driver than the open source radeon driver that you currently have running.

The kernel and xorg version in 16.04 is totally incompatible with fglrx, and AMD are not going to change that situation as they are working hard on producing, and opening up the source, for all their new drivers in Linux.

I future we may have more availability of AMDGPU for your 7970 card but not yet, and unfortunately I do not anticipate it coming in the near future; I hope I am wrong!

---

