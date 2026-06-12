---
title: "handing off keys"
date: 2011-04-16
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-16
How does a website, or any internet protocol secure it's communications? For example: If I develop a secret algorithm to encrypt my own communications in real life. I then have to tell someone else how to understand it. If a person is intercepting communications, how do they not intercept the key with the rest of the communication?

---

### Post by Some Penguin on 2011-04-16
[http://en.wikipedia.org/wiki/Asymmetric_encryption]("http://en.wikipedia.org/wiki/Asymmetric_encryption")

combined with
[http://en.wikipedia.org/wiki/Public_key_infrastructure]("http://en.wikipedia.org/wiki/Public_key_infrastructure") and/or [http://en.wikipedia.org/wiki/Web_of_trust]("http://en.wikipedia.org/wiki/Web_of_trust") for authentication.

In certain cases it's also possible to have an initial out-of-band transfer that would be very difficult to replicate later.  For instance, it might be possible to provide somebody with enough data for a one-time pad to encrypt any likely volume of traffic until the next time he can reestablish contact in a secure environment.

---

### Post by NovaAesa on 2011-04-16
If you are using a "secret" algorithm, you are doing it horribly wrong. Key distribution is usually done with public key encryption such as RSA. Once you have keys distributed, you can use a shared key encryption, e.g. AES or 3DES.

EDIT: ninja'd

---

### Post by ki4jgt on 2011-04-16
How is it possible to encrypt a communication using one key say, the public one, without being able to decrypt using the same key? Can you give me a real live example (Out of the computer)

I know this isn't very secure, but if my key was "ABC" converted to numbers would be +1 +1 +1 applied to the message "ICU" the message would become "JDV". I can get how a private key could be "CDF" or any combination of letters which when undone, take "JDV" back to "ICU" but how can encrypt a communication without being able to unencrypt it using the same key?

I'm not saying it isn't possible, but I just don't understand it :-(

---

### Post by NovaAesa on 2011-04-16
If I understand you question correctly, you want to know how it is possible to encipher a message using a publicly known key and yet not be able to decipher it using the same key.

Here's the kicker, this feat is actually impossible. The only way of providing 100% secure encryption is OTP [http://en.wikipedia.org/wiki/One-time_pad](http://en.wikipedia.org/wiki/One-time_pad)

But it can be done in a way that it's very *hard* to decipher the message using the public key. For example, in RSA the public key is a pair of numbers (n, e) and the private key is (n, d). It's possible to decipher a message enciphered using the public key only using the public key, however it is very hard! It involves calculating the totient function of n, and for the time being at least, there is no polynomial time algorithm that is able to do this.

Take a look at [http://en.wikipedia.org/wiki/RSA](http://en.wikipedia.org/wiki/RSA) it will explain the RSA algorithm way better than I ever could.

---

### Post by BkkBonanza on 2011-04-17
Public key systems use matched pairs of keys. Public and Private. Encrypting with one half can only be decrypted with the other half. So you never send the private key - only the public key. People who want to send to you encrypt with your public key since only your private key can decrypt it. And the reverse for you sending to them - encrypt with their public key, only they can decrypt with their private key.

Some basic reading on Wikipedia will clear all this up. Web site and client  certificates are based on the same idea but also includes key signing to authenticate the validity of the public keys (by third parties) embedded in them.

---

