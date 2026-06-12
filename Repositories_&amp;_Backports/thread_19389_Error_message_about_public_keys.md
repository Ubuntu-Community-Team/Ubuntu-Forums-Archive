---
title: "Error message about public keys"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by taniwha on 2005-03-11
When I reload my repositories I got this error message:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

I can install stuff, but I do not know why I get this message and how to sort it out.
Thanks in advance

---

### Post by edebont on 2005-03-11
To add the public key to your system (so the error messages won't appear again)

Open up a console and type the following commands:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --export 1f41B907 > /etc/apt/marillat.key
apt-key add /etc/apt/marillat.key

If you run apt-get update you shouldn't see any error messages.

---

### Post by ACK!! on 2005-03-12
[QUOTE=edebont]To add the public key to your system (so the error messages won't appear again)

Open up a console and type the following commands:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --export 1f41B907 > /etc/apt/marillat.key
apt-key add /etc/apt/marillat.key

If you run apt-get update you shouldn't see any error messages.[/QUOTE]

Thanks man I was getting the same error.  

That fixed me up proper like.

---

### Post by rudiz on 2005-03-12
Do I have to do the commands with sudo?

---

### Post by taniwha on 2005-03-12
[QUOTE=edebont]To add the public key to your system (so the error messages won't appear again)

Open up a console and type the following commands:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --export 1f41B907 > /etc/apt/marillat.key
apt-key add /etc/apt/marillat.key

If you run apt-get update you shouldn't see any error messages.[/QUOTE]

Done. Now, everything is fine.
Thanks a lot.

---

### Post by LongTooth on 2005-03-13
Can one use these repositories on Hoary? I had them on my Warty system. But after I upgraded to Hoary I commented them out. Are they safe to use with Hoary? Thanks.

---

