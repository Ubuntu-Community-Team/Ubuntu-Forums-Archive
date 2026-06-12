---
title: "pubkey?"
date: 2006-01-15
forum: Repositories &amp; Backports
---

### Post by qbic on 2006-01-15
I'm getting this one when I try to apt-get update, what's up? where do I get the pubkey? W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5098 W: You may want to run apt-get update to correct these problems

---

### Post by Mr_Grieves on 2006-01-15
Try:
```

apt-get upgrade
apt-get update

```

---

### Post by qbic on 2006-01-16
no
I had to wget the pubkey

---

