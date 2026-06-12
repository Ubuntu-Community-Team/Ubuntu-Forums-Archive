---
title: "Encription?"
date: 2008-01-16
forum: Programming Talk
---

### Post by AndreiMe on 2008-01-16
does anyone know a free code to show how an encription algorithm works, or maybe one already built than i can study? (for files)

---

### Post by mike_g on 2008-01-16
a very simple encryption method to start off with would be [Xor Encryption](http://www.cprogramming.com/tutorial/xor.html)

Basic xor encryption is easily crackable tho, you may also want to check out [md5 hashing](http://en.wikipedia.org/wiki/MD5).

---

### Post by AndreiMe on 2008-01-16
thx alot i'm gonna have fun with this :D

---

### Post by Martin Witte on 2008-01-16
here you got aes encryption in code [http://jclement.ca/software/pyrijndael/](http://jclement.ca/software/pyrijndael/)

---

### Post by CptPicard on 2008-01-16
> **mike_g said:**
> 
Basic xor encryption is easily crackable tho, you may also want to check out [md5 hashing](http://en.wikipedia.org/wiki/MD5).

Good luck trying to "decrypt" your md5hash. :) It's not an encryption algorithm, but a hash ... it produces a value that is intentionally practically impossible to find the original of, including for those who created it (if they no longer have the original at hand).

@OP, I would not recommend you look at actual code of implementations of encryption algorithms, but some high-level descriptions of them. They would probably be much more educational than some highly-optimized, obscure piece of source.

---

### Post by Wybiral on 2008-01-16
> **CptPicard said:**
> Good luck trying to "decrypt" your md5hash. :)

/me encrypts his project folder using MD5. Wow, it also compresses it too, all the way down to 16 bytes! Now, to decrypt it... (waits for a rainbow table to implement my project folder) ...

---

