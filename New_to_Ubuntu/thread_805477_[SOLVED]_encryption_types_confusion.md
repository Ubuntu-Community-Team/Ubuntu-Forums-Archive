---
title: "[SOLVED] encryption types confusion"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by noorez on 2008-05-24
Hi. I am experimenting with the 
Applications->Accessories->Passwords and Encryption keys utility. I first tried to create the RSA key. the option said (sign only). I then downloaded and installed thunderbird's Enigmail extension. I first tried to sign a message and send to another email account i keep for experiments and I was able to open it and get a good signature reading. I then tried to encrypt a message by using my "experiment account" to send to my primary account and it worked. However, the RSA key i generated was supposed to be for sign only. Why did it work to encrypt a message?

Another question I then have is what algorithm is best for signing and what is best for encrypting in terms of security?

---

### Post by Steve413z on 2008-05-24
there is so much debate about this, the bottom line is neither DSA or RSA is "better" as in more secure, DSA Elgamal, is the only way you can both Encrypt and Sign messages (at least using the method you are using)

---

### Post by Steve413z on 2008-05-24
I am not a cryptologist nor a mathematician,  so I am not an expert on which one is more secure, either way, it's hard enough to require some serious computing power to try to crack either one.

---

### Post by noorez on 2008-05-27
> **Steve413z said:**
> there is so much debate about this, the bottom line is neither DSA or RSA is "better" as in more secure, DSA Elgamal, is the only way you can both Encrypt and Sign messages (at least using the method you are using)

umm...perhaphs i was a bit confusing in my question. I was able to the RSA (sign only) option to generate a key which I was able to use both for signing and encryption/decryption using the Engmail extension for Thunderbird. I was just wondering why a "sign only" key was accepted for encryption.

---

### Post by noorez on 2008-05-28
another question....I created the DSA/Elgamal key. Using Thunderbird, I was able to sign a message but I could not encrypt one? I think the error said something about not being able to find the public key.....

--------

(fixed) it started working again. I created a DSA/Elgamal key for the "experiment email account". I then tried to send an encrypted message to my regular account and it worked. 

What I don't understand here is why does the "experiment account" need keys. Don't I only need the public key of the person that I'm sending to?

---

### Post by noorez on 2008-05-28
In the case of DSA/Elgamal key generation, I found two keys for DSA but only one key for Elgamal under the 
Applications->Accessories->Encryption Keys as subkey. Doesn't Elgamal use a public/private key method?

---

