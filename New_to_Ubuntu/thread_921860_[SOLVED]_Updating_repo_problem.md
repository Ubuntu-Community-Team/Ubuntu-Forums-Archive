---
title: "[SOLVED] Updating repo problem"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Ntweat on 2008-09-16
whenever i m using 

```
sudo apt-get update
```

or

```
sudo aptitude update
```

i get the following error

```
W: GPG error: http://archive.canonical.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ftp.uni-kl.de hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ftp.uni-kl.de hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ftp.uni-kl.de hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ftp.uni-kl.de hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ftp.uni-kl.de hardy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

```

how to solve it... plz help

---

### Post by phidia on 2008-09-16
Those errors are often related to your gpg key. When you enabled those repos did you also have a gpg key that you were suppose to import?
There's a guide to doing that [here]("http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-import.html"). Sorry that's a redhat guide but it's a similar process. I'll include the ubuntu one if I get a chance.

---

### Post by Ntweat on 2008-09-16
well... i m sort of new.... i did not get any key... now from where to impot it....

---

### Post by forger on 2008-09-16
Go to Applications > Accessories > Terminal, execute these commands:```

wget http://archive.ubuntu.com/ubuntu/project/ubuntu-archive-keyring.gpg -O- | sudo apt-key add -
sudo apt-key update
sudo apt-key net-update
```

Now it should be ok:
```
sudo apt-get update
```

---

### Post by Ntweat on 2008-09-17
thanks

---

