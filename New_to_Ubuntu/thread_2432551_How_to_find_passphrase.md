---
title: "How to find passphrase"
date: 2019-12-04
forum: New to Ubuntu
---

### Post by antee on 2019-12-04
Hello guys,

 During the instalation of Ubuntu 19.10 i set up login password.
 Now if i run:
 ```
ecryptfs-unwrap-passphrase
```
i get:
 ```
stat: No such file or directory
Usage:
 ecryptfs-unwrap-passphrase [file]
 or
 printf "%s" "wrapping passphrase" | ecryptfs-unwrap-passphrase [file] -
```
If i run:
 ```
ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
```
 i get:
 ```
Passphrase:
```  
 
 but there is no passphrase
Why these commands don't work.
 
 Thank you
 antee

---

### Post by CatKiller on 2019-12-04
I've never used filesystem encryption, but it's standard behaviour not to show anything when typing in a password to prevent leakage of the password length.

---

### Post by antee on 2019-12-05
According to this article
 [https://wiki.archlinux.org/index.php/Fscrypt](https://wiki.archlinux.org/index.php/Fscrypt)
 
 eCryptfs is no longer being actively developed, and its largest users have migrated to dm-crypt (Ubuntu) or to fscrypt (Android and Chrome OS).  
 
 No wonder that ecryptfs-unwrap-passphrase doesn't work.
 
 So how to find passphrase in Ubuntu 18.04 and 19.10.
 
Thank you

---

### Post by TheFu on 2019-12-05
If you don't know the passphrase, we certainly do not.  It is part of security.

As a developer, we are taught to never store plain text passwords anywhere. Only store the encrypted+salted result, so that any passphrase entered by the user can go through the same encrypt+salt process and the result of that process compared to what is stored.

Ain't no way to pull the original passphrase out. Sorry.

---

### Post by QIII on 2019-12-05
This is about to spill over into a discussion about hacking/cracking passwords.  We do not allow such discussions here.  I might suggest the Kali forums for such advice.

Closed.

---

