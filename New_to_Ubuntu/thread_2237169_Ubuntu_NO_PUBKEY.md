---
title: "Ubuntu NO_PUBKEY"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by 0N3 on 2014-07-31
```
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://ie.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ie.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ie.archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ie.archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

```


I have tried adding the keys by:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
```

This still doesn't solve my problem in fact it does nothing to help whatsoever! Any help appreciated before I just dump Ubuntu and go back to Windows as always when Ubuntu plays up causing me headache after headache for the simplest of tasks!

---

### Post by 0N3 on 2014-07-31
I also tried Y-PPA Manager clicked on Advanced button and selected "Try Import Missing GPG keys" this also had no affect on the issue!

---

### Post by plucky on 2014-07-31
Have you tried a different Repository?

Open **Software Sources** and switch your Download Server to "Main" and see if you get the same error.

Good Luck

---

### Post by 0N3 on 2014-07-31
I tried various different from my server (Ireland) and various other countries including main and still same issue :(

---

### Post by 0N3 on 2014-07-31
I got this sorted! I don't know if this was the correct thing to do but this worked for me:

```
sudo rm -R /etc/apt/trusted.gpg.d
```

Then:

```
sudo mkdir /etc/apt/trusted.gpg.d
```

I then added all my PPA's again and know it is working fine :)

Thanks for the reply appreciate it!

---

