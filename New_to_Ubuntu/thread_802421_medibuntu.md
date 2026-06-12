---
title: "medibuntu"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Neilisgreat on 2008-05-21
hello , I have done an update and keep getting error, see below
can you help?

im on 8.04 unbuntu

PG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/hardy/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Maestro23 on 2008-05-21
Add the key: [https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu)

---

### Post by Neilisgreat on 2008-05-21
sorry but how,?

---

### Post by tom56 on 2008-05-21
Run this command in a terminal:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Maestro23 on 2008-05-21
> **Neilisgreat said:**
> sorry but how,?

It's on the page a linked you to.

Edit: tom56 posted if for you.

---

### Post by Neilisgreat on 2008-05-21
many thanks !

---

