---
title: "[SOLVED] Medibuntu error?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-26
On reloading my 3rd party software sources (System->Administration->Software Sources->3rd Party Software) i'm met with the following error...

```
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

Can anyone tell me how to fix it?

Thanks in advance:KS

---

### Post by cozmicharlie on 2008-07-26
Open a terminal and copy this command at the prompt.  Should install the key.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by SunnyRabbiera on 2008-07-26
Right, make sure to follow all the instructions on the medibuntu page.

---

