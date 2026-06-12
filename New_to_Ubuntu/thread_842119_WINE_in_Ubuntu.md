---
title: "WINE in Ubuntu"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by quilltron on 2008-06-27
Thinking that Hardy Heron would be enhanced by the addition of WINE, I am balked by this error message that baffles me and none of the FAQ items cover it.
 W: GPG error:http//wine.budgetdedicated.com hardy Release: 
The following signatures couldn't be verified because the Public Key is not available: 
NO_PUBKEY:58403026387EE263 What is it telling me?  quilltron.

---

### Post by shae on 2008-06-27
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by p_quarles on 2008-06-27
It's telling you that the remote server's identity can't be verified because you haven't acknowledged their cryptographic key. shae's command will download and "install" their key so that in the future, the key will verify that you are connecting to the correct server.

For more info on the way these keys work, look up PGP and GPG on Wikipedia (or your reference source of choice).

---

