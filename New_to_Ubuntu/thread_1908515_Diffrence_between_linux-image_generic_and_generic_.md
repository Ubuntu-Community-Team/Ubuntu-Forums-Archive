---
title: "Diffrence between linux-image generic and generic pae"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by qpens on 2012-01-13
What is the difference between generic and generic pae

---

### Post by amauk on 2012-01-13
PAE is an kernel extension that allows 32bit systems to see more than 4GB of address space

A computer system has a finite address space, which is bound by the width of the CPU registers

2^32 = 4294967296 = 4GB

This is seen by the end-user as an inability to "see" more than approx. 3.5 GB of RAM
(approx 3.5 RAM + approx 0.5 other addressable stuff = 4GB limit)

PAE is an extension that allows for the transparent re-mapping of the address space so that, overall, you can address more

It's a hack to overcome an architectural limitation, and does have drawbacks
no single process can ever use more than 3GB of RAM

If you have 64bit capable hardware, go with a 64bit OS, rather than 32bit+PAE

*edit*
sorry, thought this was in the server forum....
damn browser tabs
wouldn't have given such a jargon-y answer if I'd realised this was the beginners forum

---

### Post by Basher101 on 2012-01-13
the PAE kernels are a patched version for 32 bit systems, so that the 32 bit version can allocate more than 4 GB of RAM. Usually 32 bit Operating systems are limited to a maximum of 4 GB RAM.

regards

edit: beat me to it.

---

### Post by qpens on 2012-01-13
Thanks guys

---

