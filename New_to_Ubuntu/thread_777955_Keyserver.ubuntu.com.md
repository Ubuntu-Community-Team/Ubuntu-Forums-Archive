---
title: "Keyserver.ubuntu.com"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Nxion on 2008-05-01
How do I remove pgp keys from a key server. I just recently uploaded a new keypair that I generated and noticed that there are keys on this server that are old and ones I dont use any more.

Any ideas ?

Thanks

---

### Post by Monicker on 2008-05-01
> **Nxion said:**
> How do I remove pgp keys from a key server. I just recently uploaded a new keypair that I generated and noticed that there are keys on this server that are old and ones I dont use any more.

Any ideas ?

Thanks


You don't remove them.  You generate a revocation certificate and upload that to the server, so that people know the keys are no longer valid.

You can also use a shorter expiration time when you create keys in the future.

---

### Post by Nxion on 2008-05-01
> **Monicker said:**
> You don't remove them.  You generate a revocation certificate and upload that to the server, so that people know the keys are no longer valid.

You can also use a shorter expiration time when you create keys in the future.

How do I go about generating a revoke cert ?

---

### Post by Monicker on 2008-05-01
> **Nxion said:**
> How do I go about generating a revoke cert ?


[https://help.ubuntu.com/community/GnuPrivacyGuardHowto#head-b05412360e2ef9ea7330f02542e58371ac6aa56d]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto#head-b05412360e2ef9ea7330f02542e58371ac6aa56d")


You need the private key, and the passphrase which goes with it, in order to generate the revocation certificate.  Then you upload that to the server, once you are positive that you really want to revoke that key pair.

---

