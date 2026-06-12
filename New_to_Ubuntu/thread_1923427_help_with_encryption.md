---
title: "help with encryption"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-02-10
I notice there is ecryptfs that comes with ubuntu but how would I use it to encypt a simple txt file with Terminal?  example?

---

### Post by winh8r on 2012-02-10
ecryptfs is a utility to encrypt a partition on your system, such as /home and basically encrypts and protects everything.

Using it unless you need it is not advised if there is any risk that you will forget the passphrase/security key as it is almost impossible to recover data from a locked ecryptfs partition as it is very hard to detect on the hdd.


you can use gpg to encrypt individual files

 	gpg -c file	Encrypt file
 	gpg file.gpg	Decrypt file


Just type man gpg into the terminal for more info

---

