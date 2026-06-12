---
title: "[SOLVED] Not sure about this error message"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by sag7392 on 2008-11-07
Hello all,

This error message appears when update manager is running- 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

It doesn't seem to affect anything, but my question is how can I keep this from popping up. If needed, I am running 8.04.

Thanks in advance for any responses...Linux/Ubuntu rocks!!!

---

### Post by shifty_powers on 2008-11-07
the encryption key has run out.

happens from time to time.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

should do it...

---

### Post by sag7392 on 2008-11-07
Thanks! Problem solved

---

