---
title: "Troubles with apt-get update"
date: 2016-02-12
forum: New to Ubuntu
---

### Post by logan29 on 2016-02-12
First day of using Xubuntu, the only changes I've made are that I've attempted to install Tox. After installing the repository I get this error anytime I run sudo apt-get update:
```
W: GPG error: https://pkg.tox.chat nightly InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2B076511A171ABE
W: Failed to fetch http://mirror.nexcess.net/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://mirror.nexcess.net/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://mirror.nexcess.net/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://mirror.nexcess.net/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch https://pkg.tox.chat/debian/dists/nightly/main/binary-amd64/Packages  HttpError404

W: Failed to fetch https://pkg.tox.chat/debian/dists/nightly/main/binary-i386/Packages  HttpError404

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I've tried the following solutions found online:
Running apt-get clean
Running rm /var/lib/apt/lists/*, afterwards running apt-get update

If anyone needs extra details ask, and I will provide them. Thanks!

EDIT: After looking around for a while I finally found a solution, for those who have similar issues, you may have to disable some sources in the Ubuntu Software Center if you're getting issues out of Tox and re-run the command.

---

### Post by v3.xx on 2016-02-13
Your Tox link is no good, a command will not make it work.

[https://pkg.tox.chat/debian/dists/nightly](https://pkg.tox.chat/debian/dists/nightly)[COLOR="#FF0000"]/main/[/COLOR]binary-i386/Packages

[https://pkg.tox.chat/debian/dists/nightly/](https://pkg.tox.chat/debian/dists/nightly/)

---

