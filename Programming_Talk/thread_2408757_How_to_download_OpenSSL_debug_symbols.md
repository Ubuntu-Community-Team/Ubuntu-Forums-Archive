---
title: "How to download OpenSSL debug symbols?"
date: 2018-12-22
forum: Programming Talk
---

### Post by SagaciousKJB on 2018-12-22
I'm working with OpenSSL's EVP library and was checking for leaks with valgrind, and had a problem where the output information stopped with OpenSSL's functions.  Someone on reddit told me to install openssl's debug symbols package so that my debugger would be able to show me which line of OpenSSL's library files was causing a problem too, but I have no idea how to do this.  They  mentioned on their system they'd just download and install libssl-dbgsym but I don't see any similar such package on Ubuntu.

Perhaps if I downloaded/installed it from the source version in the repositories?

---

### Post by Bachstelze on 2019-01-07
See [here]("https://wiki.ubuntu.com/Debug%20Symbol%20Packages") for how to install debugging symbols. You will probably need package *libssl-dbg* or something similar.

---

