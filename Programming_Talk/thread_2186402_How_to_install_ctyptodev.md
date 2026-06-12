---
title: "How to install ctyptodev"
date: 2013-11-07
forum: Programming Talk
---

### Post by dev9 on 2013-11-07
I am running Ubuntu server 12.04,3 LTS (linux 3.2.0.55), but I do not see any /dev/crypto

Is cryptodev builit-in, do I need to install a package (which package?), or do I need to download and make/build from cryptodev-linux.org?

Thanks.

---

### Post by Bachstelze on 2013-11-07
It does not seem to be in the repositories, you will have to compile it from source following the instructions on the website. It seems to work on 12.04, but the OpenSSL build from the repositories seems to be compiled without cryptodev support (I see no difference in performance before and after loading the module, but dev/crypto does appear).

---

