---
title: "Verifying kernel download with gpg"
date: 2010-01-18
forum: Programming Talk
---

### Post by swappo1 on 2010-01-18
I am not sure why I am getting the warning that the key is not certified with a trusted signature.
```
hopchewer:/home/hopchewer/downloads# gpg --verify linux-2.6.32.3.tar.bz2.sign linux-2.6.32.3.tar.bz2
gpg: Signature made Wed 06 Jan 2010 06:45:39 PM EST using DSA key ID 517D0F0E
gpg: Good signature from "Linux Kernel Archives Verification Key <ftpadmin@kernel.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: C75D C40A 11D7 AF88 9981  ED5B C86B A06A 517D 0F0E

```
I imported the key prior to verifying:
```
hopchewer:/home/hopchewer/downloads# gpg --keyserver wwwkeys.pgp.net --recv-keys 0x517D0F0E
gpg: requesting key 517D0F0E from hkp server wwwkeys.pgp.net
gpg: key 517D0F0E: "Linux Kernel Archives Verification Key <ftpadmin@kernel.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```
I am following the guide [http://www.kernel.org/signature.html](http://www.kernel.org/signature.html) .
Is it that the key is outdated?

---

