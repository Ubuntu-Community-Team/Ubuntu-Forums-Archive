---
title: "cryptography"
date: 2009-09-27
forum: Programming Talk
---

### Post by hsdrgmi on 2009-09-27
I'm looking for a fast way to encrypt/decrpyt in C/C++, something like AES, without using some large library.

Thank you for any suggestions.

---

### Post by slavik on 2009-09-27
tripledes might be worth a look.

keep in might than if you want to do anything serious, you will need a library because writing your own code is much more difficult (if you want your encryption to be secure).

---

### Post by smartbei on 2009-09-28
You can easily find just the source for AES... For example: [http://www.hoozi.com/Articles/AESEncryption.htm](http://www.hoozi.com/Articles/AESEncryption.htm) or [http://www.codeproject.com/KB/security/aes.aspx](http://www.codeproject.com/KB/security/aes.aspx) or best yet [http://csrc.nist.gov/archive/aes/rijndael/wsdindex.html](http://csrc.nist.gov/archive/aes/rijndael/wsdindex.html).

I recommend using that last site since it is actually NIST (the organization that set cryptographic standards and chose AES), and because it includes test vectors.

---

