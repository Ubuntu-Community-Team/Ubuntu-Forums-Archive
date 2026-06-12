---
title: "linux-libc-dev_2.6.24-19.34_amd64.deb  404 Not Found"
date: 2008-11-24
forum: Packaging and Compiling Programs
---

### Post by green_bergamot on 2008-11-24
Hi,

I'm trying to install the c++ related packages on my amd64 box, but apt-get fails on:

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.34
  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-19.34_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-19.34_amd64.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I there anything i can do to fix it?

Thanks,

---

### Post by loomsen on 2008-11-24
Humm, just updated mine earlier... should work actually, try another server.

The main server to be sure.
> 
docter[~] apt-show-versions linux-libc-dev
linux-libc-dev/intrepid-proposed uptodate 2.6.27-10.20
docter[~] 


Do you need that specific verion then?

---

### Post by green_bergamot on 2008-11-24
Hi loomsen, I need another something, but not the server :)

It worked after update for me as well,

Thanks!

---

