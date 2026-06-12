---
title: "Full Disk Encryption On Ubuntu 8.04 Hardy Heron"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Gost-Taras on 2008-09-14
Hello guys

I recently downloaded Ubuntu 8.04 that uses Alternative installation method from Softpedia website. Basically all it does is encrypts entire system, and LVM. 

My question is does anyone generally anyone know what kind of encryption it uses and how secure it actually is?

Would be possible for a advnaced hackers or organisations to actully crack it ?

Just curious 

Also on ubuntu which uses encryption of LVM does not require so much updates as normal one ? what really the difference ? 

When i first installed normal ubuntu i had about 250 updates to install it but with encrypted one only 130. 

But you get all the applications and everything identical. except that there is some extra download sources such as from your cd about 73 in total

---

### Post by scorp123 on 2008-09-14
> **Gost-Taras said:**
>  My question is does anyone generally anyone know what kind of encryption it uses and how secure it actually is?  [http://luks.endorphin.org/](http://luks.endorphin.org/)

> **Gost-Taras said:**
>  Would be possible for a advnaced hackers or organisations to actully crack it ? If you used a weak password (e.g. dictionary word + too short) then yes; same of course if you wrote down the password on a sticky note and glued it next to the screen ... Don't laugh, I have seen people do this! :(

> **Gost-Taras said:**
>  When i first installed normal ubuntu i had about 250 updates to install it but with encrypted one only 130.  You probably downloaded **Ubuntu 8.04** the first time you installed Ubuntu, but then **Ubuntu 8.04.1** the second time. Canonical updated their ISO's to 8.04.1 some weeks ago, so the OS is already partially patched when you install it ... Hence: less to download after the installation.

---

