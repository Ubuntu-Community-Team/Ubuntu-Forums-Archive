---
title: "[SOLVED] Get a W: GPG error message when runing update manager"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Spooky5 on 2008-07-17
I get the following message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

What should I do?

---

### Post by Vivaldi Gloria on 2008-07-17
> **Spooky5 said:**
> I get the following message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

What should I do?

It seems that you have added the medibuntu repo without adding its key. The command for it is this:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

See

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bhadotia on 2008-07-17
Have you installed the medibuntu-keyring package. This might be possibly because you don't have that package .

---

### Post by iaculallad on 2008-07-17
> **Spooky5 said:**
> I get the following message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

What should I do?

On your terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Spooky5 on 2008-07-17
Aha! Don't know how I managed to do that, lol. :-k

Thank you all! I think it's fixed now.

---

