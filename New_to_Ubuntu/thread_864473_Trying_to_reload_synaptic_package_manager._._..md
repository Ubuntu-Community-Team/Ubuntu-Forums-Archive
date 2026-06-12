---
title: "Trying to reload synaptic package manager. . ."
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-19
Hey:

Absolute beginner here. I'm trying to reload synaptic package manager and keep gettin this error: 

"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

It appears that other data is not being downloaded as well.

Thank you,
Ed

---

### Post by Oldsoldier2003 on 2008-07-19
> **Whatrymes said:**
> Hey:

Absolute beginner here. I'm trying to reload synaptic package manager and keep gettin this error: 

"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

It appears that other data is not being downloaded as well.

Thank you,
Ed

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
[QUOTE=Ubuntu Wiki]You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu. [/QUOTE]

That should sort you out.
[https://help.ubuntu.com/community/Medibuntu#Adding](https://help.ubuntu.com/community/Medibuntu#Adding) the Repositories

---

### Post by ibutho on 2008-07-19
Download medibuntu-key.gpg from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) and install it using apt-key e.g.
```
sudo apt-key add medibuntu-key.gpg
```

---

### Post by Whatrymes on 2008-07-19
Thanks, awesome as usuall!!

Ed

---

