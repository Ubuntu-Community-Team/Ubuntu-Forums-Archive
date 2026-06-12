---
title: "GPG Error: Wine"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by vfrankli on 2008-06-17
Hello, does anyone know if this will cause updating problems?


W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by Happy_Man on 2008-06-17
That just means that it's not an "official" Ubuntu update server. It's fine, go ahead and install whatever.

---

### Post by bodhi.zazen on 2008-06-17
for security purposes apt-get uses gpg to ensure the integrity of the software you are installing.

that error message indicates you have not imported the proper gpg key for the wine repository.

for a more detailed explanation :

[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

---

### Post by kansasnoob on 2008-06-17
I ran into the same thing and this fixed it:

[http://wiki.winehq.org/GPGKey](http://wiki.winehq.org/GPGKey)

But, that was in Gutsy. Not sure if it still works in Hardy.

---

### Post by fbuchele on 2008-08-04
Confirmation: It works on Hardy.

---

