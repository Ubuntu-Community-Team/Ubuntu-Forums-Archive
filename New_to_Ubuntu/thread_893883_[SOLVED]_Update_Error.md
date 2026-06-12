---
title: "[SOLVED] Update Error"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-18
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

What is this trying to tell me?  What can I do about it?  Thanks

---

### Post by spiderbatdad on 2008-08-18
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

[http://ubuntuforums.org/showthread.php?t=713009](http://ubuntuforums.org/showthread.php?t=713009)

---

### Post by jfbays on 2008-08-18
The info from your link seemed to work.  That is: the Update Error message no longer appears.  Thanks.

---

### Post by sergiom99 on 2008-08-22
thanks dude, I think I fixed it too.

---

