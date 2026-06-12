---
title: "[SOLVED] Repository Problems"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Wake Rider on 2008-06-28
I have put a fresh install of Ubuntu 8.04 on my laptop, and when I go to system update and click the check button, this error message comes up:

Could not download all repository indexes:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

What do I do??:confused:

---

### Post by iaculallad on 2008-06-28
What about using the terminal for update, does it display the same error?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Wake Rider on 2008-06-28
> **iaculallad said:**
> What about using the terminal for update, does it display the same error?

```
sudo apt-get update && sudo apt-get upgrade
```

Same error...

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by wormser on 2008-06-28
Try changing your download location.  System> Administration> Software Sources> Download from.

---

### Post by Wake Rider on 2008-06-28
> **wormser said:**
> Try changing your download location.  System> Administration> Software Sources> Download from.

I changed my software sources from the New Zealand ones to the main ones which has stopped this error occurring. Thank you!

---

