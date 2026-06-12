---
title: "[Python] Best encryption to use"
date: 2011-05-10
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-10
I'm writing a chat client. I'm going to implement an encryption key which two users share. (Every user pair has their own encryption key) So:

User A + User B: key1
User A + User C: key2
User B + User C: Key3

So every two people get their own keys to communicate with. The messages can be of any length. What is the best way to encrypt them?

---

### Post by ve4cib on 2011-05-10
Two options I can think of off the top of my head:

1- assign each user a random 64-bit key.  When user 1 and user 2 want to encrypt messages between each other, they simply user key1+key2 as the key for a 128-bit AES algorithm.  It's not super-secure, but it's easy

2- each user has an RSA public/private key.  When user 1 and user 2 want to encrypt messages they use private1+public2 (for user 1) or private2+public1 (for user 2).  RSA has the neat property that if you encrypt a message using your own private key, plus the public key of the other person, the message can be decrypting user the other private key and the other public key, allowing secure communication between two users.

---

### Post by ki4jgt on 2011-05-10
> **ve4cib said:**
> Two options I can think of off the top of my head:

1- assign each user a random 64-bit key.  When user 1 and user 2 want to encrypt messages between each other, they simply user key1+key2 as the key for a 128-bit AES algorithm.  It's not super-secure, but it's easy

2- each user has an RSA public/private key.  When user 1 and user 2 want to encrypt messages they use private1+public2 (for user 1) or private2+public1 (for user 2).  RSA has the neat property that if you encrypt a message using your own private key, plus the public key of the other person, the message can be decrypting user the other private key and the other public key, allowing secure communication between two users.

Is RSA safe from MITM attacks? I plan to route the traffic through (Untrusted) third-party sources. I would like to keep the traffic as safe as possible and keep users from receiving messages which aren't intended for them. . . I know anything can be decrypted, but I want the users to be able to have as much security as possible. Not to mention the problem when those third parties (WILL) try to insert data into those messages. I've already got message varification. Every message is directed through 3 third party sources. If the message is altered in any way by one of them, the other two will be used. If those messages are different, the user will not get a message at all.


EDIT: Does Python have any built in RSA modules?

---

### Post by ve4cib on 2011-05-11
Provided you're never transmitting the private keys then RSA is secure.  I'm assuming that each client is setting up their own key on their own machine.

---

### Post by nvteighen on 2011-05-11
If you go for public encryption, wouldn't it be much better to use OpenGPG? There's the python-gpgme package, and it'd let you use a well-known and well-tested implementation.

If you go for RSA, I think PyCrypto (python-crypto in APT) has an implementation of it. Look at [http://www.dlitz.net/software/pycrypto/](http://www.dlitz.net/software/pycrypto/)

---

### Post by CptPicard on 2011-05-11
For shared-key channels, you may want to check out

[http://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange](http://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)

---

### Post by ve4cib on 2011-05-11
> **nvteighen said:**
> If you go for public encryption, wouldn't it be much better to use OpenGPG? There's the python-gpgme package, and it'd let you use a well-known and well-tested implementation.

I believe OpenGPG implements RSA for for its asymmetric encryption.

---

### Post by ki4jgt on 2011-05-11
> **ve4cib said:**
> Provided you're never transmitting the private keys then RSA is secure.  I'm assuming that each client is setting up their own key on their own machine.

Yes, and the public keys WILL NOT be exchanged over the client. The public keys will be placed in a "Connection File" which the users will have to exchange beforehand or the service will not even work.


EDIT: If I add one of these packages to my program. How can I add it to my user's python directories?

---

### Post by ki4jgt on 2011-05-16
Program just went in a new direction :-( But I have a question, how when using RSA can someone not just place the encryption in reverse from the public key and simply impersonate the original author of the post? Because no matter what key I used to encrypt the message, it can always be decrypted using the same key only reversing the algorithm. I thought about changing keys, but once they get one key, they have no problem getting every key which follows :-( Which means, third parties must be involved :-(

---

### Post by nvteighen on 2011-05-16
> **ki4jgt said:**
> Program just went in a new direction :-( But I have a question, how when using RSA can someone not just place the encryption in reverse from the public key and simply impersonate the original author of the post? Because no matter what key I used to encrypt the message, it can always be decrypted using the same key only reversing the algorithm. I thought about changing keys, but once they get one key, they have no problem getting every key which follows :-( Which means, third parties must be involved :-(

You can't reverse the RSA algorithm. The only known way to decrypt a message in RSA is by using the inverse key. Currently the only way to attack RSA is by developing more efficient methods to find the inverse key (prime factoring, specially).

The strength of RSA lies on the "RSA problem" :P. If M is the plaintext, K the cipher, k the key used and m the modulus, then you know that K is:

```

K = M^k (mod m)           (1)

```

That's the RSA formula. Now, "inverting" the algorithm would imply this:

```

M = K^(1/k) (mod m)       (2)

```

But while exponentiation of an integer is guarranteed to return one and only integer value, the root may return multiple values, which all will have to be integers because we're in modulo arithmetics. Nowadays, there's no known deterministic way to take roots in modulo arithmetics and showing one would award you quite a name in theoretical mathematics. In other words, we still don't know how to solve (2); all we've got are some statistical ways to guess the possible roots.

I guess someone more familiar with this sort of maths will explain this better than the linguist I am :P

---

### Post by ve4cib on 2011-05-16
To encrypt an RSA message shared between two users you need:

- recipient's public key
- sender's private key
- sender's passphrase

And to decrypt the message the recipient needs:
- sender's public key
- recipient's private key
- recipient's passphrase


In order to spoof a message from Alice to Bob, a hacker (say Eve) would need Alice's private key and Alice's passphrase.  If Eve is missing either of those parts then Bob will not be able to decrypt the message at all; it will be corrupt.

That's assuming you're doing signed encryption (i.e. the sender's public key is used when decrypting the message).  For unsigned encryption then yes, anyone can use Bob's public key, encrypt a message, and send it to him, claiming to be Alice.

But that's really no different than someone impersonating Alice with an unencrypted message.  In order to thwart that kind of impersonation you should use signed encryption.

---

### Post by ki4jgt on 2011-05-16
Where can I find a good tutorial on how to write my own RSA function?

---

